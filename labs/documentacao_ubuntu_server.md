# Documentação de Coleta de Informações — Ubuntu Server

## Visão Geral

Este guia apresenta comandos administrativos para coletar informações de infraestrutura em servidores Linux Ubuntu, organizados por categorias e subcategorias.

---

# 🖥️ 1. Hardware do Servidor

## 🧠 1.1 Processador (CPU)

| Informação | Comando |
|---|---|
| Informações completas da CPU | `lscpu` |
| Detalhes avançados | `cat /proc/cpuinfo` |
| Uso em tempo real | `top` |
| Monitoramento avançado | `htop` |
| Arquitetura do sistema | `uname -m` |

### Exemplo

```bash
lscpu
```

---

## 🧮 1.2 Memória RAM

| Informação | Comando |
|---|---|
| Resumo da memória | `free -h` |
| Informações detalhadas | `cat /proc/meminfo` |
| Slots físicos da RAM | `sudo dmidecode -t memory` |
| Uso em tempo real | `top` ou `htop` |

### Exemplo

```bash
free -h
```

---

## 💽 1.3 Hard Disk (Discos)

| Informação | Comando |
|---|---|
| Listar discos | `lsblk` |
| Espaço utilizado | `df -h` |
| Informações detalhadas | `sudo fdisk -l` |
| Identificar UUID | `blkid` |

### Exemplo

```bash
lsblk
```

---

## 📁 1.4 Partições

| Informação | Comando |
|---|---|
| Partições montadas | `df -hT` |
| Estrutura de partições | `lsblk -f` |
| Tabela de partições | `sudo parted -l` |

### Exemplo

```bash
df -hT
```

---

# 🌐 2. Rede

## 🛜 2.1 Placas de Rede

| Informação | Comando |
|---|---|
| Interfaces de rede | `ip addr` |
| Informações resumidas | `ip -br addr` |
| Hardware da NIC | `sudo lshw -class network` |
| Interfaces disponíveis | `ls /sys/class/net` |

### Exemplo

```bash
ip -br addr
```

---

## ⚙️ 2.2 Configurações de Rede (DHCP ou Estático)

### Verificar configuração Netplan

```bash
cat /etc/netplan/*.yaml
```

### DHCP habilitado

```yaml
network:
  version: 2
  ethernets:
    ens33:
      dhcp4: true
```

### IP Estático

```yaml
network:
  version: 2
  ethernets:
    ens33:
      dhcp4: false
      addresses:
        - 192.168.1.100/24
      gateway4: 192.168.1.1
      nameservers:
        addresses:
          - 8.8.8.8
```

### Aplicar configurações

```bash
sudo netplan apply
```

---

## 🌍 2.3 DNS e Gateway

| Informação | Comando |
|---|---|
| Gateway padrão | `ip route` |
| DNS configurado | `cat /etc/resolv.conf` |
| Teste de conectividade | `ping 8.8.8.8` |

---

# ⚙️ 3. Serviços do Sistema

## 🔧 3.1 Serviços Instalados

| Informação | Comando |
|---|---|
| Pacotes instalados | `dpkg -l` |
| Serviços systemd | `systemctl list-unit-files --type=service` |

---

## ▶️ 3.2 Serviços Ativos

| Informação | Comando |
|---|---|
| Serviços ativos | `systemctl list-units --type=service --state=running` |
| Status de serviço específico | `systemctl status nginx` |
| Verificar boot automático | `systemctl is-enabled nginx` |

---

# 🔄 4. Atualizações do Sistema

## 📦 4.1 Atualizações Disponíveis

| Informação | Comando |
|---|---|
| Atualizar lista de pacotes | `sudo apt update` |
| Verificar upgrades | `apt list --upgradable` |
| Atualizar sistema | `sudo apt upgrade -y` |
| Atualização completa | `sudo apt full-upgrade -y` |

---

## 🧹 4.2 Limpeza do Sistema

| Informação | Comando |
|---|---|
| Remover pacotes obsoletos | `sudo apt autoremove -y` |
| Limpar cache | `sudo apt clean` |

---

# 📊 5. Script Básico de Inventário

```bash
#!/bin/bash

echo "==============================="
echo "INVENTÁRIO DO SERVIDOR"
echo "==============================="

echo ""
echo "### HOSTNAME ###"
hostname

echo ""
echo "### CPU ###"
lscpu | grep "Model name"

echo ""
echo "### MEMÓRIA ###"
free -h

echo ""
echo "### DISCO ###"
df -h

echo ""
echo "### PLACAS DE REDE ###"
ip -br addr

echo ""
echo "### SERVIÇOS ATIVOS ###"
systemctl list-units --type=service --state=running

echo ""
echo "### ATUALIZAÇÕES DISPONÍVEIS ###"
apt list --upgradable
```

---

# ✅ Resumo Executivo

| Categoria | Principais Comandos |
|---|---|
| CPU | `lscpu` |
| RAM | `free -h` |
| Disco | `lsblk`, `df -h` |
| Rede | `ip addr` |
| DHCP/Estático | `cat /etc/netplan/*.yaml` |
| Serviços | `systemctl` |
| Atualizações | `apt update` |

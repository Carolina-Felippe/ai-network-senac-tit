# Documentação do Servidor Ubuntu Docker

Este documento apresenta um resumo técnico padronizado do servidor Ubuntu Server 24.04.4 LTS com Docker-CE, organizado em categorias de fácil leitura.

## 1. Informações Gerais do Servidor

| Categoria | Descrição | Configuração |
|-----------|-----------|--------------|
| 🖥️ Sistema Operacional | Nome e versão | Ubuntu 24.04.4 LTS |
| 🧩 Distribuição | ID e codename | ubuntu / noble |
| 🗂️ Kernel | Versão do kernel Linux | 6.8.0-107-generic |
| 🏷️ Nome do host | Hostname do servidor | ctlinux01 |
| 🖧 Virtualização | Tipo e fornecedor | VirtualBox / Oracle |
| 📊 Uptime | Tempo ligado | 2h11 |
| 👥 Usuários conectados | Sessões ativas | 11 |
| 📈 Load average | Carga média | 0.02, 0.04, 0.00 |

> Esta seção mostra que o servidor é uma máquina virtual Ubuntu atualizada, rodando há pouco tempo e com baixa carga de processamento.

## 2. Informações de Hardware do Servidor

| Categoria | Descrição | Configuração |
|-----------|-----------|--------------|
| 🧠 Processador | Modelo e fabricante | Intel(R) Core(TM) i7-14700K |
| ⚙️ Cores e threads | CPU(s) e topologia | 2 CPUs, 2 cores físicos, 1 socket |
| 🧬 Arquitetura | Tipo de CPU | x86_64 |
| 💾 Memória RAM | Total disponível | 3.9 GB |
| 🔁 Swap | Total disponível | 3.9 GB |
| 🗃️ Cache | Somatório de caches | L1d 64 KiB, L1i 128 KiB, L2 8 MiB, L3 66 MiB |
| 🛡️ Virtualização | Recursos do processador | Hypervisor KVM disponível |

> O servidor tem recursos modestos de hardware, suficiente para cargas de teste ou serviços leves, mas não é um ambiente de alto desempenho.

## 3. Partições e Armazenamento

| Categoria | Descrição | Configuração |
|-----------|-----------|--------------|
| 💽 Disco físico | Capacidade total | 50 GB |
| 📂 Partição /boot | Tamanho | 2 GB |
| 📂 Partição raiz | Tamanho | 48 GB |
| 📊 Uso do root | Ocupação do sistema | 19% usado (8.5 GB de 47 GB) |
| 🧾 Espaço disponível | /boot e / | 89% livre no root, 89% livre em /boot |

> O armazenamento principal está longe do limite, o que é bom para manutenção e atualizações no servidor.

## 4. Informações de Rede do Servidor

| Categoria | Descrição | Configuração |
|-----------|-----------|--------------|
| 🌐 Interface principal | Interface de rede | enp0s3 |
| 🧾 IPv4 | Endereço e máscara | 10.24.82.200/24 |
| 🔌 Gateway padrão | Rota padrão | 10.24.82.1 via enp0s3 |
| 🐳 Rede Docker | Bridge Docker | 172.17.0.1/16 |
| 🧭 DNS | Servidores DNS ativos | 8.8.8.8, 8.8.4.4 |
| 🚪 Portas em escuta | Serviços acessíveis | 22, 53, 9000 |

> O servidor está conectado a uma rede local com IP fixo e usa DNS público. A presença de Docker cria uma rede interna adicional separada.

## 5. Informações de Serviços e Processos

| Categoria | Descrição | Configuração |
|-----------|-----------|--------------|
| 🐳 Docker | Runtime ativo | docker.service e containerd.service ativos |
| 🧱 Portainer | Gerenciamento de containers | portainer.service ativo |
| 🔒 SSH | Acesso remoto | ssh.service ativo na porta 22 |
| 📨 Logs | Sistema de logs | rsyslog.service ativo |
| 🌐 Rede | Gerenciamento de rede | systemd-networkd.service ativo |
| 🌍 DNS local | Resolução de nomes | systemd-resolved.service ativo |
| ⏲️ Sincronização de horário | NTP | systemd-timesyncd.service ativo |

> Os serviços essenciais de containerização, rede e acesso remoto estão em execução, indicando que o servidor é usado para rodar containers e administração remota.

## 6. Informações de Softwares e Atualização

| Categoria | Descrição | Configuração |
|-----------|-----------|--------------|
| 🔄 Atualizações disponíveis | Total de pacotes listados | 31 pacotes |
| 🐳 Docker | Pacotes Docker atualizáveis | docker-ce, docker-ce-cli, docker-ce-rootless-extras, docker-buildx-plugin, docker-compose-plugin |
| 📦 Systemd | Componentes de sistema atualizáveis | systemd, systemd-resolved, systemd-sysv, systemd-timesyncd, libsystemd0, udev |
| 🛠️ Ferramentas de sistema | Atualizações importantes | coreutils, binutils, lshw, fwupd, nftables, netplan |
| 🧩 Outros | Pacotes adicionais | ubuntu-drivers-common, sosreport |

> Há atualizações pendentes importantes, especialmente para Docker e componentes do sistema. Recomenda-se agendar manutenção para aplicar essas atualizações com segurança.

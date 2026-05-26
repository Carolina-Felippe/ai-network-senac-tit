# Guia de Importação da Máquina Virtual Ubuntu Server 22.04.4 LTS no Oracle VirtualBox 7.2

## Curso Livre de Inteligência Artificial Voltada a Redes de Computadores
### SENAC São Paulo – Unidade Lapa Tito

---

# Objetivo
Importar a imagem virtual `UbuntuServer-OnPremises.ova` no Oracle VirtualBox 7.2, configurar a rede em modo Bridge (Ponte) utilizando a rede local `10.24.82.0/24` do laboratório e iniciar a máquina virtual para acesso remoto via SSH.

---

# Pré-Requisitos

Antes de iniciar, confirme os seguintes itens:

✅ Sistema Operacional: Microsoft Windows 11  
✅ Oracle VirtualBox 7.2 instalado  
✅ Arquivo da máquina virtual disponível em:

```text
Downloads\UbuntuServer-OnPremises.ova
```

✅ Rede cabeada conectada no laboratório  
✅ Permissão de acesso ao computador do laboratório  

---

# Etapa 1 — Abrir o Oracle VirtualBox

## Passos

1. Clique no menu **Iniciar** do Windows.
2. Pesquise por:

```text
Oracle VirtualBox
```

3. Clique em:

🟦 **Oracle VirtualBox**

---

# Etapa 2 — Importar a Máquina Virtual OVA

## Passos

1. No menu superior do VirtualBox clique em:

📂 **Arquivo → Importar Appliance**

---

2. Na janela de importação clique em:

📁 **Escolher Arquivo**

---

3. Navegue até:

```text
Downloads\UbuntuServer-OnPremises.ova
```

---

4. Selecione o arquivo:

🟧 `UbuntuServer-OnPremises.ova`

5. Clique em:

✅ **Abrir**

---

6. Clique em:

➡️ **Próximo**

---

7. Revise as configurações da máquina virtual.

⚠️ Não altere as configurações padrão fornecidas pelo professor.

---

8. Clique em:

✅ **Finalizar**

---

9. Aguarde a importação da máquina virtual.

⏳ Esse processo pode levar alguns minutos.

---

# Etapa 3 — Configurar Rede em Modo Bridge (Ponte)

## Objetivo
Permitir que a máquina virtual receba um endereço IP da rede local do laboratório `10.24.82.0/24`.

---

## Passos

1. No Oracle VirtualBox selecione a máquina virtual:

🖥️ `UbuntuServer-OnPremises`

---

2. Clique em:

⚙️ **Configurações**

---

3. Clique na opção:

🌐 **Rede**

---

4. Em:

```text
Adaptador 1
```

Marque:

✅ **Habilitar Placa de Rede**

---

5. Em:

```text
Conectado a:
```

Selecione:

🌉 **Placa em modo Bridge (Ponte)**

---

6. Em:

```text
Nome:
```

Selecione a placa de rede física cabeada do laboratório.

Normalmente aparece como:

```text
Intel Ethernet
```

ou

```text
Realtek PCIe
```

⚠️ Não selecionar Wi‑Fi.

---

7. Clique em:

✅ **OK**

---

# Etapa 4 — Iniciar a Máquina Virtual

## Passos

1. Selecione a máquina virtual:

🖥️ `UbuntuServer-OnPremises`

---

2. Clique em:

▶️ **Iniciar**

---

3. Aguarde o carregamento do Ubuntu Server.

---

# Etapa 5 — Verificar Endereço IP da Máquina Virtual

## Objetivo
Confirmar que a máquina virtual recebeu um IP da rede do laboratório.

---

## Passos

1. Faça login no Ubuntu Server.

---

2. Execute o comando:

```bash
ip addr
```

ou

```bash
ip a
```

---

3. Localize a interface de rede.

Normalmente:

```text
enp0s3
```

ou

```text
eth0
```

---

4. Verifique se recebeu um IP semelhante a:

```text
10.24.82.X
```

Exemplo:

```text
10.24.82.150
```

✅ Isso indica que o modo Bridge está funcionando corretamente.

---

# Etapa 6 — Verificar Serviço SSH

## Objetivo
Garantir que o acesso remoto via SSH esteja ativo.

---

## Passos

1. No Ubuntu Server execute:

```bash
sudo systemctl status ssh
```

---

2. Verifique se aparece:

```text
active (running)
```

✅ Isso indica que o SSH está ativo.

---

# Etapa 7 — Testar Acesso Remoto SSH

## Objetivo
Acessar remotamente a máquina virtual.

---

## Passos

1. No Windows abra:

🖥️ **PowerShell**

ou

🖥️ **Prompt de Comando (CMD)**

---

2. Execute o comando:

```bash
ssh usuario@IP_DA_VM
```

Exemplo:

```bash
ssh aluno@10.24.82.150
```

---

3. Caso apareça a mensagem:

```text
Are you sure you want to continue connecting?
```

Digite:

```text
yes
```

---

4. Informe a senha do usuário.

✅ Acesso remoto realizado com sucesso.

---

# Resumo Final

## Processo realizado

✅ Importação da imagem `.ova`  
✅ Configuração da rede em modo Bridge  
✅ Integração com rede local `10.24.82.0/24`  
✅ Inicialização da máquina virtual  
✅ Verificação do IP  
✅ Teste de acesso remoto SSH  

---

# Observações Importantes

⚠️ Sempre utilizar a placa de rede cabeada do laboratório.  
⚠️ Não alterar configurações da máquina virtual sem orientação do professor.  
⚠️ O endereço IP pode mudar conforme o DHCP da rede do laboratório.  
⚠️ Caso a VM não receba IP da rede `10.24.82.0/24`, revisar a configuração Bridge.

---

# Fim do Guia


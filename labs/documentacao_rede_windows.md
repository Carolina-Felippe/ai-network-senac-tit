# 📘 Documentação de Rede — Estação Windows

---

# 🖥️ 1. Informações Gerais do Host

| 🏷️ Propriedade | 📄 Valor |
|---|---|
| Nome do Host | `TIT0728108W11-1` |
| Domínio DNS Primário | `senacsp.edu.br` |
| Tipo de Nó | Híbrido |
| Roteamento IP | Não habilitado |
| Proxy WINS | Não habilitado |
| Lista de Pesquisa DNS | `senacsp.edu.br` |

---

## 📖 Resumo Explicativo

Esta seção identifica o computador na rede corporativa.

- **Nome do Host:** é o nome único do computador dentro da rede.
- **DNS Primário:** define o domínio utilizado para localizar serviços e dispositivos internos.
- **Tipo de Nó Híbrido:** método utilizado pelo Windows para resolução de nomes na rede.
- **Roteamento IP Desabilitado:** indica que o computador não funciona como roteador.
- **WINS Desabilitado:** serviço antigo de resolução de nomes NetBIOS não está sendo utilizado.

---

# 🌐 2. Interfaces de Rede Detectadas

| 🔢 ID | 🧩 Interface | 🖧 Tipo |
|---|---|---|
| 8 | VirtualBox Host-Only Ethernet Adapter | Virtual |
| 12 | Intel(R) Ethernet Connection (17) I219-LM | Física |
| 1 | Software Loopback Interface 1 | Loopback |

---

## 📖 Resumo Explicativo

O computador possui três interfaces principais:

- **Interface Física Intel:** conexão real utilizada para acessar a rede da empresa e internet.
- **VirtualBox Host-Only:** utilizada para comunicação entre máquinas virtuais.
- **Loopback:** interface interna do sistema operacional usada para testes locais.

---

# 🔗 3. Associação MAC Address ↔ Transporte TCP/IP

| 🖥️ Endereço MAC | 🚚 Nome de Transporte |
|---|---|
| `D8-43-AE-E2-45-23` | `\\Device\\Tcpip_{BCF1DF38-5D19-42B7-A95F-8F671FCDAD23}` |
| `0A-00-27-00-00-08` | `\\Device\\Tcpip_{94C3DFC7-8CAC-4FA7-B97D-A2519F55808F}` |

---

## 📖 Resumo Explicativo

- O **Endereço MAC** é o identificador físico único de cada placa de rede.
- O **Nome de Transporte TCP/IP** representa o identificador interno utilizado pelo Windows para gerenciar a comunicação da interface de rede.

Cada adaptador de rede possui um MAC Address exclusivo.

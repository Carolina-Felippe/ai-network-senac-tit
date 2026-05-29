# Documentação Técnica — Otimização e Hardening de Serviços Linux Ubuntu Server

## Visão Geral do Ambiente

| Serviço | Porta | Tecnologia | Status |
|---|---|---|---|
| OpenSSH Server | 22/TCP | SSH | Ativo |
| Apache2 Server | 80/TCP | Web Server | Ativo |
| GLPI Help Desk | 8888/TCP | Aplicação Web PHP | Ativo |
| Apache Tomcat 11 | 8080/TCP | Java Application Server | Ativo |
| MySQL Server | 3306/TCP | Banco de Dados | Ativo |
| Grafana Server | 3000/TCP | Observabilidade | Ativo |
| Prometheus Server | 9091/TCP | Monitoramento | Ativo |
| Node Exporter | 9100/TCP | Métricas do Sistema | Ativo |
| WordPress CMS | Não identificado | CMS PHP | Não detectado |

---

# 1. Hardening — OpenSSH Server

## Melhorias Recomendadas

| Categoria | Recomendação | Benefício |
|---|---|---|
| Autenticação | Desabilitar login root remoto (`PermitRootLogin no`) | Reduz ataques diretos ao root |
| Segurança | Utilizar autenticação por chave SSH | Elimina brute force por senha |
| Rede | Alterar porta padrão 22 | Reduz scans automatizados |
| Controle de acesso | Permitir apenas usuários específicos (`AllowUsers`) | Minimiza exposição |
| Proteção | Instalar Fail2Ban | Bloqueio automático de IPs maliciosos |

### Configuração Recomendada

```bash
/etc/ssh/sshd_config
```

```bash
PermitRootLogin no
PasswordAuthentication no
PubkeyAuthentication yes
AllowUsers administrador
MaxAuthTries 3
```

---

# 2. Hardening — Apache2 Server

## Melhorias Recomendadas

| Categoria | Recomendação | Benefício |
|---|---|---|
| SSL/TLS | Implementar HTTPS com TLS 1.2+ | Comunicação segura |
| Headers HTTP | Adicionar headers de segurança | Mitiga XSS e Clickjacking |
| Diretórios | Desabilitar directory listing | Impede exposição de arquivos |
| WAF | Instalar ModSecurity | Proteção contra ataques web |

### Configuração Recomendada

```apache
ServerTokens Prod
ServerSignature Off
TraceEnable Off
```

---

# 3. Hardening — Apache Tomcat Server

## Melhorias Recomendadas

| Categoria | Recomendação | Benefício |
|---|---|---|
| Manager App | Restringir acesso ao `/manager` | Evita administração indevida |
| Usuários | Remover contas padrão | Reduz comprometimento |
| HTTPS | Habilitar SSL/TLS | Comunicação segura |
| Deploy | Remover aplicações padrão | Reduz superfície de ataque |

---

# 4. Hardening — MySQL Server

## Melhorias Recomendadas

| Categoria | Recomendação | Benefício |
|---|---|---|
| Segurança inicial | Executar `mysql_secure_installation` | Remove configurações inseguras |
| Root remoto | Desabilitar acesso root remoto | Reduz exposição |
| Rede | Bind apenas em localhost | Restringe acesso externo |
| Backup | Implementar backups automatizados | Continuidade operacional |

### Configuração Recomendada

```ini
bind-address = 127.0.0.1
local-infile = 0
symbolic-links = 0
```

---

# 5. Hardening — Grafana Server

## Melhorias Recomendadas

| Categoria | Recomendação | Benefício |
|---|---|---|
| Login padrão | Alterar senha admin | Evita acesso indevido |
| HTTPS | Habilitar TLS | Proteção de credenciais |
| Autenticação | Integrar LDAP/OAuth | Controle centralizado |
| Usuários | Aplicar RBAC | Controle granular |

---

# 6. Hardening — Prometheus Server

## Melhorias Recomendadas

| Categoria | Recomendação | Benefício |
|---|---|---|
| Rede | Restringir acesso à porta 9091 | Segurança |
| HTTPS | Habilitar TLS | Comunicação segura |
| Firewall | Permitir somente IPs autorizados | Segmentação |

---

# 7. Hardening — Node Exporter

## Melhorias Recomendadas

| Categoria | Recomendação | Benefício |
|---|---|---|
| Rede | Bind apenas localhost | Reduz exposição |
| Firewall | Restringir porta 9100 | Controle de acesso |
| TLS | Habilitar HTTPS | Proteção de tráfego |

---

# 8. Hardening — GLPI Help Desk

## Observação Técnica

O GLPI está publicado na porta:

```text
8888/TCP
```

Sendo servido pelo Apache2.

## Melhorias Recomendadas

| Categoria | Recomendação | Benefício |
|---|---|---|
| HTTPS | Implementar SSL/TLS | Segurança de credenciais |
| Plugins | Remover plugins não utilizados | Reduz riscos |
| Uploads | Restringir tipos de arquivos | Mitiga malware |
| Backup | Backup diário do banco e arquivos | Recuperação |

---

# 9. Hardening — WordPress CMS

## Observação Técnica

O WordPress não foi identificado:
- Como serviço systemd;
- Como porta dedicada;
- Nem explicitamente nos processos ativos.

## Melhorias Recomendadas

| Categoria | Recomendação | Benefício |
|---|---|---|
| Atualizações | Atualizar Core, temas e plugins | Correção de vulnerabilidades |
| Segurança | Instalar WAF (Wordfence/ModSecurity) | Proteção |
| HTTPS | Forçar SSL/TLS | Segurança |
| XML-RPC | Desabilitar se não utilizado | Reduz ataques |

---

# Recomendações Gerais do Servidor Ubuntu

| Categoria | Recomendação |
|---|---|
| Firewall | Implementar UFW |
| IDS/IPS | Instalar Wazuh ou Fail2Ban |
| Logs | Centralizar logs |
| Atualizações | Automatizar updates de segurança |
| Auditoria | Habilitar auditd |
| Antimalware | Instalar ClamAV |

---

# Firewall Recomendado (UFW)

```bash
ufw default deny incoming
ufw default allow outgoing

ufw allow 22/tcp
ufw allow 80/tcp
ufw allow 443/tcp
ufw allow 3000/tcp
ufw allow 8080/tcp
ufw allow 9091/tcp

ufw enable
```

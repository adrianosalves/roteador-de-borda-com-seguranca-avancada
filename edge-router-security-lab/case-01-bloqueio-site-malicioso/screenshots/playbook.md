
# Playbook — Caso 01: Bloqueio de Site Malicioso (Web Filter)

**Stack**: Roteador de Borda (Filtro Web)  
**Objetivo**: Bloquear acesso a domínios/URLs maliciosos sem impactar tráfego legítimo.  
**Ambiente**: LAB (WAN/DMZ/LAN)  
**Privacidade**: Todas as informações sensíveis foram **anonimizadas** (hostnames, IPs, domínios, usuários, IDs). Veja `screenshots/DISCLAIMER.md`.

![01 Contexto](https://github.com/adrianosalves/roteador-de-borda-com-seguranca-avancada/blob/main/edge-router-security-lab/case-01-bloqueio-site-malicioso/screenshots/01-contexto.png?raw=true)

---

## 1) Contexto
- Categoria alvo: Malware / Phishing
- Domínio/URL (anonimizado): `malicious.example`
- Política: Bloqueio por categoria + exceções necessárias

![regra bloqueio sites](https://github.com/adrianosalves/roteador-de-borda-com-seguranca-avancada/blob/main/edge-router-security-lab/case-01-bloqueio-site-malicioso/screenshots/02.1-configuracao.png)

---

## 2) Configuração Aplicada
1. Habilitar Web Filter e base de categorias.
2. Criar política:
   - Escopo: LAN→WAN
   - Ação: **Block** para Malware/Phishing
   - Exceções (se necessário): atualizações legítimas

![02.2 Configuracao](https://github.com/adrianosalves/roteador-de-borda-com-seguranca-avancada/blob/main/edge-router-security-lab/case-01-bloqueio-site-malicioso/screenshots/02.2-configuracao.png?raw=true)
---

## 3) Validação
- Acessar `https://malicious.example` → **bloqueado**  
- Acessar sites confiáveis → **permitidos**

![03 Validacao](https://github.com/adrianosalves/roteador-de-borda-com-seguranca-avancada/blob/main/edge-router-security-lab/case-01-bloqueio-site-malicioso/screenshots/03-validacao.png)

---

## 4) Logs/Relatórios
- Verificar evento categorizado como bloqueio por Web Filter.
- Registrar timestamp e host afetado.

![04 1 logs](https://github.com/adrianosalves/roteador-de-borda-com-seguranca-avancada/blob/main/edge-router-security-lab/case-01-bloqueio-site-malicioso/screenshots/04.1-logs.png)

![04 2 logs](https://github.com/adrianosalves/roteador-de-borda-com-seguranca-avancada/blob/main/edge-router-security-lab/case-01-bloqueio-site-malicioso/screenshots/04.2-logs.png)

---

## 5) Lições Aprendidas
- Manter categorias críticas em **Block**.
- Monitorar falsos positivos e ajustar allowlist com revisão.
- Considerar **SSL inspection** (se disponível) e impacto

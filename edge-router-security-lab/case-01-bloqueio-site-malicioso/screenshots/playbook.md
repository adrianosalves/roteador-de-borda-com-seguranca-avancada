
# Playbook — Caso 01: Bloqueio de Site Malicioso (Web Filter)

**Stack**: Roteador de Borda (Filtro Web)  
**Objetivo**: Bloquear acesso a domínios/URLs maliciosos sem impactar tráfego legítimo.  
**Ambiente**: LAB (WAN/DMZ/LAN)  
**Privacidade**: Todas as informações sensíveis foram **anonimizadas** (hostnames, IPs, domínios, usuários, IDs). Veja `screenshots/DISCLAIMER.md`.

---

## 1) Contexto
- Categoria alvo: Malware / Phishing
- Domínio/URL (anonimizado): `malicious.example`
- Política: Bloqueio por categoria + exceções necessárias


---

## 2) Configuração Aplicada
1. Habilitar Web Filter e base de categorias.
2. Criar política:
   - Escopo: LAN→WAN
   - Ação: **Block** para Malware/Phishing
   - Exceções (se necessário): atualizações legítimas

![regra bloqueio sites](https://github.com/adrianosalves/roteador-de-borda-com-seguranca-avancada/blob/main/edge-router-security-lab/case-01-bloqueio-site-malicioso/screenshots/02.1-configuracao.png.png)

---

## 3) Validação
- Acessar `https://malicious.example` → **bloqueado**  
- Acessar sites confiáveis → **permitidos**

![03 Validacao](https://github.com/adrianosalves/roteador-de-borda-com-seguranca-avancada/blob/main/edge-router-security-lab/case-01-bloqueio-site-malicioso/screenshots/03-validacao.png)

---

## 4) Logs/Relatórios
- Verificar evento categorizado como bloqueio por Web Filter.
- Registrar timestamp e host afetado.

![url malicioso](https://github.com/adrianosalves/roteador-de-borda-com-seguranca-avancada/blob/main/edge-router-security-lab/case-01-bloqueio-site-malicioso/screenshots/detection-url-maliciosos.png)

---

## 5) Lições Aprendidas
- Manter categorias críticas em **Block**.
- Monitorar falsos positivos e ajustar allowlist com revisão.
- Considerar **SSL inspection** (se disponível) e impacto


# Playbook — Caso 02: Alerta IDS para Tráfego Suspeito

**Stack**: Roteador de Borda (IDS)  
**Objetivo**: Detectar tráfego anômalo/sondagem sem bloqueio automático (modo IDS).  
**Ambiente**: LAB (Suricata/ET Open, se aplicável)  
**Privacidade**: Todas as informações sensíveis foram **anonimizadas**. Veja `screenshots/DISCLAIMER.md`.

---

## 1) Contexto
- Assinatura/Regra: `ET SCAN Nmap - OS Detection` (exemplo)
- Interface monitorada: LAN/WAN
- Perfil: Balanced (ruído x visibilidade)

![01 contexto](https://github.com/adrianosalves/roteador-de-borda-com-seguranca-avancada/blob/main/edge-router-security-lab/case-02-alerta-ids-trafego-suspeito/screenshots/01-contexto.png?raw=true)

**Screenshot**  
`screenshots/01-contexto.png`  
> **Anonimizar**: nomes de interface, IPs reais, hostname do roteador.

---

## 2) Configuração IDS
1. Habilitar IDS e conjunto de regras (ET Open).
2. Ajustar performance (pattern matcher).
3. Definir logging e retenção.



**Screenshot**  
`screenshots/02-configuracao.png`  
> **Anonimizar**: IDs de regras, nomes internos, endereços IP.


---

## 3) Validação
- Simular scan controlado em LAB.
- Confirmar geração do alerta (assinatura, origem/destino).



**Screenshot**  
`screenshots/03-validacao.png`  
> **Anonimizar**: IP origem (ex.: `192.168.10.50`), IP destino (`192.168.10.1`/`8.8.8.8`), MAC addresses.

---

## 4) Logs/Alertas
- Revisar evento: severidade, timestamp, assinatura.
- Exportar evidência para documentação.

**Screenshot**  
`screenshots/04-logs.png`  
> **Anonimizar**: nomes de usuário, domínios, GUIDs/IDs.

---

## 5) Ações e Lições
- Triage para falso positivo vs. atividade legítima.
- Regras barulhentas → tuning/threshold.
- Considerar mover assinaturas críticas para **IPS/Drop** em produção.

---


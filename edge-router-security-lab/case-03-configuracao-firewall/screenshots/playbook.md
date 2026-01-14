
# Playbook — Caso 03: Configuração de Firewall (Segmentação e Bloqueio)

**Stack**: Roteador de Borda (Firewall Statefull)  
**Objetivo**: Aplicar princípio de **menor privilégio**, segmentar e proteger perímetro.  
**Ambiente**: LAB (Zonas LAN/DMZ/WAN)  
**Privacidade**: Informações sensíveis **anonimizadas**. Veja `screenshots/DISCLAIMER.md`.

---

## 1) Contexto
- Zonas: LAN (192.168.10.0/24), WAN (203.0.113.0/24 fictício)
- Política: Deny by default + explicit allows
- Logs: habilitar em regras críticas

**Screenshot**  
`screenshots/01-contexto.png`  
> **Anonimizar**: sub-redes reais, nomes de objetos, hostname do roteador.

---

## 2) Regras Criadas
1. **Permitir**: LAN→WAN (HTTP/HTTPS/DNS)
2. **Bloquear**: inbound não solicitado (WAN→LAN)
3. Ativar anti-spoofing/stateful inspection

ASUS router uses following methods to detect suspicious attack.
1. SYN-Flooding Protection : Only allow one TCP/SYN packet to pass per second.
2. Port Scanner Protection : Protect router from port scanning via external port scan tool
3. Ping of Death : Only allow one ICMP packet(type 8) to pass per second or drop the length of ICMP packet over 65535.

Even if this feature can protect it from suspicious packets pass, the home network still have chance to be paralyzed by DDoS bonnet attack due to bandwidth can't effort massive packets. 
DoS protection can help system to be restored after paralyzing by DDoS attacks and at least keep LAN to LAN service working if system is not overloading.



**Screenshot**  
`screenshots/02-configuracao.png`  
> **Anonimizar**: comentários internos, IDs de regras, nomes de grupos.

---

## 3) Validação
- Testar tráfego permitido (HTTP/HTTPS).
- Testar bloqueios (ping/SSH onde não permitido).
- Checar logs de `accept/drop`.

**Screenshot**  
`screenshots/03-validacao.png`  
> **Anonimizar**: IPs e hostnames dos clientes (ex.: `CLIENT-01`, `192.168.10.25`).

---

## 4) Logs/Relatórios
- Registrar eventos de bloqueio relevantes com timestamp.
- Exportar logs para documentação.

**Screenshot**  
`screenshots/04-logs.png`  
> **Anonimizar**: IPs, domínios internos, MAC address, IDs.

---

## 5) Manutenção e Lições
- Exceções temporárias com data de expiração.
- Revisões periódicas: regras órfãs e shadowed.
- Padronizar nomeação/comentários nas regras.

---

# 🖧 Projeto de Rede — Loja de Varejo com Controle de Estoque e CFTV

**Disciplina:** Computer Network  
**Instituição:** UniFECAF  
**Aluno:** Rosandro  
**Ano:** 2026

---

## 📋 Sobre o Projeto

Este repositório contém o projeto final da disciplina **Computer Network**, que consiste no planejamento e design de uma rede de computadores para a loja de roupas da cliente **Ana**.

A rede foi projetada para suportar simultaneamente:

- **3 caixas registradoras** (PDV)
- **1 maquininha de cartão** de crédito/débito
- **1 impressora** de rede
- **2 tablets** de gestão (Wi-Fi)
- **1 servidor local** (estoque + gravações CFTV)
- **4 câmeras IP** de segurança (CFTV)

---

## 📦 Arquivos do Repositório

| Arquivo | Descrição |
|---|---|
| `Relatorio_Rede_Loja_Ana.pdf` | Relatório teórico completo (Parte 1 da entrega) |
| `Diagrama_Rede_Loja_Ana.drawio` | Diagrama de rede para importar no Draw.io (Parte 2 da entrega) |
| `Roteiro_Video_Pitch.md` | Roteiro completo do vídeo pitch de 4 minutos (Parte 3 da entrega) |

---

## 🏗️ Arquitetura da Rede

### Topologia: Estrela

Todos os dispositivos se conectam ao switch central, garantindo isolamento de falhas e facilidade de gerenciamento.

```
INTERNET (WAN)
     │
  [MODEM]
     │  Ethernet Cat6
[ROTEADOR/FIREWALL]
  Gateway: 192.168.1.1
  DHCP | DNS | VLANs
     │  Gigabit Trunk
 [SWITCH 24 portas]
  ┌───────┼────────┐
  │       │        │
VLAN 10  VLAN 20  VLAN 30
(PDV)   (CFTV)  (Gestão)
```

---

## 🔀 Segmentação por VLANs

| VLAN | Nome | Dispositivos | Faixa IP |
|---|---|---|---|
| **VLAN 10** | PDV | 3 Caixas, Maquininha, Impressora | 192.168.10.0/24 |
| **VLAN 20** | CFTV | 4 Câmeras IP, Servidor | 192.168.20.0/24 |
| **VLAN 30** | Gestão | 2 Tablets (Wi-Fi) | 192.168.30.0/24 |

---

## 🔢 Endereçamento IP (Resumo)

| Dispositivo | IP | Tipo |
|---|---|---|
| Roteador (Gateway) | 192.168.1.1 | Fixo |
| Servidor Local | 192.168.20.2 | Fixo |
| Caixa 1 | 192.168.10.10 | Fixo |
| Caixa 2 | 192.168.10.11 | Fixo |
| Caixa 3 | 192.168.10.12 | Fixo |
| Maquininha | 192.168.10.13 | Fixo |
| Impressora | 192.168.10.14 | Fixo |
| Câmera 1–4 | 192.168.20.10–13 | Fixo |
| Tablets | 192.168.30.101–150 | DHCP |

**DNS:** 8.8.8.8 (primário) / 8.8.4.4 (secundário)  
**Máscara:** 255.255.255.0 (/24) em todas as VLANs

---

## 🔒 Segurança

- Isolamento de tráfego por VLANs (PDV protegido por PCI-DSS)
- Firewall no roteador com regras entre segmentos
- Wi-Fi com WPA3 para a rede de gestão
- Servidor com backup periódico das gravações
- Retenção mínima de 30 dias de CFTV

---

## 🚀 Escalabilidade

A arquitetura suporta expansão sem substituição de equipamentos:
- Novas câmeras IP: apenas conectar na VLAN 20
- Mais caixas PDV: apenas conectar na VLAN 10
- Segunda filial: VPN site-to-site via roteador
- Migração para ERP em nuvem: conexão WAN já disponível

---

## 🛠️ Como Abrir o Diagrama

1. Acesse [app.diagrams.net](https://app.diagrams.net)
2. Clique em **File → Open from → Device**
3. Selecione o arquivo `Diagrama_Rede_Loja_Ana.drawio`
4. O diagrama abrirá com todos os dispositivos, IPs e VLANs coloridas

---

## 📽️ Vídeo Pitch

> Link do vídeo: *(adicionar após publicação no YouTube)*

---

*Projeto desenvolvido para fins acadêmicos — UniFECAF 2026*

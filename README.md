# 🏠 Homelab de Infraestrutura, Redes e Segurança da Informação

Ambiente pessoal de laboratório dedicado ao estudo prático e aplicado de administração de sistemas, redes, automação e segurança da informação. Construído do zero em hardware físico, com foco em resolver problemas reais de infraestrutura — não apenas seguir tutoriais.

##  Visão Geral

O homelab roda sobre **Ubuntu Server**, hospedando serviços de rede, armazenamento e segurança em containers Docker, em um ambiente controlado e isolado.

**Hardware:** HP G42 (notebook reaproveitado como servidor com seu incrivel i5 de 1ª geração) 

##  Arquitetura

┌──────────────────────────────────────────────┐
│              HP G42 - Ubuntu Server          │
│                                              │
│              ┌───────────────┐               │
│              │    Docker /   │               │
│              │ Docker Compose│               │
│              └───────┬───────┘               │
│                      │                       │
│      ┌───────────────┼───────────────┐       │
│      │               │               │       │
│ ┌─────────┐    ┌─────────────┐  ┌──────────┐ │
│ │ Pi-hole │    │  Nextcloud  │  │  OSIRIS  │ │
│ │  (DNS)  │    │ (Armazena-  │  │ (OSINT)  │ │
│ │         │    │  mento)     │  │          │ │
│ └─────────┘    └─────────────┘  └──────────┘ │
│                                              │
│              ┌──────────────┐                │
│              │  Tailscale   │                │
│              │  (VPN Mesh)  │                │
│              └──────────────┘                │
|──────────────────────────────────────────────|


##  Serviços Implementados

| Serviço | Função |
|---|---|
| **Pi-hole** | Filtragem de DNS em toda a rede, bloqueio de anúncios e domínios maliciosos |
| **Tailscale** | VPN mesh para acesso remoto seguro à infraestrutura |
| **Docker / Docker Compose** | Orquestração e isolamento de containers |
| **Nextcloud** | Armazenamento em nuvem privado (self-hosted) |
| **OSIRIS** | Ferramenta de OSINT e análise de ameaças (Next.js) |

##  Desafios Técnicos Resolvidos

Este projeto foi construído resolvendo problemas reais de infraestrutura, entre eles:

- **Conflito de porta 53**: resolução de conflito entre `systemd-resolved` e Pi-hole para permitir filtragem de DNS em toda a rede.
- **Configuração de blocklists avançadas**: implementação de listas StevenBlack, Hagezi (Pro/Pro+/TIF) e listas anti-scam no Pi-hole.
- **Instabilidade de armazenamento USB**: diagnóstico de falhas UAS (USB Attached SCSI) e correção via ajuste de quirks no kernel.
- **Falha de rede após reinicialização**: correção de configuração DHCP via Netplan.
- **Conflitos de rede em containers**: resolução de dependências de rede Docker e conflitos de porta na implantação do OSIRIS.
- **Limitação de hardware**: identificação de incompatibilidade AVX no processador, impedindo a execução de MongoDB 6.x (dependência do UniFi Controller) — documentado como estudo de caso de compatibilidade hardware/software.

##  Objetivo do Projeto

Aplicar na prática conceitos estudados em certificações (Cisco, Fortinet) e formação em Segurança da Informação, desenvolvendo experiência real em:

- Administração de sistemas Linux
- Redes de computadores (DNS, DHCP, VPN)
- Containerização e orquestração (Docker)
- Armazenamento e backup self-hosted
- Fundamentos de análise OSINT

##  Tecnologias Utilizadas

`Ubuntu Server` `Docker` `Docker Compose` `Pi-hole` `Tailscale` `Nextcloud` `Netplan`

## 👤 Autor

**Esttevão Pereira Silva**
Estudante de Segurança da Informação |
[LinkedIn](https://linkedin.com/in/esttevao-pereira-silva) · esttevaopereira1@gmail.com

---

*Este é um projeto pessoal em constante evolução, usado como ambiente de estudo prático e portfólio técnico.*

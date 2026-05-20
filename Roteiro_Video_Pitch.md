# 🎥 ROTEIRO — VÍDEO PITCH (4 MINUTOS)
## Projeto de Rede para Loja de Varejo com Controle de Estoque e CFTV
### Disciplina: Computer Network — UniFECAF

---

> **DICA ANTES DE GRAVAR:**
> - Abra o diagrama no Draw.io e deixe em tela cheia
> - Fale olhando para a câmera, com naturalidade
> - Você pode usar o cursor do mouse para apontar os elementos no diagrama enquanto fala
> - Grave em ambiente silencioso, com boa iluminação

---

## ⏱️ [0:00 – 0:30] — ABERTURA: O PROBLEMA DA ANA

*[Olhe para a câmera, sorria, fale com confiança]*

> "Olá! Meu nome é Rosandro e neste vídeo vou apresentar o meu projeto de rede de computadores para a disciplina Computer Network da UniFECAF.
>
> O cenário que me foi proposto é o seguinte: Ana é proprietária de uma loja de roupas e ela tem um problema real. Ela possui vários dispositivos na loja — três caixas registradoras, dois tablets, uma impressora, uma maquininha de cartão, quatro câmeras de segurança e um servidor local — e tudo isso precisa estar conectado, funcionando ao mesmo tempo, de forma segura e sem interrupções.
>
> O meu desafio foi projetar a rede ideal para essa loja. E é isso que vou mostrar agora."

---

## ⏱️ [0:30 – 1:30] — SOLUÇÃO: TOPOLOGIA E DECISÕES DO PROJETO

*[Mostre o diagrama na tela, aponte para a hierarquia central]*

> "A solução que eu desenvolvi usa a **topologia em estrela** — que é a mais adequada para esse cenário. Nessa topologia, todos os dispositivos se conectam a um ponto central, que é o switch. Se um cabo ou dispositivo falhar, só ele é afetado, e o resto da rede continua funcionando. É simples, confiável e fácil de expandir no futuro.
>
> A hierarquia da rede funciona assim — e você pode ver isso no diagrama:
>
> Primeiro, temos a **internet**, que entra na loja pelo modem da operadora.
> O modem passa o sinal para o **roteador**, que é o coração da rede. É ele que gerencia tudo: distribui os endereços IP automaticamente via DHCP, define o Gateway — ou seja, a porta de saída para a internet — e também tem um firewall integrado para proteger a rede.
> Do roteador, o sinal vai para o **switch gerenciável**, que conecta todos os dispositivos cabeados da loja.
> E para os tablets, temos um **Access Point**, que fornece o Wi-Fi.
>
> Uma decisão importante que tomei foi organizar a rede em três grupos separados, chamados de **VLANs** — Redes Locais Virtuais. Vou explicar isso agora."

---

## ⏱️ [1:30 – 2:30] — COMPONENTES: EQUIPAMENTOS E SERVIÇOS

*[Aponte cada área colorida do diagrama ao mencionar as VLANs]*

> "A rede está dividida em três VLANs — que são como bairros virtuais dentro da mesma rede física, cada um isolado dos outros por segurança.
>
> A **VLAN 10, em verde**, é o segmento do PDV — Ponto de Venda. Aqui estão as três caixas registradoras, a maquininha de cartão e a impressora. Todos com endereços IP fixos na faixa 192.168.10.X. Esse isolamento é fundamental para proteger os dados de pagamento.
>
> A **VLAN 20, em amarelo**, é o segmento do CFTV — as câmeras de segurança. As quatro câmeras IP se conectam ao switch via cabo de rede e enviam o vídeo diretamente para o servidor local, que armazena as gravações. Separar as câmeras evita que o alto volume de tráfego de vídeo prejudique o desempenho das caixas. Os IPs das câmeras ficam na faixa 192.168.20.X.
>
> A **VLAN 30, em roxo**, é o segmento de Gestão. Os dois tablets da Ana e da equipe se conectam via Wi-Fi ao Access Point e têm acesso ao servidor de estoque. Como são dispositivos móveis, eles recebem endereço IP automaticamente via DHCP, na faixa 192.168.30.X.
>
> O servidor local fica na interseção das VLANs 20 e 30: ele recebe as gravações das câmeras pela VLAN 20 e disponibiliza o sistema de estoque para os tablets pela VLAN 30.
>
> Para resolução de nomes na internet, utilizei o DNS do Google — 8.8.8.8 como primário e 8.8.4.4 como secundário."

---

## ⏱️ [2:30 – 3:30] — DIAGRAMA: VISÃO GERAL DA REDE

*[Percorra o diagrama com o cursor, mostrando os caminhos de conexão]*

> "Olhando o diagrama, podemos acompanhar visualmente o caminho dos dados:
>
> *[Aponte para o topo]* Aqui em cima temos a internet — a WAN. O sinal entra pelo modem...
> *[Desça com o cursor]* ...passa para o roteador, que gerencia toda a rede e aplica as regras de firewall...
> *[Continue descendo]* ...vai para o switch central, que distribui as conexões para cada segmento...
> *[Aponte para a esquerda]* ...à esquerda, os dispositivos de PDV, em verde, todos conectados por cabo Ethernet...
> *[Aponte para baixo]* ...abaixo, as câmeras e o servidor de CFTV, em amarelo, também por cabo — as câmeras inclusive recebem energia pelo próprio cabo de rede, usando tecnologia PoE...
> *[Aponte para a direita]* ...e à direita, o Access Point transmite o Wi-Fi para os tablets de gestão, representado pelas linhas tracejadas em roxo.
>
> As linhas contínuas representam conexões cabeadas por Ethernet Cat6. As linhas tracejadas representam conexão sem fio, o Wi-Fi. Cada dispositivo tem seu endereço IP anotado no diagrama, junto com a máscara de sub-rede e o Gateway."

---

## ⏱️ [3:30 – 4:00] — FECHAMENTO: SEGURANÇA, ESCALABILIDADE E CONCLUSÃO

*[Olhe para a câmera novamente, fale com confiança]*

> "Em relação à segurança, além do isolamento por VLANs, o firewall do roteador bloqueia tráfego entre segmentos que não precisam se comunicar, o Wi-Fi usa WPA3 para autenticação segura, e o servidor tem política de backup das gravações das câmeras.
>
> E pensando no futuro: essa rede é escalável. Se a Ana quiser adicionar mais câmeras, mais caixas ou até abrir uma segunda filial com VPN, a infraestrutura já suporta isso sem precisar trocar os equipamentos principais.
>
> Em resumo: o projeto da rede da loja da Ana resolve todos os requisitos do cenário — conectividade eficiente para todos os 12 dispositivos, segurança com segmentação por VLANs, câmeras sempre operacionais com gravação segura no servidor, e uma arquitetura preparada para crescer.
>
> É isso! Obrigado pela atenção."

---

## 📋 CHECKLIST ANTES DE POSTAR

- [ ] Vídeo tem no máximo 4 minutos
- [ ] Diagrama está visível durante a explicação
- [ ] Você mencionou: topologia, VLANs, IP, DHCP, DNS, Gateway, firewall
- [ ] Você justificou as escolhas de topologia e dispositivos
- [ ] Postar no YouTube (pode ser não listado) e copiar o link para entregar

---

*Roteiro desenvolvido para a disciplina Computer Network — UniFECAF — 2026*

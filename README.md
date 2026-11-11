# 🌊 Correio das Águas — Terminal Comunitário & Dashboard ONG

**Projeto:** Global Solution 2026.2 — Engenharia de Software / FIAP  
**Tema:** CitizenTech — Tecnologia para pessoas

## 🔗 Link do Projeto (Wokwi)
Acesse a simulação interativa completa aqui: **[Projeto Correio das Águas no Wokwi](https://wokwi.com/projects/480255733629197313)**

---

## 📖 Descrição do Projeto

O **Correio das Águas** é uma solução de impacto socioambiental projetada para comunidades ribeirinhas da Amazônia com conectividade inexistente ou limitada. O sistema aproveita os **barcos de transporte regular de passageiros** para atuar como pontes de dados ("Data Mules").

Este repositório contém a prova de conceito (PoC) da arquitetura, composta por duas pontes:
1. **Terminal Comunitário (ESP32 no Wokwi):** Um totem offline de baixo consumo onde moradores registram necessidades básicas (água, alimentos, roupas) recebendo um código privado.
2. **Dashboard da ONG (HTML/JS Web):** Um painel rodando na cidade que recebe os pedidos automaticamente via protocolo MQTT quando o barco alcança uma área com internet.

**Slogan:** *Conectando necessidades, transportando soluções.*

---

## 🛠️ Abstrações da Simulação

Para validar as regras de negócio do escopo no ambiente restrito de hardware do Wokwi, aplicamos as seguintes abstrações:

* **Entrada por Voz -> Push Buttons:** O escopo prevê cadastro por voz para acessibilidade. Na simulação, utilizamos botões coloridos para representar as categorias.
* **Acessibilidade Sonora (Pessoas Cegas):** O circuito conta com um **Buzzer** que emite bipes de confirmação e alertas, atendendo ao requisito de interação não exclusivamente visual.
* **Privacidade (Código Privado):** O sistema gera um protocolo alfanumérico (Ex: `AGUA-101`) para não expor nomes publicamente na tela.
* **Barco / Nuvem (MQTT):** O botão de atracação (preto) aciona o envio dos dados da memória local do ESP32 para o Broker MQTT público (HiveMQ), simulando a chegada do barco à cidade e a transmissão dos dados.

---

## 💻 Componentes e Tecnologias

**Hardware (Simulado):**
* 01 x ESP32 (DevKit V4) - Microcontrolador com Wi-Fi
* 01 x Display LCD 16x2 (I2C)
* 04 x Push Buttons (3 categorias + 1 barco)
* 03 x LEDs (Status) e Resistores
* 01 x Buzzer (Piezoelétrico)

**Software e Protocolos:**
* **C++ (Arduino IDE):** Lógica do microcontrolador (FSM).
* **PubSubClient:** Biblioteca para comunicação MQTT no ESP32.
* **MQTT via WebSockets:** Para integração em tempo real com o Front-end.
* **HTML/CSS/JS:** Dashboard da ONG (`ong-dashboard.html`).

---

## 🚀 Como Executar a Demonstração Completa

Para ver a comunicação assíncrona acontecendo em tempo real:

1. **Inicie o Painel da ONG:**
   * Baixe o arquivo `ong-dashboard.html` deste repositório e abra-o no seu navegador (Chrome/Edge).
   * Aguarde o status verde: *"Online - Pronto para receber atualizações do barco"*.
2. **Inicie o Terminal (Wokwi):**
   * Abra o link do projeto no Wokwi.
   * Clique em **Play** (Start Simulation) e aguarde o Wi-Fi conectar.
3. **Registre Pedidos Offline:**
   * Pressione os botões **Azul** (Água) ou **Amarelo** (Alimentos). O LCD mostrará o código gerado.
4. **Simule a Atracação do Barco:**
   * Clique no botão **Preto** (Barco).
   * Observe a mágica: os dados sairão do Terminal Comunitário, viajarão pela nuvem (MQTT) e aparecerão instantaneamente na tabela da página Web aberta no seu computador!

---

## 👥 Equipe (Correio das Águas)

* **Nicolas Ramalho** - RM 572939
* **João Arruda** - RM 570342
* **Diogo Bittar** - RM 569657

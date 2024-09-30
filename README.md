# Projeto IoT: **Acelerando o Futuro** - Monitoramento de Temperatura em Corridas de Fórmula E

Este projeto faz parte da solução proposta para a Mahindra chamada "Acelerando o Futuro", cujo objetivo é promover a mobilidade elétrica através das corridas de Fórmula E. O foco desta aplicação é monitorar e exibir, em tempo real, a temperatura dos locais das corridas, utilizando dispositivos IoT e uma dashboard interativa. Além disso, o sistema possui controles visuais de LEDs e um servo motor para demonstrar reações automáticas baseadas em condições climáticas.

## Objetivos do Projeto

1. **Monitoramento de temperatura em tempo real** com um sensor DHT11 conectado ao Arduino Uno.
2. **Visualização dos dados** via dashboard no Node-RED.
3. **Automação de dispositivos** como LEDs e servo motor, reagindo automaticamente com base na temperatura.
4. **Integração entre IoT, back-end e front-end** para uma solução completa de monitoramento e controle.

## Arquitetura da Solução

### 1. **Dispositivos IoT**
   - **Arduino Uno**: Usado para coletar dados do sensor de temperatura e umidade DHT11.
   - **Sensor DHT11**: Coleta a temperatura e a umidade do ambiente.
   - **LEDs e Servo Motor**: Respostas automáticas baseadas na temperatura. LEDs indicam status (verde para temperatura <= 25°C e vermelho para > 25°C). O servo motor é acionado para simular mecanismos de controle de temperatura.

### 2. **Back-end**
   - **Node-RED**: Plataforma de fluxo para conectar o Arduino à dashboard e processar os dados recebidos. O Node-RED recebe os dados do Arduino via comunicação serial (USB) e exibe em uma interface gráfica.
   - **Servidor Local**: Node.js rodando em um servidor local ou na nuvem para hospedar a interface e o fluxo de dados.

### 3. **Front-end**
   - **Dashboard Node-RED**: Interface web para monitoramento e controle visual dos dados de temperatura e umidade em tempo real. Os dados do sensor são atualizados e exibidos ao usuário em gráficos e indicadores.
   - **Integração com APIs**: Caso haja necessidade, a aplicação pode ser estendida para integrar APIs de previsão do tempo ou outros dispositivos IoT para mais funcionalidades.

### Diagrama da Arquitetura Proposta

```plaintext
+------------------+      +---------------+      +-----------------+      +---------------+
|  Sensor DHT11    | ---> |  Arduino Uno   | ---> |    Node-RED      | --->|  Dashboard     |
+------------------+      +---------------+      +-----------------+      +---------------+
         ^                        |                           |
         |                        |                           v
+------------------+        +-------------+           +-----------------+
|  LED Verde/LED R  |        | Servo Motor |           |  Controle via   |
+------------------+        +-------------+           |   Interface     |
                                                     +-----------------+

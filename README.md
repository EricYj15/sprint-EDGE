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
```

Recursos Necessários
1. Dispositivos IoT
Arduino Uno: Microcontrolador para ler os dados do sensor.
Sensor DHT11: Sensor de temperatura e umidade.
LEDs: Verde e Vermelho para representar estados da temperatura.
Servo Motor: Para simular reações mecânicas ao aumento da temperatura.
Cabos de conexão: Fios jumper para as ligações entre os componentes.
Protoboard: Para montar o circuito.
2. Back-end
Node-RED: Software de programação visual para conectar e processar os dados do Arduino.
Servidor Local ou Nuvem: Para hospedar o Node-RED e a dashboard.
Biblioteca ArduinoJson: Para converter os dados em JSON e enviá-los ao Node-RED.
3. Front-end
Dashboard Node-RED: Interface web para visualização dos dados.
API de Comunicação Serial: Para receber dados do Arduino via porta USB.
Instruções de Uso
1. Montagem do Circuito
Conecte o sensor DHT11 ao pino digital 7 do Arduino Uno.
Conecte o LED verde ao pino digital 13 e o LED vermelho ao pino digital 12.
Conecte o servo motor ao pino digital 11.
Monte o circuito em uma protoboard usando cabos jumper para fazer as conexões com o Arduino.
2. Configuração do Ambiente de Desenvolvimento
Instale o Arduino IDE: Para programar o Arduino.

Download Arduino IDE
Instale as bibliotecas necessárias no Arduino IDE:

Vá para Sketch > Incluir Biblioteca > Gerenciar Bibliotecas...
Instale a biblioteca DHT Sensor Library by Adafruit.
Instale a biblioteca ArduinoJson.
Instale a biblioteca Servo.
Configure o Node-RED:

Instale o Node-RED no seu sistema.
Abra o Node-RED e configure um fluxo para receber os dados via porta serial.
Use a biblioteca node-red-dashboard para criar uma interface gráfica.
3. Upload do Código para o Arduino
Copie o código fornecido no Arduino IDE.
Selecione a placa Arduino Uno em Ferramentas > Placa > Arduino Uno.
Selecione a porta COM correta em Ferramentas > Porta.
Faça o upload do código para o Arduino.
4. Execução do Projeto
Conecte o Arduino ao computador.
Inicie o Node-RED e abra a interface da dashboard.
Visualize os dados de temperatura e umidade atualizados na dashboard em tempo real.
Observe as mudanças nos LEDs e no servo motor com base nos valores de temperatura.
Requisitos
Arduino Uno
Node.js com o Node-RED instalado
Bibliotecas ArduinoJson, DHT11 e Servo
Browser compatível com Node-RED Dashboard
Ambiente físico (Protoboard, LEDs, Servo Motor, Fios Jumper)
Dependências
Arduino IDE: Instalar aqui
Node.js: Instalar aqui
Biblioteca Node-RED Dashboard: Instale no Node-RED com o comando:
npm install node-red-dashboard

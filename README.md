# Forno de refusão para componentes SMD controlado por STM32 e Raspberry Pi

![License](https://img.shields.io/github/license/LegiusAndrade/reflow-oven-nextjs-front?style=flat-square)
![Badge](https://img.shields.io/badge/status-DESENVOLVIMENTO-green)

<img src="https://shields.io/badge/TypeScript-3178C6?logo=TypeScript&logoColor=FFF&style=flat-square" height="30"/>
<img src="https://img.shields.io/badge/.NET-512BD4?style=for-the-badge&logo=dotnet&logoColor=white" height="30"/>
<img src="https://img.shields.io/badge/next.js-000000?style=for-the-badge&logo=nextdotjs&logoColor=white" height="30"/>
<img src="https://img.shields.io/badge/postgresql-4169e1?style=for-the-badge&logo=postgresql&logoColor=white" height="30"/>



![Forno de refusão](src_external/image/Imagem%20DALL-E%203%20Forno.jpeg)
## Visão Geral
Este projeto é um forno para soldagem de componentes SMD, com controle preciso de temperatura e monitoramento em tempo real. O sistema é composto por uma placa de potência e uma placa de controle integradas, permitindo controle e supervisão de maneira prática via interface web.

## Componentes Principais

### Placa de Potência
- **Microcontrolador:** STM32G431C6T6
- **Entrada:** 127VAC retificada por ponto de diodos
- **Conversor:** DC-DC tipo buck para controle de tensão na resistência
- **Sensores:**
  - Leitura de tensão na entrada e saída usando o DMA do microcontrolador.
  - **Sensor de temperatura:** 
    - **Forno:** Tipo K com CI (MAX31855) integrado com alta precisão usando comunicação SPI com DMA
    - **Placa de potência:** um NTC caracterizado pelo &beta;
- **Controle de Malha Fechada:** Baseado em PID.
- **Ventiladores controlador por PWM:**
  - Resfriamento da PCB.
  - Controle de temperatura do forno com PID.
- **Comuicação:** RS422 isolado com protocolo proprietário

### Placa de Controle 
- **Processador:** Raspberry PI 4B ou Orange Pi 5 Pro
- **Comuicação:** RS422 isolado com protocolo proprietário
- **Interface de controle:**
  - **Frontend:** NextJS 15 + Tailwind CSS.
  - **Backend:** .NET Framework 8.0.
  - **Banco de Dados:** PostgreSQL.

## Funcionalidades
### Controle do Forno
   - Configuração de **temperatura** e **tempo** para ciclos de solda.
   - Controle de **malha fechada** baseado na leitura do sensor de temperatura fazendo o controle PID da tensão de saída.

### Monitoramento em Tempo Real
   - **Temperaturas:** PCB e forno.
   - **Tensões:** Entrada e saída.
   - **Corrente:** Saída.
   - **Ventiladores:** Velocidade em RPM.
   - **Alarmes:** Condições configuráveis, como RPM baixa ou tensões fora do limite.

### Interface do Usuário
   - Monitoramento e controle via interface web responsiva.
   - CRUD para gerenciamento de usuários com diferentes níveis de permissão.

### Alarmes e Segurança
   - Alarmes configuráveis:
     - RPM abaixo do limite nos ventiladores.
     - Tensão fora do intervalo permitido.
     - Temperatura acima do limite de segurança.
   - Sistema robusto para garantir a segurança do equipamento e dos componentes.

## Como Usar
### 1. Configuração do Sistema:
  - Conecte a placa de potência à placa de controle.
  - Certifique-se de que os sensores e ventiladores estão funcionando.

### 2. Interface Web:
  - Acesse a aplicação via navegador ou display touch.
  - Configure os parâmetros desejados (temperatura, tempo, etc.).

### 3. Monitoramento:
  - Visualize informações em tempo real e responda a alarmes caso sejam gerados.

## Tecnologias Utilizadas

**Hardware:** STM32G431C6T6, Raspberry Pi ou Orange Pi 5 Pro.

**Software:** 
- NextJS 15, TailwindCSS (Front-end).
- .NET Framework 8.0, PostgreSQL (Back-end).

## Contribuições
_**Contribuições são bem-vindas! Sinta-se à vontade para abrir issues ou enviar pull requests.**_

## Licença
Este projeto é licenciado sob a [Licença MIT](https://pt.wikipedia.org/wiki/Licen%C3%A7a_MIT).
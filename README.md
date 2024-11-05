# Sistema de Segurança e Monitoramento de Gás

## Índice
- [Sobre o Projeto](#sobre-o-projeto)
- [Funcionalidades](#funcionalidades)
- [Componentes](#componentes)
- [Especificações Técnicas](#especificações-técnicas)
- [Organização Eletrônica](#organização-eletrônica)
- [Montagem Mecânica](#montagem-mecânica)
- [Funcionamento do Sistema](#funcionamento-do-sistema)
- [Configuração](#configuração)
- [Manutenção](#manutenção)
- [Limitações](#limitações)
- [Expansões Futuras](#expansões-futuras)
- [Solução de Problemas](#solução-de-problemas)
- [Referências](#referências)
- [Licença](#licença)

## Sobre o Projeto
Este projeto consiste em um sistema de segurança automatizado para monitoramento de gases nocivos em ambientes fechados. O sistema utiliza um sensor de gás MQ-7 para detectar a presença de gases perigosos e um conjunto de sensor ultrassônico acoplado a um servo motor para realizar uma varredura contínua do ambiente, identificando a presença de pessoas. Em caso de detecção de gás, o sistema emite alertas sonoros e visuais, além de enviar notificações via Bluetooth para um dispositivo móvel.

## Funcionalidades
- Detecção de gases nocivos no ambiente
- Varredura contínua de 180 graus para identificar pessoas
- Emissão de alertas sonoros em caso de detecção de gás
- Indicação visual através de LEDs do status da área
- Envio de notificações via Bluetooth
- Sistema modular e adaptável para diferentes ambientes

## Componentes
1. Arduino UNO
2. Sensor ultrassônico HC-SR04
3. Servo Motor
4. Sensor de gás MQ-7
5. Buzzer
6. Módulo Bluetooth HC-05
7. LED Vermelho
8. LED Verde
9. Protoboard
10. 2x Resistores 330Ω (para os LEDs)
11. Jumpers macho-macho
12. Jumpers macho-fêmea

## Especificações Técnicas
- Alcance do sensor ultrassônico: até 3 metros
- Ângulo de varredura do servo: 180 graus
- Threshold do sensor de gás: 50 (ajustável via código)
- Taxa de transmissão Bluetooth: 38400 baud
- Tensão de operação: 5V (via Arduino)
- Intervalo entre notificações: 5 segundos

## Organização Eletrônica
1. **Sensor Ultrassônico HC-SR04**
   - VCC → 5V
   - GND → GND
   - TRIG → Pino 7
   - ECHO → Pino 6

2. **Servo Motor**
   - Vermelho (VCC) → 5V
   - Marrom/Preto (GND) → GND
   - Laranja/Amarelo (Sinal) → Pino 9

3. **Sensor de Gás MQ-7**
   - VCC → 5V
   - GND → GND
   - AO (Saída Analógica) → Pino A0

4. **Buzzer**
   - Positivo (+) → Pino 8
   - Negativo (-) → GND

5. **LED Vermelho**
   - Ânodo (+) → Resistor 330Ω → Pino 4
   - Cátodo (-) → GND

6. **LED Verde**
   - Ânodo (+) → Resistor 330Ω → Pino 5
   - Cátodo (-) → GND

7. **Módulo Bluetooth HC-05**
   - VCC → 5V
   - GND → GND
   - TX → Pino 2
   - RX → Pino 3

## Montagem
1. O sensor ultrassônico deve ser fixado na parte superior do servo motor
2. O conjunto servo+ultrassônico deve ser posicionado em local com livre movimento para rotação
3. O sensor de gás deve ser instalado em posição adequada para detecção
4. LEDs devem ser posicionados de forma visível
5. Considerar espaço para ventilação do sensor MQ-7

## Funcionamento do Sistema

### Inicialização
1. Teste inicial de todos os componentes
2. Calibração do servo motor
3. Estabelecimento da comunicação Bluetooth
4. LED verde e vermelho piscam para confirmação

### Operação Normal
1. **Monitoramento de Gás**
   - Leitura contínua do sensor MQ-7
   - Comparação com threshold definido
   - Ativação do protocolo de segurança quando necessário

2. **Varredura de Área**
   - Movimento contínuo do servo motor (0° a 180°)
   - Leituras do sensor ultrassônico a cada 30 graus
   - Detecção de pessoas até 3 metros de distância

3. **Sistema de Alertas**
   - Alarme sonoro em caso de detecção de gás
   - LED Verde: área livre
   - LED Vermelho: pessoas detectadas
   - Notificações Bluetooth com informações detalhadas

### Protocolo de Segurança
1. Detecção de gás acima do threshold:
   - Ativação do buzzer
   - Intensificação da varredura
   - Envio de notificações
   - Atualização dos indicadores visuais

2. Detecção de pessoas:
   - Alteração do padrão de alerta
   - Notificação específica via Bluetooth
   - Registro do ângulo de detecção

## Configuração

### Configuração do Hardware
1. Montar o circuito conforme esquema de conexões
2. Verificar todas as conexões antes de energizar
3. Confirmar o posicionamento mecânico dos sensores

### Configuração do Software
1. Carregar o código no Arduino
2. Parear o módulo Bluetooth HC-05 (senha padrão: 1234)
3. Monitorar funcionamento inicial via Serial Monitor
4. Ajustar parâmetros se necessário:
   - GAS_THRESHOLD (sensibilidade do sensor de gás)
   - DISTANCE_THRESHOLD (distância de detecção)
   - SCAN_DELAY (velocidade de varredura)
   - NOTIFICATION_DELAY (intervalo entre notificações)

## Manutenção e Cuidados
1. Verificar periodicamente as conexões
2. Limpar os sensores quando necessário
3. Calibrar o sensor de gás periodicamente
4. Verificar o funcionamento do servo motor
5. Testar o sistema de comunicação Bluetooth

##  Limitações e Considerações
1. Alcance máximo do sensor ultrassônico: 3 metros
2. Tempo de aquecimento do sensor MQ-7: ~20 segundos
3. Área de cobertura limitada ao ângulo de varredura
4. Alcance do Bluetooth: ~10 metros (sem obstáculos)

## Possíveis Expansões Futuras
1. Integração com outros tipos de sensores
2. Implementação de sistema Wi-Fi
3. Desenvolvimento de aplicativo móvel dedicado
4. Adição de backup de bateria
5. Integração com sistemas de ventilação

## Solução de Problemas
1. **Sistema não inicializa:**
   - Verificar alimentação
   - Confirmar conexões
   - Verificar código no Arduino

2. **Falha na detecção:**
   - Calibrar sensores
   - Verificar posicionamento
   - Ajustar thresholds

3. **Problemas de comunicação:**
   - Verificar pareamento Bluetooth
   - Confirmar configurações de comunicação
   - Verificar distância do dispositivo móvel

## Referências
- [Arduino Documentation](https://www.arduino.cc/reference/en/)
- HC-SR04 Datasheet
- MQ-7 Datasheet
- HC-05 Bluetooth Module Documentation

## Licença
Este projeto está sob a licença MIT.

---
Desenvolvido por Ryan Haiala Conceição Damasceno - 2024

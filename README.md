## 1. Descrição Completa do Problema

As enchentes e os desastres naturais associados, como deslizamentos de terra, são um problema crônico e devastador em diversas regiões do Brasil. Anualmente, comunidades inteiras são impactadas, resultando em:

* **Perda de Vidas:** O mais trágico dos impactos, muitas vezes devido à falta de tempo hábil para evacuação.
* **Prejuízos Materiais:** Destruição de residências, comércios, infraestrutura pública (pontes, ruas) e perda de bens pessoais.
* **Impacto Econômico:** Paralisação de atividades, perda de safras, interrupção de serviços e sobrecarga dos sistemas de saúde e assistência social.
* **Trauma Social:** Desalojamento de famílias, estresse pós-traumático e desestruturação de comunidades.

## 2. Visão Geral da Solução

O projeto propõe uma solução tecnológica para o monitoramento e alerta precoce de enchentes, visando proteger vidas e reduzir prejuízos. Trata-se de um sistema inteligente baseado em Arduino que utiliza sensores para detectar mudanças no nível da água e nas condições climáticas, emitindo alertas claros e em tempo real.

O protótipo inicial utiliza os seguintes componentes:

* **Arduino Uno:** Microcontrolador responsável por processar os dados dos sensores e controlar os atuadores (LEDs, Buzzer).
* **Sensor Ultrassônico HC-SR04:** Mede a distância entre o sensor e a superfície da água, permitindo determinar o nível.
* **Sensor de Luminosidade (LDR - Light Dependent Resistor):** Detecta a intensidade da luz ambiente, podendo ser usado como um indicador simplificado de condições de chuva (baixa luminosidade = tempo nublado/chuvoso).
* **LEDs (Verde, Amarelo, Vermelho):** Atuam como indicadores visuais do nível de alerta:
    * **Verde:** Nível seguro.
    * **Amarelo:** Atenção / Nível da água subindo.
    * **Vermelho:** Perigo / Nível da água muito alto (risco de enchente).
* **Buzzer:** Emite um alerta sonoro em situações de perigo.
* **Resistores:** Necessários para limitar a corrente dos LEDs e para montar o divisor de tensão do LDR.
* **Protoboard e Fios Jumper:** Para montagem e conexão dos componentes.

<h3>Como Funciona</h3>

O sistema realiza as seguintes etapas:

1.  **Monitoramento da Luminosidade:** O LDR mede a intensidade da luz ambiente. Se a luminosidade estiver abaixo de um limiar pré-definido (`CHUVA`), o sistema considera que há condições de chuva e prossegue para a verificação do nível da água. Caso contrário, indica uma mensagem dizendo que não há risco de enchente no momento.
2.  **Medição do Nível da Água:** Quando condições de chuva são detectadas (ou se for o modo de monitoramento contínuo de água), o sensor ultrassônico é ativado. Ele emite um pulso sonoro e mede o tempo que leva para o pulso retornar após ricochetear na superfície da água. Com base nesse tempo, a distância até a água é calculada.
3.  **Cálculo da Altura da Água:** A distância lida pelo ultrassônico é usada para calcular a altura da água em relação ao ponto mais baixo (fundo do rio/córrego), considerando a altura de instalação do sensor.
4.  **Sistema de Alerta:** A altura da água (ou a distância do sensor à água) é comparada com limiares de segurança pré-definidos:
    * **Nível Seguro (LED Verde):** A distância lida é maior que o limiar de alerta.
    * **Nível de Alerta (LED Amarelo):** A distância lida está entre o limiar de perigo e o de alerta, indicando que o nível da água está subindo e requer atenção.
    * **Nível de Perigo (LED Vermelho + Buzzer):** A distância lida é muito pequena (a água está muito perto do sensor), indicando um nível crítico e alto risco de enchente. O buzzer é acionado para um alerta sonoro.
5.  **Feedback Visual e Sonoro:** Os LEDs e o buzzer fornecem feedback imediato sobre a situação.

### 3. Passo a Passo para Simular no Wokwi

1.  **Inicie a Simulação:** Iniciar simulação.
2.  **Indicar chuva no photoresistor:** Para que o ultrassonico comece a rodar e detectar a chuva é preciso abaixar a luminosidade no photoresistor.
    * Arraste-o para a **esquerda** para simular **menos luz** (tempo nublado ou chuvoso).
    * Arraste-o para a **direita** para simular **mais luz** (dia claro).
3.  **Interaja com o Sensor Ultrassônico:** Agora com o sensor da chuva funcionando, basta mexer com sensor ultrassônico HC-SR04 onde você pode arrastar com o mouse. Este objeto simula a superfície da água.
    * **Mova este objeto para perto do sensor** para simular um **nível de água alto**.
    * **Mova este objeto para longe do sensor** para simular um **nível de água baixo**.
    * É possível ver como os **LEDs** (Verde, Amarelo, Vermelho) e o **Buzzer** (em caso de perigo) respondem a essas mudanças, indicando os diferentes níveis de alerta (seguro, atenção, perigo).


Link projeto wokwi: https://wokwi.com/projects/432708979210447873 <br>
Link vídeo demonstrativo: https://youtu.be/3dCwsJ2L7f8 <br>
Integrantes: Bernardo Moreira Lopes Sousa rm:564103 / Francisco Nogueira de Queiroz rm:566309
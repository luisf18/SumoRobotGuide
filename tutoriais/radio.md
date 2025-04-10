# 📡 Rádio Controle

A comunicação por rádio é composta por dois elementos principais: um **transmissor** (o rádio em si) e um **receptor** no robô. Cada marca utiliza protocolos próprios — por exemplo, a FlySky usa AFHDS e AFHDS-2A. O protocolo define como os sinais são enviados e interpretados, então é essencial garantir que o receptor seja compatível com o rádio escolhido.

---

## FlySky FS-i6 e FS-i6X

São, de longe, uma das melhores opções custo-benefício para quem está começando. Muito usados em aeromodelismo, também funcionam bem para sumô.

A diferença entre os dois modelos é simples:
- **FS-i6**: até 6 canais.
- **FS-i6X**: até 10 canais.

Ambos utilizam o protocolo **AFHDS-2A** e têm uma interface fácil de usar.

![Flysky](../img/flysky.jpg)

A FlySky também oferece vários modelos de receptores — com mais ou menos canais, com ou sem telemetria:

![Receptores Flysky](../img/flysky_receptores.png)

Existem ainda receptores alternativas compatíveis com o protocolo, bastante usados em competições:

![Receptores alternativos](../img/flysky_receptores_alternativos.png)

- **FS2A**: Muito compacto, com 4 canais PWM. Excelente para robôs pequenos.  
- **FS-RX2A**: Envia todos os canais por um único pino via **PPM ou iBUS**. É menor ainda, mas exige decodificação no microcontrolador — por isso, é menos usado.

---

## Rádio pistola 2.4GHz TX-4

Os rádios tipo "pistola" são bastante populares entre pilotos de sumô, pois oferecem uma experiência de controle mais intuitiva — gatilho para frente/trás e volante para esquerda/direita.

O modelo **TX-4** é uma ótima opção de entrada, encontrado por cerca de R$80 no AliExpress (sem taxas). Vem com um receptor de 4 canais. A única limitação é que ele possui poucos ajustes de canal no próprio rádio — mas isso pode ser compensado facilmente no código, se você estiver usando Arduino ou ESP.

![Rádio pistola](../img/RadioPistola.jpg)

---

## 🌐 ESPNOW

**ESPNOW** é um protocolo de comunicação rápida em 2.4GHz da **Espressif**, ideal para quem usa ESP32. Permite comunicação direta entre dois ou mais dispositivos, **sem a necessidade de um receptor separado**.

![ESPNOW](../img/ESPNOW.png)

[Tutorial introdutório sobre ESPNOW](https://randomnerdtutorials.com/esp-now-esp32-arduino-ide/)

### ✅ Vantagens
- Barato (usa apenas ESPs)
- Projeto mais compacto, sem receptor externo
- Permite telemetria (bateria, corrente etc.)

### ⚠️ Desvantagens
- Requer cuidado com interrupções e estabilidade
- É preciso montar ou adaptar seu próprio rádio
- **Evite joysticks genéricos baratinhos** — muitos são imprecisos ou ruins

### 💡 Experiência pessoal
Gosto bastante do ESPNOW e é o que tenho usado nos meus robôs ultimamente. Desenvolvi uma biblioteca que facilita a conexão: [ESPNOW_device](https://github.com/luisf18/ESPNOW_device). Ela conecta via nome e senha (a senha ainda está em desenvolvimento 😅), o que é mais simples que usar o MAC.

Modifiquei rádios comerciais colocando um ESP no lugar da controladora:

![Radios ESPNOW](../img/ESPNOW_radios.png)

Se você **não quer montar um rádio do zero**, dá pra adaptar o seu com um **conversor PPM → ESPNOW**, conectado na porta **Trainer** do rádio ou até internamente. Já utilizei essa estratégia com uma plaquinha compacta que projetei, e funciona muito bem!

![Conversor externo](../img/ESPNOW_radio_conversor.png)  
![Conversor](../img/ESPNOW_conversor.png)

---

## 🔵 Bluetooth

O Bluetooth é um protocolo muito comum, usado em controles de videogame (PS3, PS4) e celulares. Existem várias formas de usá-lo no sumô:

### 🎮 Usando controle de PS3 ou PS4

Muitas equipes utilizam controles de console. Existem bibliotecas prontas para lidar com eles, desde que o microcontrolador suporte **Bluetooth Classic** (não apenas BLE).

> ⚠️ O ESP32 tradicional suporta Bluetooth Classic. Já os modelos **ESP32-C3** e **S3** **não suportam**, só possuem **BLE**.

![Controle PS4](https://img.youtube.com/vi/hXP_kQ_EbkA/maxresdefault.jpg)  
🧑🏼‍💻 [Tutorial em português ensinando como fazer](https://www.youtube.com/watch?v=hXP_kQ_EbkA)

### 📱 Usando um celular como controle

Não é a forma mais confortável, mas funciona! Para competições iniciais ou testes, pode ser uma boa saída.

![Apps](../img/apps.png)

**Apps recomendados:**
1. [Arduino Bluetooth Controller](https://play.google.com/store/apps/details?id=com.giristudio.hc05.bluetooth.arduino.control)
2. [BT Car Controller - Arduino/ESP](https://play.google.com/store/apps/details?id=com.giristuido.bluetooth.car.controller)
3. [Serial Bluetooth Terminal (debug)](https://play.google.com/store/apps/details?id=de.kai_morich.serial_bluetooth_terminal)

**Recebendo os sinais:**  
Você pode usar módulos clássicos como **HC-05 (Android)** ou **HC-06 (iOS)**. No entanto, hoje em dia, compensa mais usar um **ESP32**, que já possui Bluetooth integrado.

![Bluetooth modules](../img/modulos_bt.png)

---

## 🔀 Mixagem de canais

Mixagem é o processo de combinar dois canais de controle (geralmente velocidade e rotação) para gerar os sinais que vão para os motores.

Isso permite, por exemplo:
- Um canal controla a velocidade (frente/trás)
- Outro controla a rotação (esquerda/direita)

---

### Formas de fazer mixagem:

- **No rádio:** via configurações da própria interface (como nos rádios FlySky)
- **No ESC:** alguns ESCs com dois canais já têm mixagem embutida, ativada por jumper
- **No microcontrolador:** usando código (ideal para quem usa ponte H simples)

---

### Exemplos de mixagem:

As imagens abaixo mostram as formas mais comuns de distribuir os canais em diferentes tipos de controle. O conceito vale tanto para rádios como FlySky quanto para controles como PS4 ou aplicativos de celular.

#### Rádios pistola (TX-4)
O gatilho controla a velocidade e o volante a rotação.

![Mixagem pistola](../img/mix_pistola.png)

#### FlySky com mixagem ativada
Stick vertical controla velocidade; stick horizontal controla rotação.

![Mixagem no FlySky](../img/mix_flisky.png)

#### ❌ FlySky sem mixagem
Cada stick controla uma roda diretamente — o controle fica bem mais difícil.

![Sem mixagem](../img/no_mix_flisky.png)

---

### De onde vem as equações de mixagem?

Elas vêm da **modelagem cinemática inversa**, que calcula as velocidades das rodas a partir da velocidade desejada do robô (linear e angular).  

Aqui estão as equações com limitação de valor:

$$
v_r =
\begin{cases}
2000 & \text{se } ch_2 + ch_1 - 1500 > 2000 \\
1000 & \text{se } ch_2 + ch_1 - 1500 < 1000 \\
ch_2 + ch_1 - 1500 & \text{caso contrário}
\end{cases}
$$

$$
v_l =
\begin{cases}
2000 & \text{se } ch_2 - ch_1 + 1500 > 2000 \\
1000 & \text{se } ch_2 - ch_1 + 1500 < 1000 \\
ch_2 - ch_1 + 1500 & \text{caso contrário}
\end{cases}
$$

**Código**

o código abaixo funciona num Arduino ou ESP com os canais CH1 e CH2 conectados em dois pinos. 

```cpp

void radio_update(){
    
    // Leitura do sinal PWM
    int ch1 = pulseIn(CH1_PIN, HIGH, 25000); // Canal de rotação (ex: stick horizontal)
    int ch2 = pulseIn(CH2_PIN, HIGH, 25000); // Canal de velocidade (ex: stick vertical)

    // limita o sinal
    ch1 = constrain(ch1, 1000, 2000);
    ch2 = constrain(ch2, 1000, 2000);

    // Mixagem
    int vr = constrain(ch2 + ch1 - 1500, 1000, 2000); // Roda direita
    int vl = constrain(ch2 - ch1 + 1500, 1000, 2000); // Roda esquerda

    // [Opcional] Converter as velocidade em sinal PWM para ponte H
    // onde PWM_MAX é o valor máximo de PWM: 255, 1023...
    vr = map( vr, 1000, 2000, -PWM_MAX, PWM_MAX );
    vl = map( vl, 1000, 2000, -PWM_MAX, PWM_MAX );

    // Enviar para os motores ou PWM conforme sua lógica
    setMotorRightSpeed(vr);
    setMotorLeftSpeed(vl);
}
```
## Exemplos

Adicionar futuramente exemplos completos:
- Arduino + HC05 + celular
- Arduino + Receptor + flysky (com pulsein)
- Arduino + Receptor + flysky (com interrupt)
- ESP32 + Bluetooth + Celular
- ESP32 + ESPNOW

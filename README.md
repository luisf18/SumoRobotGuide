# SumoRobotGuide
Um guia para começar da melhor forma nas competições de sumô de robôs.

*Então você quer começar a montar robôs de sumo né? Ótima escolha!*

## 🔗 Outros tópicos disponíveis
- 🛒 [Lojas recomendadas](./lojas.md)
- 💻 [Aplicativos](./apps.md)

## Super Resumo das regras

No sumô de robôs dois robôs disputam em uma arena circular chamada **Dohyo** com o objetivo de empurrar o adversário para fora. As disputas ocorrem em até 3 **rounds**, sendo o terceiro um desempate caso cada um esteja com um ponto. Vence o robô que obtiver 2 pontos de **Yuko**. Essa pontuação também pode ser obtida caso o adiversário cometa alguma infração (mais detalhes nas regras).

Regra mais atual em atividade no brasil:
[Regra2023](./Regras/Regras+-+Sumo_2023_RSM.pdf)  
**Fonte:** Site Robocore

## Categorias de sumô

As categorias de sumô são divididas por peso e dimenssões limite, e podem ser subdivididas em autônomo (**Auto**) ou rádio controlado (**RC**).

| Categoria         | variações | Diâmetro Dohyo | Peso Máximo     | Largura Máx. | Comprimento Máx. | Altura Máx. |
|-------------------|------|-----------|----------|---------------|---------------------|--------------|
| **Nano Sumo**     | Auto | 19,25 cm    | 25 g     | 2,5 cm        | 2,5 cm              | 2,5 cm       |
| **Micro Sumo**    | Auto | 38,5 cm   | 100 g    | 5,0 cm        | 5,0 cm              | 5,0 cm       |
| **Mini Sumo**     | Auto e RC | 77 cm   | 500 g    | 10,0 cm       | 10,0 cm             | Livre        |
| **Mega Sumo**     | Auto e RC | 154 cm    | 3 kg     | 20,0 cm       | 20,0 cm             | Livre        |
| **Sumo LEGO**     | Auto | 77 cm    | 1 kg     | 15,2 cm       | 15,2 cm             | Livre        |

![Alt text](img/categorias.png)

## Videos de demonstração

**obs:** esse video não esta acelerado :P  
[![Assista no YouTube](https://img.youtube.com/vi/tBy5Q2gKjaw/hqdefault.jpg)](https://www.youtube.com/watch?v=tBy5Q2gKjaw)


## Glossário

O sumô de robôs surgiu no japão então a maioria dos termos são em japones, vou destacar aqui os principais.

- **Dohyo**: é a Arena circular onde ocorrem as disputas.
- **Shikiri-sen**: Marcação proxima ao centro da arena que delimita onde os robôs podem ser posicionados.
- **Tawara**: Borda branca do dohyo que serve para indicar ao robô se esta proximo da borda.
- **Round**: Tempo no qual os dois robôs lutam um tentando empurrar o outro para fora
- **Yuko**: pontuação recebida, vence aquele que obtiver dois pontos **Yuko**.

![Alt text](img/Dohyo.png)



## 1 - Mini Sumo

Aviso: A seguir, focar um pouco mais no mini sumo porque é o robô que tenho mais experiência, mas boa parte da teoria se aplica as outras categorias com excessão de alguns tópicos relacionado ao MegaSumo, uma vez que ele usa imãs que alteram drasticamente sua dinâmica.

### X.X - Aspectos gerais

Existem alguns dilemas que são recorrentes no sumo. O objetivo do sumo é empurrar o outro adversário para fora, como realizar isso? A resposta não é unica! Ao longo do tempo foram surgindo algumas soluções e estratégias. Um dilema dos dilemas mais comuns é a questão da Força vs Velocidade, principalmente no Mega Sumo onde da pra ter muita força e ou muita velocidade! Existem outras questões também como estratégia, rampagem, sensoriamento, bandeiras, espetos etc. Estratégias diferentes que ajudar a empurrar o oponente ou dissoadilo.

Principais aspectos de um robô de sumô:

- Força
- Velocidade
- Estratégia
- Sensoriamento
- Rampa ou outro elementos como bandeiras
- Treino, tanto no Auto como no RC para fazer as escolhas mais adequadas

*com isso ja da pra fazer as cartinhas de trunfo* 😂

### 1.1 - Principais peças

Irei Listar e dividir as peças para montar o robo em seções, tentarei ser o mais generalista possivel, cobrindo os tipos de robôs mais comuns. Alguns robôs podem escapar a essa classificação (e isso é ótimo! sinal que a categoria continua viva e trazendo inovações :P).

- **Sistema de locomoção:** Sistema responsável por fazer o robô se mover pelo dohyo, engloba as peças e circuitos relacionados a fazerem o robô se locomover. Em geral: rodas, motores, ESCs ou Pontes H.
- **Sistema de processamento:** Sistema responsável por fazer o robô se mover em função dos sinais do rádio, no caso rádio controlador, ou em função dos sinais dos sensores e estratégias de movimentação. Peças: microcontrolador / placa-mãe.
- **Alimentação:** Sistema repsonsavel por fornecer energia para o robô se mover e energizar suas placas e sensores.
- **Sensoriamento:** Conjunto de sensores utilizados no robô para identificar o ambiente, permitindo que ele identifique o robô adversário, tawara, etc.
- **Estrutura:** A estrutura responsável por manter as peças do robô no lugar desejado, e com o centro de massa no local desejado.
- **Sistemas de luta:** Elementos usados para dissoadir ou empurrar o robô adiversário. Exemplos mais comuns: Rampas, bandeiras e cordas. 
- **Rádio receptor:** Circuito que recebe os sinais do Rádio controle.

---

### Capítulos
- [Força](./tutoriais/force.md)
- [Rampagem](./tutoriais/blade.md)
- [Rodas](./tutoriais/wheels.md)
- [Baterias](./tutoriais/power.md)
- [Rádio comunicação](./tutoriais/radio.md)

### Capítulos em desenvolvimento
- [Motores e seus drivers](./tutoriais/motors.md)
- [Estratégias](./tutoriais/strategy.md)
- [Estrutura](./tutoriais/struct.md)
- [Sensores](./tutoriais/sensors.md)
- [Sistema de locomoção e cinemática](./tutoriais/kinematics.md)


---

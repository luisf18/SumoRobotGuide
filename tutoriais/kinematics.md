# Sistema de Locomoção e Cinemática

O sistema de locomoção é responsável por fazer o robô se mover pelo dohyo. Em cerca de **99,9% dos projetos**, são utilizadas **duas rodas com tração independente**, por serem simples, muito eficientes na transmissão de força e mobilidade do robô. Alguns poucos projetos experimentais utilizam esteiras — e, raramente (nuca kkk), pernas.

> 🤖 **E por que não vemos robôs com pernas?**  
> Embora seja permitido pelas regras, robôs com pernas são difíceis de construir e, nas técnicas de combate atuais, têm menor eficiência. Rodas garantem um robô mais **baixo, estável e previsível**, o que é essencial em lutas de sumô.

---

## 🔍 Comparativo de sistemas de locomoção

| Sistema de locomoção                 | Dificuldade | Eficiência | Distribuição de massa e impacto |
|-------------------------------------|-------------|------------|----------------------------------|
| **2 rodas com rampa na frente**     | Baixa       | Alta       | Parte do peso vai para as rodas (tração) e o restante mantém a lâmina rente ao chão. Ótimo equilíbrio. |
| **4 rodas ou 2 esteiras com rampa** | Média       | Alta       | A tração é alta, mas há pouco peso na lâmina — o que pode atrapalhar a rampagem. |
| **Pernas (hipotético)**             | Alta        | Média-baixa| Pouco estáveis para empurrões diretos, complexas de projetar e controlar. |

---

## Sistema de Locomoção Diferencial

O sistema mais utilizado em mini sumôs é o **diferencial**, onde duas rodas independentes são posicionadas simetricamente. Com esse arranjo, o robô consegue:

1. Mover-se em linha reta (rodas com mesma velocidade e sentido).
2. Girar no próprio eixo (rodas com mesma velocidade e sentidos opostos).
3. Fazer curvas suaves (rodas com velocidades diferentes).

![Movimentos1](../img/move_1.png)
![Movimentos2](../img/move_2.png)

Esse sistema **não permite movimento lateral**, como em robôs com rodas omnidirecionais — mas isso não é uma limitação no sumô, onde controle frontal é o mais importante.

---

### ⚠️ Desafios práticos: "O robô não anda reto!"

Mesmo aplicando sinais idênticos aos motores, é comum o robô desviar levemente. Os motivos principais:

- Diferenças nos motores (mesmo do mesmo lote).
- Assimetria nos pneus (desgaste ou tamanho).
- Distribuição de massa desequilibrada.

![Problema de desvio](../img/loc_problema.png)

---

### ✅ Soluções possíveis e boas práticas:

1. **Construa um robô simétrico:** use motores e rodas iguais, e distribua bem o peso, tente deixa-lo o mais simétrico possivel  

2. **Correção no rádio (modo RC):**  
   Ajuste a curva de resposta ou aplique um fator de correção proporcional ao desvio. Isso ajuda bastante — o resto é **treino do piloto**!

3. **Compensação via sensores (modo autônomo):**  
   Estratégias bem projetadas ajustam as velocidades com base no sensor que está enxergando o oponente. Exemplo:
   - Se os dois sensores veem o inimigo → vá reto.
   - Se só um vê → reduza o lado correspondente até reequilibrar.

4. **Correção com giroscópio (nível avançado):**  
   Use um sensor de rotação (giroscópio) com controle PID (ou outros) para manter o ângulo.  
   > 💡 Pouco comum em sumôs, mas muito eficiente quando bem calibrado.

---

## 📐 Modelagem Cinemática

Vamos agora entender de forma analítica como o movimento do robô depende das velocidades das rodas (**cinemática direta**).

No modelo diferencial, o movimento do robô pode ser decomposto em:

- **Velocidade linear**: $v$  
- **Velocidade angular (rotação)**: $\omega$

> 🔎 *Cinemática direta* descreve o **movimento resultante** do robô ($v$ e $\omega$) a partir das velocidades aplicadas nas rodas ($v_L$ e $v_R$).

As equações da **cinemática direta** são:


$$
v = \frac{v_R + v_L}{2}
$$

$$
\omega = \frac{v_R - v_L}{l}
$$

**Onde:**

- $v_L$, $v_R$: velocidades da roda esquerda e direita (em m/s)  
- $v$: velocidade linear do robô  
- $\omega$: velocidade angular (rad/s)  
- $l$: distância entre as rodas (em m)

---

### 🧪 Exemplos:

1. **Ambas as rodas a 1 m/s e $l = 0{,}01$ m:**

$$
v = \frac{1 + 1}{2} = 1 \text{ m/s} \\
\omega = \frac{1 - 1}{0{,}01} = 0 \text{ rad/s}
$$

➡️ O robô anda em linha reta para frente.

---

2. **Roda direita a 1 m/s e esquerda a -1 m/s:**

$$
v = \frac{1 + (-1)}{2} = 0 \text{ m/s} \\
\omega = \frac{1 - (-1)}{0{,}01} = 200 \text{ rad/s} \approx 1910 \text{ RPM}
$$

➡️ O robô gira no próprio eixo, sem se deslocar.

---

### 📌 Conclusão:

As equações explicam bem o **movimento ideal** do robô, mas **não modelam imperfeições** como atrito desigual, folgas ou diferenças de motor.  
Mesmo assim, são **fundamentais para controle**, e ajudam a entender a mixagem de canais.

🔗 [Mais sobre modelagem cinemática de robôs diferenciais](https://www.cs.columbia.edu/~allen/F17/NOTES/icckinematics.pdf)
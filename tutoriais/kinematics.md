# Sistema de locomo e cinemática

O sistema de locomoção é responsável por fazer o robô se mover no dohyo. 99,9% dos projetos usam rodas por que é uma forma simples e eficiente de trasmitir o movimento dos motores para o robô, alguns raros projetos usam esteiras.

*porque não temos mini sumôs com pernas?*  
Teoricamente é possivel e permitido pelas regras. Apesar de ser muito legal não são adotados por dois motivos principais: Dificuldade de montar e eficiência em relação as rodas consseguem deixar o robô mais baixo e estavel, dificultando que ele seja virado.

| Sistema de locomoção |  dificuldade | eficiência | distribuição de masa |
|----------------------|-----------|------------|------------|
| 2 rodas com rampa na frente | facil | alta | boa parte do peso vai para as rodas proporcionado tração e o restante ajuda a manter a rampa rente ao chão. |
| 4 rodas ou duas esteiras com rampa na frente | médio por conta do espaço | alta | Praticamente todo o peso está nas rodas / esteiras resultando em mais tração e consequentemente força, mas acaba sendo pior para rampar pois não tem tanto peso na rampa para deixala rente ao chão. |
| pernas (hipotético) | alto | médio baixo (tendo em vista as técnicas atuais de combate que envolvem rampar e empurrar) |  |

### 1.2.1 - Sistema de locomoção diferêncial

Em robótica o sistema adotado nos sumôs é chamado de diferencial, nele dois conjunto motor e roda identicos são posicionadas de forma simétrica uma oposta a outra. desta forma temos 3 possibilidades de movimentos:

1. motores com velocidades iguais e mesmo sentido
2. motores com velocidades iguais e sentido oposto
3. motores com velocidades diferentes e mesmo sentido

![Alt text](img/move_1.png)
![Alt text](img/move_2.png)

Perceba que essa disposição permite que o robo se mova em praticamente todas as direções exceto na diretação das roda, ou seja, um movimento lateral. Isso pode ser atingido com rodas omnidirecionais, mas não existem grandes vantagens no seu uso para sumo, em geral, esse sistema ja é o suficiente e funciona bem.

**Problemas dessa forma de locomoção:** Não da pra ganhar todas! O grande problema desse sistema aparece quando são aplicadas tensões iguais nos motores e ele deveria andar perfeitamente em linha reta mas não é oq acontece. A explicação pra isso se deve a asimetrias entre os dois lados do robô, como pequenas diferenças entre os raios da rodas, diferênças no motores (mesmo que tenha nascido da mesma fabrica um ao lado do outro) e diferenças na distribuição de peso entre as rodas.

![Alt text](img/loc_problema.png)

**Solução para o problema:**

1. Busque deixar o robô o mais simétrico possivel, de preferencia com motores e rodas do mesmo fabricante e um projeto que não acumule peso muito de um lado só. Não entre em panico se mesmo assim o robô anida estiver curvando, isso ajuda a reduzir o problema mas sempre haveram assimetrias.
2. Caso o seu robô seja radio controlado isso pode ser compensado no radio, de forma proporcional a velocidade da roda que estiver mais rápida. Com isso ja da pra melhorar bastante o restante é treino do piloto!
3. Caso o seu robô seja autonomo essa diferença não vai afetar muito o desempenho do robô porque geralmente o sensoriamento compensa essa diferênça. Por exemplo: imagine um robô com dois sensores virados para frente um do lado direito e um do esquerdo. Caso ele enxergue um robô na sua frente com os dois sensores ele se move para frente, no entanto como ele se move um pouco curvo uma hora um dos sensores vai parar de enxergar nesse instante a estratégia deve reduzir a velocidade do lado que esta exergando para curvar e manter o robô no seu campo de visão até que os dois voltam a enxergar e assim continua.
4. Solução chique: usar um giroscópio e um controlador que mede a diferença entre a rotação desejada e a rotação real, atuando para reduzir a diferênça a zero. (praticamente ninguém usa kkk mas se estiver bem calibrado funciona muuuito bem)

**Um pouco de matemática:**

Até o momento falei de forma intuitiva sobre o movimento do robô em função das velocidades das rodas. Agora vou ser um pouco mais analítico e apresentar algumas equações — sem me alongar demais. Neste modelo, o movimento é decomposto em velocidade linear de deslocamento ($v$) e rotação ($\omega$):

$$
v = \frac{v_R+v_L}{2}
$$

$$
\omega = \frac{v_R-v_L}{l}
$$

Onde:  
$v_L$ - Velocidade da roda esquerda em m/s.  
$v_R$ - Velocidade da roda direita em m/s.  
$v$ - velocidade linear (tangente à trajetória) em m/s  
$l$ - distancia entre as rodas em metros  
$\omega$ - velocidade angular (rotação em torno do centro entre as rodas) em rad/s  

Essas equações descrevem a oque é chamado em robótica de modelagem cinemática direta do robô, ou seja, elas decrevem o movimento final do robô em função do movimento dos atuadores, que reste caso são os motores das rodas.

Vamos testar essas equações:

1. se tiver uma velocidade de $1m/s$ nas duas rodas e $l=0,01\text{m}$:

$$
v = \frac{1+1}{2} = 1\text{ m/s}
$$

$$
\omega = \frac{1-1}{l} = 0\text{ rad/s}
$$

**ou seja:** o robô de move em linha reta para frente porque $v=1m/s$ positivo e sem fazer curva ja que $\omega = 0$

2. se tiver uma velocidade de $1m/s$ na roda direita e $-1m/s$ na esquerda com $l=0,01\text{m}$:

$$
v = \frac{1-1}{2} = 0 \text{ m/s}
$$

$$
\omega = \frac{1-(-1)}{0,01} = 200\text{ rad/s} \approx 1910 \text{ RPM}
$$

**ou seja:** o robô se rotaciona em torno do próprio eixo mas sem deslocamento.

Em resumo as equações descrevem bem o movimento esperado do robô em função das velocidades das rodas, mas não representam as imprefeições de montagem do robô, tenha isso em mente.  

Essas equações são uteis na mixagem do robô caso precise fazer. Ou caso queira se aprofundar no sistema de controle de movimentação do robô.

[Mais sobre modelagem cinemática de robôs diferenciais](https://www.cs.columbia.edu/~allen/F17/NOTES/icckinematics.pdf)
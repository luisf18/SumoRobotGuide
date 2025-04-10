### 1.3 Estrutura

Fazendo o equilibrio dinâmico do robô, supondo que ele está andando em linha reta com velocidades iguais nas rodas e que não empina.

![Alt text](img/DLC.png)

$$
mg = N_{\text{rodas}} + N_{\text{lâmina}}
$$

$$
ma = F_{\text{rodas}} - F_{\text{lâmina}}
$$

$$
0 = N_{\text{lâmina}}W + maz_{\text{CM}} - mgx_{\text{CM}}
$$

**onde:**

- $N$: força normal  
- $m$: massa do robô  
- $g$: aceleração da gravidade  
- $F$: forças horizontais  
- $W$: distância da roda até a ponta da lâmina  
- $x_{\text{CM}}, z_{\text{CM}}$: coordenadas do centro de massa  

conclusões sobre essas equações:

0. A terceira equação nos lembra que a normal é limitada ao peso do robô, a soma da normal nas rodas e na lamina é igual a força peso.

Se todo o peso estiver nas rodas o robô sera muito forte mas poderá empinar muito facilmente e a rampa não estaram tão rente ao chão. 

Mas se o peso estiver mais na rampa tera muito atrito na rampa e pouca tração nas rodas para ele se locomover. 

O ideal é balancear a normal, deixando um pouco mais nas rodas do que na rampa, não existe uma formula mágica mas algo em torno de cerca de 70% nas rodas e 30% na rampa pode dar bons resultados. Se chamar a proporção do peso nas rodas de $K_{\text{roda}}$

$$
mg = N_{\text{rodas}} + N_{\text{lâmina}}
$$

$$
N_{\text{rodas}} = K_{\text{roda}} mg
$$

$$
N_{\text{rodas}} = ( 1-K_{\text{roda}} ) mg
$$

$$
N_{\text{lâmina}}W = mgx_{\text{CM}} - maz_{\text{CM}}
$$

$$
( 1-K_{\text{roda}} ) = x_{\text{CM}}/W - (a/g)z_{\text{CM}}/W
$$

$$
 K_{\text{roda}} = \left(1 - \frac{x_{\text{CM}}}{W}\right) + a\left(\frac{z_{\text{CM}}}{gW}\right)
$$

1. A terceira equação descreve a condição para o robo não empinar. Caso $N_{\text{lâmina}}$ seja negativo o robô empinou.

$$
0 = N_{\text{lâmina}}W + maz_{\text{CM}} - mgx_{\text{CM}}
$$

No limite de empinar $N_{\text{lâmina}} = 0$ porque ele esta praticamente empinado então a normal na lamina tende a zero. Nesse caso a equação será:

$$
mgx_{\text{CM}} = ma_{\text{limite}}z_{\text{CM}}
$$

$$
a_{\text{limite}} = g\frac{ x_{\text{CM}} }{ z_{\text{CM}} }
$$

**Explicando:** essa equação descreve a aceleração máxima para que o robô não empine. ou seja, quanto menor o centro de massa menor $z_{\text{CM}}$ fazendo com que a aceleração limite seja maior e de preferencia impossivel de ser alcançada.

**Aprendizado:** Quanto menor o centro de massa e mais longe das rodas mais estavel. Como o centro de massa não pode estar muito distante da roda então a solução é reduzir sua altura.




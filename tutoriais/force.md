# Força 🦾

A primeira coisa que vem à cabeça no sumô é: **quem for mais forte, vence**. E de fato, um robô mais forte tem mais chances de empurrar o adversário para fora — mas essa força só é eficaz se algumas condições forem atendidas:

1. **É preciso alcançar o oponente.**  
   No caso de robôs rádio controlados, isso depende da habilidade do piloto. Já nos autônomos, é o conjunto de sensores e a estratégia embarcada no microcontrolador que define como o robô encontra e ataca o adversário.

2. **É preciso se manter em contato sem ser repelido.**  
   Imagine dois robôs em formato de caixa, sem rampas ou lâminas: qualquer contato permite empurrar o outro. Agora, se um deles tiver lâminas, espetos ou rampas mal posicionadas, pode acabar sendo rampado ou até virado ao fazer contato — o que abre espaço para estratégias mais elaboradas de combate.  


**Como ser “mais forte”?**  
   A força que o robô consegue aplicar depende diretamente da tração das rodas no chão. Essa força de tração é limitada pelo atrito — e se ele for superado, as rodas derrapam, desperdiçando energia.

A equação clássica do atrito é:

$$
F_{at} = N\mu
$$

Onde:  
- $F_{at}$ é a força de atrito máxima antes de derrapar;  
- $N$ é a força normal (basicamente o peso sobre a roda);  
- $\mu$ é o coeficiente de atrito entre roda e piso.

Portanto, para maximizar a força:
- Use **materiais com alto coeficiente de atrito** (como alguns silicones que chegam a $\mu = 1{,}7$ em madeira);
- **Aumente a normal nas rodas**, ou seja, distribua mais peso sobre elas.

Como a gravidade é constante, a única forma de aumentar a força peso ($P=mg$) é aumentar a **massa do robô** — daí a limitação de peso nas categorias, para manter a competição justa.

Por fim, é importante **equilibrar o peso** entre rodas e lâmina.  
O ideal é concentrar a maior parte da força normal nas rodas, mas manter uma fração na lâmina ajuda a mantê-la rente ao chão, melhorando a estabilidade e a capacidade de rampar o oponente. Mais detalhes sobre distribuição de peso na parte de estrutura.

---
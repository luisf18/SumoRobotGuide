# Rodas ou esteiras

As rodas (ou esteiras) são essenciais em robôs de sumô — são elas que transmitem a força gerada pelos motores para o movimento real do robô no dohyo. A escolha certa pode fazer toda a diferença no desempenho.

---

## 🔍 O que buscar em uma roda:

- **Coeficiente de atrito**  
  Quanto maior o atrito entre o pneu e o chão, maior a força máxima do robô.

  $$
  F \leq N_{\text{rodas}} \mu_{\text{estático}} \quad \text{(sem derrapagem)}
  $$  

  $$
  F = N_{\text{rodas}} \mu_{\text{dinâmico}} \quad \text{(com derrapagem)}
  $$

- **Diâmetro da roda**  
  Rodas menores aumentam a força transmitida ao solo, aproveitando melhor o torque dos motores. Por outro lado, reduzem a velocidade máxima.  

$$
F = \frac{\tau_{\text{motor}}}{r_{\text{roda}}}
$$

$$
v = r_{\text{roda}} \cdot \omega_{\text{motor}}
$$

- **Largura**  
  As rodas para mini sumo devem ser largas para ajudar a distribuir a força pela seção transversal do pneu, evitando que ele venha a romper.

---

## Materiais

- **Pneus:**  
  Normalmente feitos de silicone, por sua alta aderência e maciez — características ideais para obter o máximo atrito com o dohyo.

- **Hub (núcleo da roda):**  
  Conecta o eixo do motor ao pneu. Geralmente feitos de alumínio ou aço (para maior inércia e pressão sobre o solo).  
  Também podem ser impressos em 3D, pode ser uma boa alternativa para quem esta começando.

---

## 🛒 Onde adquirir

**🇧🇷 No Brasil:**  
A [Robocore](https://www.robocore.net/busca/StickyMAX) vende hubs de alumínio e pneus com diferentes graus Shore (unidade que indica a maciez).

![](https://d229kd5ey79jzj.cloudfront.net/939/images/939_2_H.png?20250210105650)

**🌍 Fora do Brasil:**  
A [JSUMO](https://www.jsumo.com/silicone-wheel-sets) oferece uma grande variedade de rodas e hubs. As de **33×20 mm** são bastante populares e, entre as que testei, estão entre as que oferecem melhor atrito.

![](https://www.jsumo.com/slt20-aluminum-silicone-wheel-set-33mmx20mm-pair-38-19-B.jpg)

**🔧 Opções DIY:**  
Para quem gosta de colocar a mão na massa, é possível **fazer seus próprios pneus de silicone**. Já testei e, com paciência, dá pra obter resultados excelentes. O hub pode ser impresso em 3D.  
👉 [Veja esse tutorial completo](https://mcuoneclipse.com/2017/12/28/making-perfect-sticky-diy-sumo-robot-tires/) com testes comparativos e passo a passo da fabricação.

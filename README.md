# Cellular Automaton & Game JiangNanHurry

## Introduction
My zero-copy undergraduate work (award grade A), a Processing-based cellular automaton and a Unity-based 3D game around COVID-19 topic, implemented by C# and Java.

## Video demonstration

**Cellular Automaton** -> https://www.bilibili.com/video/BV1F54y1R7UC

**Game JiangNanHurry** -> https://www.bilibili.com/video/BV1Xp4y1D76t

<img src="https://github.com/fwyc0573/COVID-19Topic/blob/main/fig/4.4.jpg" height="250" />   <img src="https://github.com/fwyc0573/COVID-19Topic/blob/main/fig/fig1.png" height="250" /><br/>

<!-- ![screen2](https://github.com/fwyc0573/HurryJiangNan/blob/main/fig/fig1.png) -->

## Project Overview

### Modelling and analysis
I first modeled the transmission of COVID-19 and predicted the number of infections for the infectious disease model based on the paper 《Modified SEIR and AI prediction of the epidemics trend of COVID-19 in China under public health interventions》. I refined the SEIR model to be a new one, called SEIPRD, by adding the two cases of death and isolation classes.

<!-- fig2 fig3 -->
<!-- fig4 -->

```
def SEIPRD_model(self, population, t):
    param = np.zeros(6)
    S, E, I, P, R, D = population
    param[0] = - self.beta_1 * S * I / self.N - self.beta_2 * E * S / self.N #dS/dt
    param[1] = self.beta_1 * S * I / self.N + self.beta_2 * E * S / self.N - self.xigema * E  #dE/dt
    param[2] = self.xigema * E - self.gamma * I - self.p * I - self.d * I#dI/dt
    param[3] = self.p * I - self.gamma * P #dP/dt
    param[4] = self.gamma * I + self.gamma * P  # dR/dt
    param[5] = self.d * I # dD/dt
    return param
```


<img src="https://github.com/fwyc0573/COVID-19Topic/blob/main/fig/fig4.png" height="100" />  <img src="https://github.com/fwyc0573/COVID-19Topic/blob/main/fig/fig5.png" height="100" />   <img src="https://github.com/fwyc0573/COVID-19Topic/blob/main/fig/fig6.png" height="100" />   <img src="https://github.com/fwyc0573/COVID-19Topic/blob/main/fig/fig7.png" height="100" /><br/>


### Cellular Automaton

I applied an improved model SEIRD (with the addition of the death class) to model the writing of cellular automata, which is a system consisting of cellular objects whose state shifts over time. 

The cellular automaton contains a total of six modes: basic mode, vaccination mode, isolation measures mode, population density mode, age segmentation mode, and super-spreader mode.


<div align=center>
<img src="https://github.com/fwyc0573/COVID-19Topic/blob/main/fig/1.2.jpg" height="150" />  <img src="https://github.com/fwyc0573/COVID-19Topic/blob/main/fig/1.3.jpg" height="150" /><img src="https://github.com/fwyc0573/COVID-19Topic/blob/main/fig/2.3.jpg" height="150" />  <img src="https://github.com/fwyc0573/COVID-19Topic/blob/main/fig/2.4.jpg" height="150" />
 
<img src="https://github.com/fwyc0573/COVID-19Topic/blob/main/fig/3.1.jpg" height="150" />  <img src="https://github.com/fwyc0573/COVID-19Topic/blob/main/fig/3.2.jpg" height="150" /><img src="https://github.com/fwyc0573/COVID-19Topic/blob/main/fig/4.3.jpg" height="150" />  <img src="https://github.com/fwyc0573/COVID-19Topic/blob/main/fig/4.4.jpg" height="150" />
    
<img src="https://github.com/fwyc0573/COVID-19Topic/blob/main/fig/5.3.jpg" height="150" />  <img src="https://github.com/fwyc0573/COVID-19Topic/blob/main/fig/5.4.jpg" height="150" /><img src="https://github.com/fwyc0573/COVID-19Topic/blob/main/fig/6.1.jpg" height="150" />  <img src="https://github.com/fwyc0573/COVID-19Topic/blob/main/fig/6.3.jpg" height="150" />
</div>


### Game JiangNanHurry

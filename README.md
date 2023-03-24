# Cellular Automaton & Game HurryJiangNan

## Introduction
My undergraduate work (award grade A), a Unity-based 3D game and a Processing-based cellular automaton around the COVID-19 topic, implemented by C# and Java.

## Video demonstration

**Cellular Automaton** -> https://www.bilibili.com/video/BV1F54y1R7UC
**Game HurryJiangNan** -> https://www.bilibili.com/video/BV1Xp4y1D76t

<!-- ![screen2](https://github.com/fwyc0573/HurryJiangNan/blob/main/fig/fig1.png) -->

## Project Overview

### Modelling and analysis
I first modeled the transmission of COVID-19 and predicted the number of infections for the infectious disease model based on the paper 《Modified SEIR and AI prediction of the epidemics trend of COVID-19 in China under public health interventions》.

<!-- fig2 fig3 -->


```
def SEIR_model(self, population, t):
    param = np.zeros(4)
    S, E, I, R = population
    r = 3  #  Number of contacts per capita
    param[0] = - self.beta_1 * r * S * I / self.N - self.beta_2 * r * E * S / self.N#dS/dt
    param[1] = self.beta_1 * S * r * I / self.N + self.beta_2 * r * E * S / self.N - self.xigema * E  #dE/dt
    param[2] = self.xigema * E - self.gamma * I  #dI/dt
    param[3] = self.gamma * I  #dR/dt
    return param
```
<!-- fig4 -->

Then, I refined the SEIR model to be a new one, called SEIPRD, by adding the two cases of death and isolation classes.
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

### Cellular Automaton




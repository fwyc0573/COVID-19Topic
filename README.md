# Cellular Automaton & Game JiangNanHurry

## Introduction
My zero-copy undergraduate work (grade A awarded), a Processing-based cellular automaton and a Unity-based 3D game around COVID-19 topic, implemented by C# and Java.

## Video demonstration

**Cellular Automaton** -> https://www.bilibili.com/video/BV1F54y1R7UC

**Game JiangNanHurry** -> https://www.bilibili.com/video/BV1Xp4y1D76t

<img src="https://github.com/fwyc0573/COVID-19Topic/blob/main/fig/4.4.jpg" height="250" />   <img src="https://github.com/fwyc0573/COVID-19Topic/blob/main/fig/fig1.png" height="250" /><br/>

<!-- ![screen2](https://github.com/fwyc0573/HurryJiangNan/blob/main/fig/fig1.png) -->

## Cellular Automaton

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


### Cellular Automaton Implementation

I applied an improved model SEIRD (with the addition of the death class) to model the writing of cellular automata, which is a system consisting of cellular objects whose state shifts over time. 

The cellular automaton contains a total of six modes: basic mode, vaccination mode, isolation measures mode, population density mode, age segmentation mode, and super-spreader mode.


<div align=center>
<img src="https://github.com/fwyc0573/COVID-19Topic/blob/main/fig/1.2.jpg" height="150" />  <img src="https://github.com/fwyc0573/COVID-19Topic/blob/main/fig/1.3.jpg" height="150" /><img src="https://github.com/fwyc0573/COVID-19Topic/blob/main/fig/2.3.jpg" height="150" />  <img src="https://github.com/fwyc0573/COVID-19Topic/blob/main/fig/2.4.jpg" height="150" />
 
<img src="https://github.com/fwyc0573/COVID-19Topic/blob/main/fig/3.1.jpg" height="150" />  <img src="https://github.com/fwyc0573/COVID-19Topic/blob/main/fig/3.2.jpg" height="150" /><img src="https://github.com/fwyc0573/COVID-19Topic/blob/main/fig/4.3.jpg" height="150" />  <img src="https://github.com/fwyc0573/COVID-19Topic/blob/main/fig/4.4.jpg" height="150" />
    
<img src="https://github.com/fwyc0573/COVID-19Topic/blob/main/fig/5.3.jpg" height="150" />  <img src="https://github.com/fwyc0573/COVID-19Topic/blob/main/fig/5.4.jpg" height="150" /><img src="https://github.com/fwyc0573/COVID-19Topic/blob/main/fig/6.1.jpg" height="150" />  <img src="https://github.com/fwyc0573/COVID-19Topic/blob/main/fig/6.3.jpg" height="150" />
</div>



## Game JiangNanHurry

The player has to find the potion, which can cures COVID-19, hidden in the building as soon as possible and use it on the required number of sick students to pass the game. The map of the game is based on the 3D modeling of my undergraduate university, where each student has his or her own routine (e.g. classes, meals, etc.) The contagion of COVID-19 is based on the SEIRD model.

The game plot is divided into 2 main stages:
- Phase 1: The player must maintain the indicators by implementing specific measures (buttons and sliders at the top left of the screen) and must search the map to find the medicine as quickly as possible. If any two of the indicators score less than 60 or are infected then the challenge fails; if the player succeeds in picking up the potion while maintaining the indicators, he/she will successfully enter the second stage.
- Stage 2: Find the potent medicine. Players will be required to apply the potent medicine to the required number of sick students within the time limit. If the player completes the task within the time limit, he/she succeeds; if not, he/she fails.


### Script Organization and Class Diagrams
<img src="https://github.com/fwyc0573/COVID-19Topic/blob/main/fig/15.png" height="170" />  <img src="https://github.com/fwyc0573/COVID-19Topic/blob/main/fig/16.png" height="170" />  <img src="https://github.com/fwyc0573/COVID-19Topic/blob/main/fig/17.png" height="170" />
</br>

### Maps, Architectural Design and Modelling
<img src="https://github.com/fwyc0573/COVID-19Topic/blob/main/fig/13.png" height="190" />  <img src="https://github.com/fwyc0573/COVID-19Topic/blob/main/fig/14.png" height="190" />  <img src="https://github.com/fwyc0573/COVID-19Topic/blob/main/fig/18.png" height="190" />

<img src="https://github.com/fwyc0573/COVID-19Topic/blob/main/fig/21.png" height="151" />  <img src="https://github.com/fwyc0573/COVID-19Topic/blob/main/fig/19.png" height="151" />  <img src="https://github.com/fwyc0573/COVID-19Topic/blob/main/fig/20.png" height="151" />
</br>

### Game Characters and State Machines
<img src="https://github.com/fwyc0573/COVID-19Topic/blob/main/fig/22.png" height="141" />  <img src="https://github.com/fwyc0573/COVID-19Topic/blob/main/fig/23.png" height="141" />  <img src="https://github.com/fwyc0573/COVID-19Topic/blob/main/fig/24.png" height="141" />
</br>




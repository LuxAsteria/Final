# Final
###2014301020172 尹梦迪 物基二班 大三
***
##Quantum Mechanics
***
###Abstract
![img](https://github.com/LuxAsteria/test3/blob/master/i_CjvqCksE8bVdnvPI9RXw%253D%253D%252F8796093022260942412.jpeg)

The number of problems which can be solved precisely is small, most notably the harmonic oscillator, a particle trapped in a box and the hydrogen atom. Here, we are going to investigate some quantum problems numerically, including the motion of a particle in a box( the time-independent schödinger equation), the transation of the wavepacket in 1-d situation( the time-dependent schödinger equation) as well as the transation of wavepacket in 2-d situation. 

The first problem is the easiest one, which could be solved using array and simple loops. The last one, because it is a 2-d problem, we need to take advantage of matrixs to calculate. What's more, for the reason that the function used to solve the wave function contained more than one variable, one is associated with time, another one is associated with position, so after i'd referred to some documents, the calculation successfully be done by utilizing leapfrog method. The second problem can be better understood by showing it in animation, and in this assignment i'v achieved that.
***
###Introduction
***
####Theory
####Time-independent schödinger equation:some preliminaries
The time-independent Schödinger equation for a particle in three dimensions is:

<img src="http://latex.codecogs.com/gif.latex?-\frac{\hbar^{2}}{2m}\nabla^{2}\Psi+V(\vec{r})=E\Psi" alt="" title="" />        (1.1)

Where <img src="http://latex.codecogs.com/gif.latex?\hbar" alt="" title="" /> is Planck's constant, m is the mass of the particle, V is the potential energy, E is the energy of the particle,<img src="http://latex.codecogs.com/gif.latex?\Psi" alt="" title="" />is the wave function. As is well known with quantum theory, it is much easier to write this equation down than to reallly understand it. The key quantity here is the wave fucntion, which has no direct classical counterpart. In the most general case, <img src="http://latex.codecogs.com/gif.latex?\Psi" alt="" title="" />is a complex function of position and, when properly normalized, <img src="http://latex.codecogs.com/gif.latex?\Psi(\vec{r})*\Psi(\vec{r})" alt="" title="" /> is the probability per unit volume that the particle will be found at <img src="http://latex.codecogs.com/gif.latex?\vec{r}" alt="" title="" />

 First consider the 1-d situation.
 
 ![img](https://github.com/LuxAsteria/test3/blob/master/shijing.jpg)
 
 Then the equation could be simplified :
 
 <img src="http://latex.codecogs.com/gif.latex?-\frac{\hbar^{2}}{2m}\frac{d^{2}\Psi}{dx^{2}}=E\Psi" alt="" title="" />   
 (1.2)
 
 It has a general solution:
 
 <img src="http://latex.codecogs.com/gif.latex?\Psi=Ae^{ikx}" alt="" title="" />
 
 The first method to solve the problem will be the shooting and matching methods. According to the prerequists, we have <img src="http://latex.codecogs.com/gif.latex?\Psi(0)=0" alt="" title="" /> and <img src="http://latex.codecogs.com/gif.latex?\frac{d\Psi}{dt}\not=0" alt="" title="" /> at x=0
 
 Some process had been skipped for simplicity, and to calculate, we can use the equation bellow:
 
 <img src="http://latex.codecogs.com/gif.latex?\Psi_{n+1}=2\Psi_{n}-\Psi_{n-1}-2\Delta(x)^{2}(E-V_{n})\Psi_{n}" alt="" title="" /> 
 (1.3)
 
 ###Time-dependent Schödinger equation:Direct solution(1d)
 The time-dependent Schödinger equation could be expressed as:
 
 <img src="http://latex.codecogs.com/gif.latex?-\frac{\hbar^{2}}{2m}\nabla^{2}\Psi+V(\vec{r})\Psi=i\hbar\frac{\partial\Psi}{\partial(t)}" alt="" title="" /> 
 (2.1)
 
 The left-hand part can be subsititude by the Hamiltonian operator H. After a series of calculation, we can finally obtain:
 
 <img src="http://latex.codecogs.com/gif.latex?\Psi(m+1,n+1)+[2i\lambda-2\Delta(x)^{2}V(m)-2]\Psi(m,n+1)+\Psi(m-1,n+1)=-\Psi(m+1,n)+[2i\lambda+2\Delta(x)^{2}V(m)+2]\Psi(m,n)-\Psi(m-1,n)" alt="" title="" /> 
 (2.2)
 
 In which<img src="http://latex.codecogs.com/gif.latex?\lambda=\frac{2\Delta(x)^{2}}{\Delta(t)}" alt="" title="" /> 
 
 We can set the initial state as:
 
 <img src="http://latex.codecogs.com/gif.latex?\Psi(x,t=0)=Ce^{\frac{-(x-x_{0})^{2}}{\sigma^{2}}}e^{ik_{0}x}" alt="" title="" /> 
 
 It's noticable that here the wave function has 2 parts: the real part and the imaginary part. Apparently, it's difficult us to do the numerical calculation for the wave function of different positions are mingled with each other on the left side. To seperate them, thanks for the hint given by the textbook, we can use leapfrog method.
 
 ###Time-dependent Schödinger equation: 2 dimension
 When it comes to the 2d situation, definitely, the equation will be more complicated:
 
 <img src="http://latex.codecogs.com/gif.latex?\nabla^{2}R(x,y,t)=\frac{R(x+\Delta(x),y,t)-2R(x,y,t)+R(x-\Delta(x),y,t)}{\Delta(x)^{2}}+\frac{R(x,y+\Delta(y),t)-2R(x,y,t)+R(x,y-\Delta(y),t)}{\Delta(y)^{2}}=\frac{R(x+\Delta(x),y,t)+R(x-\Delta(x),y,t)+R(x,y+\Delta(y),t)+R(x,y-\Delta(y),t)-4R(x,y,t)}{\Delta(x)^{2}}" alt="" title="" /> 
 (3.1)
 
 Here, we need apply matrix to the problem.
 ***
###Solution
 
 First, the wave will be reflected when it hits a 'wall'.
 
 
 ![img](https://github.com/LuxAsteria/test3/blob/master/wall.png)
 
 ![img](https://github.com/LuxAsteria/test3/blob/master/wall1.png)
 
 ![img](https://github.com/LuxAsteria/test3/blob/master/屏幕快照%202017-01-01%20下午6.08.19.png)
 
 
 The wave could be discribed in 2 parts: the imaginary part and the real part.
 
 ![img](https://github.com/LuxAsteria/test3/blob/master/wave%20conj.png)
 
 The imaginary part:
 
 ![img](https://github.com/LuxAsteria/test3/blob/master/wavepimg.png)
 
 The real part:
 
 ![img](https://github.com/LuxAsteria/test3/blob/master/waveprea%3B.png)
 
 [For code please click here](https://github.com/LuxAsteria/Final/blob/master/code)
 ***
 When it comes to the time-dependent schödinger equation (1d), we can see the evolution of wave clearly in the following animation:
 Ps: in the first animation, v=-1x10<sup>6</sup>(when x>0.6),v=0(when x< 0.6), x is ranging from 0 to 1, dx=0.0001,dt=5x10<sup>-7</sup>,c=10,k=500,x0=0.4; while in the second animation, all the variables are the same, except that v times -1.
 
 ![anim](https://github.com/LuxAsteria/test3/blob/master/wavepacket.gif)
 
 ![anim](https://github.com/LuxAsteria/test3/blob/master/wavepacket2.gif)
 
 [For code please click here](https://github.com/LuxAsteria/Final/blob/master/code)

***
Let's investigate the time-dependent Schödinger equation(2d),and show the situation of wave in 3-d and 2-d pictures. 
From the first to the last one, they are arranged in order of time, 2 pictures (one 3-d and another one is 2-d) forms a group.

###t=0
![img](https://github.com/LuxAsteria/test3/blob/master/屏幕快照%202017-01-01%20下午4.13.17.png)

![img](https://github.com/LuxAsteria/test3/blob/master/t%3D03d.png)


###t=0.0003
![img](https://github.com/LuxAsteria/test3/blob/master/k%3D302d.png)

![img](https://github.com/LuxAsteria/test3/blob/master/k%3D30.png)


###t=0.0008
![img](https://github.com/LuxAsteria/test3/blob/master/k%3D502d.png)

![img](https://github.com/LuxAsteria/test3/blob/master/k%3D50.png)


###t=0.001
![img](https://github.com/LuxAsteria/test3/blob/master/k%3D802d.png)

![img](https://github.com/LuxAsteria/test3/blob/master/k%3D80.png)


###t=0.0015
![img](https://github.com/LuxAsteria/test3/blob/master/k%3D1002d.png)

![I](https://github.com/LuxAsteria/test3/blob/master/k%3D100.png)


###t=0.0018
![img](https://github.com/LuxAsteria/test3/blob/master/k%3D130.png)

![img](https://github.com/LuxAsteria/test3/blob/master/k%3D1303d.png)


[For code please click here](https://github.com/LuxAsteria/Final/blob/master/code)

***
###Conclusion
After all, we are happy to see that the numerical method could be applied in solving quantum mechanic problems. The leapfrog method appears to be relatively useful when it comes to investigating second-order problems.However, it's remarkable that the value of dx will conspicuously influence the calculation, when dx is too small, the wave function will diverge before it comes to the wall, while if the value is too large, the function will hardly appear to be a 'wave'(or move).
***
###Acknowledge

[1]Computational Physics, Edition 2, Nicholas J.Giordano


'
##ps:all rights reserved!

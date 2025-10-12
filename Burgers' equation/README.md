# Burgers' 2D equations

$$
\begin{aligned}
\frac{\partial u}{\partial t} + u \frac{\partial u}{\partial x} + v \frac{\partial u}{\partial y} &= \nu \left( \frac{\partial^2 u}{\partial x^2} + \frac{\partial^2 u}{\partial y^2} \right), \\
\frac{\partial v}{\partial t} + u \frac{\partial v}{\partial x} + v \frac{\partial v}{\partial y} &= \nu \left( \frac{\partial^2 v}{\partial x^2} + \frac{\partial^2 v}{\partial y^2} \right),
\end{aligned}
$$

where:
- $u(x, y, t)$ and $v(x, y, t)$ are the velocity components in the $x$ and $y$ directions,
- $\nu$ is the kinematic viscosity,
- $t$ is time.

These are Burgers' equations for 2D. these are derived from Navier strokes equations by taking following assumptions:
## Assumptions to Derive the 2D Burgers' Equation from Navier–Stokes

1. **Neglect pressure gradient**  
   The pressure term $\nabla p$ is dropped to focus purely on convection and diffusion effects. This simplifies the equations by removing the need to solve for pressure.

2. **No external forces**  
   External body forces like gravity are ignored, further simplifying the model.

3. **Relaxed incompressibility**  
   In some versions of the Burgers' equation, the incompressibility condition  
   $\frac{\partial u}{\partial x} + \frac{\partial v}{\partial y} = 0$  
   is dropped to simplify the analysis or numerical solution.

4. **Simplified 2D velocity field**  
   Both velocity components $u(x, y, t)$ and $v(x, y, t)$ are retained, but the flow is treated in a simplified 2D framework without pressure coupling.

## Concept of ML
You don't need to solve those equations don't worry, just knowing how to do differentiation is sufficient for this task. In this task you need to explore the concept of Physics in Deep Learning. It's fine if you hate physics, for now just take this as math.

Explore the concepts of PINN, create your own dataset (synthetic), train a PINN, optimize the loss function and predict.
Once you done those you might think this is unnecessary but believe me if you felt so then you did something wrong. create a small training dataset still you will achive great accuracy

## Task Instruction
steps:

- Create synthetic Burgers' 2D dataset with varying $\nu$ and it should be time series too
- visualize them, explain how the patterns look
- create a grouped split for train and test i.e. train dataset and test dataset should not have anything in common, even $\nu$ (then only you will see the greatness of PINN)
- visualize and compare true with predicted
- Try adding noise and see how well it avoids noise, and what hyper parameters need to be changed to get better results with lot of noise

## Note

The task you will do is far for reality as this is a synthetic dataset, I appriciate a lot if you could find a real dataset (not only Burgers' equation) with real world senarios or physics solver data points and train your PINN on it. 🥲

There are a lot of other crazy CFD problems out there. There are majorly 3 catogaries
1. Heat Transfer
2. Mass transfer
3. fluid flow

These are where PINN are mostly used. But it can be used anywhere either if there is a lot of noise on something that was supposed to follow physics or if there are PDEs that are very complex to solve.

Hope this task opens you a new niche in Data Science for you

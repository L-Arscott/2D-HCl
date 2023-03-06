# 2D-HCl simulation

## Crystalisation of 2D HCl molecules
Atoms are treated as point-like. We observe crystallisation (the formation of a regular pattern) as the molecules are cooled. Cooling of the molecules is achieved by placing the system in a simulated temperature bath.  
Periodic boundary conditions are in effect.


<p float="left">
  <img src="https://user-images.githubusercontent.com/64332150/223279770-517bf702-da41-4f83-bc38-073e1a26a440.gif">
  <img align = "top" src="https://user-images.githubusercontent.com/64332150/223276367-50ad6ff6-a059-4837-a1b4-401f18b40504.jpg" width="150">
</p>



## Evolution of potential energies
Here a step represents 50 ns.
![4_pot_graphs](https://user-images.githubusercontent.com/64332150/223277696-e8acd356-1a62-4f3a-b991-4796e1a00563.png)

Potential energy of all kinds clearly decrease over time. The temperature bath removes excess kinetic energy, while the system enters a more energetically favourable state over time, minimising energy stored in bonds, electrostatic interactions, and van der Waals interactions.

## Final state: radial distribution function
![rdf](https://user-images.githubusercontent.com/64332150/223277915-08ffbd4b-351d-4faf-afbf-8b0242165d73.png)

The first spike is obviously due to the bonded atom. The next two spikes are also very pronounced and it takes a fairly large distannce r for fluctuations to start disappearing. This suggests long range ordering and shows our molecules have crystalised.

## Task Details
This task is a Molecular Dynamics Simulation of two-dimensional Hydrochloric acid.

Particles are initiated in a 2D box.

Three forces will are at play :
Bond forces will pair Hydrogen and Chlorine atoms together. They modelled according to a harmonic oscillator :

$$\vec{F_{bond, a, b}} = -k\left(|\vec{x_{a}} - \vec{x_{b}}| - r_{0}\right)\dfrac{\vec{x_{a}} - \vec{x_{b}}}{|\vec{x_{a}} - \vec{x_{b}}|}$$

All particles except particles within the same molecule interact via Coulomb forces:

$$\vec{F}_{Coul}(\vec{r}_{i, j})=\dfrac{1}{4\pi\varepsilon_{0}}\dfrac{q_{i}q_{j}}{r^{2}_{i, j}}\dfrac{\vec{r_{i, j}}}{r_{i, j}}$$

Finally, Chlorine atoms interact via van der Waals forces:

$$\vec{F_{LJ}}=\left(12\dfrac{C_{12}}{r_{i, j}^{13}} - 6\dfrac{C_{6}}{r_{i, j}^{13}}\right)\dfrac{\vec{r_{i, j}}}{r_{i, j}}$$

Particles will be moved according to the leap frog algorithm.
The Berendsen thermostat is used to simulate coupling to a heat bath.

Particles are initialised at a temperature of 10 000K, while a heat bath cools them down to 100K.

The goal is to observe crystalisation of the HCl molecules.

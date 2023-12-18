In low energy physics, scattering is a standard tool to explore [[solid state]] systems, for example: [[neutron scattering]], [[electron scattering]], [[x-ray scattering]].

## Phase Shifts

> answer from [this](https://physics.stackexchange.com/questions/8132/phase-shifts-in-scattering-theory/8324#8324) stack question

Suppose you treat scattering of a particle in a central potential. This means that the Hamiltonian $H$ commutes with the angular momentum operators $L^2$ and $L_z$. Hence, you can find simultaneous eigenfunctions $\psi_{k,l,m}$. 

You might know, for example from the solution of the hydrogen atom, that these functions can be expressed in terms of the spherical harmonics:

$$\psi_{k,l,m}(x) = R_{k,l}(r) \Psi_m^l(\theta, \varphi)$$
where the radial part satisfies

$$\frac{1}{r^2} \frac{d}{dr} \left( r^2 \frac{dR_{k,l}}{dr}\right)

+\left(n^2 - U(r) - \frac{l(l+1)}{r^2}\right) R_{k,l} = 0$$
with $U(r) = 2m/\hbar^2 V(r)$, your central potential, and $k$ is the particle's wavenumber, i.e., $E = \frac{\hbar^2 k^2}{2m}.$



The first step is to look for a special case with simple solutions. This would be the **free particle**, with $U(r) = 0$. Then, the radial equation is a special case of Bessel's equation. The solutions are the *spherical Bessel functions* $j_l(kr)$ and $n_l(kr)$, where the $j_l$ are *regular* at the origin whereas the $n_l$ are *singular* at the origin. Hence, for a free particle, the solutions are superpositions of the $j_l$:

$$\psi(x) = \sum_{l,m} a_{l,m} j_l(kr) Y^l_m(\theta, \varphi)$$



If we also have axial symmetry, only $m = 0$ is relevant. Then we can rewrite the spherical harmonics using Legendre polynomials. This will lead to

$$\psi(x) = \sum_{l,m} A_{l} j_l(kr) P_l(\cos \theta)$$

One important special case of such an expansion is the **Rayleigh plane wave expansion**

$$e^{ikz} = \sum_l (2l+1) i^l j_l(kr) P_l(\cos\theta)$$

which we will need in the next step.



We move away from free particles and consider scattering from a potential with a **finite range** (this excludes Coulomb scattering!). So, $U(r) = 0$ for $r > a$ where $a$ is the range of the potential. For simplicity, we assume axial symmetry. Then, *outside* the range, the solution must be again that of a free particle. But this time, the origin is not included in the range, so we can (and, in fact, must) include the $n_l(kr)$ solutions to the Bessel equations:

$$\psi(r) = \sum_l (a_l j_l(kr) + b_l n_l(kr)) P_l(\cos \theta)$$

Note how the solution for a given $l$ has two parameters $a_l$ and $b_l$. We can think of another parametrization: $a_l = A_l \cos\delta_l$ and $b_l = -A_l \sin \delta_l$. The reason for doing this becomes apparent in the next step:



The spherical Bessel functions have *long range approximations*:

$$j_l(kr) \sim \frac{\sin(kr - l\pi/2)}{kr}$$

$$n_l(kr) \sim \frac{\cos(kr - l\pi/2)}{kr}$$

which we can insert into the wavefunction to get a long range approximation. After some trigonometry, we get

$$\psi(r) \sim \sum_l \frac{A_l}{kr} \sin(kr - l\pi/2 + \delta_l) P_l(\cos \theta)'$$

So, this is what our wavefunction looks like for large $r$. **But** we already know how it *should* look: if the incoming scattered particle is described as a plane wave in $z$-direction, it is related to the scattering amplitude $f$ via

$$\psi(\vec{x}) \sim e^{ikz} + f(\theta) \frac{e^{ikr}}{r}.$$

Obviously, both forms for writing down a long-range approximation for $\psi$ should give the same, so we use the Rayleigh plane wave expansion to rewrite the latter form. We also rewrite the $\sin$ function using complex exponentials. The ensuing calculations are a bit tedious, but not complicated in itself. You just insert the expansions. What we can do afterwards is comparing the coefficients in both expressions for the same terms, e.g. equation the coefficients for $e^{-ikr}P_l(\cos\theta)$ will give you

$$A_l = (2l+1)i^l e^{i\delta_l}$$

whereas equating coefficients for $e^{ikr}$ gives you

$$f(\theta) = \frac{1}{2ik} \sum_l (2l+1) \left( e^{2i\delta_l} - 1 \right) P_l(\cos \theta).$$



**Interpretation of the Phase Shift:** Remember the long range limit of the wavefunction. It led to an expression for the $l$-th radial wavefunction in the long-range of

$$u_l(r) = kr\psi_l(r) \sim A_l \sin(kr - l\pi/2 +\delta_l).$$

For a free particle, the phase shift $\delta_l$ would be $0$. One could therefore say that the phase shift measures how far the asymptotic solution of your scattering problem is displaced at the origin from the asymptotic free solution.



**Interpretation of the Partial Wave Expansion:** In the literature, you will often come across terms such as $s$-wave scattering. The partial wave expansion decomposes the scattering process into the scattering of incoming waves with definite angular momentum quantum number. It explains in which way $s$-, $p$-, $d$-waves etc. are affected by the potential. For low energy scattering, only the first few $l$-quantum numbers are affected. If all but the first term are discarded, only the $s$-waves take part in the scattering process. This is an approximation that is, for example, made in the scattering of the atoms in a Bose-Einstein condensate.

In an ideal experiment we begin with a sharp beam of particles (A), with a definite [[momentum]], that are scattering from a local target (B).

The collision can be [[elastic collisions]] or [[inelastic collisions]]. [[Absorption]] is also possible.

We want to find the [[Scattering Theory#Scattering Cross Section |Scattering Cross Section]] $\sigma$. 
### Scattering Cross Section






## Scattering in a Central Potential

[Source](https://archive.int.washington.edu/users/mjs5/Class_560/lec560_2/node1.html)

Consider a wave-packet that is scattering of a centre. We want to find the probability of finding the particle in the wave packet to be at some angle wrt to the initial direction. 

A wave-packet is contains many plane waves and we reduce the problem to individual plane waves, which can later be [[convolved]] to approximate the wave-packet. 

The plane wave is $e^{ikz}$, where $k = |k| = \sqrt{2 \mu E}$, with $\mu$ as the [[reduced mass]].

The plane wave can be expanded, into [[angular momentum states]], in the z-direction

$$
e^{ikz} = e^{ikr \cdot cos\theta} = \sum_{l=0} (2l +1) i^{l} j_{l}(kr) P_l (cos \theta)
$$


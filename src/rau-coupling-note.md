Hey Nic,

Yes, the next step is to include the coupling to the electric field. This is usually done in these case via the vector potential, using that

$$
E = -\frac{dA}{dt}
$$

This is better for our purposes that using a scalar potential since to implement a uniform $E$ you'd need $V(x) = -Ex$ which would break translation invariance. By using $A$ we maintain translation invariance and get the benefits of Bloch's theorem. The vector potential appears with the momentum as

$$
\frac{(p + eA)^2}{2m} + V(x) = \text{const.} + \left(\frac{p^2}{2m} + V(x)\right) + \frac{e}{m}A(t)\cdot p
$$

where $p$ is the usual momentum operator. Now using the plane-wave basis you've got a set of eigenstates of that first part $(p^2/2m+V(x))$ in the form

$$
\psi_n(x) = \sum_G e^{i(k+G)x} C_n(G)
$$

where those $C_n(G)$ are the eigenvectors for your diagonalization. So in that basis we've got

$$
\left(\frac{p^2}{2m}+V(x)\right)\psi_n(x) = E_n \psi_n(x)
$$

So in this basis this first part is diagonal.

Our next goal is to include the time-dependent field and so we've got to write the $\frac{e}{m}A(t)\cdot p$ part in this basis -- that's what Shubham's notes are doing. Basically you need to compute all the matrix elements
of the momentum operator in this basis:

$$
\int dx\cdot\psi^*_n(x)\cdot \left(\frac{e}{m}A(t)\cdot \hat{p}\right) \cdot \psi_m(x) = \frac{e}{m}A(t)\int\psi_n(x) \hat{p} \psi_m(x)dx
$$

This can be reduced using the decomposition of psi_n(x) into plane-waves as in Shubham's notes, but it'll be non-diagonal. Once we've got that we'll stick this all into the TDSE and use a numerical ODE solver to compute the wave-fcn as it changes in time.

\- Jeff Rau

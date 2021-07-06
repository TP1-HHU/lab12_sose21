# Lab 12
### Nonlinear Schrödinger equation
----
In this lab, you will implement a second-order splitting method for the nonlinear Schrödinger equation

<p align="center">
<img src="stuffy_stuff/nls1.png" width="250">
</p>

The problem can be re-formulated as
<p align="center">
<img src="stuffy_stuff/nls2.png" width="180">
</p>
where
<p align="center">
<img src="stuffy_stuff/nls3.png" width="180">.
</p>

The operator in the formal solution 
<p align="center">
<img src="stuffy_stuff/nls4.png" width="300">
</p>

is approximated as (Strang splitting)

<p align="center">
<img src="stuffy_stuff/nls5.png" width="400"> .
</p>

Thus, one time-step formally becomes

<p align="center">
<img src="stuffy_stuff/nls6.png" width="300"> .
</p>

----

To calculate what the linear operator *L* does, we use an
implicit Euler scheme or the semi-implicit Crank-Nicholson method
to solve
<p align="center">
<img src="stuffy_stuff/nls7.png" width="130">.
</p>

The implicit Euler gives the system of linear equations
<p align="center">
<img src="stuffy_stuff/nls8.png" width="400">.
</p>

This can be solved using a slightly adapted version of the 
`step`-function of lab 11.

---

For the time-step with the nonlinear operator *N*, we make use of the
local (i.e. for every *x*) conservation of <img src="stuffy_stuff/f3.png" width="25">.

The nonlinear time-step becomes
<p align="center">
<img src="stuffy_stuff/nls10.png" width="270">.
</p>


---

Complete the program skeleton by inserting two new functions: `lin_step`
and `nlstep`, which propagate the solution according to the linear and
the nonlinear operator.

You can test these two functions independently. If you only apply the 
linear operator, the initially localized wave-packet should disperse
as you are simulating the potential-free Schrödinger equation.
If you only apply the nonlinear operator, then you should see only 
variations of the real and imaginary part of the solution, but not
of <img src="stuffy_stuff/f3.png" width="25">.

---

Plot in GNUplot using
`do for [i=0:50]{p 'psi_'.i; pause 0.1;set yr[0:0.4]} `

sepsisLDS
=========

An implementation of EM on an LDS with a known input, following Blocker (2008). I assume the affine term=0.

The equations per patient are:

$x_t = F x_{t-1} + B u_t + \epsilon_t, \epsilon_t ~ N_k(0,Q)$

$z_t = h + H x_t + \omega_t, \omega_t ~ N_n(0, R)$ for $t \in [0, T]$.

Import data and create initial "guesses" for the parameters {F, B, H, Q, R}.

Data should be formatted as follows: column1=heart rate, column2=pressors, column3=ringers, column4=saline. The first column name is assumed to be 'HR'.

Method for estimate.py: Given the parameters and the last known value in the test set, compute the estimated current hidden state. Now, plug this value and the values for $u$ at the next time step into the transition model and solve for the estimated next hidden state. Plug this value into the observation model to solve for the estimated next observation.

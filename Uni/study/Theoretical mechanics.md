#uni
# Dynamics of material points
## Center of mass
$$
\overline{r_c} = \frac{\sum_{k = 1}^n m_k \overline{r_k}}{\sum_{k =1}^n m_k}
$$
$$
m\overline{r_c} = \int \overline{r} \ dm
$$
## Dynamical structures
Let $\overline{Q}$ be the momentum, $\overline{K}$ be the angular momentum, $T$ be the kinetic energy
### Momentum structure
#### The law of momentum conservation

$$
\overline{Q} = m\overline{v} 
$$
$$
\overline{Q} = \sum_{k =1}^n m_k \overline{v_k}
$$
The isolated system has $\overline{Q} = const$

#### The Newton's second law
$$
m_k \ddot{\overline{r_k}} = \overline{F_k} \ \ \ \ \ (1)
$$
Let $\overline{F^e}$ be external forces and $\overline{F^i}$ be internal forces
$$
\dot{\overline{Q}} = \overline{F^e}
$$
### Angular momentum structure
$$
\overline{K} = \overline{r} \times \overline{Q}
$$
$$
\overline{K} = \sum_{k=1}^nm_k \overline{r_k} \times \dot{\overline{r_k}} = \sum_{k=1}^n \overline{r_k} \times \overline{Q_k}
$$
#### The law of angular momentum conservation
$$
\dot{\overline{K}} = \overline{M^e}
$$
$\overline{M^e}$ is the external angular momentum

Multiply (1) on both sides by $\overline{r_k}$ from the left
$$
\frac{d}{dt}(m_k\overline{r_k} \times \dot{\overline{r_k}}) = m_k\overline{r_k} \times \ddot{\overline{r_k}}
$$
We will get
$$
m_k\overline{r_k} \times \ddot{\overline{r_k}} = \overline{r_k} \times \overline{F_k} = \overline{r_k} \times (\overline{F_k^e} + \overline{F_k^i})
$$


After all we got the initial formula

#### The movement of the center of mass theorem
$$
m_k \ddot{\overline{r_k}} = \overline{F_k^e}
$$
$$
\sum_{k=1}^nm_k\ddot{\overline{r_k}} = \overline{F^e}
$$

The system of material points moves as a whole. We can substitute it with the center of mass and consider its movement by sum of external forces

#### The center of mass kinetic moment
$$
\overline{K} = \sum_k m_k\overline{r_k} \times \dot{\overline{r_k}}
$$
Let $\overline{r_k} = \overline{r_c} + \overline{\rho_k}$
$$
\overline{K} = \sum_k m_k(\overline{r_c} + \overline{\rho_k}) \times (\dot{\overline{r_c}} + \dot{\overline{\rho_k}}) = \sum_k m_k\overline{r_c} \times \dot{\overline{r_c}} + \sum_k m_k\overline{\rho_k} \times \dot{\overline{\rho_k}} + \sum_k m_k\overline{r_c} \times \dot{\overline{\rho_k}} + \sum_k m_k\overline{\rho_k} \times \dot{\overline{r_c}}
$$
$\sum_k m_k\overline{\rho_k} \times \dot{\overline{\rho_k}} = 0$ and  $\sum_k m_k\overline{r_c} \times \dot{\overline{\rho_k}} = 0$ therefore
$$
\overline{K} = \sum_k m_k(\overline{r_c} + \overline{\rho_k}) \times (\dot{\overline{r_c}} + \dot{\overline{\rho_k}}) = \sum_k m_k\overline{r_c} \times \dot{\overline{r_c}} + \sum_k m_k\overline{\rho_k} \times \dot{\overline{r_c}} = \sum_k m_k\overline{r_c} \times \dot{\overline{r_c}} + \overline{K_c}
$$
We have the following result
$$
\overline{K} = m\overline{r_c} \times \dot{\overline{r_c}} + \overline{K_c}
$$
$$
\overline{M^e} = \sum_k \overline{r_k} \times \overline{F_k} = \sum_{k=1}^n (\overline{r_c} + \overline{\rho_k}) \times \overline{F^e_k} = \overline{r_c} \times \overline{F^e} + \overline{M_c}
$$
Therefore
$$
\overline{M^e} = \overline{r_c} \times \overline{F^e} + \overline{M_c^e} = \dot{\overline{K}}
$$
and
$$
m\overline{r_c} \times \ddot{\overline{r_c}} + \overline{K_c} = \overline{r_c} \times \overline{F^e} + \overline{M_c^e}
$$

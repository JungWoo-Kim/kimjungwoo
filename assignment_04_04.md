## 1. General Instruction

#### (1) github history

- you have to make `git commit` and `git push` at least 5 times for each notebook file
- you can write a message for `git commit -m "MESSAGE"` as you want for your information
- you can use any name for the branch to commit and you can use as many branches as you want
- you have to submit your github history for all the notebook files in PDF format

#### (2) python notebook

- you have to fill up all the blanks in each notebook
- you can add your own functions and produce intermediate results at any place within the codes block
- you have to use the given functions to produce final results without any extra codes within the results block
- you can write comments in MARKDOWN format at any place in each notebook for your information

## 2. Finite difference

Let $`f : \Omega \mapsto \mathbb{R}`$ be a function $`f(x, y)`$where $`(x, y) \in \Omega`$ denotes its 2-dimensional domain. 

#### (1) First-order Derivative

- forward difference

```math
\frac{\partial f}{\partial x}(x, y) = \frac{f(x+h, y) - f(x, y)}{h}
```

```math
\frac{\partial f}{\partial y}(x, y) = \frac{f(x, y+h) - f(x, y)}{h}
```

- backward difference

```math
\frac{\partial f}{\partial x}(x, y) = \frac{f(x, y) - f(x-h, y)}{h}
```

```math
\frac{\partial f}{\partial y}(x, y) = \frac{f(x, y) - f(x, y-h)}{h}
```

- central difference

```math
\frac{\partial f}{\partial x}(x, y) = \frac{f(x+h, y) - f(x-h, y)}{2 h}
```

```math
\frac{\partial f}{\partial y}(x, y) = \frac{f(x, y+h) - f(x, y-h)}{2 h}
```

#### (2) Second-order Derivative

```math
\frac{\partial^2 f}{\partial x^2}(x, y) = \frac{f(x+h, y) - f(x, y)}{h} - \frac{f(x, y) - f(x-h, y)}{h}
```

```math
\frac{\partial^2 f}{\partial y^2}(x, y) = \frac{f(x, y+h) - f(x, y)}{h} - \frac{f(x, y) - f(x, y-h)}{h}
```

```math
\frac{\partial^2 f}{\partial x^2}(x, y) = \frac{f(x+h, y) + f(x-h, y) - 2 f(x, y)}{h}
```

```math
\frac{\partial^2 f}{\partial y^2}(x, y) = \frac{f(x, y+h) + f(x, y-h) - 2 f(x, y)}{h}
```

#### (3) Gradient operator

```math
\nabla f(x, y) = \left( \frac{\partial f}{\partial x}(x, y),  \frac{\partial f}{\partial y}(x, y) \right)
```

#### (4) Laplace operator

```math
\Delta f(x, y) = \nabla \cdot \nabla f(x, y) = \frac{\partial^2 f}{\partial x^2}(x, y) + \frac{\partial^2 f}{\partial y^2}(x, y)
```

```math
\Delta f(x, y) = \frac{f(x+h, y) + f(x-h, y) + f(x, y+h) + f(x, y-h) - 4 f(x, y)}{h}
```

## 3. Heat Equation

Let $`u : \Omega \times \mathbb{N} \mapsto \mathbb{R}`$ be a function $`u(x, y ; t)`$where $`(x, y) \in \Omega`$ denotes its 2-dimensional spatial domain and $`N`$ denotes its 1-dimensional temporal domain. 

#### (1) Isotropic diffusion process


```math
\frac{\partial u}{\partial t} (x, y : t) = \Delta u(x, y : t)
```

- initial condition

```math
u(x, y ; 0) = f(x, y)
```

- Neumann boundary condition
  
```math
\frac{\partial u}{\partial n}(x, y ; t) = 0 
```

- discretisation

```math
\frac{u(x, y ; t + \delta t) - u(x, y ; t)}{\delta t} = \Delta u(x, y : t)
```

```math
u(x, y ; t + \delta t) - u(x, y ; t) = \delta t \left( \Delta u(x, y : t) \right)
```

```math
u(x, y ; t + \delta t) = u(x, y ; t) + \delta t \left( \frac{u(x+h, y ; t) + u(x-h, y ; t) + u(x, y+h ; t) + u(x, y-h ; t) - 4 u(x, y ; t)}{h} \right)
```

#### (2) Algorithm

```python
delta_t           = 0.1
h                 = 1
number_iteration  = 100
u                 = f

for t in range(number_iteration):

   u_x_forward    = compute_derivative(data = u, direction = x, scheme = forward, boundary_condition = neumann)
   u_x_backward   = compute_derivative(data = u, direction = x, scheme = backward, boundary_condition = neumann)
   u_y_forward    = compute_derivative(data = u, direction = y, scheme = forward, boundary_condition = neumann)
   u_y_backward   = compute_derivative(data = u, direction = y, scheme = backward, boundary_condition = neumann)

   laplace_u      = (u_x_forward - u_x_backward + u_y_forward - u_y_backward) / h
   u              = u + delta_t * laplace_u 
```

## 4. Complete the notebook 

- download the notebook file [assignment_04.ipynb](https://gitlab.com/byungwoohong/class-machine-learning-2021-1/-/blob/master/assignment/04/assignment_04.ipynb)
- complete the blank in the codes so that the expected outputs can be produced
- you have to use your own image other than the one given in the notebook file
- parameter selection
    - $`\delta t = 0.1`$
    - $`h = 1`$

## 5. list of submission

1. completed notebook file in PDF format
2. github history in the course of completiing the notebook file in PDF format

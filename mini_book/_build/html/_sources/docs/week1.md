---
jupytext:
  text_representation:
    extension: .md
    format_name: myst
kernelspec:
  display_name: Python 3
  language: python
  name: python3
---

(week1)=

# Week1 - overview of ODEs

## Overview of ordinary differential equations (ODEs)
- linear -> superposition
- nonlinear -> cannot solve
- constant coefficients are nice.

## First order linear ODEs
- general form: $$\frac{dy}{dt} = ay + q(t) \text{ or } \frac{dy}{dt} = a(t)y + q(t)$$
- rate of change: $$\frac{dy}{dt}$$

### Examples of first order ODE. 
solve and assume y(0)=1.
1. $$\frac{dy}{dt}=y \rightarrow y(t)=e^{t}$$
2. $$\frac{dy}{dt}=-y \rightarrow y(t)=e^{-t}$$
3. $$\frac{dy}{dt}=2ty \rightarrow y(t)=e^{t^{2}}$$
4. $$\frac{dy}{dt}=y^{2} \rightarrow y(t)=\frac{1}{1-t}$$


## Second order linear ODEs
- second order derivative indicates acceleration or curvature: $$\frac{d^{2}y}{dt^{2}}$$
- Hooke's Las: $$\frac{d^{2}y}{dt^{2}} = -ky$$
- fundamental equation of mechanics $$my''+by'+ky=f(t),$$ where by' implies dampling.

## System of n equations
- first order system, A is a n by n matrix: $$\frac{d\vec{y}}{dt}=A\vec{y}$$
- second order system, S is a matrix: $$\frac{d^{2}\vec{y}}{dt^{2}}=-S\vec{y}$$

## Numerical solutions
- MATLAB ode45
- neural network to solve ODEs
- ChatGPT to solve ODEs (BE CAREFULL!)

## Partial differential euqations (PDEs)
- heat equation: $$\frac{\partial u}{\partial t}=\frac{\partial^{2} u}{\partial x^{2}}$$
- wave equation: $$\frac{\partial^{2} u}{\partial t^{2}}=\frac{\partial^{2} u}{\partial x^{2}}$$
- Laplace equation: $$\frac{\partial^{2} u}{\partial x^{2}}+\frac{\partial^{2} u}{\partial y^{2}}=0$$

## The calculus you need
- derivitives of functions: $$x^{n}, \sin{x}, \cos{x}, e^{x}, \ln{x}$$
- rules for derivatives:
	- sum rule
	- product rule
	- quotient rule
	- chain rule: $$\frac{dy}{dt}=\frac{dy}{dx}\frac{dx}{dt}$$
- fundamental theorem of calculus:

$$
  \int_{a}^{b} \frac{dy}{dx}\,dx = y(b) - y(a)
$$

$$
  \frac{d}{dx}\int_{a}^{x} f(s)\,ds = f(x)
$$

### An example, use all rules
Show that below function y(t) solves $$\frac{dy}{dt}=y+q{t},$$ where q(t) is an external source term. 
\begin{eqnarray*}
y(t) &=& \int_{0}^{t}e^{t-s}q(s)\,ds\\
\Longrightarrow y(t) &=& \int_{0}^{t}e^{t-s}q(s)\,ds = e^{t}\int_{0}^{t}e^{-s}q(s)\,ds\\
\Longrightarrow \frac{dy}{dt} &=& e^{t}\int_{0}^{t}e^{-s}q(s)\,ds + e^{t}(e^{-t}q(t)) = y(t) + q(t)
\end{eqnarray*}

## Tangent line to a graph
- Taylor expansion series: 
\begin{eqnarray*}
f(t+\Delta t) \approx f(t)+\Delta t\frac{df}{dt}(t) + \frac{\Delta t^{2}}{2!}\frac{d^{2}f}{dt^{2}}(t)+\cdots + \frac{\Delta t^{n}}{n!}\frac{d^{n}f}{dt^{n}}(t)
\end{eqnarray*}

## Discretized differentiation
$$\frac{dy}{dx} \approx \frac{\Delta y}{\Delta x}$$
- approximate y:
$$\Delta y \approx \frac{dy}{dx}\Delta x \rightarrow y(x_{o}+\Delta x) \approx y(x_{o})+\Delta x\frac{dy}{dx}(x_{o}), \text{ assuming we know } \frac{dy}{dx}$$
- Newton's method (finding roots):
\begin{eqnarray*}
\Delta x \approx \frac{\Delta y}{\frac{dy}{dx}} \rightarrow x_{1} - x_{o} = \frac{y(x_{1})-y(x_{o})}{\frac{dy}{dx}(x_{o})}
\end{eqnarray*}
- central difference
\begin{eqnarray*}
\frac{dy}{dx}\approx \frac{\Delta y}{\Delta x} = \frac{y(x+\frac{1}{2}\Delta x)-y(x-\frac{1}{2}\Delta x)}{\Delta x}
\end{eqnarray*}

## Solve our first ODE
\begin{eqnarray*}
\frac{dy}{dt} = ay, \text{ given } y(0) = y_{o}
\end{eqnarray*}
We don't know how to solve, but we can guess the exponential-type solution:
\begin{eqnarray*}
y(t) = Ae^{\alpha t}, \text{ and so the problem is to find } A \text{ and } \alpha.
\end{eqnarray*}
\begin{eqnarray*}
\frac{dy}{dt} = A\alpha e^{\alpha t} \Longrightarrow \alpha = a \Longrightarrow y(t) = Ae^{at}
\end{eqnarray*}
\begin{eqnarray*}
y(0) = y_o{} = Ae^{a\times 0} = A \Longrightarrow y(t)=y_{o}e^{at}
\end{eqnarray*}
- if a>0, then the solution grows exponentially
- if a<0, then the solution decays exponentially

## Geometry veiw of ODEs
analytic vs geometry:
\begin{eqnarray*}
y'(t)=f(x,y) \leftrightarrow \text{ direction field}\\\\
\text{solution } y(x) \leftrightarrow \text{ integral curve}
\end{eqnarray*}

## Superposition
- additivity
\begin{eqnarray*}
F(x_{1}+x_{2}) = F(x_{1}) + F(x_{2})
\end{eqnarray*}
- homogeneity (porportionality a is a scaler)
\begin{eqnarray*}
F(ax) = aF(x)
\end{eqnarray*}
- use additivity and homogeneity, we can derive:
\begin{eqnarray*}
F(ax_{1}+bx_{2}) = aF(x_{1}) + bF(x_{2}),
\end{eqnarray*}
which is also called linear combination

### Linear ODEs?
- are they linear ODEs?
\begin{eqnarray*}
y'=ky, \\
y'+y^{3}t=y,\\
y'+\cos{x}y=x^{3},\\
\frac{y'}{y}=t^{2},\\ 
x^{2}yy'+4x=x^{3}
\end{eqnarray*}
- show below ODE does not satisify superposition.
\begin{eqnarray*}
y'+y^{2}=q(t)
\end{eqnarray*}

## Existence and uniqueness
For the linear first-order ODE, we are not touching the existence, as it is hard to prove consdering the scale of this class. On the other hand, the uniqueness is rather straightforward. Consider

\begin{eqnarray*}
\frac{dy}{dt} + ay = q(t), y(0)=y_{0}
\end{eqnarray*}

Assume two solutions are different
\begin{eqnarray*}
y_{1}(t) \neq y_{2}(t), \forall t
\end{eqnarray*}

\begin{eqnarray*}
\frac{y_{1}}{dt}&+&ay_{1}=q(t)\\\\
\frac{y_{2}}{dt}&+&ay_{2}=q(t)\\\\
\end{eqnarray*}

Subtract the two equation, we can get

\begin{eqnarray*}
\frac{d(y_{1}-y_{2})}{dt} + a(y_{1}-y_{2}) = 0
\end{eqnarray*}

Let 
\begin{eqnarray*}
Y&=&y_{1}-y_{2}, Y(0)=0\\\\
&\Longrightarrow& \frac{dY}{dt}=-aY\\\\
&\Longrightarrow& Y=e^{-at}, \forall t\\\\
&\Longrightarrow& Y(0) = 0 = A \\\\
&\Longrightarrow& Y(t) = 0, \forall t \\\\
&\Longrightarrow& y_{1}(t) = y_{2}(t), \forall t.
\end{eqnarray*}

This is a contradiction! So the two solutions have to be the same for all t.

## Homogeneous ODE and solution
Consider
\begin{eqnarray*}
\frac{dy}{dt} = ay, y(0)=y_{0}
\end{eqnarray*}

Assume solution is in exponential form
\begin{eqnarray*}
y(t) = Ae^{\alpha t}.
\end{eqnarray*}

Plug it into the ODE
\begin{eqnarray*}
A\alpha e^{\alpha t} = aAe^{\alpha t} \rightarrow \alpha = a \rightarrow y(t)=Ae^{at}
\end{eqnarray*}

Use initial condition, we can get
\begin{eqnarray*}
y(0)=y_{0}=Ae^{a\cdot 0}=A \rightarrow y(t) = y_{0}e^{at}
\end{eqnarray*}

## Solution structure
Consider the ODE with initial condition
\begin{eqnarray*}
\frac{dy}{dt}=ay+q(t), \text{  given } y(0),
\end{eqnarray*}
where q(t) is the source term.

We can separate solution into two parts:

- homogeneous solution or null solution with no source term, which comes from y(0):
\begin{eqnarray*}
\frac{y_{h}}{dt} = ay_{h}.
\end{eqnarray*}

- particular solution, which comes from q(t):
\begin{eqnarray*}
\frac{y_{p}}{dt} = ay_{p} + q(t)
\end{eqnarray*}

- general solution or complete solution
\begin{eqnarray*}
y(t) = y_{h}(t) + y_{p}(t)
\end{eqnarray*}












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

(lecture3)=

# Lecture3 - integrating factor, separable equations, and exact solution, 

## Integrating factor
Consider the first-order ODE:

\begin{eqnarray}
\frac{dy}{dt} = a(t)y + q(t).
\end{eqnarray}

Note that now a is a function of t. We solve it by an integrating factor M (M(0)=1):

$$
\frac{dM}{dt} = -a(t)M.
$$

If a is a constant, then
$$
M = e^{-at}.
$$

If a is a function of t, then
$$
M = e^{-\int_{0}^{t}a(s)ds}.
$$

The idea is to consider My and make it in the form of a total derivative:
$$
\frac{dMy}{dt} = \frac{dy}{dt}M - a(t)My = Mq
$$

Integrate both side from 0 to t, we can get:
$$
M(t)y(t) - M(0)y(0) = \int^{t}_{0} M(s)q(s)ds
$$

$$
\rightarrow M(t)y(t) = y(0) + \int^{t}_{0} M(s)q(s)ds
$$

Divided by M on both sides:
$$
y(t) = y(0)e^{\int^{t}_{0} a(s)ds} + \frac{\int^{t}_0{M(s)q(s)ds}}{e^{-\int^{t}_0{a(s)ds}}}
$$

$$
\rightarrow y(t) = y(0)e^{\int^{t}_{0} a(s)ds} + \int^{t}_0{e^{-\int^{s}_0{a(T)dT}}q(s)ds}\cdot e^{\int^{t}_0{a(k)dk}}
$$

$$
\rightarrow y(t) = y(0)e^{\int^{t}_{0} a(s)ds} + \int^{t}_0{e^{\int^{t}_0{a(k)dk - \int^{s}_0{a(T)dT}}}q(s)ds}
$$

```{note}
If a is a constant, above equation gives "the formula" for very particular solution:
$$
y_{vp}(t) = \int^{t}_0{e^{a(t-s)}q(s)ds}
$$

And the complete solution is:
$$
y(t) = y(0)e^{at} + \int^{t}_0{e^{a(t-s)}q(s)ds}
$$


```


```{note}
In engineering school or discipline, people use different notations.
 
"Geometrically, the general solution of an ODE is a family of infinitely many solution curves, one for each value of the constant c. If we choose a specific c, we obtain what is called a particular solution of the ODE. A particular solution does not contain any arbitrary constants." from Advanced Engineering Mathematics by Erwin Kreyszig.

We call them [general solution] and [particular solution], respectively.
```

````{prf:example}
Using integrating factor to solve
$$
t\frac{dy}{dt}-y=t^{3}
$$

1. Rearrange equation: $$\frac{dy}{dt}-\frac{1}{t}y = t^{2} \rightarrow \frac{dy}{dt} = \frac{1}{t}y +  t^{2}$$

2. Integrating factor: M(t) = $$e^{-\int \frac{1}{t}dt} = e^{-ln(t)} = \frac{1}{t}$$ 

3. Rearrange equation: $$\frac{1}{t}\frac{dy}{dt} - \frac{1}{t^2}y = t $$

4. Take integration: $$\frac{d\frac{y}{t}}{dt} = t \rightarrow \frac{y}{t} = \frac{1}{2}t^{2}+C \rightarrow y=\frac{t^3}{2}+Ct$$

Use initial condition to get C.

````

## Separable equations
Consider ODE in the form:

$$
\frac{dy}{dt} = \frac{g(t)}{f(y)}.
$$

Then we can get and solve for y(t):
$$
\int_{y(0)}^{y(t)} f(y)dy = \int_{0}^{t}g(s)ds.
$$

````{prf:example}
$$
\frac{dy}{dt} = \frac{t}{y} \rightarrow \int_{y(0)}^{y(t)} ydy = \int_{0}^{t}tdt = \frac{1}{2}t^2
$$

$$
\rightarrow \frac{1}{2}y(t)^{2} - \frac{1}{2}y(0)^{2} = \frac{1}{2}t^2
$$

$$
\rightarrow y(t)^{2} = y(0)^{2} + t^{2} \rightarrow y(t) = \pm\sqrt{y(0)^{2} + t^{2}}
$$

Note that y(0) allows y=t and y=-t.

````

## Exact solution
Consider ODE in the form:
$$
\frac{dy}{dt} = \frac{g(y,t)}{f(y,t)}
$$






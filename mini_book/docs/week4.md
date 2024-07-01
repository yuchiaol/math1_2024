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

(week4)=

# Week4 -  fundamental equation of mechanics

\begin{eqnarray*}
&mx''& = &-kx& - &cx'&\\
&\uparrow& &\uparrow& &\uparrow&\\
&\text{Force (Newton)}& &\text{spring (Hooke)}& &\text{dash pot/damping}&
\end{eqnarray*}

\begin{eqnarray*}
\Longrightarrow mx''+cx'+kx=0\\\\
\Longrightarrow x''+ \frac{c}{m}x'+ \frac{k}{m}x=0
\end{eqnarray*}

```{figure} /_static/figures/car_ode.jpeg
:scale: 10%
:name: car
```

## Second order linear (homogeneous) ODEs
- to find two independent solutions (homogeneous solutions)
- general form: 
\begin{eqnarray*}
\frac{d^{2}y}{dt^{2}}+A\frac{dy}{dt}+By=0, \text{ given } y(0)=1, y'(0)=0.
\end{eqnarray*}
- basic method guess and plug in the exponential solution:
\begin{eqnarray*}
\text{try } y(t)&=&e^{rt}\\\\ 
\rightarrow r^{2}e^{rt} + Are^{rt} &+& Be^{rt} = 0\\\\
\rightarrow r^{2} + Ar &+& B = 0 \text{ characteristic equation}.
\end{eqnarray*}

- we can solve r:
\begin{eqnarray*}
r=\frac{-A\pm \sqrt{A^{2}-4B}}{2}
\end{eqnarray*}

## Case1: two real roots (overdamping)
\begin{eqnarray*}
r_{1} \neq r_{2} \rightarrow y(t)=c_{1}e^{r_{1}t}+c_{2}e^{r_{2}t}
\end{eqnarray*}

````{prf:example}
:label: my-example1

\begin{eqnarray*}
y''+4y'+3y=0, y(0)=1, y'(0)=0
\end{eqnarray*}

The characteristic equation is
\begin{eqnarray*}
r^{2}&+&4r+3=0\\\\
&\Longrightarrow& (r+3)(r+1)=0 \rightarrow r=-3, -1\\\\
&\Longrightarrow& y(t)=c_{1}e^{-3t}+c_{2}e^{-t}
\end{eqnarray*}

Use initial conditions
\begin{eqnarray*}
y(0)&=&1=c_{1}+c_{2}, \\\\
y'(0)&=&0=-3c_{1}-c_{2}\\\\
&\Longrightarrow& c_{1}=\frac{-1}{2}, c_{2}=\frac{3}{2}\\\\
&\Longrightarrow& y(t)=\frac{-1}{2}e^{-3t}+\frac{3}{2}e^{-t}
\end{eqnarray*}
````

```{note}
Why the solutions are always "damped"? Can you link this result to the value of r?
```

- the plot for possible solutions y(t):
```{figure} /_static/figures/overdamp.png
:scale: 50%
:name: overdamp
```

## Case2: two equal roots (critical damping)
\begin{eqnarray*}
r_{1} = r_{2} = -a \rightarrow (r+a)^{2}=0 \rightarrow r^{2}+2ar+a^{2}=0.
\end{eqnarray*}

So the ODE can be expressed as:
\begin{eqnarray*}
y''+2ay'+a^{2}y=0.
\end{eqnarray*}

Now we only have one solution:
\begin{eqnarray*}
y(t)=e^{-at}=y_{1}(t)
\end{eqnarray*}

But we need one more. Let's try this:
\begin{eqnarray*}
\text{let } y_{2}(t)=u(t)y_{1}(t)\\\\
a^{2}&\times& (y_{2} = ue^{-at})\\\\
2a&\times& (y_{2}'=u(-ae^{-at}) +u'e^{-at})\\\\
1&\times& (y_{2}''=a^{2}e^{-at}u-ae^{-at}u'-ae^{-at}u'+e^{-at}u'')\\\\
&\Longrightarrow& 0 = 0 + 0 + e^{-at}u''\\\\
&\Longrightarrow& u'' = 0 \rightarrow u'=c_{1} \rightarrow u(t) = c_{1}t+c_{2}.
\end{eqnarray*}

We take another solution and obtain the general solution:
\begin{eqnarray*}
y_{2}(t) &=& te^{-at}\\\\
y(t) &=& Cy_{1}(t) + Dy_{2}(t) = Ce^{-at}+Dte^{-at}
\end{eqnarray*}

## Case 3: complex roots (undamped/underdamped)
We get the complex solution
\begin{eqnarray*}
y_{c}(t) = e^{(a+bi)t} = u + iv, \text{ where } u, v \in \mathbb{R}
\end{eqnarray*}

````{prf:theorem}
:label: my-theorem

If u+iv is the complex solution to

\begin{eqnarray*}
y''+Ay'+By = 0,
\end{eqnarray*}

where A and B are real. Then u and v are real solutions.

````

````{prf:proof}
:class: dropdown
Plug the complex solution into the ODE:

\begin{eqnarray*}
(u+iv)'' + A(u+iv)' + B(u+iv) = 0\\\\
\Longrightarrow (u''+Au'+Bu) + i(v''+Av'+Bv) = 0.
\end{eqnarray*}

The only way that this equation holds is the real part equal to zero and imaginary part equal to zero. 
So the linear combination of u and v is the general solution:

\begin{eqnarray*}
y(t) = c_{1}u(t) + c_{2}v(t)
\end{eqnarray*}

````
So the complex solution is
\begin{eqnarray*}
\tilde{y_c}(t) = e^{at+ibt}=e^{at}\cos{bt} + ie^{at}\sin{bt}.
\end{eqnarray*}

And the general solution is
\begin{eqnarray*}
y(t) = e^{at}(c_{1}\cos{bt} + c_{2}\sin{bt})
\end{eqnarray*}

```{note}
How about considering this complex solution
\begin{eqnarray*}
y_{c}(t) = e^{at-ibt} \text{?}
\end{eqnarray*}
Can we obtain the same general solution? And why?
```

````{prf:example}
:label: my-example2

\begin{eqnarray*}
y''+4y'+5y=0, y(0)=1, y'(0)=0
\end{eqnarray*}

The characteristic equation is
\begin{eqnarray*}
r^{2}&+&4r+5=0\\\\
&\Longrightarrow& r=\frac{-4\pm \sqrt{-4}}{2} = -2\pm i\\\\
\end{eqnarray*}

So the complex solution is:
\begin{eqnarray*}
e^{(-2\pm i)t} \rightarrow e^{-2t}(\cos{t}\pm \sin{t})
\end{eqnarray*}

The general solution is therefore:
\begin{eqnarray*}
y(t) &=& e^{-2t}(c_{1}\cos{t}+c_{2}\sin{t})\\\\
y'(t) &=& -2e^{-2t}(c_{1}\cos{t}+c_{2}\sin{t}) + e^{-2t}(-c_{1}\sin{t}+c_{2}\cos{t})
\end{eqnarray*}

Use initial conditions
\begin{eqnarray*}
y(0)&=&1=c_{1}, \\\\
y'(0)&=&0=-2c_{1}+c_{2} \rightarrow c_{2}=2\\\\
&\Longrightarrow& y(t)=e^{-2t}(\cos{t}+2\sin{t})=\sqrt{5}e^{-2t}\cos{}(t-\phi)
\end{eqnarray*}

This is a solution underdamped.

````

Let us now revisit the problem with slightly modification on the coefficients:
\begin{eqnarray*}
y'' &+& 2py'+\omega_{o}^{2}y=0,\\\\
\text{where } &\omega_{o}& \text{is the natural frequency and p represents the damping.} 
\end{eqnarray*}

The characteristic equation is
\begin{eqnarray*}
r^{2} + 2pr + \omega_{o}^{2} = 0 \\\\
\rightarrow r = -p \pm \sqrt{p^{2}-\omega_{o}^{2}}
\end{eqnarray*}

- if p=0, then there is no damping or called undamped.
\begin{eqnarray*}
&&y''+\omega_{o}^{2}y=0\\\\
&\Longrightarrow& r=\pm i\omega_{o}\\\\
&\Longrightarrow& y(t) = c_{1}\cos{\omega_{o}t} + c_{2}\sin{\omega_{o}t} = A\cos{}(\omega_{o}t-\phi)
\end{eqnarray*}

- if another case
\begin{eqnarray*}
p^{2}-\omega_{o}^{2} < 0 \rightarrow p<\omega_{o},
\end{eqnarray*}
then we call the solution underdamped.

````{prf:definition}
:label: my-definition1
We define the pseudo-frequency as:
\begin{eqnarray*}
\omega_{d}^{2} = \omega_{o}^{2} - p^{2}
\end{eqnarray*}
````

\begin{eqnarray*}
r = -p \pm \sqrt{-\omega_{d}^{2}} = -p \pm i\omega_{d}
\end{eqnarray*}

So the general solution is
\begin{eqnarray*}
y(t) &=& e^{-pt}(c_{1}\cos{}(\omega_{d}t) + c_{2}\sin{}(\omega_{d})) \\\\
&=& Ae^{-pt}\cos{}(\omega_{d}t-\phi)
\end{eqnarray*}

## Similarity between electrical and spring-dash pot system
```{figure} /_static/figures/similarity_ode.jpeg
:scale: 20%
:name: similar
```




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

(Lecture2)=

# Lecture2 - responses to inputs & complexify

## Response to exponential input
Consider an ODE: 
\begin{eqnarray}
\frac{dy}{dt}=ay+e^{st},
\end{eqnarray}
where a and s are known. We call y(t) the "exponential response" and exponential term on right hand side the "input" or "forcing".

Assume initial condition at t =0: $$y=y(0)$$, we now look for particular solution in the form of:
$$y_{p}(t) = Ye^{st}$$

Plug it into the ODE, we can get
$$Yse^{st} = aYe^{st} + e^{st} \rightarrow Ys=Ya+1 \rightarrow (s-a)Y=1 \rightarrow Y=\frac{1}{s-a}$$

The complete solution is
$$y(t)=y_{p}(t)+y_{h}(t) = \frac{e^{st}}{s-a} + Ce^{at}$$

To determine C, we use the initial condition
$$y(0)=\frac{1}{s-a}+C \rightarrow C = y(0) - \frac{1}{s-a}$$

So the solution is
$$y(t) = \frac{e^{st}}{s-a} + [y(0)-\frac{1}{s-a}]e^{at} = \frac{e^{st}-e^{at}}{s-a}+y(0)e^{at}$$

We also define the very particular solution
$$y_{vp}(t) = \frac{e^{st}-e^{at}}{s-a} \rightarrow y_{vp}(0) = 0$$

Note that we can calculate the very particular solution this way:
$$
y_{vp} = \int_{0}^{t}e^{a(t-x)}e^{sx}dx = e^{at}\int_{0}^{t}e^{(s-a)x}dx = e^{at}\frac{1}{s-a}e^{(s-a)x}
 \verb|\||^{x=t}_{x=0} \
=\frac{e^{st}-e^{at}}{s-a}
$$

```{note}
If s=a, then the resonance occurs.
What is the solution? How can we get the solution?
We can use L'Hospital's rule:
$$
\lim_{s\rightarrow a} \frac{\frac{d}{ds}(e^{st}-e^{at})}{\frac{d}{ds}(s-a)} 
= \lim_{s\rightarrow a} \frac{te^{st}}{1} = te^{at}
$$
```

## Response to oscillating input

Consider an ODE:
\begin{eqnarray}
\frac{dy}{dt}=ay+\cos (\omega t), y(0) = y_{0},
\end{eqnarray}

We look for particular solution (we already know homogeneours solution, right?) in the form of:
$$
y_{p}(t) = M\cos (\omega t) + N\sin (\omega t)
$$

Plug it into the ODE:
$$
-\omega M\sin (\omega t) + \omega N \cos (\omega t) = aM\cos (\omega t) + aN\sin (\omega t) + \cos (\omega t)
$$

Compare the coefficients:
$$
-aM+\omega N = 1, -\omega M - aN = 0
$$

We can use matrix-vector form (linear algebra) to solve M and N, right?
$$
\rightarrow M = \frac{-a}{\omega{^2}+a^{2}}, N = \frac{\omega}{\omega{^2}+a^{2}}
$$

We could also consider the polar form:
$$
y_{p}(t) = G\cos (\omega t - \alpha) = G(\cos (\omega t)\cos (\alpha)+\sin (\omega t)\sin (\alpha))
$$

So that
$$
M=G\cos (\alpha), N=G\sin (\alpha),
$$
$$
M^{2} + N^{2} = G^{2} \rightarrow G = \sqrt{M^{2}+N^{2}}
$$
$$
\frac{G\sin (\alpha)}{G\cos (\alpha)} = \frac{N}{M} \rightarrow \tan (\alpha) = \frac{N}{M}
$$

And that
$$
\frac{dy}{dt}=G(-\sin (\omega t-\alpha))\omega = aG\cos (\omega t-\alpha) + \cos (\omega t)
$$
$$
\rightarrow -G(\sin (\omega t)\cos (\alpha) - \sin (\alpha)\cos (\omega t)) = aG(\cos (\omega t)\cos (\alpha)+\sin (\omega t)\sin (\alpha)) + \cos (\omega t)
$$
$$
\rightarrow G(\sin (\alpha)\cos (\omega t) - \sin (\omega t)\cos (\alpha) - a\cos (\omega t)\cos (\alpha)-a\sin (\omega t)\sin (\alpha)) = \cos (\omega t)
$$

## Formula for calculating very particular solution
To this end, I would like to recap the forumla mentioned in previous lecture:
$$
\frac{dy}{dt} = ay + q(t),
$$
where q(t) is the input.
\begin{eqnarray}
y_{vp}(t) = \int_{s=0}^{s=t}e^{a(t-s)}q(s)ds = e^{at}\int_{s=0}^{s=t}e^{-as}q(s)ds
\end{eqnarray}

And the general or complete solution is	
$$
y(t) = y(0)e^{at} + e^{at}\int_{s=0}^{s=t}e^{-as}q(s)ds
$$

Check 
$$
\frac{dy_{vp}}{dt} = ay_{vp} + q(t), y_{vp}(0) = 0
$$

## Response to constant input
Assume q(t) is equal to a constant C, then the general or complete solution is:
\begin{eqnarray}
y(t) &=& y(0)e^{at} + e^{at}\int_{s=0}^{s=t}e^{-as}Cds\\
&=& y(0)e^{at} + Ce^{at}(\frac{-1}{a})e^{-as}\verb|||^{s=t}_{s=0} \\
&=& y(0)e^{at} + Ce^{at}(\frac{-1}{a})(e^{-at}-1) \\
&=& y(0)e^{at} + (\frac{C}{a}e^{at}-\frac{C}{a}) \\
&=& y(0)e^{at} + \frac{C}{a}(e^{at}-1) \\
&=& y(0)e^{at} - y_{\infty}e^{at} + y_{\infty} \\
&\rightarrow& y(t) - y_{infty} = e^{at}(y(0)-y_{infty})
\end{eqnarray}
- if a>0 and C.0, then y(t) grows or amplieis IC.
- if a<0, then y(t) approach = -c/a.

## Response to complex exponential input
Consider ODE:
$$
\frac{dy_c}{dt} = ay_{c} + \cos (\omega t) + i\sin (\omega t) = ay + e^{i\omega t}
$$

Let
$$
y_{c}(t) = Ye^{i\omega t} \rightarrow i\omega Ye^{i\omega t} = aYe^{i\omega t} + e^{i\omega t}
\rightarrow i\omega Y - aY = 1 \rightarrow Y = \frac{1}{i\omega -a}
$$

We use polar form, which is good for multiplication.
$$
i\omega -a = re^{i\alpha} = \sqrt{a^{2}+\omega^{2}}e^{i\alpha}
$$
$$
\rightarrow y_{c}(t) = \frac{1}{i\omega -a}e^{i\omega t} = \frac{1}{\sqrt{a^{2}+\omega^{2}}}e^{-i\alpha}e^{i\omega t} = \frac{1}{\sqrt{a^{2}+\omega^{2}}}e^{i(\omega t-\alpha)}
$$
$$
\tan \alpha = \frac{-\omega}{a}
$$

The real part of the solution is:
$$
y(t) = \frac{1}{\sqrt{a^{2}+\omega^{2}}}\cos (\omega t - \alpha) = G\cos (\omega t - \alpha)
$$
We call G "gain".

Let's summarize the logic and steps solving complex ODEs. We want to solve
$$
\frac{dy}{dt} = ay + A\cos (\omega t) + B\sin (\omega t).
$$

1. complexify the ODE to (real to complex):
$$
y_{c}' -ay_{c} = Re^{i(\omega t-\phi)}
$$

2. solve the complex solution:
$$
y_{c} = \frac{R}{i\omega - a}e^{i(\omega t-\phi)} = RGe^{i(\omega t-\phi-\alpha)}
$$

3. the real part of the complex solution is the desired read solution (complex to real):
$$y = \Re{(y_c)}$$

Now let's reframe the problem and solve the ODE:
$$
\frac{dy}{dt} = ay + \cos (\omega t), y(0)=y_{0}
$$

1. homogeneous solution
$$
y_{h}(t) = Ae^{at} = y_{0}e^{at}
$$

2. particular solution. Consider complex solution:
$$
y_{p}(t) = \Re{(y_{c}(t))} =  \Re{(Be^{i\omega t})}
$$
$$
\rightarrow i\omega Be^{i\omega t} = aBe^{i\omega t} + e^{i\omega t}
$$
$$
\rightarrow B(i\omega -a) = 1 \rightarrow B=\frac{1}{i\omega -a}
$$

Use polar form:
$$
\rightarrow i\omega -a = re^{i\alpha} = \sqrt{\omega^{2}+a^{2}}e^{i\alpha}
$$

$$
\rightarrow B=\frac{1}{\sqrt{\omega^{2}+a^{2}}}e^{-i\alpha}
$$

$$
y_{c} = \frac{1}{\sqrt{\omega^{2}+a^{2}}}e^{-i\alpha}e^{i\omega t} = \frac{1}{\sqrt{\omega^{2}+a^{2}}}e^{i(\omega t-\alpha)} = \frac{1}{\sqrt{\omega^{2}+a^{2}}}(\cos (\omega t-\alpha)+i\sin (\omega t-\alpha))
$$

$$
y_{p} = \Re(y_c) =  \frac{1}{\sqrt{\omega^{2}+a^{2}}}\cos (\omega t-\alpha)
= \frac{1}{\sqrt{\omega^{2}+a^{2}}}(\cos (\omega t)\cos (\alpha) + \sin (\omega t)\sin (\alpha))
$$

As
$$
\cos (\alpha) = \frac{-a}{\sqrt{\omega^{2}+a^{2}}}
$$
$$
\sin (\alpha) = \frac{\omega}{\sqrt{\omega^{2}+a^{2}}}
$$

So 
$$
y_{p} = \frac{-a}{\omega^{2}+a^2}\cos (\omega t) + \frac{\omega}{\omega^{2}+a^2}\sin (\omega t)
$$

3. complete solution
$$
y = y_{0}e^{at} - \frac{a}{\omega^{2}+a^2}\cos (\omega t) + \frac{\omega}{\omega^{2}+a^2}\sin (\omega t)
$$

## Response to step function and delta function inputs
Let's introduce three interesting functions:
1. ramp function
$$
R(t) = 0, t < 0
$$
$$
R(t) = t, t \geq 0
$$
2. step function
$$
H(t) = 0, t < 0
$$
$$
H(t) = 1, t \geq 0
$$
3. delta function
$$
\delta (t) = \infty, t = 0
$$
$$
\delta (t) = 0, t\neq 0
$$

```{note}
The derivitive is strange, but integral works. Three properties:
$$
\int_{-\infty}^{\infty}\delta (t)dt = H(\infty) - H(-\infty) = 1 - 0 = 1
$$
$$
\int_{-\infty}^{\infty}\delta (t)f(t)dt = f(0)
$$
$$
\int_{-\infty}^{\infty}\delta (t-T)e^{t}dt = e^{T}
$$
```

Let's consider the ODE with delta function input:
$$
\frac{dy}{dt} = ay + \delta (t-T)
$$

Homogeneous solution:
$$
y_{h}(t) = y(0)e^{at}
$$

We use "the formula" to calculate the (very) particular solution:
$$
y_{p}(t) = e^{at}\int_{s=0}^{s=t}e^{-as}\delta (s-T)ds = e^{at}e^{-aT} = e^{a(t-T)}
$$

So the complete solution is:
$$
y(t) = y(o)e^{at} + e^{a(t-T)}
$$

Is this the solution when t=0? How could you modify the solution?













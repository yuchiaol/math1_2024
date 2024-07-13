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
````{prf:example}
:label: my-example_exp_response1
If s=a, then the resonance occurs.
What is the solution? How can we get the solution?
We can use L'Hospital's rule:
$$
\lim_{s\rightarrow a} \frac{\frac{d}{ds}(e^{st}-e^{at})}{\frac{d}{ds}(s-a)} 
= \lim_{s\rightarrow a} \frac{te^{st}}{1} = te^{at}
$$
````
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





















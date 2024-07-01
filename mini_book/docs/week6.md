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

(week6)=

# Week6 - exponential response formula (ERF)

## The ERF framework
This method gives us guide to find the nonhomogeneous (particular) solutions for exponential-type forcing or source term.
Consider the second order ODE:
\begin{eqnarray*}
A''+by'+cy &=& e^{\alpha x}, \alpha \in \mathbb{C} \\\\
&=& e^{(a+i\omega)x}\\\\
\Longrightarrow (D^{2}+AD+B)y &=& P(D)y = e^{\alpha x}
\end{eqnarray*}

Below exponential inputs are all special cases of exponential function
\begin{eqnarray*}
e^{ax}, \sin{}(\omega x), \cos{}(\omega x), e^{ax}\sin{}(\omega x), e^{ax}\cos{}(\omega x)
\end{eqnarray*}


````{prf:example}
:label: my-example_erf1
\begin{eqnarray*}
P(D)e^{\alpha x} = P(\alpha)e^{\alpha x}
\end{eqnarray*}
````

````{prf:theorem}
:label: my-theorem_erf1
Exponential-input theorem

\begin{eqnarray*}
y_{p} = \frac{e^{\alpha x}}{p(\alpha)} \text{ solves } P(D)y=e^{\alpha x}
\end{eqnarray*}
````

````{prf:proof}
if 
\begin{eqnarray*}
P(D)y_{p} = e^{\alpha x},
\end{eqnarray*}
then
\begin{eqnarray*}
P(D)\frac{e^{\alpha x}}{P(\alpha)} = \frac{1}{P(\alpha)}P(D)e^{\alpha x} = \frac{1}{P(\alpha)}P(\alpha)e^{\alpha x} = e^{\alpha x}
\end{eqnarray*}

````

````{prf:example}
:label: my-example_erf2
\begin{eqnarray*}
y''-y'+2y=10e^{-x}\sin{}(x)
\end{eqnarray*}

We first complixy the ODE, solve the particular solution, and find its imaginary part:
\begin{eqnarray*}
\tilde{y_{p}}'' - \tilde{y_{p}}' + 2\tilde{y_{p}} &=& 10e^{(-1+i)x} \\\\
P(D) = (D^{2} - D + 2) &\rightarrow& P(\alpha) = \alpha^{2}-\alpha+2
\end{eqnarray*}

\begin{eqnarray*}
(D^{2} - D + 2)\tilde{y_{p}} &=& 10e^{(-1+i)x} \\\\
\Longrightarrow \tilde{y_{p}} = \frac{10e^{(-1+i)x}}{(-1+i)^{2}-(-1+i)+2} &=& \frac{10e^{(-1+i)x}}{3-3i} = \frac{5}{3}(1+i)e^{(-1+i)x}.
\end{eqnarray*}

So the particular solution is:
\begin{eqnarray*}
y_{p} = \mathfrak{Im}(\tilde{y_{p}}) = \frac{5}{3}e^{-x}(\sin{}(x)+\cos{}(x)) = \frac{5}{3}e^{-x}\sqrt{2}(\cos{}(x-\frac{\pi}{4}))
\end{eqnarray*}

````

````{prf:theorem}
:label: my-theorem_erf2
Exponential-shift theorem

\begin{eqnarray*}
P(D)e^{ax}u(x) = e^{ax}P(D+a)u(x)
\end{eqnarray*}
````

````{prf:proof}
Consider
\begin{eqnarray*}
P(D)e^{ax}u(x) &=& (D^{2}+AD+B)e^{ax}u(x) \\\\
&=& D^{2}(e^{ax}u)+AD(e^{ax}u)+B(e^{ax}u) \\\\
&=& D(D(e^{ax}u))+AD(e^{ax}u)+B(e^{ax}u) \\\\
&=& D(ae^{ax}u+e^{ax}Du) + A(ae^{ax}u+e^{ax}Du) + B(e^{ax}u) \\\\
&=& e^{ax}(a^{2}u+aDu+aDu+D^{2}u+aAu+ADu+Bu) \\\\
&=& e^{ax}(D^{2}u+2aDu+a^{2}u+A(Du+au)+Bu) \\\\
&=& e^{ax}((D+a)^{2}u+A(D+a)u+Bu) \\\\
&=& e^{ax}P(D+a)u(x)
\end{eqnarray*}

````

````{prf:theorem}
:label: my-theorem_erf3
Resonance
\begin{eqnarray*}
(D^{2}+AD+B)y = e^{ax},
\end{eqnarray*}
where a is complex. 

1. If P(a) = 0,  a is a simple root of P(D), then the particular solution is

\begin{eqnarray*}
y_p{ = \frac{xe^{ax}}{P'(a)}}
\end{eqnarray*}

2. If a is a double root, then the particular solution is

\begin{eqnarray*}
y_p{ = \frac{x^{2}e^{ax}}{P''(a)}}
\end{eqnarray*}

````

````{prf:proof}
1. simple root case.
\begin{eqnarray*}
P(D) &=& (D-b)(D-a) = D^{2} - (a+b) + ab, a\neq b \\\\
P'(D) &=& (D-a) + (D-b)) \\\\
P'(a) &=& a-b \\\\
P(D)\frac{xe^{ax}}{P'(a)} &=& e^{ax}\frac{P(D+a)x}{P'(a)} \\\\
&=& \frac{e^{ax}(D+a-b)(D+a-a)x}{P'(a)} = \frac{e^{ax}(D+a-b)Dx}{P'(a)} \\\\
&=& \frac{e^{ax}(a-b)}{a-b} = e^{ax}
\end{eqnarray*}

````

````{prf:example}
:label: my-example_erf3
\begin{eqnarray*}
y''-3y'+2y = e^{x}\\\\
\Longrightarrow P(D) = D^{2}-3D+2
\end{eqnarray*}
So 1 is a simple root.

\begin{eqnarray*}
P'(D) = 2D-3\\\\
P'(1) = -1
\end{eqnarray*}

The particular solution is
\begin{eqnarray*}
y_{p} = \frac{xe^{x}}{-1} = -xe^{x}
\end{eqnarray*}

````

````{prf:proof}
2. double root case.
\begin{eqnarray*}
P(D) &=& (D-a)(D-a) \\\\
P'(D) &=& (D-a) + (D-a) = 2(D-a) \\\\
P'(a) &=& 2(a-a)=0 \\\\
P''(D) &=& 2, P''(a) = 2\\\\
P(D)y_{p} &=& P(D)\frac{x^{2}e^{ax}}{P''(a)}=\frac{e^{ax}P(D+a)x^{2}}{2} \\\\
&=& \frac{e^{ax}Dx^{2}}{2} = e^{ax}\frac{2Dx}{2}=e^{ax}
\end{eqnarray*}

````

## Resonance revisit
Now we can revisit the resonance case with ERF. Consider below ODE and assume input frequency is not equal to the natural frequency.
\begin{eqnarray*}
y'' + \omega_{o}^{2}y &=& \cos{}(\omega_{1}t), \omega_{o} \neq \omega_{1} \\\\
(D^{2}+\omega_{o}^{2})y &=& \cos{}(\omega_{1}t) \rightarrow P(D) = (D^{2} + \omega_{o}^{2})
\end{eqnarray*}

Complexify the ODE:
\begin{eqnarray*}
(D^{2} + \omega_{o}^{2})\tilde{y_{p}} &=& e^{i\omega_{1}t} \\\\
\Longrightarrow \tilde{y_{p}} &=& \frac{e^{i\omega_{1}t}}{(i\omega_{1})^{2}+\omega_{o}^{2}} = \frac{e^{i\omega_{1}t}}{\omega_{o}^{2}-\omega_{1}^{2}} \\\\
\Longrightarrow y_{p} &=& \Re (\tilde{y_{p}}) = \frac{\cos{}(\omega_{1}t)}{\omega_{o}^{2}-\omega_{1}^{2}}, \text{  not a very particular solution.} \\\\
\text{We can see if } \omega_{1} \approx \omega_{o} \text{, big amplitude occurs.}
\end{eqnarray*}

Consider a very particular solution:
\begin{eqnarray*}
y_{vp} = \frac{\cos{}(\omega_{1}t)}{\omega_{o}^{2}-\omega_{1}^{2}} - \frac{\cos{}(\omega_{o}t)}{\omega_{o}^{2}-\omega_{1}^{2}}\\\\
\lim_{\omega_{1}\to \omega_{o}}\frac{\cos{}(\omega_{1}t)-\cos{}(\omega_{o}t)}{\omega_{o}^{2}-\omega_{1}^{2}}
\end{eqnarray*}
When the two frequencies are very similar:
\begin{eqnarray*}
\lim_{\omega_{1}\to \omega_{o}}\frac{-\sin{}(\omega_{1}t)t}{-2\omega_{1}} = \frac{t\sin{}(\omega_{o}t)}{2\omega_{o}}
\end{eqnarray*}

```{note}
The geometric meaning of the very particular solution is "beats":
\begin{eqnarray*}
\frac{\cos{}(\omega_{1}t)-\cos{}(\omega_{o}t)}{\omega_{o}^{2}-\omega_{1}^{2}} 
&=& \frac{2\sin{}(\frac{\omega_{o}-\omega_{1}}{2}t)\sin{}(\frac{\omega_{o}+\omega_{1}}{2}t)}{\omega_{o}^{2}-\omega_{1}^{2}} \\\\
&\approx& \frac{2\sin{}(\frac{\omega_{o}-\omega_{1}}{2}t)\sin{}(\omega_{o}t)}{\omega_{o}^{2}-\omega_{1}^{2}}
\end{eqnarray*}
````

When resonance occurs, we can apply ERF directly:
\begin{eqnarray*}
\omega_{1} &=& \omega_{o}\\\\
(D^{2} + \omega_{o}^{2})y_{p} &=& \cos{}(\omega_{o}t) \rightarrow P(D) = (D^{2} + \omega_{o}^{2}).
\end{eqnarray*}

Complexify the equation, we can get
\begin{eqnarray*}
(D^{2} + \omega_{o}^{2})\tilde{y_{p}} &=& e^{i\omega_{o}t}, \\\\
P(i\omega_{o}) &=& (i\omega_{o})^{2} + \omega_{o}^{2} = 0 \\\\
P'(i\omega_{o}) &=& 2i\omega_{o} \\\\
\Longrightarrow \tilde{y_{p}} &=& \frac{te^{i\omega_{o}t}}{2i\omega_{o}} \\\\
\Longrightarrow y_{p} &=& \Re (\tilde{y_{p}}) = \frac{t\sin{}(\omega_{o}t)}{2\omega_{o}}
\end{eqnarray*}












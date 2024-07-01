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

(week7)=

# Week7 - variation of parameters

## The fundamental set of solutions amd Wronskian
Consider linear ODE:
\begin{eqnarray*}
&\text{   }& y''+p(t)y'+q(t)y=0 \\\\
y_{1}(t) \text{ and } &y_{2}(t)& \text{ form a fudamental set of solutions (fss) if:} \\\\
&1.& y_{1}, y_{2} \text{ are solutions of the ODE.} \\\\
&2.& \text{every solution } y(t) \text{ of the ODE can be written as:}\\\\
&\text{    }& y(t) = c_{1}y_{1}(t) + c_{2}y_{2}(t)
\end{eqnarray*}

````{prf:theorem}
:label: my-theorem_vp1
Two solutions form a fss if the determinat

\begin{eqnarray*}
W(t) = 
\begin{vmatrix}
     y_{1}(t) & y_{2}(t) \\
     y_{1}'(t) & y_{2}'(t) 
\end{vmatrix}
\neq 0
\end{eqnarray*}
W(t) is called Wronskian.

````

````{prf:example}
:label: my-example_vp1
Consider the ODE:
\begin{eqnarray*}
y''+y=0
\end{eqnarray*}
Show that
\begin{eqnarray*}
y_{1}(t)=\sin{}(t), y_{2}(t)=\cos{}(t)
\end{eqnarray*}
form a fss of this ODE.
1. they are solutions to the ODE.
2. 
\begin{eqnarray*}
W(t) =
\begin{vmatrix}
     \sin{}(t) & \cos{}(t) \\
     \cos{}(t) & -\sin{}(t)
\end{vmatrix}
= -\sin{}^{2}(t) - \cos{}^{2}(t) = -1
\neq 0
\end{eqnarray*}

````

## Variation of parameters
Consider the ODE:
\begin{eqnarray*}
1y''+B(t)y'+C(t)y=f(t).
\end{eqnarray*}

Suppose we have two homogeneous solutions:
\begin{eqnarray*}
y_{1}(t), y_{2}(t)
\end{eqnarray*}

The idea is to construct the particular solution as the form of
\begin{eqnarray*}
y_{p}(t)=c_{1}(t)y_{1}(t) + c_{2}(t)y_{2}(t), \\\\
c_{1}(t), c_{2}(t) \text{ are called the varying parameters.}
\end{eqnarray*}

if
\begin{eqnarray*}
c_{1}'(t)y_{1}(t) &+& c_{2}'(t)y_{2}(t) = 0 \\\\
c_{1}'(t)y_{1}'(t) &+& c_{2}'(t)y_{2}'(t) = f(t) \\\\
\Longrightarrow 
W(t) &=&
\begin{vmatrix}
     y_{1}(t) & y_{2}(t) \\
     y_{1}'(t) & y_{2}'(t)
\end{vmatrix}
\neq 0 \\\\
&\Longrightarrow& y_{1}(t), y_{2}(t) \text{ form a fss}
\end{eqnarray*}

then
\begin{eqnarray*}
y_{p}(t) &=& y_{1}\int{\frac{W_{1}}{W}dt} +  y_{2}\int{\frac{W_{2}}{W}dt} \\\\
W_{1} &=& 
\begin{vmatrix}
     0 & y_{2}(t) \\
     f(t) & y_{2}'(t)
\end{vmatrix} \\\\
W_{2} &=&
\begin{vmatrix}
     y_{1}(t) & 0 \\
     y_{1}'(t) & f(t)
\end{vmatrix} \\\\
\end{eqnarray*}

So the particular solution is:
\begin{eqnarray*}
y_{p}(t) = y_{1}(t)\int{\frac{-y_{2}(t)f(t)}{W}dt} +  y_{2}(t)\int{\frac{y_{1}(t)f(t)}{W}dt}
\end{eqnarray*}

````{prf:example}
:label: my-example_vp2
\begin{eqnarray*}
y_{1}(t) = e^{s_{1}t}, y_{2}(t) = e^{s_{2}t}
\end{eqnarray*}
\begin{eqnarray*}
W(t) = 
\begin{vmatrix}
     y_{1} & y_{2} \\
     y_{1}' & y_{2}'
\end{vmatrix}
= 
\begin{vmatrix}
     e^{s_{1}t} & e^{s_{2}t} \\
     s_{1}e^{s_{1}t} & s_{2}e^{s_{2}t}
\end{vmatrix}
=
(s_{2}-s_{1})(e^{s_{1}t}e^{s_{2}t})
\end{eqnarray*}

\begin{eqnarray*}
y_{p}(t) &=& e^{s_{1}t}\int{\frac{-e^{s_{2}T}f(T)}{(s_{2}-s_{1})e^{s_{1}T}e^{s_{2}T}}dT} + e^{s_{2}t}\int{\frac{e^{s_{1}T}f(T)}{(s_{2}-s_{1})e^{s_{1}T}e^{s_{2}T}}dT}\\\\
&=& \frac{-1}{s_{2}-s_{1}}\int{e^{s_{1}(t-T)f(T)dT}} + \frac{1}{s_{2}-s_{1}}\int{e^{s_{2}(t-T)f(T)dT}}\\\\
&=& \int{g(t-T)f(T)dT}\\\\
g(t) &=& \frac{e^{s_{1}t}-e^{s_{2}t}}{s_{1}-s_{2}}, \text{ growth factor}
\end{eqnarray*}


````


````{prf:example}
:label: my-example_vp3
\begin{eqnarray*}
y''=2y'+y=e^{x}\ln{x}
\end{eqnarray*}

1. 
\begin{eqnarray*}
r^2-2r+1 = 0 &\rightarrow& (r-1)^{2} = 0 \rightarrow y_{h}(x) = c_{1}e^{x} + c_{2}xe^{x} \\\\
\text{ take } y_{1}(x) &=& e^{x}, y_{2}(x) = xe^{x}
\end{eqnarray*}

2. check
\begin{eqnarray*}
y_{1}(x) \text{ and } y_{2}(x) \text{ form a fss}
\end{eqnarray*}

\begin{eqnarray*}
W(x) &=& 
\begin{vmatrix}
     e^{x} & xe^{x} \\
     e^{x} & e^{x}+xe^{x}
\end{vmatrix}
= e^{2x}+xe^{2x}-xe^{2x} = e^{2x} \neq 0 \\\\
W_{1}(x) &=& 
\begin{vmatrix}
     0 & xe^{x} \\
     e^{x}\ln{x} & e^{x}+xe^{x}
\end{vmatrix}
= -xe^{2x}\ln{x} \\\\
W_{2}(x) &=& 
\begin{vmatrix}
     e^{x} & 0 \\
     e^{x} & e^{x}\ln{x}
\end{vmatrix}
= e^{2x}\ln{x}
\end{eqnarray*}

3. calculate the particular solution
\begin{eqnarray*}
y_{p} &=& y_{1}\int{\frac{W_{1}}{W}dx} + y_{2}\int{\frac{W_{2}}{W}dx} \\\\
&=& e^{x}\int{\frac{-xe^{2x}\ln{x}}{e^{2x}}dx} + xe^{x}\int{\frac{e^{2x}\ln{x}}{e^{2x}}dx} \\\\
&=& -e^{x}\int{x\ln{x}dx} + xe^{x}\int{\ln{x}dx}\\\\
&=& -e^{x}(\frac{1}{2}x^{2}\ln{x}-\frac{1}{2}\int{xdx}) + xe^{x}(x\ln{x}-\int{xd\ln{x}})\\\\
&=& -e^{x}(\frac{1}{2}x^{2}\ln{x}-\frac{1}{4}x^{2}) + xe^{2}(x\ln{x}-x)
\end{eqnarray*}

4. caclulate the general solution
\begin{eqnarray*}
y(x) = y_{h}(x) + y_{p}(x)
\end{eqnarray*}

````







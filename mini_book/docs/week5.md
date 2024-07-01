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

(week5)=

# Week5 - method of undetermined coefficients
This method gives us guide to find the nonhomogeneous (particular) solutions.
Consider the general form of second order ODE:
\begin{eqnarray*}
A''+by'+cy = q(t)
\end{eqnarray*}
We guess the form of nonhomogeneous (particular) solutions based on the form of q(t):
\begin{eqnarray*}
q(t) &\rightarrow& y_{p}(t)\\\\
t, 1 &\rightarrow& a+bt\\\\
e^{st} &\rightarrow& Ye^{st} \text{(if resonance: } Yt^{n}e^{st})\\\\
te^{st} &\rightarrow& (a+bt)e^{st}\\\\
\sin{}(\omega t), \cos{}(\omega t) &\rightarrow& M\cos{}(\omega t) + N\sin{}(\omega t)\\\\
t\cos{}(\omega t) &\rightarrow& (a+bt)\cos{}(\omega t) + (c+dt)\sin{}(\omega t)\\\\
e^{i\omega t}, e^{-i\omega t} &\rightarrow& Ye^{-i\omega t}
\end{eqnarray*}


````{prf:example}
:label: my-example3
\begin{eqnarray*}
y''+5y'+6y=e^{4t}
\end{eqnarray*}

1. homogeneous solution:
\begin{eqnarray*}
r^2+5r+6=0 \rightarrow r = -2, -3\\\\
\Longrightarrow y_{h}(t) = c_{1}e^{-2t}+c_{2}e^{-3t}
\end{eqnarray*}

2. nonhomogeneous/particular solution by guessing the form of source/input term.
We have one undetermined coefficient Y.
\begin{eqnarray*}
y_{p}(t) &=& Ye^{4t} \rightarrow 16Y+20Y+6Y = 1 \rightarrow Y=\frac{1}{42} \\\\
&\Longrightarrow& y_{p}(t) = \frac{1}{42}e^{4t}
\end{eqnarray*}

3. general/complete solution:
\begin{eqnarray*}
y(t) = c_{1}e^{-2t}+c_{2}e^{-3t} + \frac{1}{42}e^{4t}
\end{eqnarray*}

````

````{prf:example}
:label: my-example4
\begin{eqnarray*}
y''+5y'=e^{it}
\end{eqnarray*}

1. homogeneous solution:
\begin{eqnarray*}
r^2+r=0 \rightarrow r(r+1)=0 \rightarrow = 0, -1\\\\
\Longrightarrow y_{h}(t) = c_{1}e^{0t}+c_{2}e^{-t} = c_{1}+c_{2}e^{-t}
\end{eqnarray*}

2. nonhomogeneous/particular solution by guessing the form of source/input term.
We have one undetermined coefficient Y.
\begin{eqnarray*}
y_{p}(t) &=& Ye^{it} \rightarrow Y(i^{2}+i) = 1 \rightarrow Y=\frac{1}{i-1} \\\\
&\Longrightarrow& y_{p}(t) = \frac{1}{i-1}e^{it}
\end{eqnarray*}

3. general/complete solution:
\begin{eqnarray*}
y(t) = c_{1}+c_{2}e^{-t} + \frac{1}{i-1}e^{it}
\end{eqnarray*}

````

````{prf:example}
:label: my-example5
\begin{eqnarray*}
y'''+2y''+y'=e^{3t}
\end{eqnarray*}

1. homogeneous solution:      
\begin{eqnarray*}
r^{3}+2r^{2}+r=0 \rightarrow r(r+1)^{2}=0 \rightarrow = 0, -1, -1\\\\
\Longrightarrow y_{h}(t) = c_{1}e^{0t}+c_{2}e^{-t} + c_{3}te^{-t} = c_{1}+c_{2}e^{-t} + c_{3}te^{-t}
\end{eqnarray*}

2. nonhomogeneous/particular solution by guessing the form of source/input term.
We have one undetermined coefficient Y.
\begin{eqnarray*}
y_{p}(t) &=& Ye^{3t} \rightarrow 27Y+18Y+3Y = 1 \rightarrow Y=\frac{1}{48} \\\\
&\Longrightarrow& y_{p}(t) = \frac{1}{i-1}e^{it}
\end{eqnarray*}

3. general/complete solution:
\begin{eqnarray*}
y(t) = c_{1}+c_{2}e^{-t} + c_{3}te^{-t} + \frac{1}{48}e^{3t}
\end{eqnarray*}

````

````{prf:example}
:label: my-example6
\begin{eqnarray*}
y''+y'+y=t
\end{eqnarray*}

- nonhomogeneous/particular solution by guessing the form of source/input term.
We have two undetermined coefficients.
\begin{eqnarray*}
y_{p}(t) &=& a+bt \rightarrow b+a+bt = t \rightarrow b=1, a=-1 \\\\
&\Longrightarrow& y_{p}(t) = -1+t
\end{eqnarray*}

````

````{prf:example}
:label: my-example7
\begin{eqnarray*}
y''+y'+y=\sin{}(t)
\end{eqnarray*}

- nonhomogeneous/particular solution by guessing the form of source/input term.
We have two undetermined coefficient Y.
\begin{eqnarray*}
y_{p}(t) &=& c_{1}\cos{}(t) + c_{2}\sin{}(t) \\\\
&\Longrightarrow& -c_{1}\cos{}(t) - c_{2}\sin{}(t) - c_{1}\sin{}(t) + c_{2}\cos{}(t) + c_{1}\cos{}(t) + c_{2}\sin{}(t) = \sin{}(t) \\\\
&\Longrightarrow& c_{2} = 0, c_{1}=-1 \\\\
&\Longrightarrow& y_{p}(t) = -\cos{}(t)
\end{eqnarray*}

````

````{prf:example}
:label: my-example8
\begin{eqnarray*}
y''+y'+y=t\sin{}(t)
\end{eqnarray*}

- nonhomogeneous/particular solution by guessing the form of source/input term.
We have four undetermined coefficients.
\begin{eqnarray*}
y_{p}(t) &=& (a+bt)\cos{}(t) + (c+dt)\sin{}(t)
\end{eqnarray*}

````







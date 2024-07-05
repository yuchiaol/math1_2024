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

(week2)=

# Week2 - responses to inputs & complexify

## Response to exponential input
Consider an ODE: $$\frac{dy}{dt}=ay+e^{st},$$ where a and s are known. We call y(t) the "exponential response" and exponential term on right hand side the "input" or "forcing".

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



\begin{eqnarray}
\frac{dy}{dt}=ay+e^{st}
\end{eqnarray}


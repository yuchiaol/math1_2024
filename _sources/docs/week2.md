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
Consider ODE: $$\frac{dy}{dt}=ay+e^{st},$$ where a and s are known. We call y(t) the "exponential response" and exponential term on right hand side the "input" or "forcing".

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

Consider a case when s=a. This is when resonance occurs. What is the solution? How can we get the solution?

\begin{eqnarray}
\frac{dy}{dt}=ay+e^{st}
\end{eqnarray}


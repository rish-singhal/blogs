---
title: "Interesting Integral"
mathjax: true
layout: post
comments: true
---

This is one of my favourite integral and my proof

**Show that** $$\int_{0}^{\infty}\frac{\sin{x}}{x} dx = \frac{\pi}{2}$$

Let $$f(t) = \int_{0}^{\infty}\frac{\sin{tx}}{x} dx$$, and take laplace transform on both sides

$$\begin{aligned}
        \mathscr{L}\{f(t)\} &= \int_{0}^{\infty} e^{-st} (\int_{0}^{\infty}\frac{\sin{tx}}{x} dx) dt\\
        &= \int_{0}^{\infty}\frac{\int_{0}^{\infty} e^{-st} \sin{tx} dt}{x} dx = \int_{0}^{\infty}\frac{\mathscr{L}\{{sin(xt)}\}}{x} dx\\
        &= \int_{0}^{\infty}\frac{\frac{x}{x^2 + s^2}}{x} dx = \int_{0}^{\infty}\frac{1}{x^2 + s^2} dx\\
        &= \frac{1}{s^2}\int_{0}^{\infty}\frac{1}{{(\frac{x}{s})}^2 + 1} dx
    \end{aligned}$$

Let $$x = s \tan{\theta}$$, then $$dx = s \times {\sec{\theta}}^2 d{\theta}$$

$$\begin{aligned}
        \mathscr{L}\{f(t)\} &= \frac{1}{s^2}\int_{0}^{\frac{\pi}{2}}\frac{s \times {\sec^2{\theta}}}{{\tan^2{\theta}} + 1} d{\theta}\\
        &= \frac{1}{s}\int_{0}^{\frac{\pi}{2}}\frac{ {\sec^2{\theta}}}{{\sec^2{\theta}}} d{\theta} = \frac{1}{s}\int_{0}^{\frac{\pi}{2}} 1\ d{\theta}\\
        &= \frac{1}{s} \times \frac{\pi}{2}\\
    \end{aligned}$$

Now taking inverse of laplace transform both sides,

$$\begin{aligned}
       \mathscr{L}^{-1}\{\mathscr{L}\{f(t)\}\} &= \mathscr{L}^{-1}\{{\frac{1}{s} \times \frac{\pi}{2}}\} = \frac{\pi}{2}\\
       f(t) &= \frac{\pi}{2}
    \end{aligned}$$

Hence, it can be seen that

$$\begin{aligned}
        f(t) = \int_{0}^{\infty}\frac{\sin{tx}}{x} dx = \frac{\pi}{2}\\
    \end{aligned}$$
    
taking $$t = 1$$,

$$\begin{aligned}
        \int_{0}^{\infty}\frac{\sin{x}}{x} dx = \frac{\pi}{2}\\
    \end{aligned}$$

Hence proved.

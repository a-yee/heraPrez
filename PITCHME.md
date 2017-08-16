# Mathematical Motivations of HERA

By Alex Yee

---
<canvas data-chart="radar">
<!-- 
{
 "data": {
  "labels": ["Delivery Ratio", "Replicas", "Delay"],
  "datasets": [
   {
    "data":[70, 1, 50],
    "label":"Direct Delivery","backgroundColor":"rgba(20,220,220,.3)"
   },
   {
    "data":[88, 50, 35],
    "label":"Prophet","backgroundColor":"rgba(30,219,20,.3)"
   },
   {
    "data":[95, 100, 15],
    "label":"Epidemic","backgroundColor":"rgba(220,120,120,.3)"
   }
  ]
 }, 
 "options": { "responsive": "true" }
}
-->
</canvas>
---
### Issues with Prophet

 - Susceptible to artificially large predictability values
 - Mountain problem
 - Can't handle localized cluster of nodes that interact frequently

+++
__Direct Encounters__
$$P(a,b) = P(a,b)\_{old} + \left(1 - P(a,b)\_{old}\right) \cdot
    P\_{init}$$

__Transitive Update__
$$P(a,c) = P(a,c)\_{old} + \left(1 - P(a,c)\_{old}\right)\cdot
    P(a,b)\cdot P(b,c) \cdot \beta$$

__Aging__
$$P(a,b) = P(a,b)\_{old} \cdot \gamma^{k}$$

---
### Hop Expansion

$$\begin{align} 
    preds &= \begin{bmatrix}
    p(z\_0) \\\
    p(z\_1) \\\
    p(z\_2) \\\
    \vdots \\\
    p(z\_N) 
    \end{bmatrix}
\end{align} \rightarrow 
\begin{bmatrix}
    m^{(0)}(z\_0) & m^{(0)}(z\_1) & \cdots & m^{(0)}(z\_N) \\\
    m^{(1)}(z\_0) & m^{(1)}(z\_1) & \cdots & m^{(0)}(z\_N) \\\
    m^{(2)}(z\_0) & m^{(2)}(z\_1) & \cdots & m^{(2)}(z\_N) \\\
    \vdots & \vdots & \ddots & \vdots \\\
    m^{(H)}(z\_0) & m^{(H)}(z\_1) & \cdots & m^{(H)}(z\_N)
\end{bmatrix}$$

---
### HERA Formulas

__Direct Encounters__
$$m\_{new}^{(0)}(z\_0,z\_1) = m\_{old}^{(0)}(z\_0,z\_1) + 1$$

__Transitive Update__
$$m\_{new}^{(h)}(z\_0, i) = m\_{old}^{(h)}(z\_0,i) + \lambda\_h \cdot
    m\_{old}^{(h-1)}(z\_1,i)$$

$$\text{where } i \in \\{ \text{set of encountered nodes} \\}
    \text{ s.t. } i \neq z\_1$$
$$\text{where } h=1,...,H \text{ for } h \in \mathbb{N}$$

+++
### $$\vec\lambda$$ Gives You Control

 - The $$\lambda\_{h}$$ in HERA's update process, simulates how much you trust
   new information
 - Local weighting control
 - Not just hops but control over non-direct encounters.

+++?image=img01.png
<!-- .slide: data-background-transition="none" -->

---?code=HeraRouter.java&lang=java

@[357-360](Message forwarding decision)

+++
### Decision Inequality

$$\Omega\_{z\_0}(z\_k) > \Omega\_{z\_1}(z\_k)$$

$$p(z\_k) \in \mathbb{R} \implies \text{need } \Omega\_{z\_i}(z\_k) \in \mathbb{R}$$

$$p(z\_k) \approx \begin{align}
    M\_{z\_{0}}(z\_k) &= \begin{bmatrix}
        m^{(0)}(z\_k) \\\
        m^{(1)}(z\_k) \\\
        m^{(2)}(z\_k) \\\
        \vdots \\\
        m^{(H)}(z\_k) \\\
    \end{bmatrix}
\end{align}$$


+++

$$\Omega\_{z\_{0}}(z\_{k}) = \sum\_{h=0}^{H} \gamma\_{h} \cdot
    m\_{z\_0}^{(h)}(z\_{k})$$

$$\Omega\_{z\_{0}}(z\_{k}) = \vec\gamma \cdot \vec M\_{z\_{0}}(z\_{k})$$

+++
### $$\vec \gamma$$ & Global Control

 - $$\vec \gamma$$ inside of $$\Omega\_{z\_{0}}(z\_{k})$$ controls how much
   weight each hop matters gloabally
 - Answers, "How much should we care about hop h in message passing?"
 - $$\vec\gamma$$ represents a way to control which information (AKA hops) we
   find important.

---
### Conclusion

 - HERA gives you more control over the message passing decisions
 - Multi-layer control over encounter information

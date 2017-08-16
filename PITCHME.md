# Mathematical Motivations of HERA

By Alex Yee

---
<canvas data-chart="radar">
<!-- 
{
 "data": {
  "labels": ["Delay", "Replicas", "Delivery Ratio"],
  "datasets": [
   {
    "data":[65,59,80,81,56,55,40],
    "label":"Prophet","backgroundColor":"rgba(20,220,220,.8)"
   },
   {
    "data":[1,19,98,45,77,12,55],
    "label":"Epidemic","backgroundColor":"rgba(30,219,20,.8)"
   },
   {
    "data":[28,48,40,19,86,27,90],
    "label":"Direct Delivery","backgroundColor":"rgba(220,120,120,.8)"
   }
  ]
 }, 
 "options": { "responsive": "true" }
}
-->
</canvas>
---
# Issues with Prophet

 - Susceptible to 

+++
Direct Encounters
$$P(a,b) = P(a,b)\_{old} + \left(1 - P(a,b)\_{old}\right) \cdot
    P\_{init}$$

Transitive Update
$$P(a,c) = P(a,c)\_{old} + \left(1 - P(a,c)\_{old}\right)\cdot
    P(a,b)\cdot P(b,c) \cdot \beta$$

Aging
$$P(a,b) = P(a,b)\_{old} \cdot \gamma^{k}$$

---
# Hop Expansion

$$\begin{align} 
    preds &= \begin{bmatrix}
    p(z0) \\\
    p(z1) \\\
    \vdots \\\
    p(zN) 
    \end{bmatrix}
\end{align} \rightarrow 
\begin{bmatrix}
    m^{(0)}(z0) m^{(0)}(z1) \cdots m^{(0)}(zN) \\
    m^{(1)}(z0) m^{(1)}(z1) \cdots m^{(0)}(zN) \\
    m^{(2)}(z0) m^{(2)}(z1) \cdots m^{(2)}(zN) \\
    \vdots \vdots \ddots \vdots \\
    m^{(H)}(z0) m^{(H)}(z1) \cdots m^{(H)}(zN)
\end{bmatrix}$$

---
# HERA Formulas

Direct Encounters
$$m\_{new}^{(0)}(z0,z1) = m\_{old}^{(0)}(z0,z1) + 1$$

Transitive Update
$$m\_{new}^{(h)}(z0, i) = m\_{old}^{(h)}(z0,i) + \lambda\_h \cdot
    m\_{old}^{(h-1)}(z1,i)$$

$$\text{where } i \in i=1,...,H$$

+++?image=img01.png
<!-- .slide: data-background-transition="none" -->

---
# Decision Making in HERA



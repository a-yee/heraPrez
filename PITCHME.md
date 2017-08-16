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
### Issues with Prophet

 - Susceptible to artificially large predictability values
 - Mountain problem
 - Can't handle localized cluster of nodes that interact frequently

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

$$\text{where } i=1,...,H$$

+++?image=img01.png
<!-- .slide: data-background-transition="none" -->

---
### Decision Making in HERA



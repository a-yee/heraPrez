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

Direct Contact

+++?image=imgFile
<!-- .slide: data-background-transition="none" -->

---
# HERA Update Formulas

$$m\_{new}^{(0)}(z0,z1)$$
$$\text{m}\_{new}^{(0)}(z0,z1)$$
$$m\_{new}^{\left(0\right)}\left(z0,z1\right)$$

Transitive Update
$$m_{new}^{(h)}(z0, i) = m_{old}^{(h)}(z0,i) + \lambda_h \cdot m_{old}^{(h-1)}(z1,i)$$

$$\sum_{i=0}^n i^2 = \frac{(n^2+n)(2n+1)}{6}$$
+++?image=img01.png
<!-- .slide: data-background-transition="none" -->

---











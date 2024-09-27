We explain in this readme.md file, by a concrete example, how in the files .nb of the folder we obtain the canonical model by use of the theorem of Petri and compute the automorphism group.

First, we take the list of modular forms
for $C$ a concrete quotient curve of level $N$, each modular forms correspond to an abelian variety factor in the $\mathbb{Q}$-isogeny decomposition of the jacobian of $C$ (this list of modular forms for a quotient curve $C$ is obtained by the use of a Magma code that you can find in another folder
in this github). After, we obtain a basis of the differential forms of $C$ over the rationals, for this we need to lift the above modular forms to modular forms at level $N$ and also with rational coefficients. Once we obtain such basis, we can apply linear algebra to obtain the canonical model (by use of Petri theorem).

Secondly we explain the method in order to reach all involutions over the rational field for a quotient modular
curve which does not have any repeated factor in the Jacobian decomposition (once we have already the equations of the canonical model in a concrete way which the variables of the equations are choise related with the $\mathbb{Q}$-isogeny factors of the Jacobian decomposition of $C$).

For few concrete non-hyperelliptic quotient modular curve
$C:=X_0(N)/W_N$ that we used in the paper on automorphisms of quotient modular curve
 we add a file with Mathematica code where we compute
the Petri model equation for $C$ and check if $C$ has any 
involution or not. The usual notation for the file corresponding to
$C$ is NW_N+some details.nb The mathematica code was running in
Mathematica

##Example

-Quotient curve $X_0(210)/\angle w_6, w_{10},w_{15}\rangle$.

First we take the new modular forms that appears in the
$\mathbb{Q}$-decomposition of $Jac(X_0(210)/\angle w_6,w_{10},w_{15}\rangle)$ (By use of a code in magma also in this github, another folder) 
and lift them to
modular forms of level 210 by the use of the operators $B_d$ (see for
example Notation and Lemma 2.1 in paper Bars-Kamel-Schweizer
``Bielliptic quotient modular curves", or Bars-González ``Bielliptic quotient curves $X_0^*(N)$, Lemma 2.1, Prop.2.2). 
In this way we obtain a
$\mathbb{Q}$-basis of the differentials for the quotient modular
curve (with the usual isomorphism between weight two modular forms
and differentials).


```mathematica

f1 = q - q^2 - 2*q^3 + q^4 + 2*q^6 + q^7 - q^8 + q^9 - 2*q^12 - 
  4*q^13 - q^14 + q^16 + 6*q^17 - q^18 + 2*q^19 - 2*q^21 + 2*q^24 - 
  5*q^25 + 4*q^26 + 4*q^27 + q^28 - 6*q^29 - 4*q^31 - q^32 - 6*q^34 + 
  q^36 + 2*q^37 - 2*q^38 + 8*q^39 + 6*q^41 + 2*q^42 + 8*q^43 - 
  12*q^47 - 2*q^48 + q^49 + 5*q^50 - 12*q^51 - 4*q^52 + 6*q^53 - 
  4*q^54 - q^56 - 4*q^57 + 6*q^58 - 6*q^59 + 8*q^61 + 4*q^62 + q^63 + 
  q^64 - 4*q^67; f2 = 
 q - q^2 + q^3 - q^4 - 2*q^5 - q^6 - q^7 + 3*q^8 + q^9 + 2*q^10 + 
  4*q^11 - q^12 - 2*q^13 + q^14 - 2*q^15 - q^16 - 6*q^17 - q^18 + 
  4*q^19 + 2*q^20 - q^21 - 4*q^22 + 3*q^24 - q^25 + 2*q^26 + q^27 + 
  q^28 - 2*q^29 + 2*q^30 - 5*q^32 + 4*q^33 + 6*q^34 + 2*q^35 - q^36 + 
  6*q^37 - 4*q^38 - 2*q^39 - 6*q^40 + 2*q^41 + q^42 - 4*q^43 - 
  4*q^44 - 2*q^45 - q^48 + q^49 + q^50 - 6*q^51 + 2*q^52 + 6*q^53 - 
  q^54 - 8*q^55 - 3*q^56 + 4*q^57 + 2*q^58 + 12*q^59 + 2*q^60 - 
  2*q^61 - q^63 + 7*q^64 + 4*q^65 - 4*q^66; f3 = 
 q + q^3 - 2*q^4 - q^5 + q^7 - 2*q^9 - 3*q^11 - 2*q^12 + 5*q^13 - 
  q^15 + 4*q^16 + 3*q^17 + 2*q^19 + 2*q^20 + q^21 - 6*q^23 + q^25 - 
  5*q^27 - 2*q^28 + 3*q^29 - 4*q^31 - 3*q^33 - q^35 + 4*q^36 + 
  2*q^37 + 5*q^39 - 12*q^41 - 10*q^43 + 6*q^44 + 2*q^45 + 9*q^47 + 
  4*q^48 + q^49 + 3*q^51 - 10*q^52 + 12*q^53 + 3*q^55 + 2*q^57 + 
  2*q^60 + 8*q^61 - 2*q^63 - 8*q^64 - 5*q^65;
f4 = q + a*q^2 + (-a - 1)*q^3 + (-a + 2)*q^4 + q^5 - 4*q^6 - 
  q^7 + (a - 4)*q^8 + (a + 2)*q^9 + 
  a*q^10 + (a + 1)*q^11 + (-2*a + 2)*q^12 + (a + 3)*q^13 - 
  a*q^14 + (-a - 1)*q^15 - 
  3*a*q^16 + (-a - 3)*q^17 + (a + 4)*q^18 + (2*a - 2)*q^19 + (-a + 2)*
   q^20 + (a + 1)*q^21 + 4*q^22 + (-2*a - 2)*q^23 + 4*a*q^24 + 
  q^25 + (2*a + 4)*q^26 + (a - 3)*q^27 + (a - 2)*q^28 + (-3*a - 1)*
   q^29 - 4*q^30 + (a - 4)*q^32 + (-a - 5)*q^33 + (-2*a - 4)*q^34 - 
  q^35 + a*q^36 + 
  6*q^37 + (-4*a + 8)*q^38 + (-3*a - 7)*q^39 + (a - 4)*q^40 - 
  2*a*q^41 + 
  4*q^42 + (2*a + 6)*q^43 + (2*a - 2)*q^44 + (a + 2)*q^45 - 
  8*q^46 + (3*a - 1)*q^47 + 12*q^48 + q^49 + 
  a*q^50 + (3*a + 7)*q^51 + 2*q^52 + 
  2*a*q^53 + (-4*a + 4)*q^54 + (a + 1)*q^55 + (-a + 4)*
   q^56 + (2*a - 6)*q^57 + (2*a - 12)*q^58 - 
  4*q^59 + (-2*a + 2)*q^60 - 
  6*a*q^61 + (-1 - 2)*q^63 + (a + 4)*q^64 + (a + 3)*q^65; f5 = 
 q + q^2 + q^3 - q^4 + q^5 + q^6 + q^7 - 3*q^8 + q^9 + q^10 - q^12 - 
  6*q^13 + q^14 + q^15 - q^16 + 2*q^17 + q^18 - 8*q^19 - q^20 + 
  q^21 + 8*q^23 - 3*q^24 + q^25 - 6*q^26 + q^27 - q^28 - 2*q^29 + 
  q^30 + 4*q^31 + 5*q^32 + 2*q^34 + q^35 - q^36 - 2*q^37 - 8*q^38 - 
  6*q^39 - 3*q^40 - 6*q^41 + q^42 + 4*q^43 + q^45 + 8*q^46 + 8*q^47 - 
  q^48 + q^49 + q^50 + 2*q^51 + 6*q^52 + 10*q^53 + q^54 - 3*q^56 - 
  8*q^57 - 2*q^58 + 4*q^59 - q^60 - 2*q^61 + 4*q^62 + q^63 + 7*q^64 - 
  6*q^65; f6 = 
 q + a*q^2 - q^3 + 3*q^4 - q^5 - a*q^6 + q^7 + a*q^8 + q^9 - 
  a*q^10 + (-2*a + 2)*q^11 - 3*q^12 - 2*a*q^13 + a*q^14 + q^15 - 
  q^16 - 2*q^17 + a*q^18 + (2*a + 2)*q^19 - 3*q^20 - 
  q^21 + (2*a - 10)*q^22 + 4*q^23 - a*q^24 + q^25 - 10*q^26 - q^27 + 
  3*q^28 - 2*q^29 + a*q^30 + (2*a + 6)*q^31 - 
  3*a*q^32 + (2*a - 2)*q^33 - 2*a*q^34 - q^35 + 
  3*q^36 + (4*a + 2)*q^37 + (2*a + 10)*q^38 + 2*a*q^39 - a*q^40 - 
  2*q^41 - a*q^42 - 4*a*q^43 + (-6*a + 6)*q^44 - q^45 + 
  4*a*q^46 + (-4*a + 4)*q^47 + q^48 + q^49 + a*q^50 + 2*q^51 - 
  6*a*q^52 + (-2*a - 8)*q^53 - a*q^54 + (2*a - 2)*q^55 + 
  a*q^56 + (-2*a - 2)*q^57 - 2*a*q^58 + 4*a*q^59 + 3*q^60 - 
  2*q^61 + (6*a + 10)*q^62 + q^63 - 13*q^64 + 2*a*q^65;
f7 = q - q^2 - q^3 + q^4 - q^5 + q^6 - q^7 - q^8 + q^9 + q^10 - 
  4*q^11 - q^12 - 2*q^13 + q^14 + q^15 + q^16 - 6*q^17 - q^18 - q^20 +
   q^21 + 4*q^22 - 8*q^23 + q^24 + q^25 + 2*q^26 - q^27 - q^28 + 
  10*q^29 - q^30 - 8*q^31 - q^32 + 4*q^33 + 6*q^34 + q^35 + q^36 + 
  2*q^37 + 2*q^39 + q^40 - 2*q^41 - q^42 + 8*q^43 - 4*q^44 - q^45 + 
  8*q^46 + 4*q^47 - q^48 + q^49 - q^50 + 6*q^51 - 2*q^52 + 10*q^53 + 
  q^54 + 4*q^55 + q^56 - 10*q^58 + 4*q^59 + q^60 - 6*q^61 + 8*q^62 - 
  q^63 + q^64 + 2*q^65; f8 = 
 q + q^2 + q^3 + q^4 + q^5 + q^6 - q^7 + q^8 + q^9 + q^10 - 4*q^11 + 
  q^12 - 2*q^13 - q^14 + q^15 + q^16 + 2*q^17 + q^18 + 4*q^19 + q^20 -
   q^21 - 4*q^22 - 8*q^23 + q^24 + q^25 - 2*q^26 + q^27 - q^28 - 
  2*q^29 + q^30 + q^32 - 4*q^33 + 2*q^34 - q^35 + q^36 + 6*q^37 + 
  4*q^38 - 2*q^39 + q^40 - 6*q^41 - q^42 - 4*q^43 - 4*q^44 + q^45 - 
  8*q^46 + q^48 + q^49 + q^50 + 2*q^51 - 2*q^52 - 10*q^53 + q^54 - 
  4*q^55 - q^56 + 4*q^57 - 2*q^58 + 12*q^59 + q^60 + 14*q^61 - q^63 + 
  q^64 - 2*q^65;
P4 = x^2 + x - 4;
P6 = x^2 - 5;

[*14, 21, 35, 35, 105, 105, 210, 210*]

X4 = Table[ Solve[P4 == 0, x][[i, 1, 2]], {i, 1, 2}]
X6 = Table[ Solve[P6 == 0, x][[i, 1, 2]], {i, 1, 2}]

f41 = -((f4 /. a -> X4[[1]]) - (f4 /. a -> X4[[2]]))/( Sqrt[17]) // 
   Expand;
f42 = ((f4 /. a -> X4[[1]]) + (f4 /. a -> X4[[2]]) + f41)/( 2) // 
   Expand;

f61 = -((f6 /. a -> X6[[1]]) - (f6 /. a -> X6[[2]]))/( Sqrt[5]) // 
   Expand;
f62 = ((f6 /. a -> X6[[1]]) + (f6 /. a -> X6[[2]]) + f61)/( 2) // 
   Expand;


g1 = f1 + 5 (f1 /. q -> q^5) // Expand;
g11 = g1 + 3 (g1 /. q -> q^3) // Expand;
g2 = f2 - 2 (f2 /. q -> q^2) // Expand;
g21 = g2 - 5 (g2 /. q -> q^5) // Expand;
g3 = f3 + 2 (f3 /. q -> q^2) // Expand;
g31 = g3 + 3 (g3 /. q -> q^3) // Expand;
g41 = f41 - 2 (f41 /. q -> q^2) // Expand;
g411 = g41 - 3 (g41 /. q -> q^3) // Expand;
g42 = f42 - 2 (f42 /. q -> q^2) // Expand;
g421 = g42 - 3 (g42 /. q -> q^3) // Expand;
g5 = f5 - 2 (f5 /. q -> q^2) // Expand;
g61 = f61 + 2 (f61 /. q -> q^2) // Expand;
g62 = f62 + 2 (f62 /. q -> q^2) // Expand;

h1 = Series[g11, {q, 0, 55}]; h2 = Series[g21, {q, 0, 55}]; h3 = 
 Series[g31, {q, 0, 55}]; h4 = Series[g411, {q, 0, 55}]; h5 = 
 Series[g421, {q, 0, 55}]; h6 = Series[g5, {q, 0, 55}]; h7 = 
 Series[g61, {q, 0, 55}]; h8 = Series[g62, {q, 0, 55}]; h9 = 
 Series[f7, {q, 0, 55}];

h10 = Series[f8, {q, 0, 55}];

```````


Here, the decomposition of the Jacobian is:
$$1_{E14a,f1}+1_{E21a,f2}+1_{E35a,f3}+2_{35.2.a.b,f4}+1_{E105a,f5}+2_{105.2.a.b,f6}+1_{E210d,f7}+1_{E210e,f8}$$
where we use Cremona tables notation for elliptic curves and LNMD notation for higher dimension abelian varieties $A_f$.

We observe that the respective levels of the modular forms are [*14, 21, 35, 35, 105, 105, 210, 210*].

Note that $f4$ and $f6$ corresponds to factors $A_f$ of dimension two, thus the modular forms $f4$, and $f6$
are defined over quadratic fields corresponding to $P4$ and $P6$ respectively, and to obtain
a $\mathbb{Q}$-basis for such modular forms we proceed as bellow and we obtain $f41,f42$, and $f61$, $f62$.

After finding such basis, we need to lift $f1$ from level 14 to level 210 such that the action of the AL-involutions
$w_{6},w_{10},w_{15}$ act as 1, and we obtain such lift by use of the operators $B_d$ following Lemma 2.1 and Prop. 2.2
of the Bars, González paper ``Bielliptic quotient modular curves $X_0^*(N)$" (result derived from Atkin-Lehner paper ''Hecke operators").

This procedure to lift until level 210 we need to deal for all the modular forms of the base which level is strictly lower than 210, i.e. for 
$$f_1,f_2,f_3,f_{41},f_{42},f_5,f_{61},f_{62}.$$
Once we reach level 210 but impossing in such liftings that $w_{6},w_{10},w_{15}$ act as 1, we obtain the
basis of the modular forms at level 210 which we can compute the Petri model.


We compute the canonical model (by a theorem of Petri) via solving the following linear system.

We show how obtain such canonical model in the quotient curve in the example $X_0(210)/\langle w_6, w_{10},w_{15}\rangle$.



``````mathematica



P0 = {x1^2, x2^2, x3^2, x4^2, x5^2, x6^2, x7^2, x8^2, x9^2, x10^2, 
    x1 x2, x1 x3, x1 x4, x1 x5, x1 x6 , x1 x7, x1 x8, x1 x9,  x1 x10, 
    x2 x3, x2 x4, x2 x5, x2 x6, x2 x7, x2 x8, x2 x9, x2 x10, x3 x4, 
    x3 x5, x3 x6, x3 x7, x3 x8, x3 x9, x3 x10,  x4 x5, x4 x6, x4 x7, 
    x4 x8, x4 x9, x4 x10, x5 x6, x5 x7, x5 x8, x5 x9, x5 x10,  x6 x7, 
    x6 x8, x6 x9,  x6 x10, x7 x8, x7 x9, x7 x10, x8 x9, x8 x10, 
    x9 x10}.{a1, a2, a3, a4, a5, a6, a7, a8, a9, a10, a11, a12, a13, 
    a14, a15, a16, a17, a18, a19, a20, a21, a22, a23, a24, a25, a26, 
    a27, a28, a29, a30, a31, a32, a33, a34, a35, a36, a37, a38, a39, 
    a40, a41, a42, a43, a44, a45, a46, a47, a48, a49, a50, a51, a52, 
    a53, a54, a55};

Q = P0 /. {x1 -> h1, x2 -> h2, x3 -> h3, x4 -> h4, x5 -> h5, x6 -> h6,
    x7 -> h7, x8 -> h8, x9 -> h9, x10 -> h10}; l = 
 Table[Coefficient[ Q, q, i], {i, 2, 63}]; T = 
 Solve[l == {0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 
     0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0,
      0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 
     0}, {a1, a2, a3, a4, a5, a6, a7, a8, a9, a10, a11, a12, a13, a14,
     a15, a16, a17, a18, a19, a20, a21, a22, a23, a24, a25, a26, a27, 
    a28, a29, a30, a31, a32, a33, a34, a35, a36, a37, a38, a39, a40, 
    a41, a42, a43, a44, a45, a46, a47, a48, a49, a50, a51, a52, a53, 
    a54, a55}][[1]]
QQ = (P0 /. T) // Factor // Numerator

QQ /. {x1 -> h1, x2 -> h2, x3 -> h3, x4 -> h4, x5 -> h5, x6 -> h6, 
  x7 -> h7, x8 -> h8, x9 -> h9, x10 -> h10}

``````````````

The last outline line should appear $0[q]^{57}$ claiming that is almost zero, i.e. that the
model obtained $QQ$ is zero when we substitute the variables by the basis of modular 
forms, is particular the number of degree 2 equations in the canonical model
are given by the free $a_{j}$ that are not fixed in the outline result from Solve[l==....], 
in particular we obtain exactly $(g-2)(g-3)/2$ degree two equations corresponding to the free variables $a_{j}$ which remain free
in solving the linear system (this is enough to obtain the canonical model for non-hyperelliptic quotient curves of genus $>3$ 
if such quotient curve is not a smooth quintic plane curve or a trigonal curve).


Let us now go to determine the automorphism group for the quotient modular curve.

Because no repeated factor in the Jacobian decomposition over the rationals
all automorphism over the rationals are involutions acting as +1 or +1 in each factor from the 
Q-decomposition of the abelian variety, thus need to check if
any $x1\mapsto \pm x1$, $x2\mapsto\pm x2$, $x3\mapsto \pm x3$, $(x_4,x5)\mapsto \pm (x_4,x_5)$,
$x6\mapsto \pm x6$, $(x7,x8)\mapsto\pm (x7,x8)$, $x9\mapsto \pm x9$ and $x10\mapsto x10$.

All these, are the all possible involutions, and need to check if keep invariant the canonical
model or not, which is quite easy, we propose the following mathematica code:


``````mathematica


QQ1 = (QQ - (QQ /. {x1 -> x1, x2 -> x2, x3 -> -x3, x4 -> -x4, 
       x5 -> -x5, x6 -> -x6, x7 -> -x7, x8 -> -x8, x9 -> -x9, 
       x10 -> -x10})) // Factor
QQ1 /. {x1 -> h1, x2 -> h2, x3 -> h3, x4 -> h4, x5 -> h5, x6 -> h6, 
   x7 -> h7, x8 -> h8, x9 -> h9, x10 -> h10};

QQ1 = (QQ - (QQ /. {x1 -> x1, x2 -> x2, x3 -> x3, x4 -> -x4, 
        x5 -> -x5, x6 -> -x6, x7 -> -x7, x8 -> -x8, x9 -> -x9, 
        x10 -> -x10})) // Factor;
QQ1 /. {x1 -> h1, x2 -> h2, x3 -> h3, x4 -> h4, x5 -> h5, x6 -> h6, 
   x7 -> h7, x8 -> h8, x9 -> h9, x10 -> h10};
QQ1 = (QQ - (QQ /. {x1 -> x1, x2 -> x2, x3 -> x3, x4 -> x4, x5 -> x5, 
        x6 -> -x6, x7 -> -x7, x8 -> -x8, x9 -> -x9, x10 -> -x10})) // 
   Factor;
QQ1 /. {x1 -> h1, x2 -> h2, x3 -> h3, x4 -> h4, x5 -> h5, x6 -> h6, 
   x7 -> h7, x8 -> h8, x9 -> h9, x10 -> h10};

QQ1 = (QQ - (QQ /. {x1 -> x1, x2 -> x2, x3 -> x3, x4 -> -x4, 
        x5 -> -x5, x6 -> x6, x7 -> x7, x8 -> x8, x9 -> x9, 
        x10 -> x10})) // Factor;
QQ1 /. {x1 -> h1, x2 -> h2, x3 -> h3, x4 -> h4, x5 -> h5, x6 -> h6, 
   x7 -> h7, x8 -> h8, x9 -> h9, x10 -> h10};
QQ1 = (QQ - (QQ /. {x1 -> x1, x2 -> x2, x3 -> x3, x4 -> x4, x5 -> x5, 
        x6 -> x6, x7 -> x7, x8 -> x8, x9 -> -x9, x10 -> -x10})) // 
   Factor;
QQ1 /. {x1 -> h1, x2 -> h2, x3 -> h3, x4 -> h4, x5 -> h5, x6 -> h6, 
   x7 -> h7, x8 -> h8, x9 -> h9, x10 -> h10};

````````

running all the situations, for example we reach an involution in the following
situation

````mathematica


QQ1 = (QQ - (QQ /. {x1 -> x1, x2 -> x2, x3 -> x3, x4 -> x4, x5 -> x5, 
        x6 -> -x6, x7 -> x7, x8 -> x8, x9 -> -x9, x10 -> x10})) // 
   Factor;
QQ1 /. {x1 -> h1, x2 -> h2, x3 -> h3, x4 -> h4, x5 -> h5, x6 -> h6, 
  x7 -> h7, x8 -> h8, x9 -> h9, x10 -> h10}

`````````

the output is $O[q]^{57}$, therefore here we obtain that QQ1 is zero, therefore we obtain an involution.

Running all the possible situations (recall that only need to check action of $\pm 1$ in the variables of the canonical model obtained, 
we get all the involutions for the modular curves, one is the above involutions and there are exactly two more:


````mathematica


QQ1 = (QQ - (QQ /. {x1 -> x1, x2 -> -x2, x3 -> x3, x4 -> -x4, 
        x5 -> -x5, x6 -> -x6, x7 -> x7, x8 -> x8, x9 -> x9, 
        x10 -> -x10})) // Factor;
QQ1 /. {x1 -> h1, x2 -> h2, x3 -> h3, x4 -> h4, x5 -> h5, x6 -> h6, 
  x7 -> h7, x8 -> h8, x9 -> h9, x10 -> h10}

QQ1 = (QQ - (QQ /. {x1 -> -x1, x2 -> x2, x3 -> -x3, x4 -> x4, 
        x5 -> x5, x6 -> -x6, x7 -> -x7, x8 -> -x8, x9 -> x9, 
        x10 -> x10})) // Factor;
QQ1 /. {x1 -> h1, x2 -> h2, x3 -> h3, x4 -> h4, x5 -> h5, x6 -> h6, 
  x7 -> h7, x8 -> h8, x9 -> h9, x10 -> h10}

`````````````

Thus see the file xzerow6w10w15.nb for all the computations (and the checking for all situations that needed).
Finally, we can conclude that all automorphism
over $\mathbb{Q}$ of the quotient curve $X_0(210)/\langle w_6,w_{10},w_{15}\rangle$ are $C_2\times C_2$. Because 210 is square-free, we have that all automorphism of the quotient curve are rational, thus
in this case we obtain all the automorphism group for such quotient modular curve.



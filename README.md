# Mathematics-for-Data-Science
Learnings from Essential Mathematics for Data Science Book 

## Ch1: Basic Math and Calculus Review

### Number Theory

1. Natural Number = {1,2,3....}
2. Whole Number = {0,1,2,3....}
3. Integers = {....-3,-2,-1,0,1,2,3,4....}
4. Rational Numbers = can be expressed as a fraction. ex $\frac{2}{3}$, $\frac{2}{1}$. So, all finite deciamls and integers. + & -.
5. Irrational Numbers = cannot be expressed as a fraction. ex. $\pi$, $\sqrt2$ etc.
6. Real Number = {rational and irrational}
7. Complex and imaginary numbers = $\ e$ , $\ i$ etc.

### Order of Operations = PEMDAS

ex: solve - $\ 2 \times \frac{\left( 3 + 2 \right) ^2}{  5 }- 4$

```python
my_value = 2*(3+2)**2 / 5 - 4
print(my_value) # prints 6.0
```
Tip: ALways use parenthesis for more clarity

```python
my_value = 2*((3+2)**2/5)-4
print(my_value)
```

### Variables 

named placeholder for unspecified or unknown number

```python
x=int(input("please input a number\n"))
prd=3*x
print(prd)
```

### Functions 

input $\rightarrow$ function $\rightarrow$ output

```python
#declaring linear function in python

def f(x):
    return 2 *x +1

x_val=[0,1,2,3]
for x in x_val:
    y=f(x)
    print(y)
```

```python
#graphing the above function

import sympy import *

x =symbols('x')
f=2*x+1
plot(f)
```

Ex: exponential function f(x) = $\ x^2 + 1$

``` python
from sympy import *
x =symbols('x')
f = x**2 + 1
plot(f)
```
Ex: two-variable graph

```python
from sympy import *
from sympy.plotting import plot3d

x,y =symbols('x y')
f = 2*x + 3*y
plot3d(f)
```

### Summations 

$\sum_ {i=1}^5  2 i$ = (2)1+ (2)2 + (2)3 + (2)4 + (2)5

```python
summation = sum(2*i for i in range (1,6)) # range only takes [x,y) not [x,y]
print(summation)
```
### Exponents 

multiplying a number by itself

$\ 2^3$ = 2x2x2 = 8

### Logarithms

finds power for a specific number and base. Has applications in measuring earthquakes to managing volume in stereo

ex: $\log_{a} b = x \leftrightarrow \ a^x =b$

```python
#log in python
# 2 raised to what power is 8
x = log(8,2)
print(x) #3.0
```
Useful properties :

1. $\log\left( a \times b \right) = \log\left(a\right) + \log\left(b\right)$
2. $\log\left( \frac{a}{b} \right) = \log\left(a\right) - \log\left(b\right)$
3. $\log \left( a^n \right) = n \times \log \left(a\right)$
4. $\log\left(1\right)=0$
5. $\log \left( x^{-1} \right) = \log \left( \frac{1}{x} \right) = -\log \left(x\right)$

### Euler's Number 
A property of Euler’s number is its exponential function is a derivative to itself, which is convenient for exponential and logarithmic functions.

$\lim_{n \to \infty} \left( 1 + \frac{1}{n} \right) ^ n = e = 2.71828169...$

```python
from sympy import *
n=symbols('n')
f=(1+(1/n))**n
res=limit(f,n,oo)

print(res) # e
print(result.evalf()) # 2.718281...
```

### Natural Logarithms

when e is the base of log, it is called natural log. notation: ln()

$\log_{e}{10} = \ln 10$

```python
from math import log

x=log(10)
print(x) # 2.3025...
```

### Limits 

As we have seen with Euler’s number, some interesting ideas emerge when we forever increase or decrease an input variable and the output variable keeps approaching a value but never reaching it.

$\ f(x) = \frac{1}{x}$

```python
from sympy import *
x=symbols('x')
f=1/x
res = limit(f,x,oo)
print(res) # 0 
plot(res)
```
### Derivatives

A derivative tells a slope of a function and is useful to measure the rate of change at any point in a function.

$\frac{d}{dx} x^2 = 2x$

```python
from sympy import *
x=symbols('x")
f=x**2
dx_f = diff(f)
print(dx_f) # 2*x
```

### Partial Derivative 

Derivatives of functions that have multiple input variable.

ex: $\frac{d}{dy} 2 x^3 + 3 y^3 = 9 y^2$

```python
from sympy import *
from sympy.plotting import plot3d

x,y=symbols('x y')
f=2*x**3 + 3*y**3
dx_f=diff(f,x)
dy_f=diff(f,y)

print(dx_f) #6*x**2
print(dy_f) #9*y**2

plot3d(f)
```

#### Using Limits to calculate derivatives

Using Limits, we can define the slope of a tangent to a function.

When given a function f(x), and given a point P( $\ x_0$ , f( $\ x_0$ )) on f, if we want to find the slope of the tangent line to f at P, we can do this by picking a nearby point Q ($\ x_0$ + h , f($ x_0$ + h )
![image](https://github.com/Vineet-Loyer/Mathematics-for-Data-Science/assets/30760868/332af38b-7238-474f-9114-7de637462d8f)

Q is h units away from P, h is snall

then find the slope of PQ, the slope of scant line eqn = $\ m_{sec}  \frac{f( \ x_0 + h) - f( \ x_0)}{h}$

We can say that, if h is small, the slope of this scant line should be a good approximation of slope of tangent line.

so, $\ m_{tan} = \lim_{h \to 0} \frac{f(\ x_{0} + h) - f( \ x_{0})}{h}$ 

this is also derivative equation, written as $\ f^{'}{x} = \lim_{h \to 0} \frac{f(x +h) - f(x)}{h}$ ; if the limits exisits f is said to be differential at x, otherwise f is non-differential at x.

```python
#using limits to calculate slope in python

from sympy import *

# "x" and step size "s"
x,s=symbols('x s')
#declare function
f=x**2

slope_f = (f.subs(x,x+s) -f)/((x+s) - x)

#substitutes 2 for x
slope_2 = slope_f.subs(x,2)

#calculates slope at x=2, as step size approaches 0
result = limit(slope_2,s,0)

print(result) # 4
```

```python
# using limits to calculate derivative
from sympy import *

x,s=symbols('x s')

#function dec.
f=x**2

#slope b/w two points
slope_f=(f.subs(x,x+s)-f)/(x+s)-x)

#calculates derivative function
result=limit(slope_f,s,0)

print(result) #2x

```

## The Chain Rule

When we build a neural network, we are going to need a special math trick called chain rule - it is a formula used to find derivative of a composite function.

Example: $\ y = x^2 + 1$ and $\ z = y^3 - 2$
we can say that $\ z = \left( x^2 + 1 \right)^3 - 2$

``` python 
from sympy import *

z=(x**2 + 1)**3 -2
dz_dx = diff(z,x)
print(dz_dx)  # 6*x*(x**2 + 1)**2
```

How about calculating the derivative without chain rule ?

$\frac{dy}{dx} \left( x^2 + 1 \right) = 2x$

$\frac{dz}{dx} \left(y^3 - 2 \right) = 3y^2$

$\frac{dz}{dx} = (2x)(3y^2) = 6xy^2 = 6x(x^2 + 1)^2$ 

```python
from sympy import *
x,y =symbols('x y')
y1=x**2+1
dy_dx = diff(y1)
z=y**3 -2
dz_dy = diff(z)

dz_dx_chain = (dy_dx * dz_dy).subs(y,y1)
dz_dx_no_chain = diff(z.subs(y,y1))

print(dz_dx_chain) #6*x(x**2 + 1)**2
print(dz_dx_no_chain) #6*x*(x**2 + 1) **2
```
## Integrals

Finding area under the curve for a given range.

![image](https://github.com/Vineet-Loyer/Mathematics-for-Data-Science/assets/30760868/d2f80653-a6e7-4d72-bc5a-ea3b9b59cac0)
Packing rectangles under the curve to calculate area.

The mroe the rectangles mroe accurate the area.

```python
#integral approximation in Python

def approximate_integral(a,b,n,f):
    delta_x= (b-a)/n
    total_sum=0
    for i in range(1,n+1)
        midpoint = 0.5 *(2*a + delta_x *(2*i -1))
        total_sum+=f(midpoint)
    return total_sum*delta_x
def my_function(x)
    return x**2 +1
area = approximate_integrals(a=0,b=1,n=5,f=my_function) #dividing in 5 rectangles

print(area) # 1.33
```
similarly, if n=10000

```python
area = approximate_integral(a=0,b=1,n=1000,f=my_function)
print(area) # 1.3333333
```

Using Sympy for performing integration

```python
from sympy import *

x= symbols('x')
f=x**2 + 1
area = integrate(f,(x,0,1))
print(area)
```

Using limits to calculate integrals
```python
from sympy import *

# Declare variables to SymPy
x, i, n = symbols('x i n')

# Declare function and range
f = x**2 + 1
lower, upper = 0, 1

# Calculate width and each rectangle height at index "i"
delta_x = ((upper - lower) / n)
x_i = (lower + delta_x * i)
fx_i = f.subs(x, x_i)

# Iterate all "n" rectangles and sum their areas
n_rectangles = Sum(delta_x * fx_i, (i, 1, n)).doit()

# Calculate the area by approaching the number
# of rectangles "n" to infinity
area = limit(n_rectangles, n, oo)

print(area) # prints 4/3
```

## Ch2: Probability

Imp concepts wrt DS - baye's Theorem , binomial distribution, beta distribution

### Probability vs Odds
Probability P(X) = $\frac{Favourable_Outcomes}{Total_number_of_outcomes}$
whereas, Odds O(X) = $\frac{chances_of_winning}{chances_of_losing}$

Since, Chances of Losing = 1 - Chances of Winning (in mutually exclusive outcomes)
Example - Odds of winning a cricket match for India against England is 7:3 ->  i.e 7 chances of winning, 3 chances of losing.
In probability terms - $\frac{winning} {(winning + losing )}$ = $\frac{7}{10}$ or 0.7 or 70%

Thus, P(X) = $\frac{O(X)}{1 + O(X)}$

### Joint Probabilities (AND)

EX - Proabability of getting a Heads AND a 6 on a die ? 

P( A AND B ) = P(A) x P(B) 

### Union Probabilities (OR)

EX - Getting a 4 OR a 6 on a die ?

P(A OR B) = P(A) + P(B) - P ( A AND B )


why  " - P(A AND B)?" -> to remove duplicates

ex: Getting a head  OR  a 6 on a die ? -> possible sets:    *H1*  *H2*  *H3*  *H4*  *H5*  *H6* T1 T2 T3 T4 T5 *T6* = so favourable outcomes = 7, total outcomes = 12 ; therefore P(H OR 6) = $\frac{7}{12}$

via Formula = P(H) = $\frac{1}{2}$ ; P(6) = $\frac{1}{6}$

P( H OR 6) = $\frac{1}{2} + \frac{1}{6} - \frac{1}{12}$
           = $\frac{4}{6} - \frac{1}{12}$
           = $\frac{7}{12}$
### Baye's Theorem and Conditional Probability



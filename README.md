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



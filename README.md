# Correlation and regression for data analysis
# Aim : 

To analyse given data using coeffificient of correlation and regression line
![image](https://user-images.githubusercontent.com/104613195/168224136-d6b64e64-7d3d-4775-9337-c8f96fe41f2d.png)


# Software required :  

Python

# Theory:

Correlation describes the strength of an association between two variables, and is completely symmetrical, the correlation between A and B is the same as the correlation between B and A. However, if the two variables are related it means that when one changes by a certain amount the other changes on an average by a certain amount.  

If y represents the dependent variable and x the independent variable, this relationship is described as the regression of y on x. The relationship can be represented by a simple equation called the regression equation. The regression equation representing how much y changes with any given change of x can be used to construct a regression line on a scatter diagram, and in the simplest case this is assumed to be a straight line.

# Procedure :

![image](https://user-images.githubusercontent.com/104613195/168225866-ac8f6610-bdc3-4ac2-a24e-2b24ba08e189.png)

# experiment

![image](https://github.com/ramjan1729/Correlation_Regression/assets/103921593/9eb48cbf-8ca3-4cd9-8440-ff45fd98333e)
# program:
```
import numpy as np
import math
import scipy.stats
L=[int(i) for i in input().split()]
N=len(L)
M=max(L) 
X=[]
f=[]
for i in range (M+1):
   c = 0
   for j in range(N):
       if L[j]==i:
           c=c+1
   f.append(c)
   X.append(i)
Sff=np.sum(f)
p=[]
for i in range(M+1):
   p.append(f[i]/Sff) 
mean=np.inner(X,p)
p=[]
E=[]
xi=[]
print("X P(X=x) Obs.Fr Exp.Fr xi")
print("--------------------------")
for x in range(M+1):
   p.append(math.exp(-mean)*mean**x/math.factorial(x))
   E.append(p[x]*Sff)
   xi.append((f[x]-E[x])**2/E[x])
   print("%2.2f %2.3f %4.2f %3.2f %3.2f"%(x,p[x],f[x],E[x],xi[x]))
print("--------------------------")
cal_chi2_sq=np.sum(xi)
print(f"Calculated value of Chi square is {cal_chi2_sq:.2f}")
table_chi2=scipy.stats.chi2.ppf(1-.01,df=M)
print(f"Table value of chi square at 1 level is {table_chi2:.2f}")
if cal_chi2_sq<table_chi2:
   print("The given data can be fitted in poisson Distribution at 1% LOS")
else:
   print("The given data cannot be fitted in Poisson Distribution at 1% LOS")
```
developed by: kiruthika vasanthi.M 
reg no. 212225040189

# output:
<img width="804" height="578" alt="WhatsApp Image 2026-05-28 at 20 53 34" src="https://github.com/user-attachments/assets/850759d0-e474-4ccc-9adf-970b429c3504" />

# Result
The Poisson distribution is fitted for the objects arrived from feeder per minute and the data is tested using Chi-square test.


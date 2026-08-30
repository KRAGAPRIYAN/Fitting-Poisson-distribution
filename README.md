# Fitting-Poisson-Distribution

**Date:** 28/07/2026

## EXP: 2 — Fitting Poisson Distribution

### Aim

To fit Poisson distribution for the arrival of objects per minute from the feeder.

### Software Required

* Python
* Visual component tool

### Theory

The Poisson distribution is the discrete probability distribution of the number of events occurring in a given time period, given the average number of times the event occurs over that time period.

![Poisson Distribution Formula](<Screenshot 2026-08-30 151242.png>)

* An event can occur any number of times during a time period.
* Events occur independently.
* The rate of occurrence is constant.
* The probability of an event occurring is proportional to the length of the time period.

### Procedure

![Procedure](<Screenshot 2026-08-30 151302.png>)

### Program

**Name:** K RAGAPRIYAN
**Reg. No:** 212225040323

```python
import numpy as np

import math

import scipy.stats

L=[int(i) for i in input().split()]

N=len(L); M=max(L) 

X=list();f=list()

for i in range(M+1):

    c = 0

    for j in range(N):

        if L[j]==i:

            c=c+1

    f.append(c)

    X.append(i)

sf=np.sum(f)

p=list()

for i in range(M+1):

    p.append(f[i]/sf) 

mean=np.inner(X,p)

p=list();E=list();xi=list()

print("X P(X=x) Obs.Fr Exp.Fr xi")

print("--------------------------")

for x in range(M+1):

    p.append(math.exp(-mean)*mean**x/math.factorial(x))

    E.append(p[x]*sf)

    xi.append((f[x]-E[x])**2/E[x])

    print("%2.2f %2.3f %4.2f %3.2f %3.2f"%(x,p[x],f[x],E[x],xi[x]))

print("--------------------------")

cal_chi2_sq=np.sum(xi)

print("Calculated value of Chi square is %4.2f"%cal_chi2_sq)

table_chi2=scipy.stats.chi2.ppf(1-.01,df=M)

print("Table value of chi square at 1 level is %4.2f"%table_chi2)

if cal_chi2_sq<table_chi2:

    print("The given data can be fitted in poisson Distribution at 1% LOS")

else:

    print("The given data cannot be fitted in Poisson Distribution at 1% LOS")
```

### Output

![Output](<Screenshot 2026-08-30 151317.png>)

### Results

The Poisson distribution is fitted for the objects arrived from feeder per minute and the data is tested using Chi-square test.

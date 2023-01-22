# Project-1---Visualize-ODE-w-SciPy
# import required libraries
import numpy as np
from scipy.integrate import odeint
import matplotlib.pyplot as plt

# function that returns ds/dt
def model(s,n,f):
    dsdt = f/(((-f * n) + n + f) * ((-f * n) + n + f))
    print(dsdt)
    return dsdt

# initial condition
s0 = 1

# x values increasing from 1 to 100
n = np.linspace(1,200, 1000)
# solve ODEs
f = 0.95
y1 = odeint(model,s0,n,args=(f,))
f = 0.90
y2 = odeint(model,s0,n,args=(f,))
f = 0.75
y3 = odeint(model,s0,n,args=(f,))
f = 0.50
y4 = odeint(model,s0,n,args=(f,))
f = 1
y5 = odeint(model, s0, n, args=(f,))

# plot results
plt.plot(n,y1,'r-',linewidth=2,label='p=0.95')
plt.plot(n,y2,'b--',linewidth=2,label='p=0.90')
plt.plot(n,y3,'g:',linewidth=2,label='p=0.75')
plt.plot(n,y4,'y+',linewidth=2,label='p=0.50')
plt.xlabel('Number of Processors (n)')
plt.ylabel('Speedup')
plt.legend()
plt.show()


# Plots the graph where the program is 100% parallelizable
# to show it is linear
"""
plt.plot(n,y5,'md',linewidth=2,label='p=1.00')
plt.xlabel('Number of Processors (n)')
plt.ylabel('Speedup')
plt.legend()
plt.show()
"""

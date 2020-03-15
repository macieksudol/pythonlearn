# pythonlearn
#proste wykresy

import matplotlib.pyplot as plt
import math as m
tab=[]
z=0
for x in range(1,300):
    tab.append(m.sin(z+3.14)+2)
    z=z+0.1

plt.plot(tab,color='r')
plt.grid( linestyle='-', linewidth=1)
plt.show()

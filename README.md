# ML-Assignment-4
Exploring the PageRank algorithm.

import numpy as np
import numpy.linalg as la
from readonly.PageRankFunctions import *
np.set_printoptions(suppress=True)
L=np.array([[0,   1/2, 1/3, 0, 0,   0 ],
            [1/3, 0,   0,   0, 1/2, 0 ],
            [1/3, 1/2, 0,   1, 0,   1/2 ],
            [1/3, 0,   1/3, 0, 1/2, 1/2 ],
            [0,   0,   0,   0, 0,   0 ],
            [0,   0,   1/3, 0, 0,   0 ]])

eVals, eVecs = la.eig(L) #understood# Gets the eigenvalues and vectors
order = np.absolute(eVals).argsort()[::-1] # Orders them by their eigenvalues
eVals = eVals[order]
eVecs = eVecs[:,order]

r = eVecs[:, 0] # Sets r to be the principal eigenvector
100 * np.real(r / np.sum(r))#understood # Make this eigenvector sum to one,
                             #then multiply by 100 Procrastinating Pats

#poweriterationmethod
r=100*np.ones(6)/6
print(r)
r= L @ r
print(r)
for i in np.arrange(5):
    r=L @ r

print(r)
#answerafterconvergence
r=100*np.ones(6)/6
lastR=r
r= L @ r
i=0
while la.norm(lastR-r)>.01:
    lastR=r
    r=L @ r
    i+=1
print(str(i)+"iterations to convergence")
print(r)


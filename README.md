# 3body

## Quick writeup at https://cepheus.quantumgalaxies.com/whitepages

## WARNING, we found a bug and smashed it that could impact the quality of the computation...the corrected file will probably be up around Jan 21th or so...

## WARNING, processing, looks like its gonna be a few weeks...SORRY, its debugged pretty well, but runtime is ongoing on a smaller machine. 
## WARNING, you see, the critcal component here is the Condition Number of the overlap matrix ... and its not there yet.


A set of outputs related to our runtime of 3body quantum problems

    import pandas as pd
    import numpy as np


    m = pd.read_csv('matrix_0.csv')
    m = m.groupby(['Operator','bra-left','bra-right'])['Element'].mean()

    def M(i):
      """
      preprocessing...remove lowest state as its not allowed by fermi statistics.
      returns a matrix
      """
      u = np.reshape(m.loc[i].values,(24,2,24,2)))
      return np.transpose(u,(1,3,0,2))[0][0][1:24,1:24]

    def H(i):
      """
      Hamiltonian on arg 0 and polarizations in x, y, and z with 1, 2, 3.
      """
      if i == 0: 
          return sum([ M(i+1) for i in range(7)] )
      else:
          return M(i+7)
      
    def S():
      """
      Overlap
      """  
      return M(0)
  
  

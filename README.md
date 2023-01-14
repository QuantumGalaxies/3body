# 3body

## Quick writeup at https://cepheus.quantumgalaxies.com/whitepages

EE = spin 1/2 subspace
A2 = spin 3/2 subspace


A set of outputs related to our runtime of 3body quantum problems

    import pandas as pd
    import numpy as np
    
    desc = ['EE','A2']


    m = pd.read_csv('matrix_desc[x]_.csv')
    m = m.groupby(['Operator','bra-left','bra-right'])['Element'].mean()

    def M(i):
      """
      preprocessing...remove lowest state as its not allowed by fermi statistics.
      returns a matrix
      """
      MM = int(np.sqrt(len(m.loc[0])))
      
      u = np.reshape(m.loc[i].values,(MM,MM)))
      return (u)

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
  
  

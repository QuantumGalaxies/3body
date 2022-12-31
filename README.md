# 3body
A set of outputs related to our runtime of 3body quantum problems

    import pandas as pd
    import numpy as np


    m = pd.read_csv('matrix_0.csv')
    m = m.groupby(['Operator','bra-left','bra-right'])['Element'].mean()

    def M(i):
      """
      preprocessing...
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
  
  

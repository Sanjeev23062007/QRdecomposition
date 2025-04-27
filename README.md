# Algorithm for QR Decomposition
## Aim:
To implement QR decomposition algorithm using the Gram-Schmidt method.
## Equipment’s required:
1.	Hardware – PCs
2.	Anaconda – Python 3.7 Installation / Moodle-Code Runner
## Algorithm:
### Step 1:	
Intialize the matrix Q and u
### Step 2:	
The vector u and e is given by
   
   ![ex4](https://github.com/user-attachments/assets/a780768a-b94f-405b-88f9-d654bf46a688)

   ![ex6](https://github.com/user-attachments/assets/069835e8-52f6-4c2e-abc2-414389f4a454)

   ![ex3](https://github.com/user-attachments/assets/35d9cb7f-13d5-4433-b8b6-1d2ea955274e)


### Step 3:	
Obtain the Q matrix   
    ![eqn4](./ex1.jpg)
### Step 4:	
Construct the upper triangular matrix R
    ![eqn5](./ex2.jpg)

## Program:
### Gram-Schmidt Method
```python 

Program to QR decomposition using the Gram-Schmidt method
Developed by: Sanjeev A
RegisterNumber: 212224230246

import numpy as np

def QR_Decomposition(A):
    n, m = A.shape  # get the shape of A

    Q = np.empty((n, n))  # initialize matrix Q
    u = np.empty((n, n))  # initialize matrix u

    u[:, 0] = A[:, 0]
    Q[:, 0] = u[:, 0] / np.linalg.norm(u[:, 0])

    for i in range(1, n):
        u[:, i] = A[:, i]
        for j in range(i):
            u[:, i] -= (A[:, i] @ Q[:, j]) * Q[:, j]  # get each u vector

        Q[:, i] = u[:, i] / np.linalg.norm(u[:, i])  # compute each e vector

    R = np.zeros((n, m))
    for i in range(n):
        for j in range(i, m):
            R[i, j] = A[:, j] @ Q[:, i]

    print("The Q Matrix is\n", Q)
    print("The R Matrix is\n", R)

a = np.array(eval(input()))
QR_Decomposition(a)

```

## Output
![image](https://github.com/user-attachments/assets/5f9a5809-fd76-4739-8165-a43c2365b561)


## Result
Thus the QR decomposition algorithm using the Gram-Schmidt process is written and verified the result.

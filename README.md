# Code-on-GOL
A = [[0,0,0,0,0,0],
         [0,0,0,1,0,0],
         [0,1,0,1,0,0],
         [0,0,1,1,0,0],
         [0,0,0,0,0,0],
         [0,0,0,0,0,0]]
def iterate(A):
    shape = len(A), len(A[0])
    N  = [[0,]*(shape[0]+2)  for i in range(shape[1]+2)]
    # Compute number of neighbours for each cell
    for x in range(1,shape[0]-1):
        for y in range(1,shape[1]-1):
            N[x][y] = A[x-1][y-1]+A[x][y-1]+A[x+1][y-1] \
                    + A[x-1][y]            +A[x+1][y]   \
                    + A[x-1][y+1]+A[x][y+1]+A[x+1][y+1]
    # Update cells
    for x in range(1,shape[0]-1):
        for y in range(1,shape[1]-1):
            if A[x][y] == 0 and N[x][y] == 3:
                A[x][y] = 1
            elif A[x][y] == 1 and not N[x][y] in [2,3]:
                A[x][y] = 0
    return A
for i in range(4): iterate(A)
print (A)

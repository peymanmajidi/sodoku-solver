<img style="float: right;width:200px" src="logo">

# Sodoku / سودوکو
### What is Sodoko?
Sudoku (数独, sūdoku) originally called Number Place) is a logic-based,combinatorialnumber-placement puzzle. In classic sudoku, the objective is to fill a 9×9 grid with digits so that each column   

### Sodoko Solver
We Wanna solve sodoko by python in an recursive way
So far so good. if you are intersted I am *Peyman Majidi* and this is my website: http://peymanmajidi.ir/   
Let's go



## Define Sodoko grid


```python
grid = [[5,3,0,0,7,0,0,0,0],
    [6,0,0,1,9,5,0,0,0],
    [0,9,8,0,0,0,0,6,0],
    [8,0,0,0,6,0,0,0,3],
    [4,0,0,0,0,0,0,0,1],
    [7,0,0,0,0,0,0,0,0],
    [0,6,0,0,0,0,2,8,0],
    [0,0,0,4,1,9,0,0,0],      
    [0,0,0,0,8,0,0,0,0]]       
```

## Let's print it


```python
print(grid)
```


```python
import numpy as np
print(np.matrix(grid))
```

## Lets make it pretty as sodoko is


```python
def prettify():
    print("Output: ")
    global grid
    j = 0
    for row in grid:
        i = 0
        j+=1
        for item in row:
            i+=1
            print(f" {item} ", end='')
            if i % 3 == 0 and i <9:
                print (" | ", end='')
        print()
        if j % 3 ==0 and j <9:    
            print('-'*33)

prettify()
```

## We need to solve it
Lets solve iven sodoko in a recursive way, fun part is here :)


```python
def possible(y,x,n):
    global grid
    for i in range(9):
        if grid[y][i] == n:
            return False
    for i in range(9):
        if grid[i][x] == n:
            return False
    x0 = (x//3)*3
    y0 = (y//3)*3
    
    for i in range(3):
        for j in range(3):
            if grid[y0+i][x0+j] == n:
                return False
    return True
```


```python
possible(0,2,1)
```


```python
def solve():
    global grid
    for y in range(9):
        for x in range(9):
            if grid[y][x] == 0:
                for n in range(1,10):
                    if possible(y,x,n):
                        grid[y][x] = n
                        solve()
                        grid[y][x] = 0
                return
    prettify()
    input("More?")
```


```python
solve()
```

## TODO
- [x] Meaningful comments
- [ ] Via OpenCV: Capture sokoko board and extract numbers
- [ ] Via Qt: Graphical User Interface

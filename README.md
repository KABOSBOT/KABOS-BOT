box , boxes = [1,2,3,4,5,6,7,8,9],  [ [0,0,0], [0,0,0], [0,0,0] ]
win = [ [1,2,3], [4,5,6], [7,8,9], [1,4,7], [2,5,8], [3,6,9], [1,5,9], [3,5,7] ]
O , X = [], []
BOX = 2	

def clear():
    import os ; os.system('cls' if os.name == 'nt' else 'clear')

def NumberToBox(n):
    if n <= 3 : return {'x': n-1, 'y': 0}
    if n <= 6 : return {'x': n-4, 'y': 1}
    if n <= 9 : return {'x': n-7, 'y': 2}

def drw():
    for i in box :
        if boxes[NumberToBox(i)['y']][NumberToBox(i)['x']] == 0 : print( i , end="|")
        if boxes[NumberToBox(i)['y']][NumberToBox(i)['x']] == 1 : print("X", end="|")
        if boxes[NumberToBox(i)['y']][NumberToBox(i)['x']] == 2 : print("O", end="|")
        if i in (3,6,9) : print()

def Tarn(Player):
    global BOX, O, X
    drw()
    if Player == 'O' : BOX = 2
    if Player == 'X' : BOX = 1
    CH = int(input(f'\nPlayer {Player}  Choose Anything 1-9 : '))
    if CH not in box : print('\nOnly Between 1-9 [{Player} Try again ]') ; Tarn(Player)  ; return False
    if CH in O or CH in X : print('\n You Cant Play Here [{Player} Try again ]') ; Tarn(Player) ; return False
    boxes[NumberToBox(CH)['y']][NumberToBox(CH)['x']] = BOX
    if Player == 'O' : O.append(CH)
    if Player == 'X' : X.append(CH)
    
def WinOrWhat(move):
    _WIN = []
    for _b in win : 

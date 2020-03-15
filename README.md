# pythonlearn
#silnia rekurencyjna

def silnia(n):
    if n>1:
        return n*silnia(n-1)
    else:
        return 1

a= float(input('podaj liczbe do obliczenia silni'))

print('silnia wynosi :',silnia(a))

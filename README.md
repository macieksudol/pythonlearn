# pythonlearn
#funkcja generująca ciąg fibonacciego

def fibbo(n):
    a = 0
    b = 1
    for x in range(1,n+1):
        print(b)
        b=a+b
        a=b-a

y= int(input('podaj liczbe wyrazów ciągu fibbonaciego  '))
fibbo(y)

# pythonlearn
#prosta funkcja kwadratowa bez zespolonych
tab=[]
z=0

print('wpisz parametry równania kwadratowego a*x^2 + b*x + c')
a= float(input())
b= float(input())
c= float(input())

if b*b-4*a*c>0:
    print('delta dodatnia - 2 pierwiastki')
    x1 = float((-b - m.sqrt(b * b - 4 * a * c)) / (2*a))
    x2 = float((-b + m.sqrt(b * b - 4 * a * c)) / (2*a))
    print('x1 = ',x1,' x2 = ',x2)

elif b * b - 4 * a * c < 0:
    print('delta ujemna - pierwiastki zespolone')
else:
    print('delta równa zero - jeden pierwiastek')
    x=float(-b/(2*a))
    print('x = ',x)

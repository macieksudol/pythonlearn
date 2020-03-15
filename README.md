# pythonlearn
#prosta tablica

#proste zapisywanie wartosci i wypisywanie tablicy(2 sposoby)
tab=[]
for a in range(1,11):
    print('give me number:')
    tab.append(input())

print(tab)

#or better version:

for a in range(1,11,1):
    print(tab[a-1])
    
#end to  start:
for a in range(1,11,1):
    print(tab[10-a])

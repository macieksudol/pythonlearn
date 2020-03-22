# pythonlearn
#laboratorium 1 - dalmierz ultradźwiękowy
import re
import string
import matplotlib.pyplot as plt
import statistics as stat
import math as m
odczytVL53L1X=[]  # dane z czujnika VL53L1X-LASEROWY
odczytHCSR04=[]   # dane z czujnika HC-SR04-ULTRADZWIEKOWY
temp=[]           #temperatura
realdist=[]       #rzeczywista odległosc zmierzona
imptime=[]        #czas impulsu
b=0
c=0
d=0
e=0
#ODCZYTANIE 1 CZESCI POMIARÓW
with open("dalmierz_pomiar_2.txt","r") as file:
    line = file.readlines()
    a = 10
    for y in range (1,10):#czytanie od 3ciej linijki!!

        txt1=line[a].split()
        a=a-1
        realdist.append(int(txt1[0]))
        imptime.append(float(txt1[1]))
        odczytVL53L1X.append(int(txt1[2]))
        odczytHCSR04.append(int(txt1[3]))
        temp.append(int(txt1[4]))
#ODCZYTANIE 2 CZĘSCI POMIARÓW:
with open("dalmierz_pomiar_1.txt","r") as file2:
    line2 = file2.readlines()
    a = 2
    for y in range(1, 21):  # czytanie od 3ciej linijki!!

        txt2 = line2[a].split()
        a = a + 1
        realdist.append(int(txt2[0]))
        imptime.append(float(txt2[1]))
        odczytVL53L1X.append(int(txt2[2]))
        odczytHCSR04.append(int(txt2[3]))
        temp.append(int(txt2[4]))

##poniżej wyświetlenie tabeli zapisanej wewnątrz zmiennych:
    print("wyswietlenie zapisanych list:")
    print("odl[mm] | czas[ms] | HC-SR04[mm] | VL53L1X[mm] | temp")
    for x in range(0,29):
        print(realdist[x],"        ",imptime[x],"       ",odczytVL53L1X[x],"       ",odczytHCSR04[x],"         ",temp[x])

#3.a)obliczanie czułosci=wsp kierunk. prostej regresji, wraz z niepewnością
    for x in range(0,29):
        b=b+(odczytHCSR04[x]-stat.mean(odczytHCSR04))*((imptime[x])-stat.mean(imptime))
        c=c+(odczytHCSR04[x]-stat.mean(odczytHCSR04))*(odczytHCSR04[x]-stat.mean(odczytHCSR04))


    a=b/c
    print("czułosć wynosi : ",a)

#obliczanie niepewności
    for x in range (0,29):
        d=d+(odczytHCSR04[x]*a - imptime[x])*(odczytHCSR04[x]*a - imptime[x])
        e=e+(odczytHCSR04[x]*odczytHCSR04[x])
    s=m.sqrt(d/(e*28))
print("niepewność wynosi: ",s)
#3.b)obliczanie zakresu,rozdzielczości, obszaru martwego
#3.c)obliczanie dokładności,przesunięcia
#Wykres wraz z dopasowaniem i parametrami dopasowania (modelu)
# + punkty 4,5,6,7,8

# 2.WYKRES zależności czasu trwania impulsu od położenia obiektu DLA DALMIERZA ULTRAWDZWIĘKOWEGO:
plt.plot(imptime, odczytHCSR04, color='r')
plt.grid(linestyle='-', linewidth=1)
plt.xlabel('czas trwania impulsu dla HC-SR04[ms]')
plt.ylabel('położenie obiektu [mm]')
plt.show()

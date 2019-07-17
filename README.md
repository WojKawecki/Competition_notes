#! python3
##This program will calculate all scores for each player
import pprint
from tkinter import *

print('---------------------------------------------------------')
print("Tura I")
players = []
while True:
    names = input('\nWprowadź dane zawodnika lub wklej listę zawodników:')
    if names == '':
        break
    players.append(names)
print('Zawodnicy : {0}'.format(players))

print('---------------------------------------------------------')

jury = ["Sędzia 1: ", "Sędzia 2: ", "Sędzia 3: ", "Sędzia 4: ", "Sędzia 5: "]

wszyscy_zawodnicy = {}
k = []
i = 0
for i in range((len(players))):
    print("Noty dla : " + players[i])
    print("(wprowadź noty od sędziów)")
    try:
        while True:
            A = input(jury[0])
            if A.isalpha() or A == "":
                print("Wprowadź cyfrę!")
                continue
            else:
                x = str(A)
                A = x.replace(",", ".")
                break

        while True:
            B = input(jury[1])
            if B.isalpha() or B == "":
                print("Wprowadź cyfrę!")
                continue
            else:
                x = str(B)
                B = x.replace(",", ".")
                break

        while True:
            C = input(jury[2])
            if C.isalpha() or C == "":
                print("Wprowadź cyfrę!")
                continue
            else:
                x = str(C)
                C = x.replace(",", ".")
                break

        while True:
            D = input(jury[3])
            if D.isalpha() or D == "":
                print("Wprowadź cyfrę!")
                continue
            else:
                x = str(D)
                D = x.replace(",", ".")
                break

        while True:
            E = input(jury[4])
            if E.isalpha() or E == "":
                print("Wprowadź cyfrę!")
                continue
            else:
                x = str(E)
                E = x.replace(",", ".")
                break

        oceny = {'Sędzia 1 ': float(A), 'Sędzia 2 ': float(B), 'Sędzia 3 ': float(C),
                    'Sędzia 4 ': float(D), 'Sędzia 5 ': float(E)}

        p = list(oceny.values())
        wszyscy_zawodnicy.setdefault(players[i], oceny)
        i += 1
    except ValueError:
        print("Wprowadź cyfry!")
        continue
    k.append(p)
pprint.pprint(wszyscy_zawodnicy)

root = Tk()
the_label = Label(root, text=str(zawodnicy_series))
the_label.pack()

print('---------------------------------------------------------')
## następuje zliczenie punktów wszystkich zawodników

z = 0
for i in range(len(players)):
    s = str(str(sum(k[z])) + " pkt.")
    d = str(players[z] + " otrzymał/a ")
    print(d.ljust(30) + s.rjust(20))
    z += 1

print('---------------------------------------------------------')


input("Close the window to finish...")
root.mainloop()


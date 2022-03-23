# juri lang
# Liste aller Keywords

* if
* return
* repeat
* init
* fun
```juri
fun add l r
	return l+r
# funktionsdefinition mit namen add und 2 parametern l und r

```
* operator
```juri
operator *- l r
	return (l*r)-69
# definition eines neuen operators *- 

```
* as
* iterate
* break
* import
```juri
import test/testme.jri

-> derzeit nur ein import pro Datei, importiert parst und interpretiert den Inhalt der anderen Datei
* siehe importfun
```
### standard Bibliothek
* rand()
> rand(start=optional(float),end=float) // end ist exklusiv \
> wenn rand() nur einen Parameter erhält wird der start der random range automatisch auf 0 gesetzt
```juri
n = rand(1 10)
# n evaluiert zu einer zufälligen Zahl zwischen 1 und 10
i = rand(10)
# i evaluiert zu einer zufälligen Zahl zwischen 0 und 10
```
* print()
> nimmt eine liste von floats und printet sie ohne newline am Ende
* printn()
> nimmt eine liste von floats und printet sie mit newline am Ende
* printc()
> nimmt eine liste von floats und wandelt den wert über die Ascii Tabelle in einen char um mit newline am Ende

printc(72 101 108 108 111 32 87 111 114 108 100 33 ) -> printet **Hello World!** in die Konsole


### Operator-Zeichen:
```juri
+-*/><.=!%
```

### Trennzeichen:
```juri
()[]
```

### Kommentare:
Kommentar derzeit nur am Anfang der Zeile
```juri
i = 0
print(i + 420)
# Ich bin ein Kommentar
print(69)
```


# Arrays
Arrays haben eine **feste** Größe
**Arraynamen** beginnen mit einem ```:```.
Arrays werden mit folgender Sytax deklariert:
```juri
:myList = [1 2 3 4]          Erstellt die Liste mit den gegebenen Elementen

:anotherList = [2 to 345]    Erstellt eine Liste mit den Zahlen von 2 bis 345

:longList = init 1000 0      Erstellt eine Liste mit 1000 nullen

:evenNums = init 50 as i
    i * 2                    Erstellt eine Liste mit den Zahlen 0,2,4,8... 
```

Einzelne Arrayelemente können per **Index** referenziert und geändert werden.  Das Erste Element hat den Index 0.
```juri
print(0:myList)     gibt 1 aus
print(-1:myList)    gibt 4 aus
2:myList = 99       weist dem Element an Index 2 den wert 99 zu: [1 2 99 4]
```

Um die **Länge** eines Arrays herrauszufinden fragen Es einfach.
```juri
?:myList            evaluiert zu 4
```

Um über ein Array zu **iterieren** stellt juri die ```iterate``` Anweisung zur Verfügung.
```juri
iterate :myList as x
    print(x)
```

Egal ob iterate oder in einer if schleife können wir mit dem keyword ```break``` den schleifendurchlauf unterbrechen
```juri
i = 0
if i < 10 repeat
	if i == 5
		printn(i)
		break
	i=i+1
# printet 5 in die konsole
```


Hier noch ein Beispiel wie man mit einer Klassischen If-Schleife über ein Array iteriert.
```juri
i = 0
if i < ?:myList repeat
    print(i:myList)
    i = i+1
```
### Geplante  aber noch nicht implementierte Features

**Funktionsparameter** können als Array festgelegt werden
```juri
fun snipList :list start end
    i = start
    if i <= end repeat
        print(i:list)
        i = i+1
```
**Array Pointer**
```juri
:list = [1 4]
fun add l r
	l <- :list          
	return 0:l + 1:l
	
# l wird hierbei zum original array. Veränderungen an dem Array
# innerhalb des Funktionsscopes verändern das ursprüngliche Array

:list = [1 to 10]

fun keeper modulo
	l <- :list
	if i < ?:l repeat
		if (i:l%modulo) == 1
			i:l = 0 
	i=i+1
	
keeper(2)

# evaluiert die ursprungliste zu -> :list = [0 2 0 4 0 6 0 8 0 10]
# alle ungraden Zahlen innerhalb der liste werden mit null ersetzt
	


```

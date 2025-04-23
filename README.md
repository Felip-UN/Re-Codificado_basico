# Retos primarios para la retoma
- Crear una función que realice operaciones básicas (suma, resta, multiplicación, división) entre dos números, según la elección del usuario, la forma de entrada de la función será los dos operandos y el caracter usado para la operación. entrada: (1,2,"+"), salida (3).

- Realice una función que permita validar si una palabra es un palíndromo. Condición: No se vale hacer slicing para invertir la palabra y verificar que sea igual a la original.

- Escribir una función que reciba una lista de números y devuelva solo aquellos que son primos. La función debe recibir una lista de enteros y retornar solo aquellos que sean primos.

- Escribir una función que reciba una lista de números enteros y retorne la mayor suma entre dos elementos consecutivos.

- Escribir una función que reciba una lista de string y retorne unicamente aquellos elementos que tengan los mismos caracteres. e.g. entrada: ["amor", "roma", "perro"], salida ["amor", "roma"]

## Operacion compresa
```python
#Definir un diccionario para guardar cada operacion como semifunciones
ops = {'+': lambda x, y: x + y, '-': lambda x, y: x - y, '*': lambda x, y: x * y, '/': lambda x, y: x / y}

nums1 , nums2, oper=input("Ingresa 2 numeros separados por un espacio y un operador (+ - * /): ").split()
#Convertir los valores que son numeros cadena a enteros:
nums1 = int(nums1)
nums2 = int(nums2)

resultado = ops[oper](int(nums1), int(nums2)) #Encontrar el simbolo dentro del diccionario y despues asignar valores para ejecutar la operacion

print("Resultado:", resultado)
```
EL titulo se llama operacion compresa debido a que quice que se redujera lo mas posible las lineas de codigo, en la linea de entradas use un metodo comodo a mi parecer mediante el cual puedo asignar varias variables en una sola linea de codigo mediante el uso de un split
y posteriormente transformando los valores cadena en valores enteros, ya a la hora de querer "comprimir la operacion" dije: "Como hago para solo ponerlo ahí?" pense en hacer un monton de condicionales lo cual hubiera servido pero no lo hubiera dejado compreso, posteriormente recorde las lambda pero luego era listo estarian compresas, ahora... como hago que cada caso se asigne a la hora de digitarlo que lo busque en una lista? AH! que tal un diccionario?! la llave seria el operador (cadena) y la clave puede ser cualquier cosa verdad? incluso operaciones? al parecer si y listo asignar valores a posteriori y tenemos programa completo

**Ejemplo de entrada:** 4 6 *
**salida dada:** Resultado: 24

## Palíndromo
```python
#Palindromos
comparador=[]
plab=list(input("Ingresa tu palabra!: "))#la convierto en lista
comparador.append(plab.copy()) #guardo una copia de esta lista en el compardor

plab.reverse() #la invierto con un reverse que modifica la original
comparador.append(plab.copy()) #guardo la otra compia

print(comparador) #Visualicemos las salidas

if comparador[0]==comparador[1]: #Se comparan las copias
  print("Tu palabra es un palindromo :D")
else:
  print("Tu palabra no es un palindromo :(")
```
Lo primero que pense fue lo siguiente: una cadena es una lista inmutable, convirtamosla en algo mutable :) asi desde el inicio lo que se crea es una lista estuve viendo maneras sencillas de revertirla pero lo unico que me salia era, usa reverse() o un bucle for pero uno el bucle no lo entendia, asi que aunque podria funcionar pero "no como queria" y el reverse no servia al ser una asignacion de variables y daba None :c, pero sucede que si no se asignaba sino que se definia de por si, si me daba una lista invertida asi que use eso pero dije: hmmm como los comparo? guardemoslo en una lista y comparamos no? listo... como los guardo para que no sean el mismo? porque el reverse mutaba la lista y si esta la guardaba asi como si nada se modificaba asi fuera que la linea de codigo se ejecutara antes, pero que hay de una copia eh? y listo guardas la copia y despues otra copia distinta y se comparan como si nada :)

**Ejemplo de entrada:** oso
**salida dada:** Tu palabra es un palindromo :D

**Ejemplo de entrada:** gato
**salida dada:** Tu palabra no es un palindromo :(

## Mayor suma consecutiva
```python
def mayor_suma_consecutiva(lista):
    # Verificamos si la lista tiene al menos dos elementos para sumar
    if len(lista) < 2:
        return None  # Si la lista es muy pequeña para tener pares consecutivos, asignamos None como salida

    max_suma = lista[0] + lista[1]  # Iniciamos con la primera suma

    # Iterar a partir del segundo elemento
    for i in range(1, len(lista)-1):
        consecutiva = lista[i] + lista[i + 1]  # Suma de los elementos consecutivos
        max_suma = max(max_suma, consecutiva)  # El valor mas alto se tomara como la mayor suma
    return max_suma
if __name__=="__main__":
  elementos=list(map(int, input("Ingresa valores separados por un espacio:" ).split())) #map+list
  print(elementos)
  resultado = mayor_suma_consecutiva(elementos)
  if resultado == None:
    print("No hay sufientes elementos para sumar")
  else:
    print("La mayor suma entre consecutivos es:", resultado)
```
Para este fue gran cosita, sumar cada valor en parejas y comparar cual seria la mayor, sabia que usaria max pero no sabia donde y aun mas importante una iteracion, osea el for este si fue "sencillo" indice 1 + indice siguiente eso si sin salirse del rango de la lista con lo que asi para agregar una toleracia a errores al programa agregamos una condicion en la que si no hay suficientes valores para sumar sale None y esto se utiliza mas tarde para dar una salida condicional, volviendo a la iteracion, posterior a realizar la suma comparamos este valor nuevo con el nuevo obtenido y se tomara el mayor de estos y se guardara como nuevo valor maximo.

### split() + map() + list() 
este es un metodo que me gusta usar bastante, me hace sentir "profesional" pero es una cosa bien simple, split separara la cadena principal de input en valores cadena, map convertira esos valores cadenas en valores enteros ya que usa int en este caso, y list convierte ese map de iterador logico a una lista real usable
 
```python
elementos = [int(x) for x in input("Ingresa valores separados por un espacio:").split()]
```
## Combinaciones encadenadas iguales

Stand By, Work in progress

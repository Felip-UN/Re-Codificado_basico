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

## Palíndromo

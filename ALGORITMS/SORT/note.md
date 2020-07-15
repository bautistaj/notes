# Algoritmos de ordenamiento
Tanto en la computación como en matemáticas un algoritmo de ordenamiento es un algoritmo que pone los de una lista o un vector en una secuencia dada por una relación de orden.

## Bubble sort
Ordenamiento de burbuja que funciona revisando cada elemento de la lista que va ser ordenado con el siguiente intercambiandolos si están en un orden equivocado.

```python
def bubble_sort(A):
  size_array = len(A) # c0 = 1

  for index_i in range(size_array):# c1 = n
    swap = False # c2 = 1
    for index_j in range(0, size_array - index_i - 1): # c3 = n^2
      if A[index_j] > A[index_j + 1]: # c4 = 1
        A[index_j], A[index_j + 1] = A[index_j + 1], A[index_j] # c5 = 1
        swap = True # c6 = 1
    
    if not swap: # c7 = 1
      break

if __name__ == "__main__":
    array = [2,78]
    bubble_sort(array)

# T(n) = c0 + c1*n + c2 + c3*n + c4 + c5 + c6 + c7
# T(n) = c3*n^2 + c1*n + c0 + c2 +  + c4 + c5 + c6 + c7
# T(n) = n^2 + n
# T(n) = n^2

# Time complexity = O(n^2)
# Space complexity = O(1)
```

## Selection Sort

Algoritmo que ordena una matriz al encontrar repetidamente el elemnto mínimo (Considerando el orden acsendente) de la parte no ordenada y lo pone al principio.

El algortimo mantiene 2 sub arrays.
* El array ordenado
* El array restante que no esta desordenado.

En cada iteración el elemento mínimo del arreglo desordenado se toma y se coloca el el sub array ordenado.

Considere los siguientes pasos:

Encontrar el elemnto mínimo y colocarlo al inicio.
```
[64 25 12 22 11]
[11 25 12 22 64]
[11 12 22 25 64]
```


```python
def selection_sort(A):
  size_array = len(A) # c0 = 1
  index_i = 0 # c1 = 1

  for index_i in range(size_array): # c2 = n
    low_index = index_i # c3 = 1
    
    for index_j in range(index_i + 1, size_array): # c4 = n^2
      if A[index_j] < A[low_index]: # c5 = 1
        low_index = index_j # c6 = 1
    
    A[index_i], A[low_index] = A[low_index], A[index_i] # c7 = 1

if __name__ == "__main__":
  A = [200,10000,12,35,7,8,9,2,4]
  selection_sort(A)

# T(n) = c0 + c1 + c2*n + c3 + c4*n^2 + c5 + c6 + c7
# T(n) = c4*n^2 + c2*n + c0 + c1 + c3 + c5 + c6 + c7
# T(n) = n^2 + n
# T(n) = n^2

# Time complexity = O(n^2)
# Space complexity = O(1)
```
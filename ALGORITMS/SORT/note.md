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
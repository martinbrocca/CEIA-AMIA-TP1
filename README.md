# CEIA-AMIA-TP1 - LDA/QDA y optimización matemática de modelos

Grupo de trabajo 1

**Miembros:**
- Martin Brocca <martinbrocca@gmail.com>
- Emiliano Iparraguirre <emiliano.iparraguirre22@gmail.com>
- Natalia Espector <nataliaespector@gmail.com>
- Agustin Lopez Fredes <agustin.lopezfredes@gmail.com>
- Fernando Martinez <fgmartinez1989@gmail.com>

---


Respuestas a las preguntas en el código:

### Q3: para que sirve bincount?
  - Bincount in una función de la librería NumPy que se usa para contar las ocurrencias de enteros mayores que 0 dentro de un arreglo. La función devuelve un arreglo en donde el índice representa al entero y el valor en ese índice representa la cantidad de ocurrencias de ese entero en el arreglo. En el algoritmo de QDA,  se emplea para calcular la frecuencia relativa de la clase $j$ en la muestra $\pi_j$
  
### Q4: por que el _fit_params va al final? no se puede mover a, por ejemplo, antes de la priori?
  - No puede moverse antes, debido a que  _fit_params depende de la priori, y la priori se calcula antes

### Q5: por que hace falta el flatten y no se puede directamente `X[:,y==idx]`?
  - Porque y es un vector columna y no se puede comparar con un vector fila. 
    Flatten en este caso lo convierte en arreglo de 1D y entonces si se puede hacer la comparacion con idx.
    
    En la ejecución de código sobre el dataset de vinos, se obseva que:
    
    X.shape=  (13, 124)

    y.shape=  (1, 124)
    
    y.flatten [0 1 0 1 1 0 0 1 2 2 1 1 0 0 1 2 2 2 1 1 2 1 1 1 0 2 1 1 0 0 1 1 1 0 1 0 1
               1 2 0 0 2 2 1 2 1 2 1 1 0 0 2 1 0 2 2 2 1 2 2 1 2 0 2 1 1 1 1 0 0 1 2 1 1
               0 0 2 1 1 2 0 0 1 0 0 1 2 0 1 0 0 1 0 1 0 1 0 0 0 1 2 1 2 0 2 1 1 2 2 1 0
               1 0 1 2 0 2 1 0 1 0 1 2 0]

    Por lo tanto al usar `y.flatten`, realiza efectivamente la selección de columnas de $X$ en aquellos casos que `y.flatten()=idx`


### Q6: por que se usa bias=True en vez del default bias=False?
  - Porque bias=False hace que la matriz de covarianza sea insesgada.
    De acuerdo con la documentación de NumPy, es el factor de normalización. bias=False significaría usar N-1 en la cantidad de observaciones. bias=True significaría usar N en la cantidad de observaciones.
    En el caso de la implementación de QDA, usar `bias=True` para calcular la matriz de covarianza resulta en usar el estimador de máxima verosimilitud, mientras que usar `bias=False` representa usar el estimador insesgado. 

### Q7: que hace axis=1? por que no axis=0?
  - El parámetro `axis=1` indica que el promedio se debe calcular por columnas y no por filas. 

---

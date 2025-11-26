# EJERCICIO GUIADO "ÁRBOL BINARIO"
## Marisol Rincón Solís 
## 25 de Noviembre de 2025

### Desarrollamos un código que nos compartio el profesor el cual son 3 clases una llamada NodoArbol, Arbol Binario y PruebaArbol los cuales se presentan a continuación.

## Clase NodoArbol
``` java

package com.mycompany.unidad3.EjercicioGuiadoSwing;

/*
 * NodoArbol.java
 * Representa un nodo de un árbol binario.
 * Contiene un dato entero y referencias a los hijos izquierdo y derecho.
 * 
 * 25 de Noviembre de 2025 
 * @author Marisol Rincón Solís
 * @author 1224100827.mrs@gmail.com
 */
/**
 * Clase que representa un nodo de un árbol binario.
 * Cada nodo contiene un valor entero y referencias a sus hijos izquierdo y derecho.
 */
public class NodoArbol {

    private int dato;  // Valor almacenado en el nodo
    NodoArbol hijoIzquierdo;  // Referencia al hijo izquierdo
    NodoArbol hijoDerecho;    // Referencia al hijo derecho

    /**
     * Constructor que inicializa el nodo con un valor específico.
     * @param valor Valor entero a almacenar en el nodo.
     */
    public NodoArbol(int valor) {
        this.dato = valor;
        this.hijoIzquierdo = null;
        this.hijoDerecho = null;
    }

    // Métodos getters y setters
    public int getDato() {
        return dato;
    }

    public void setDato(int nuevoDato) {
        this.dato = nuevoDato;
    }

    public NodoArbol getHijoIzquierdo() {
        return hijoIzquierdo;
    }

    public void setHijoIzquierdo(NodoArbol hijoIzquierdo) {
        this.hijoIzquierdo = hijoIzquierdo;
    }

    public NodoArbol getHijoDerecho() {
        return hijoDerecho;
    }

    public void setHijoDerecho(NodoArbol hijoDerecho) {
        this.hijoDerecho = hijoDerecho;
    }
}
```
## Clase ArbolBinario
```Java

package com.mycompany.unidad3.EjercicioGuiadoSwing;

/*
 * 
 * Implementa un árbol binario de búsqueda (BST) con operaciones de inserción y recorrido.
 * Permite insertar valores enteros y recorrer el árbol en orden (inorden).
 * 
 * 25 de Noviembre de 2025
 * @autor Marisol Rincón Solís
 * @author 1224100827.mrs@gmail.com
 */
public class ArbolBinario {
    
    private NodoArbol raiz; // Raíz del árbol

    /**
     * Constructor que inicializa un árbol vacío.
     */
    public ArbolBinario() {
        this.raiz = null;
    }
    
    // Getters y Setters
    public NodoArbol getRaiz() {
        return raiz;
    }

    public void setRaiz(NodoArbol raiz) {
        this.raiz = raiz;
    }
    
    /**
     * Aquí se mostraran los métodos de inserción 
     * (público y privado) y el recorrido.
     */

    /**
     * Método Público de Inserción: Punto de entrada para el usuario.
     * Inicia la recursión desde la raíz.
     */
    public void insertar(int valor) {
        this.raiz = insertarRecursivo(this.raiz, valor);
    }

    /**
     * Método Privado y Recursivo de Inserción.
     * @param actual El nodo que se está examinando en la recursión.
     * @param valor El valor a insertar.
     * @return El nodo modificado o el nuevo nodo creado.
     */
    private NodoArbol insertarRecursivo(NodoArbol actual, int valor) {
        // Caso Base: Si el nodo actual es null, encontramos la posición, creamos el nuevo nodo y lo retornamos.
        if (actual == null) {
            return new NodoArbol(valor);
        }

        if (valor < actual.getDato()) { // Usamos getDato() por el encapsulamiento estricto
            actual.hijoIzquierdo = insertarRecursivo(actual.hijoIzquierdo, valor);
        } else if (valor > actual.getDato()) {
            actual.hijoDerecho = insertarRecursivo(actual.hijoDerecho, valor);
        }
        // Si valor == actual.getDato(), se ignora (no permite duplicados).
        return actual; // Retorna el nodo actual sin cambios si no fue caso base.
    }

    /**
     * Método Público de Recorrido Inorden.
     * Inicia la recursión desde la raíz y muestra el resultado.
     */
    public void recorrerInorden() {
        System.out.print("Recorrido Inorden: ");
        recorrerInordenRecursivo(this.raiz);
        System.out.println();
    }

    /**
     * Método Privado y Recursivo de Recorrido Inorden (Izquierda -> Raíz -> Derecha).
     */
    private void recorrerInordenRecursivo(NodoArbol nodo) {
        if (nodo != null) {
            recorrerInordenRecursivo(nodo.hijoIzquierdo); // 1. Izquierda
            System.out.print(nodo.getDato() + " ");        // 2. Raíz (Imprimir)
            recorrerInordenRecursivo(nodo.hijoDerecho);   // 3. Derecha
        }
    }
}
```
## Clase PruebaArbol
```java

package com.mycompany.unidad3.EjercicioGuiadoSwing;
/*
 * PruebaArbol.java
 * Clase de prueba para demostrar la funcionalidad del árbol binario.
 * Inserta varios valores y realiza un recorrido inorden.
 * 
 * 25 de Noviembre de 2025
 * @author Marisol Rincón Solís
 * @author 1224100827.mrs@gmail.com
 */
public class PruebaArbol {
    public static void main(String[] args) {
 // 1. Crear una instancia de la clase gestora del árbol
 ArbolBinario arbol = new ArbolBinario();

 System.out.println("Insertando valores: 50, 30, 70, 20, 40");
 // 2. Insertar valores usando el método público
 arbol.insertar(50); // Raíz
 arbol.insertar(30); // Izquierda de 50
 arbol.insertar(70); // Derecha de 50
 arbol.insertar(20); // Izquierda de 30
 arbol.insertar(40); // Derecha de 30

 // 3. Ejecutar el recorrido para verificar el orden
 // Resultado esperado (ordenado): 20 30 40 50 70
 arbol.recorrerInorden();
 }
}
```
# EVIDENCIA DE LA FUNCIONALIDAD DEL CÓDIGO

| Prueba | Evidencia |
|--------|-----------|
| Prueba 1 | <img width="756" height="506" alt="Evidencia Prueba 1" src="https://github.com/user-attachments/assets/a370bf6c-a680-4b23-9ad6-2a31510931d3" /> |
| Prueba 2 | <img width="756" height="547" alt="Evidencia Prueba 2" src="https://github.com/user-attachments/assets/ba2cdf4e-9ad5-44ae-b9f7-df0c86a883f6" /> |




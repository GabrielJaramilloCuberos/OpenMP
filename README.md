# 🧵 Introducción a OpenMP: "Hello World" Multihilo

## 👤 Autor
**Gabriel Jaramillo Cuberos**

## 📅 Fecha
**13 de mayo, 2025**

## 📚 Materia
**Sistemas Operativos**

## 🧠 Tema
**Programación paralela - Introducción a OpenMP**

---

## 📝 Descripción

Este proyecto es un ejemplo básico de uso de OpenMP (Open Multi-Processing), una API que permite a los programas C/C++ y Fortran aprovechar múltiples núcleos del procesador mediante programación paralela con hilos (`threads`).

El programa crea una región paralela y ejecuta un simple mensaje de saludo desde cada hilo activo, utilizando la cantidad de núcleos disponibles en la máquina.

---

## 💻 Código principal

```c
#include <stdio.h>
#include <omp.h>
#include <stdlib.h>

int main(int argc, char *argv[]){
  printf("OpenMP ejecutando con %d hilos\n", omp_get_max_threads());
  
  #pragma omp parallel
  {
    printf("Hello World desde el thread %d\n", omp_get_thread_num());
  }
  return 0;
}
```

---

## ⚙️ ¿Cómo compilarlo?

Este programa necesita un compilador compatible con OpenMP. En sistemas basados en Unix (como Linux o macOS con `gcc`), puedes compilarlo con:

```bash
gcc -fopenmp programa.c -o programa
```

> Asegúrate de tener `gcc` instalado y compatible con OpenMP (`gcc --version`).

---

## 🚀 ¿Cómo ejecutarlo?

Una vez compilado, puedes ejecutarlo con:

```bash
./programa
```

Y verás una salida similar a:

```
OpenMP ejecutando con 4 hilos
Hello World desde el thread 0
Hello World desde el thread 1
Hello World desde el thread 2
Hello World desde el thread 3
```

> La cantidad de hilos puede variar dependiendo de tu procesador y la configuración de OpenMP.

---

## 🧠 ¿Qué hace cada función?

| Función | Descripción |
|--------|-------------|
| `omp_get_max_threads()` | Retorna el número máximo de hilos que OpenMP usará si no se especifica otro número. |
| `omp_get_thread_num()` | Retorna el ID del hilo actual dentro de la región paralela. |
| `#pragma omp parallel` | Indica el inicio de una región de código que debe ejecutarse en paralelo por múltiples hilos. |

---

## 🛠️ Personalización

Puedes definir el número de hilos manualmente con:

```c
omp_set_num_threads(8); // Por ejemplo, 8 hilos
```

O usar la variable de entorno:

```bash
export OMP_NUM_THREADS=8
```

---

## 📌 Observaciones

- Este programa es ideal como primer contacto con la programación paralela.
- La salida puede no estar ordenada, ya que los hilos se ejecutan simultáneamente y compiten por imprimir en pantalla.
- Para sincronizar o coordinar hilos, se puede usar directivas adicionales como `#pragma omp barrier`, `#pragma omp critical`, etc.

---

## 🏁 Conclusión

Este ejercicio demuestra cómo, con muy poco código, es posible aprovechar múltiples núcleos del procesador y ejecutar instrucciones en paralelo, algo fundamental en sistemas operativos modernos y programación de alto rendimiento.

# Creativityyyyyyyy
Repo del reto #8
## Gestor de Proyectos Personales con Generadores y Decoradores
### Descripción:
Se va a implementar un sistema de gestión de proyectos personales, ideal para estudiantes o profesionales que deseen dividir un gran proyecto en tareas pequeñas y evaluar su eficiencia.

### Funcionalidades:
Generador de Tareas:

Se implementa un generador que divida un proyecto grande en subtareas más manejables. Por ejemplo, para un proyecto de "Escribir un libro", las subtareas podrían ser: "Escribir introducción", "Escribir capítulo 1", etc.
El generador debe permitir iterar sobre las subtareas hasta que todas hayan sido completadas.
Decorador de Eficiencia:

Se crea un decorador que calcule el tiempo estimado que debería tomar cada tarea. Si se completa en menos tiempo, el decorador indicará que el trabajo fue eficiente, si no, mostrará que el trabajo fue más lento de lo esperado.

```python
import time

def medir_eficiencia(func):
    def wrapper(*args, **kwargs):
        tiempo_inicio = time.time()
        resultado = func(*args, **kwargs)
        tiempo_final = time.time()
        tiempo_tomado = tiempo_final - tiempo_inicio
        tiempo_estimado = 5  # Por ejemplo, tiempo estimado en segundos para completar una tarea
        if tiempo_tomado < tiempo_estimado:
            print(f"Tarea completada eficientemente en {tiempo_tomado} segundos")
        else:
            print(f"Tarea más lenta de lo esperado, {tiempo_tomado} segundos")
        return resultado
    return wrapper

@medir_eficiencia
def completar_tarea(tarea):
    print(f"Completando tarea: {tarea}")
    time.sleep(2)  # Simulación de tiempo de tarea
    return tarea

def generador_tareas(proyecto):
    for tarea in proyecto:
        yield tarea

# Simulación del reto
proyecto = ["Escribir introducción", "Revisar capítulo 1", "Diseñar portada"]
tareas = generador_tareas(proyecto)

for tarea in tareas:
    completar_tarea(tarea)
```
Generador de Tareas: Cada iteración producirá una tarea del proyecto hasta que todas se completen.
Decorador de Eficiencia: Evaluará si cada tarea se completó en el tiempo estimado o no.

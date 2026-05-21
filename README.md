# Laboratorio 7 — Simulación de Álbum Panini FIFA 2026

**Curso:** MM3014 Teoría de Probabilidades  
**Universidad:** Universidad del Valle de Guatemala  
**Autores:** Diego Andre Calderon Salazar (241263) · Pedro Julio Caso (241286)

---

## Descripción del proyecto

Este repositorio contiene dos notebooks de Jupyter que implementan una simulación de Monte Carlo del problema del coleccionista de estampas (*Coupon Collector Problem*), aplicado al álbum Panini del Mundial FIFA 2026.

| Archivo | Descripción |
|---|---|
| `lab7-ej1.ipynb` | **Etapa 1 — Álbum reducido (N = 100).** Familiarización con la simulación. Comparación con la fórmula teórica. |
| `lab7-ej2.ipynb` | **Etapa 2 — Álbum real FIFA 2026 (N = 980).** Estimación de sobres y costos esperados, probabilidad de éxito con presupuesto fijo y efecto del intercambio de estampas. |

---

## Requisitos del sistema

- Sistema operativo: Windows 10 / 11 (también compatible con macOS y Linux)
- Conexión a internet para la descarga inicial de herramientas

---

## Instrucciones de instalación

### Paso 1 — Instalar Python

Si no tiene Python instalado:

1. Abra su navegador y descargue el instalador desde:  
   `https://www.python.org/downloads/`  
   Se recomienda la versión **3.11** o superior.

2. Ejecute el instalador. **Importante:** marque la casilla  
   **"Add Python to PATH"** antes de hacer clic en *Install Now*.

3. Verifique la instalación abriendo **PowerShell** o **Símbolo del sistema** (`cmd`) y ejecutando:

   ```
   python --version
   ```

   Debe mostrar algo como `Python 3.11.x`.

---

### Paso 2 — Clonar o descargar el repositorio

**Opción A — Con Git:**

```
git clone <URL-del-repositorio>
cd Lab7-prob1
```

**Opción B — Sin Git:**

Descargue el archivo ZIP del repositorio desde GitHub, extráigalo y abra una terminal en la carpeta extraída.

---

### Paso 3 — Crear un entorno virtual (recomendado)

Ejecute los siguientes comandos en PowerShell o `cmd` dentro de la carpeta del proyecto:

```
python -m venv venv
venv\Scripts\activate
```

> Si PowerShell bloquea la activación, ejecute primero:  
> `Set-ExecutionPolicy -Scope CurrentUser RemoteSigned`

Sabrá que el entorno está activo cuando vea `(venv)` al inicio de la línea en la terminal.

---

### Paso 4 — Instalar las dependencias

Con el entorno virtual activo, ejecute:

```
pip install -r requirements.txt
```

Esto instalará automáticamente:

| Paquete | Versión mínima | Uso |
|---|---|---|
| `numpy` | 1.24 | Cálculo numérico y generación aleatoria |
| `matplotlib` | 3.7 | Visualización de resultados |
| `scipy` | 1.11 | Interpolación de curvas de probabilidad |
| `jupyter` | 1.0 | Entorno interactivo de notebooks |
| `ipykernel` | 6.25 | Kernel de Python para Jupyter |
| `notebook` | 7.0 | Interfaz web de Jupyter |

---

## Cómo ejecutar los notebooks

### Paso 5 — Iniciar Jupyter Notebook

Con el entorno virtual activo, ejecute:

```
jupyter notebook
```

Se abrirá automáticamente una pestaña en su navegador con el explorador de archivos de Jupyter.

---

### Paso 6 — Abrir y ejecutar un notebook

1. Haga clic en `lab7-ej1.ipynb` o `lab7-ej2.ipynb`.
2. En el menú superior seleccione **Kernel → Restart & Run All**.
3. Espere a que todas las celdas terminen de ejecutarse (las celdas muestran `[*]` mientras están en progreso y un número cuando finalizan).

> **Nota:** La simulación utiliza `R = 10,000` repeticiones con `semilla = 2026`. Los resultados son completamente reproducibles.

---

## Estructura del repositorio

```
Lab7-prob1/
├── lab7-ej1.ipynb      # Etapa 1: álbum reducido N=100
├── lab7-ej2.ipynb      # Etapa 2: álbum real N=980 (FIFA 2026)
├── requirements.txt    # Dependencias de Python
└── README.md           # Este archivo
```

---

## Resumen de resultados

### Etapa 1 (N = 100, S = 7)

| Métrica | Teórico | Simulado |
|---|---|---|
| E[sobres necesarios] | 74.11 | 72.25 |
| E[estampas repetidas] | 418.74 | 405.72 |

### Etapa 2 (N = 980, S = 7)

| Métrica | Valor |
|---|---|
| Sobres esperados (simulado) | 1,042.7 ± 177.8 |
| Costo esperado — individual | Q 9,905.61 |
| Costo esperado — mixta | Q 9,781.74 |
| Presupuesto para P(completar) = 90% | Q 12,144 |
| Reducción con intercambio al 50% | −80.3% de sobres |

---

## Solución de problemas comunes

**`python` no se reconoce como comando:**  
Reinstale Python marcando "Add Python to PATH" o use `py` en lugar de `python`.

**Error al activar el entorno virtual en PowerShell:**  
Ejecute `Set-ExecutionPolicy -Scope CurrentUser RemoteSigned` y luego reintente.

**El navegador no abre automáticamente con Jupyter:**  
Copie la URL que aparece en la terminal (del tipo `http://localhost:8888/...`) y péguela en su navegador.

**Las celdas tardan mucho:**  
La Etapa 2 realiza 10,000 simulaciones sobre un álbum de 980 estampas. El tiempo de ejecución típico es de 3 a 10 minutos dependiendo del hardware.

# DLCD
Depuración, limpieza y clasificación de datos

Módulo profesional 5109 del Curso de Especialización en Aprendizaje Automático: Gestión de Datos y Entrenamiento.
Curso académico 2026-2027.

> **Antes de empezar**, prepara tu entorno siguiendo la guía [INSTALACION.md](INSTALACION.md)
> y ejecuta el cuaderno [`00_comprobacion_entorno.ipynb`](00_comprobacion_entorno.ipynb).

## Estructura

```
DLCD/
├── INSTALACION.md                  Guía de instalación del entorno
├── 00_comprobacion_entorno.ipynb   Comprueba que todo funciona
├── pyproject.toml / uv.lock        Librerías del curso (versiones fijadas)
├── UD1/   Análisis exploratorio de datos: estructura, variables y calidad (RA1)
│   ├── Bloque_1_Analisis_exploratorio_de_datos/
│   ├── Bloque_2_AED/
│   └── Bloque_3_Calidad_de_datos/
├── UD2/   Verificación de datos mediante técnicas estadísticas (RA2)
│   ├── Bloque_1_Estadistica_Descriptiva/
│   ├── Bloque_2_Distribuciones_y_Normalidad/
│   ├── Bloque_3_Correlacion/
│   └── Bloque_4_Tests_de_Independencia/
├── Proyecto/                           Proyecto transversal (guiones por unidad)
├── Proyecto resuelto - ictus dataset/  Ejemplo de proyecto resuelto
└── mis_cuadernos/                      Tu carpeta personal (no se sube a GitHub)
```

## Uso diario

```powershell
git pull     # traer los materiales nuevos
uv sync      # actualizar las librerías si han cambiado
```

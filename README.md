# TP4 · Redes convolucionales en Skin Dataset

Clasificación de nueve clases de lesiones de piel del subconjunto ISIC provisto por la cátedra. El notebook incluye el análisis exploratorio, la comparación MLP–CNN, las variantes convolucionales, la prueba de augmentation y la evaluación final.

## Datos

Descargar el [ZIP de la versión original de la cátedra](https://github.com/cselmo/CNN-en-Skin-Dataset/archive/e6b86162899a4bd276ffce7cdc86b79454fb9e8c.zip). Extraer `data/Split_smol` junto al notebook con esta estructura:

```text
RESUELTO_CNN_Skin_ISIC.ipynb
requirements.txt
data/
└── Split_smol/
    ├── train/          # una subcarpeta por clase
    └── val/            # una subcarpeta por clase
```

El catálogo original contiene 878 imágenes. El notebook elimina duplicados por MD5 y vuelve a dividir el conjunto de forma estratificada. La carpeta `val/` de origen es parte del catálogo de entrada. El test se crea en el nuevo split.

## Reproducir la corrida

La corrida guardada usa Python 3.12.5 x64, Windows y PyTorch 2.14.0+cpu con dos hilos de cómputo. En el equipo de la corrida se completaron 65 ajustes y 1.355 épocas en alrededor de 69 minutos de reloj. `requirements.txt` fija las dependencias directas utilizadas. La verificación usó un kernel nuevo y dependencias ya instaladas.

Desde la carpeta del notebook, en PowerShell:

```powershell
py -3.12 -m venv .venv
.\.venv\Scripts\python.exe -m pip install torch==2.14.0 --index-url https://download.pytorch.org/whl/cpu
.\.venv\Scripts\python.exe -m pip install -r requirements.txt
.\.venv\Scripts\python.exe -m jupyterlab
```

En Linux se puede usar `python3.12 -m venv .venv` y `.venv/bin/python` en los tres comandos siguientes. Abrir el notebook con el kernel **Python 3** del entorno iniciado y ejecutar todas las celdas desde el comienzo. Las gráficas y tablas guardadas pueden leerse directamente. Si se hace una corrida nueva, las respuestas deben revisarse contra sus salidas y los tiempos deben interpretarse con el hardware de esa corrida.

La configuración se elige con los resultados de validación. Conservar `SEED_SPLIT = 42`. El bloque final aplica a los modelos y las semillas ya fijados. Las imágenes y los pesos entrenados se obtienen durante la reproducción y quedan fuera de los archivos del trabajo.

## Referencia

El código parte del [notebook de Carlos Selmo](https://github.com/cselmo/CNN-en-Skin-Dataset/blob/e6b86162899a4bd276ffce7cdc86b79454fb9e8c/CNN_en_Skin_Dataset.ipynb). Los ajustes de ejecución y la declaración de uso de IA están documentados en el notebook.

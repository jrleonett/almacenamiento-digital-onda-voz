# ¿Cómo se almacena digitalmente una onda de voz humana?

Desde la optica del **cómputo forense**, el análisis de señales de audio como la voz humana, es importante para la identificación de individuos, la verificación de autenticidad y la detección de manipulaciones en archivos de audio. En este apartado hablaré acerca de como se almacena digitalmente una onda de voz, utilizando las técnicas de procesamiento de señales y herramientas de programación en Python. Además, se proporciona un ejemplo práctico para grabar, analizar y visualizar la forma de onda de un archivo de audio, con un enfoque aplicado a la investigación forense.

![image](https://drive.google.com/uc?export=view&id=1EKry_Wr-m-ebiTNXmwOgyeZg676okr_b)

---

## ¿Cómo se almacena digitalmente una onda de voz?

Cuando grabamos nuestra voz, la onda de sonido (que es una señal analógica) se convierte en una señal digital mediante un proceso llamado **digitalización**. Este proceso consta de dos etapas principales:

1. **Muestreo (Sampling)**: Donde se toman muestras de la señal analógica en intervalos de tiempo muy pequeños. La cantidad de muestras por segundo se conoce como **tasa de muestreo** (por ejemplo, 44,100 muestras por segundo en un archivo de audio de calidad CD).

2. **Cuantización (Quantization)**: Es donde cada muestra se convierte en un valor numérico. En un sistema de 16 bits, cada muestra puede tomar un valor entre -32,768 y 32,767.

El resultado de esto, es una secuencia de números que representan la amplitud de la onda de sonido en cada instante de tiempo. Estos números se almacenan en un archivo de audio, junto con metadatos como la tasa de muestreo y la resolución.

---

## Aplicación en el cómputo forense.

En el cómputo forense, el análisis de archivos de audio es importante porqué permite:
- **Identificación de individuos**: Comparar patrones vocales para confirmar la identidad de un sospechoso.
- **Detección de manipulaciones**: Identificar si un archivo de audio ha sido editado o alterado.
- **Autenticación de evidencia**: Verificar la integridad de una grabación utilizada como prueba en un caso legal.

---

## Proyecto: Análisis de audio para cómputo forense.

### Descripción.
Este proyecto consiste en la realización de un programa en Python que permite:
1. Crear una carpeta para almacenar archivos de audio.
2. Cargar un archivo de audio.
3. Analizar la señal de audio en el dominio del tiempo.
4. Visualizar la forma de onda y mostrar la secuencia numérica de la señal.

### Requisitos.
- Python 3.x
- Librerías: `librosa`, `matplotlib`, `numpy`

### Instalación y uso.
1.- Clona este repositorio:

```python
git clone https://github.com/tu-usuario/analisis-audio-forense.git
```
2.- Instala las dependencias:

```python
pip install librosa matplotlib numpy
```
3.- Ejecuta el código en tu entorno Python.

---

## Código del proyecto.

### Parte 1: Crear la carpeta y cargar el archivo de audio.

```python
import os

# Crear la carpeta EVIDENCIA si no existe
carpeta_evidencia = "EVIDENCIA"
if not os.path.exists(carpeta_evidencia):
    os.makedirs(carpeta_evidencia)
    print(f"Carpeta '{carpeta_evidencia}' creada.")
else:
    print(f"La carpeta '{carpeta_evidencia}' ya existe.")

# Esperar a que se suba un archivo de audio
print(f"\nPor favor, sube un archivo de audio (formato .wav, .mp3, etc.) a la carpeta '{carpeta_evidencia}'.")
input("Presiona Enter cuando hayas subido el archivo...")

# Buscar archivos de audio en la carpeta
archivos_audio = [f for f in os.listdir(carpeta_evidencia) if f.endswith(('.wav', '.mp3', '.m4a', '.flac', '.ogg'))]

if not archivos_audio:
    print("No se encontraron archivos de audio en la carpeta.")
else:
    archivo_audio = os.path.join(carpeta_evidencia, archivos_audio[0])
    print(f"\nArchivo de audio seleccionado: {archivo_audio}")
```
----
### Parte 2: Análisis y visualización de la señal de audio.

```python
import librosa
import matplotlib.pyplot as plt
import numpy as np

# Cargar el archivo de audio
y, sr = librosa.load(archivo_audio, sr=None)  # y: señal de audio, sr: tasa de muestreo

# Calcular la duración del audio
duracion = len(y) / sr
print(f"Duración del audio: {duracion:.2f} segundos")

# Mostrar la secuencia numérica de la señal de audio
print("\nSecuencia numérica de la señal de audio (primeras 20 muestras):")
np.set_printoptions(precision=6, suppress=True)  # Mostrar valores con 6 decimales
print(y[:20])  # Muestra las primeras 20 muestras

# Generar la forma de onda
plt.figure(figsize=(10, 4))
librosa.display.waveshow(y, sr=sr)
plt.title(f'Forma de Onda del Audio: {archivos_audio[0]}')
plt.xlabel('Tiempo (s)')
plt.ylabel('Amplitud')
plt.show()
```

## Explicación del código.

### Parte 1:
- **Crea una carpeta llamada EVIDENCIA** para almacenar archivos de audio.
- **Espera a que el usuario suba un archivo de audio** y lo selecciona para su análisis.

### Parte 2:
- **Carga el archivo de audio** y extrae la señal de audio (`y`) y la tasa de muestreo (`sr`).
- **Calcula la duración del audio**.
- **Muestra la secuencia numérica** de las primeras 20 muestras de la señal.
- **Genera y muestra la forma de onda** del audio.

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/drive/1QAR8exd7P6oxLK3MTD4JF1WjgP6-YN5h?usp=sharing)

---

## Resultados esperados.

### En la consola:
- Duración del audio.
- Secuencia numérica de las primeras 20 muestras.

### Gráfica:
- Forma de onda del archivo de audio.

![image](https://drive.google.com/uc?export=view&id=1WEY16S8WdK4BCxA7Hb029vuRsR2FzOSc)

### Recomendación:
- Pueden modificar este código para que al finalizar el proceso, genere un archivo `.ZIP` donde lleve incorporado el muestreo y la imagen del análisis (revisa el código del colab de mi repositorio sobre "Análisis de metadatos y Error de ELA en imágenes digitales", te puede ayudar mucho ).

---
# Cómo citar este trabajo.
Usa la siguiente entrada BibTeX si utilizas este trabajo en tu investigación:
```bash
@article{joséRLeonett,
  title={Almacenamiento digital de voz humana en forma de Onda},
  author={José R. Leonett},
  year={2024}
}
```
---
**Licencia.**
- Este proyecto está bajo la licencia MIT. Consulta el archivo LICENSE para más detalles.



# ¿Cómo se almacena digitalmente una onda de voz humana?
![Licencia](https://img.shields.io/badge/Licencia-GNU%20GPL%20v3-blue)
![GitHub](https://img.shields.io/badge/Python-3.8%2B-green)
![GitHub](https://img.shields.io/badge/Estado-Activo-brightgreen)
![Google Colab](https://img.shields.io/badge/Google_Colab-F9AB00?style=for-the-badge&logo=google-colab&logoColor=white)
![Hugging Face](https://img.shields.io/badge/Hugging_Face-FFD21E?style=for-the-badge&logo=huggingface&logoColor=black)


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

## Funcionalidades del Proyecto.

**Carga de Archivos de Audio:**
- Permite subir archivos de audio en formatos compatibles (`.wav`, `.mp3`, `etc.`).
- Almacena los archivos en una carpeta llamada EVIDENCIA.

**Análisis de la Señal de Audio:**
- Extrae la señal de audio y la tasa de muestreo.
- Calcula la duración del audio.

**Visualización de Resultados:**
- Muestra la secuencia numérica de las primeras 20 muestras de la señal.
- Genera y visualiza la forma de onda del audio.

## Cómo Usar el Proyecto.

**En Google Colab:**
- Haz clic en el siguiente botón para abrir el proyecto en Colab:
[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/drive/1QAR8exd7P6oxLK3MTD4JF1WjgP6-YN5h?usp=sharing)
- Sigue las instrucciones en el notebook para subir un archivo de audio y ver los resultados.

**En Hugging Face Spaces:**
- Accede a la aplicación en Hugging Face Spaces:
[![Open In Colab]("https://huggingface.co/front/assets/huggingface_logo-noborder.svg"")(https://huggingface.co/spaces/leonett/analisis-audio-voz")
- Sube un archivo de audio y observa los resultados del análisis en tiempo 


## Explicación del código.

### Parte 1:
- **Crea una carpeta llamada EVIDENCIA** para almacenar archivos de audio.
- **Espera a que el usuario suba un archivo de audio** y lo selecciona para su análisis.

### Parte 2:
- **Carga el archivo de audio** y extrae la señal de audio (`y`) y la tasa de muestreo (`sr`).
- **Calcula la duración del audio**.
- **Muestra la secuencia numérica** de las primeras 20 muestras de la señal.
- **Genera y muestra la forma de onda** del audio.

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
- Este proyecto está bajo la licencia GNU General Public License v3.0. Consulta el archivo LICENSE para más detalles.



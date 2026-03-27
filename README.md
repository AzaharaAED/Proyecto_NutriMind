# Proyecto NutriMind

Este repositorio reúne los distintos notebooks y módulos que forman parte del sistema **NutriMind**, orientado a interpretar información del hogar y del usuario para generar una respuesta útil y personalizada.

## Estructura del proyecto

### `nevhor.ipynb`
Notebook dedicado a los módulos de **nevera** y **horno**.

Incluye dos procesos principales, ambos apoyados en modelos **Qwen2-VL**:

- **Nevera**:
  - Recibe una imagen del interior de una nevera.
  - Detecta los alimentos presentes.
  - Divide la imagen en cuadrículas para analizar regiones de forma independiente.
  - Estima cantidades aproximadas en función de la frecuencia con la que aparece cada alimento.
  - Está preparado para evitar duplicidades en los nombres de alimentos y corregir salidas poco útiles o inconsistentes.

- **Horno**:
  - Recibe una imagen del interior de un horno.
  - Analiza la imagen completa para identificar el **plato principal preparado**.
  - Si no puede reconocer con precisión el plato, devuelve los ingredientes principales visibles.
  - Si no detecta comida, lo indica explícitamente.

---

### `bascula.ipynb`
Notebook de ejemplo con **datos sintéticos**.

- No contiene un modelo real de predicción.
- Se utiliza para simular el funcionamiento de una báscula o entrada de peso.
- Su objetivo es servir como apoyo durante el desarrollo, las pruebas y la integración con el resto del sistema.

---

### `cuestionario.ipynb`
Notebook correspondiente al **cuestionario inicial del usuario**.

- Recoge información sobre preferencias, hábitos o restricciones.
- Permite conocer mejor al usuario antes de generar recomendaciones o decisiones personalizadas.
- Actúa como punto de entrada de contexto para el sistema general.

---

### `comanda.ipynb`
Notebook encargado de **recoger la petición del usuario**.

- Procesa lo que el usuario quiere hacer (ej. qué desea cocinar o consultar).
- Estructura esa petición en un formato usable por el sistema.
- Actúa como enlace entre la intención del usuario y el módulo general.

- Inicialmente, este módulo se diseñó para permitir al usuario introducir su petición:
  - mediante texto
  - y mediante voz, utilizando Whisper

- Sin embargo, durante el desarrollo se observó que el flujo resultaba algo engorroso para el usuario, ya que implicaba varios pasos y preguntas.

- Por este motivo, se decidió dejar esta funcionalidad **provisionalmente en pausa**, con la intención de retomarla en el futuro e implementarla de forma más sencilla y eficiente.

---

### `hogar_ia_colab_corregido.ipynb`
Notebook destinado a la **interfaz** del sistema.

- Se centra en la construcción y prueba de la interacción con el usuario.
- Organiza la presentación de entradas y salidas del sistema.
- Sirve como base visual o de demostración para conectar los distintos módulos del proyecto.

---

### `Proyecto_modulo_general_gemini_personalizado.ipynb`
Notebook principal del proyecto.

- Integra la información procedente de los distintos módulos:
  - nevera
  - horno
  - cuestionario
  - comanda
  - báscula u otras entradas disponibles
- Centraliza la lógica general del sistema.
- Además, incorpora **Gemini** como parte del procesamiento o generación de respuestas.
- Es el módulo que unifica toda la información para producir una salida final coherente y personalizada.

> **Importante:**  
> Para visualizar correctamente este notebook, se recomienda abrirlo en **Google Colab**.  
> Al subirse ejecutado a GitHub, algunas salidas no se renderizan correctamente.  
> Sin embargo, el modelo funciona y se ejecuta sin problemas en entorno Colab.

---

### `Sin_pip_Proyecto_modulo_general_gemini_personalizado.ipynb`
Versión adaptada del módulo general.

- Contiene la misma lógica base que `Proyecto_modulo_general_gemini_personalizado.ipynb`.
- Está preparado para funcionar **sin dependencias instaladas mediante `pip`**.
- Su objetivo es facilitar la ejecución en entornos web o restringidos donde no sea posible instalar paquetes de forma convencional.

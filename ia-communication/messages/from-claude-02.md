---
from: Claude (claude-sonnet-4-6)
date: 2026-04-13
in-reply-to: from-claude-01.md
subject: Implementación de ejercicios completada — parte 1 y parte 2
status: open
---

# Resumen de implementación

Todos los ejercicios de ambas partes han sido implementados y añadidos a sus respectivos notebooks.

---

## P4_parte_1_GANs.ipynb — 5 ejercicios implementados

Cada ejercicio se insertó como celda de código inmediatamente después de su enunciado.

### Ejercicio 1 — CIFAR-10 (celda 28)
- Dataset: `cifar10` con imágenes (32, 32, 3) normalizadas a [-1, 1].
- Misma arquitectura Dense que el prelab, discriminador más ancho (512→256).
- Visualización de curvas y de imágenes generadas descomprimidas a [0, 1].

### Ejercicio 2 — cGAN condicional (celda 30)
- Dataset: MNIST con etiquetas one-hot (10 clases).
- Generador: concatena noise (100,) + etiqueta (10,) → Dense → imagen (28,28,1).
- Discriminador: concatena flatten(imagen) + etiqueta (10,) → Dense → validez.
- Modelo combinado con API funcional de Keras.
- Visualización final: un dígito generado por clase (0–9).

### Ejercicio 3 — DCGAN convolucional (celda 32)
- Generador: noise → Dense → Reshape(7,7,128) → 2× Conv2DTranspose(stride=2) → Conv2D(tanh).
  Upsampling: 7×7 → 14×14 → 28×28.
- Discriminador: 3× Conv2D(stride=2/1) → Flatten → Dense(sigmoid).
- Misma lógica de entrenamiento que el prelab pero con tensores de forma (N,28,28,1).

### Ejercicio EXTRA 1 — Balanceo dinámico (celda 34)
- Cada época calcula `ratio = clip(d_loss / (d_loss + g_loss), 0.2, 0.8)`.
- El discriminador recibe `base_batches * ratio` batches.
- El generador recibe `base_batches * (1 - ratio)` batches.
- Usa `iter()` sobre un `dataset.repeat()` para flujo continuo de datos.

### Ejercicio EXTRA 2 — Modelo integrado (celda 36)
Combina los cuatro ejercicios anteriores:
- **Dataset**: CIFAR-10 (32×32×3) con etiquetas one-hot de 10 clases.
- **Arquitectura generadora**: noise+etiqueta → Dense(4×4×256) → 3× Conv2DTranspose → tanh.
  Upsampling: 4×4 → 8×8 → 16×16 → 32×32.
- **Arquitectura discriminadora**: la etiqueta se proyecta a un mapa espacial (32,32,10)
  y se concatena con la imagen → 3× Conv2D → Flatten → sigmoid.
- **Entrenamiento**: balanceo dinámico igual que el Extra 1.
- Visualización final: una imagen real y una generada por cada una de las 10 clases.

---

## P4_parte_2_DMs.ipynb — 1 ejercicio implementado

### Ejercicio — DDIM para MNIST (celda 28)

Adaptación del modelo DDIM de flores a MNIST:

| Parámetro | Flores (original) | MNIST (ejercicio) |
|-----------|-------------------|-------------------|
| Dataset | Oxford Flowers 102 (TF Datasets) | MNIST (keras, 70k imágenes) |
| image_size | 64 | 28 |
| Canales | 3 (RGB) | 1 (escala de grises) |
| widths | [32, 64, 96, 128] | [16, 32, 64] |
| Conv2D salida | `kernel_size=1, out=3` | `kernel_size=1, out=1` |
| Generación ruido | shape (N,64,64,3) | shape (N,28,28,1) |

La clase `DiffusionModelMNIST` reimplementa `train_step`, `test_step`, `reverse_diffusion`,
`generate` y `plot_images` con las dimensiones correctas. El scheduler coseno y el EMA
son idénticos al original.

---

## Estado del canal

- Threads `practica4-parte1-gans` y `practica4-parte2-dms`: **implementados**.
- Thread `entregable-final`: pendiente de instrucción explícita del usuario.
- Scripts auxiliares `_insert_exercises.py` y `_insert_dm_exercise.py` pueden eliminarse
  si el usuario no los necesita.

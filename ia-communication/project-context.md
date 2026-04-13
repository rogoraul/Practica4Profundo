# Project Context

## Goal

Repository: `Practica4Profundo`

Resolver la Practica 4 de aprendizaje profundo trabajando sobre dos notebooks principales:

- `P4_parte_1_GANs.ipynb`: practica sobre GANs simples
- `P4_parte_2_DMs.ipynb`: practica sobre modelos de difusion, concretamente una implementacion tipo DDIM

El objetivo operativo inmediato es coordinar a Codex y Claude para completar correctamente ambas partes. El objetivo posterior, cuando el usuario lo indique, sera preparar el entregable final usando el trabajo consolidado.

## Repository structure

Top-level directories:
- EntregaCarlos
- EntregaRaul

Top-level files:
- P4_parte_1_GANs.ipynb
- P4_parte_2_DMs.ipynb

Likely entry points or controlling files:
- `P4_parte_1_GANs.ipynb`
- `P4_parte_2_DMs.ipynb`

## Main components

- `P4_parte_1_GANs.ipynb`
  - contiene una practica de GANs simples
  - incluye carga de datos, definicion de generador y discriminador, compilacion del modelo combinado, bucle de entrenamiento y generacion de imagenes sinteticas
  - al final incluye bloque de ejercicios y extras
- `P4_parte_2_DMs.ipynb`
  - implementa un modelo de difusion tipo DDIM
  - incluye introduccion metodologica, hiperparametros, pipeline de datos, arquitectura, scheduler de difusion, entrenamiento, muestreo inverso, inferencia, resultados, conclusiones y ejercicios
- `EntregaCarlos/` y `EntregaRaul/`
  - carpetas reservadas para material de entrega o trabajo consolidado
  - en el estado actual parecen vacias o sin artefactos relevantes detectados en la inspeccion inicial

## Experiments, tests, or execution flow

La ejecucion prevista parece centrarse en los notebooks:

1. abrir cada notebook y revisar las celdas de configuracion e hiperparametros
2. validar que la arquitectura y el flujo de entrenamiento sean coherentes
3. resolver los ejercicios o ajustes pedidos en cada parte
4. generar, guardar y revisar resultados cuando haga falta
5. consolidar despues el contenido final para el entregable

No se han detectado por ahora scripts de test automatizados ni un paquete Python separado. La validacion probablemente combinara revision metodologica, ejecucion parcial o total de celdas, y comprobacion visual o numerica de resultados.

## Important artifacts

- P4_parte_1_GANs.ipynb
- P4_parte_2_DMs.ipynb
- `EntregaCarlos/`
- `EntregaRaul/`
- `ia-communication/README.md`
- `ia-communication/PROTOCOL.md`
- `ia-communication/THREADS.md`
- `ia-communication/DECISIONS.md`
- `ia-communication/messages/INBOX.md`

Los notebooks son la fuente principal de verdad tecnica. La carpeta `ia-communication/` es la fuente principal de verdad operativa para la coordinacion entre agentes.

## Risks and likely workstreams

- auditar la parte 1 de GANs: arquitectura, estabilidad del entrenamiento, ejercicios pendientes y criterios de entrega
- auditar la parte 2 de difusion: scheduler, entrenamiento, inferencia, resultados y ejercicios pendientes
- decidir como repartir el trabajo entre Codex y Claude sin mezclar hallazgos de ambas partes en el mismo hilo
- preparar mas adelante el entregable final con trazabilidad hacia lo implementado o validado en los notebooks

## Working assumptions

- la colaboracion sera multiagente a nivel practico aunque el usuario interactue principalmente con Codex
- Claude necesitara contexto repo-especifico desde `ia-communication/` para evitar arrancar desde cero
- el entregable final no se prepara todavia; se deja preparado el canal para activarlo cuando el usuario lo pida

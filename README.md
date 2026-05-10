# Trabajo Práctico 3: Aprendizaje No Supervisado

## Dataset

**Seeds - Semillas de Trigo**  
Fuente: https://www.kaggle.com/datasets/jmcaro/wheat-seedsuci

El dataset contiene medidas físicas de granos de trigo de 3 variedades distintas: Kama, Rosa y Canadian. Tiene 7 variables numéricas (área, perímetro, compacidad, largo del grano, ancho del grano, coeficiente de asimetría y largo del surco) y 152 muestras sin valores nulos.

## Objetivo

Aplicar técnicas de aprendizaje no supervisado (PCA y K-means) para explorar la estructura del dataset sin usar las etiquetas de variedad, y comparar los resultados obtenidos con distintas versiones del dataset.

## Estructura del repositorio

```
├── trabajo_practico_3_seeds.ipynb   # Notebook principal
└── README.md                        # Este archivo
```

## Pasos realizados

1. Carga y exploración del dataset
2. Estandarización de variables con `StandardScaler`
3. PCA completo con scree plot de varianza explicada
4. Reducción a 2 componentes principales y visualización
5. Selección de variables por correlación y árbol de decisión
6. K-means en 3 versiones del dataset (original, PCA 2D, selección de variables) con K entre 2 y 6
7. Evaluación con método del codo y silhouette score

## Principales hallazgos

- Las primeras 2 componentes del PCA explican aproximadamente el 70% de la varianza total, y en el scatter plot se pueden ver 3 grupos bastante separados.
- La matriz de correlación mostró que `area`, `perimeter` y `kernel_length` están muy correlacionadas entre sí, por lo que son redundantes.
- En las tres versiones del dataset, K=3 resultó ser el número óptimo de clusters tanto por el método del codo como por el silhouette score.
- K-means logró encontrar los 3 grupos sin conocer de antemano las etiquetas de variedad, lo que confirma que las medidas físicas de los granos contienen suficiente información para distinguir las variedades.
- La versión con PCA dio resultados similares a la original usando solo 2 dimensiones, lo que muestra que PCA conserva bien la estructura del dato.

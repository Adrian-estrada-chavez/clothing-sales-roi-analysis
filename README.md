## 🏢 Contexto del Negocio y Problemática
La empresa objeto de este estudio es un negocio familiar con **10 años** en el mercado retail de ropa. A lo largo de su historia ha experimentado un crecimiento sostenido; sin embargo, durante los **últimos 2 años**, la administración comenzó a notar una problemática crítica: a pesar de mantener un volumen constante de ventas, **el dinero en caja no alcanza y se desconoce la causa raíz**.

Ante la falta de visibilidad financiera y operativa, este proyecto nace para auditar los datos históricos, mapear los flujos de efectivo y entender en qué parte del ciclo operativo (compras, inventario estancado o devoluciones) se está perdiendo la rentabilidad del negocio.



# Análisis de Rendimiento de Ventas y Optimización de ROI - Retail

<a href="https://colab.research.google.com/github/Adrian-estrada-chavez/clothing-sales-roi-analysis/blob/main/notebooks/Clothing_sales_roi_analysis.ipynb" target="_blank">
  <img src="https://colab.research.google.com/assets/colab-badge.svg" alt="Open In Colab"/>
</a>

## 🎯 Objetivo del Proyecto
El objetivo principal de este proyecto es analizar el rendimiento de ventas de una comercializadora de ropa retail de **sucursal única** orientada al **público en general**. A través de este análisis, se identifican las categorías y marcas de productos con mayor rotación y rentabilidad para optimizar la gestión de inventario y maximizar el Retorno de Inversión (ROI) real del negocio.

---

## 🏗️ Metodología y Fases del Proyecto

### 1. Exploración y Mapeo de Datos (PostgreSQL)
Antes de procesar la información en Python, se realizó una fase de *Data Discovery* mediante consultas en PostgreSQL para auditar las tablas y entender las relaciones lógicas del modelo de negocio:
* **Núcleo de Ventas e Ingresos:** Tablas `clientes` (validando el registro único de público general), `ventas`, `detalle_venta` y `sucursales`.
* **Gestión de Costos e Inventario (La Inversión):** Tablas `compras`, `detalle_compra` y `productos` (catálogo y marcas).
* **Logística Inversa y Ajustes (El ROI Real):** Tablas `notas_credito` y `detalle_ntc` para descontar devoluciones del beneficio neto.

### 2. Extracción y Almacenamiento (ETL)
Los datos validados fueron extraídos de la base de datos local en formato CSV garantizando la codificación correcta (`UTF-8`) para evitar pérdidas de caracteres especiales mediante el comando de copia relacional:
```sql
3. Carga, Limpieza y Transformación (Python)
Utilizando un entorno modular, los datos se importaron de forma directa desde los archivos crudos alojados en el repositorio de GitHub.
SET client_encoding TO 'utf8';
\copy nombre_tabla TO 'data/raw/nombre_tabla.csv' CSV HEADER;
```
### 3. Cálculo Lógico 
Se aplicaron manipulaciones de datos utilizando Pandas y NumPy para estructurar la matriz de correlación, aislar el comportamiento de las devoluciones y determinar la velocidad de rotación.

Tratamiento de Datos: Durante el desarrollo del código, se implementó el uso de diccionarios de Python para almacenar la colección de dataframes originales, manteniendo intactos los nombres y estructuras de origen de la base de datos para preservar la claridad matemática y de negocio.

🛠️ Tecnologías Utilizadas
---
Base de Datos: PostgreSQL

Lenguaje principal: Python 3.x

Librerías de Análisis: Pandas, NumPy

Visualización: Matplotlib, Tableau.

### 🏷️ Sistema de Calificación y Envejecimiento de Stock
Para dar visibilidad inmediata al estado de las mercancías y responder a la incógnita de dónde se encuentra retenido el flujo de efectivo, se desarrolló un algoritmo de lógica condicional que clasifica el inventario en **cinco niveles críticos** según el tiempo transcurrido desde su adquisición:

* **NOVEDAD (Alta Prioridad de Exhibición):** Producto de reciente ingreso con el mayor potencial de margen completo. Requiere máxima exposición en piso de venta.
* **ACTIVO (Monitoreo Constante):** Producto con rotación regular dentro de los parámetros esperados de venta.
* **LENTA ROTACIÓN (Atención Comercial):** Mercancía que empieza a rebasar los tiempos óptimos de permanencia en exhibición. Requiere estrategias de impulso visual o ligeros incentivos.
* **LIQUIDACIÓN PRIORITARIA (Acción Inmediata):** Productos con baja demanda que ponen en riesgo la liquidez. Requiere la aplicación de promociones cruzadas o descuentos estratégicos antes de congelarse por completo.
* **DEAD STOCK / STOCK MUERTO (Fuga de Capital):** Mercancía estancada que bloquea el capital de trabajo y eleva los costos de almacenamiento. Requiere estrategias de liquidación total para recuperar el costo base.

#### 📈 Impacto Interdepartamental de esta Métrica:
Este sistema de calificación actúa como un puente de comunicación único entre tres áreas clave de la organización:
1.  **Dirección:** Permite visualizar de forma macro la salud financiera del inventario y evaluar el riesgo de pérdida de liquidez por capital congelado.
2.  **Ventas:** Funciona como guía comercial diaria para saber qué productos requieren prioridad de salida, reubicación en los aparadores principales de la sucursal o activación de descuentos antes de devaluarse.
3.  **Almacén:** Optimiza el espacio físico, identificando qué mercancía está ocupando zonas críticas de manera ineficiente para mejorar la logística de acomodo y futuras recepciones.

📉 Conclusiones Clave y Resumen Ejecutivo
---
El análisis del proyecto arrojó los siguientes hallazgos críticos para la toma de decisiones del negocio:

1. Optimización del Flujo de Caja: El éxito a corto plazo de la sucursal no depende únicamente de incrementar el volumen de ventas, sino de mejorar la calidad de las transacciones y reducir costos de almacenamiento.

2. Riesgo en el Inventario Estancado: Se identificó mercancía estancada que actualmente genera un ROI simulado inferior al 2% en caso de liquidarse por completo, comprometiendo el capital de trabajo.

3. Plan de Acción Estratégico: Para sanar el flujo de caja y alcanzar un ROI neto sostenible superior al 10%, es indispensable implementar una reducción de costos operativos, negociar agresivamente precios de adquisición con proveedores de marcas clave y reajustar los precios de venta de los artículos con alta demanda.

4. Cultura de Datos: Se identificaron áreas de oportunidad en la captura original (columnas vacías de color y talla en todos los SKUs y la falta de motivos en las notas de crédito), recomendando establecer un registro estricto para predecir con exactitud qué variantes se estancan.

## 🔒 Privacidad y Cumplimiento de Datos
> ⚠️ **Nota importante sobre los datos:** Para proteger la confidencialidad, la ventaja competitiva y la privacidad comercial de la empresa, **todos los datos utilizados en este repositorio son 100% ficticios y sintéticos**. Los nombres de clientes, registros de ventas, costos y códigos SKU han sido generados artificialmente preservando de manera exacta la lógica matemática, las proporciones financieras y el comportamiento operativo del modelo de negocio original.

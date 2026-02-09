# Optimizaci-n-de-Performance-para-An-lisis-Financiero-en-SQL
Optimización de Performance para Análisis Financiero en SQL

Optimización de Performance para Análisis Financiero en SQL
Descripción del Proyecto

Este proyecto implementa índices compuestos estratégicos sobre las tablas clave de un modelo de datos financiero con el objetivo de optimizar consultas analíticas intensivas en tiempo, típicas de análisis de mercado, eventos corporativos e indicadores técnicos.

El enfoque está orientado a escenarios de análisis cuantitativo, donde la latencia y el rendimiento de consultas históricas y recientes son críticos.

Problema que Resuelve

Las consultas financieras suelen compartir estas características:

Filtrado frecuente por ticker_id

Acceso intensivo por fechas recientes

Joins entre precios, indicadores y eventos

Ventanas temporales (últimos días, semanas o meses)

Sin índices adecuados, estas consultas generan:

Table scans costosos

Alta latencia

Poca escalabilidad al crecer el histórico de datos

Este proyecto ataca directamente ese cuello de botella.

Estrategia de Indexación

Se crean índices compuestos alineados con los patrones reales de consulta.

1. Índice en precios_diarios
CREATE INDEX idx_precios_tiempo
ON precios_diarios (ticker_id, fecha DESC);


Justificación:

Optimiza consultas por activo (ticker_id)

Prioriza acceso a datos recientes (fecha DESC)

Acelera análisis de retornos, gaps, volatilidad y tendencias

2. Índice en indicadores_tecnicos
CREATE INDEX idx_indicadores_tiempo
ON indicadores_tecnicos (ticker_id, fecha DESC);


Justificación:

Mejora el cálculo y filtrado de indicadores como RSI, SMA, kurtosis y skewness

Reduce costos en joins con precios diarios

Ideal para análisis técnicos y señales de trading

3. Índice en eventos_corporativos
CREATE INDEX idx_eventos_tiempo
ON eventos_corporativos (ticker_id, fecha, tipo_evento);


Justificación:

Optimiza búsquedas de eventos por activo y fecha

Acelera análisis de impacto post-evento

Facilita comparaciones entre tipos de eventos (Ganancias, Regulación, M&A)

Beneficios Clave

🚀 Reducción significativa del tiempo de ejecución en consultas analíticas

📈 Mejor escalabilidad a medida que crece el histórico

🔍 Consultas más eficientes para:

Estudios pre y post evento

Análisis sectoriales

Detección de anomalías estadísticas

🧠 Índices diseñados según uso real, no genérico

Casos de Uso Típicos

Impacto de eventos corporativos en precios

Análisis de volatilidad y riesgo de cola

Señales técnicas basadas en ventanas temporales

Backtesting y research cuantitativo

Requisitos

Base de datos compatible con índices compuestos (ej. SQL Server, PostgreSQL, etc.)

Tablas:

precios_diarios

indicadores_tecnicos

eventos_corporativos

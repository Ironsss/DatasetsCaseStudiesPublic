# Caso de uso — 23andMe: datos, IA y confianza

> **Propósito.** Explicar, de forma sencilla, cómo una empresa de genómica directa al consumidor puede cumplir su promesa usando ciencia de datos e inteligencia artificial sin perder la confianza del público ni incumplir la regulación.

---

## ¿De qué trata?

El caso presenta a 23andMe como ejemplo para discutir tres temas:

1. cómo convertir datos genéticos y de salud en **reportes comprensibles** para personas no expertas,
2. cómo **proteger** esa información frente a riesgos conocidos (p. ej., abuso de credenciales y extracción masiva), y
3. cómo colaborar con terceros (farmacéuticas) sin mover datos crudos, manteniendo **gobernanza** y transparencia.

---

## Problema central

**¿Cómo crecer con datos e IA sin perder la confianza del consumidor ni incumplir la regulación, cuando el negocio depende de datos genéticos sensibles?**

---

## Qué aprenderás

* Diseñar un flujo de datos “**privacidad primero**”: consentimiento por propósito, minimización y trazabilidad.
* Construir **modelos de riesgo** que sean precisos y fáciles de entender (calibración y validación por subpoblaciones).
* Integrar **seguridad de producto** desde el inicio: verificación en dos pasos, detección de comportamientos anómalos y límites adaptativos.
* Operar **colaboraciones** en entornos controlados (clean rooms) con acceso por propósito y auditoría.

---

## Datos y alcance

* Todos los **datos son ficticios** y se usan con fines educativos.
* El caso se apoya en **fuentes públicas** accesibles sin VPN ni login para el contexto histórico y regulatorio.
* No hay datos personales reales.

---

## Flujo metodológico del caso

1. **Contexto y promesa**: ¿qué quiere resolver la empresa y para quién?
2. **Datos mínimos**: diferenciar lo imprescindible de lo opcional; separar identificadores de genéticos.
3. **Calidad y sesgo**: limpieza, imputación y evaluación por subpoblaciones.
4. **Modelado y explicación**: estimar riesgo con métricas claras y lenguaje simple.
5. **Seguridad y confianza**: 2FA por defecto, detección de anomalías, límites adaptativos y planes de respuesta.
6. **Gobernanza con terceros**: entornos controlados y registro auditable de consultas.
7. **Transparencia**: métricas periódicas sobre comprensión del usuario, seguridad y desempeño del modelo.

---

## Actividades sugeridas

* **Diseño de consentimiento**: redactar microtextos sin jerga y definir cómo medir comprensión.
* **Mapa de riesgos**: proponer controles técnicos para la función “parientes de ADN” y medir su impacto en la experiencia.
* **Evaluación de sesgo**: protocolo de auditoría por subpoblaciones y plan de corrección.
* **Plan de 72 horas**: pasos y datos necesarios ante un incidente.


| Variable            | Tipo             | Descripción                                              | Unidad / Dominio                      | Rango aprox. (según generación/clipping) | Notas                                                                                 |
| ------------------- | ---------------- | -------------------------------------------------------- | ------------------------------------- | ---------------------------------------- | ------------------------------------------------------------------------------------- |
| `age`               | numérica (float) | Edad del paciente                                        | años                                  | ~20–80                                   | Medias de clúster: A≈35, B≈50, C≈62.                                                  |
| `bmi`               | numérica         | Índice de masa corporal                                  | kg/m²                                 | **16–45**                                | Recortada (clip) a 16–45.                                                             |
| `systolic_bp`       | numérica         | Presión arterial sistólica                               | mmHg                                  | **90–200**                               | Recortada.                                                                            |
| `diastolic_bp`      | numérica         | Presión arterial diastólica                              | mmHg                                  | **50–130**                               | Recortada.                                                                            |
| `resting_hr`        | numérica         | Frecuencia cardiaca en reposo                            | latidos/min                           | ~45–100                                  | No se clippea; centros: 65/75/85.                                                     |
| `hdl`               | numérica         | Colesterol HDL                                           | mg/dL                                 | **20–100**                               | Recortada.                                                                            |
| `ldl`               | numérica         | Colesterol LDL                                           | mg/dL                                 | **40–220**                               | Recortada.                                                                            |
| `triglycerides`     | numérica         | Triglicéridos                                            | mg/dL                                 | **40–600**                               | Recortada.                                                                            |
| `total_chol`        | numérica         | Colesterol total derivado                                | mg/dL                                 | ≈**70–440**                              | **Derivada**: `ldl + hdl + 0.2*triglycerides`.                                        |
| `glucose_fasting`   | numérica         | Glucosa en ayuno                                         | mg/dL                                 | **65–300**                               | Recortada.                                                                            |
| `hba1c`             | numérica         | Hemoglobina glicosilada                                  | %                                     | **4.5–12**                               | Recortada.                                                                            |
| `alt`               | numérica         | Alanina aminotransferasa                                 | U/L                                   | **5–200**                                | Recortada.                                                                            |
| `ast`               | numérica         | Aspartato aminotransferasa                               | U/L                                   | **5–200**                                | Recortada.                                                                            |
| `crp`               | numérica         | Proteína C reactiva (PCR)                                | mg/L                                  | **0.1–50**                               | Recortada.                                                                            |
| `creatinine`        | numérica         | Creatinina sérica                                        | mg/dL                                 | **0.3–6.0**                              | Recortada.                                                                            |
| `egfr`              | numérica         | Tasa de filtración glomerular estimada                   | mL/min/1.73 m²                        | **5–140**                                | Recortada.                                                                            |
| `wbc`               | numérica         | Recuento de leucocitos                                   | 10⁹/L                                 | **3–20**                                 | Recortada.                                                                            |
| `rbc`               | numérica         | Recuento de eritrocitos                                  | 10¹²/L                                | **3–7**                                  | Recortada.                                                                            |
| `platelets`         | numérica         | Plaquetas                                                | 10⁹/L                                 | **100–700**                              | Recortada.                                                                            |
| `prs`               | numérica         | Puntuación poligénica sintética (riesgo)                 | adimensional                          | **0–1**                                  | Recortada; centros: A 0.2, B 0.6, C 0.8.                                              |
| `exercise_min_week` | numérica         | Minutos de ejercicio por semana                          | min/semana                            | ~0–360                                   | Clip a ≥0; medias: A≈180, B≈60, C≈20.                                                 |
| `pc1`               | numérica         | Componente principal 1 (estructura poblacional simulada) | adimensional                          | ~−1.0–1.0                                | Centros: A 0.0, B 0.5, C −0.4.                                                        |
| `pc2`               | numérica         | Componente principal 2 (estructura poblacional simulada) | adimensional                          | ~−1.0–1.0                                | Centros: A 0.0, B −0.3, C 0.6.                                                        |
| `sex_at_birth`      | binaria (0/1)    | Sexo asignado al nacer                                   | 0=femenino, 1=masculino               | {0,1}                                    | Prob. por clúster ≈0.5.                                                               |
| `smoking_index`     | ordinal (int)    | Índice de tabaquismo                                     | 0=no, 1=ocasional/exfumador, 2=actual | **0–2**                                  | Generado con ruido por clúster (A=0, B=1, C=2 en promedio).                           |
| `bp_medication`     | binaria (0/1)    | Uso de antihipertensivos                                 | {0,1}                                 | 0–1                                      | Prob. por clúster: A≈0.05, B≈0.35, C≈0.70.                                            |
| `statin_use`        | binaria (0/1)    | Uso de estatinas                                         | {0,1}                                 | 0–1                                      | Prob. por clúster: A≈0.10, B≈0.45, C≈0.75.                                            |
| `cluster`           | categórica       | Etiqueta de clúster “verdadera”                          | {`A`,`B`,`C`}                         | —                                        | **A**=saludable/bajo riesgo; **B**=riesgo metabólico; **C**=alto riesgo cardio-renal. |

### Notas generales

* **Tamaño**: 100 filas. Distribución de clústeres: A=35, B=35, C=30.
* **Ruido**: cada variable se genera alrededor de un **centro por clúster** con desviación estándar (`noise_sd`) y, en varios casos, se aplica **recorte (clip)** a rangos plausibles.
* **Ausentes**: no se generan valores perdidos; cualquier NA provendría de procesos posteriores.
* **Escenarios de uso**: EDA, clustering visual (PCA), clasificación (KNN), y ejemplo de “feed” tipo laboratorio (una línea CSV sin encabezado siguiendo el orden de columnas).


La promesa se cumple cuando conviven datos mínimos y de calidad, modelos calibrados y explicables, seguridad proactiva y gobernanza visible. Así, el usuario gana **claridad y control**, la ciencia avanza con **evidencia reproducible** y la organización crece **sin perder la confianza**.

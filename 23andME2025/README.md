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

---

## Preguntas guía

* **Datos mínimos**: ¿qué recolectarías para cumplir la promesa sin invadir la privacidad?
* **Valor real**: ¿cómo medirías utilidad para el usuario, validez científica y confianza?
* **Riesgos clave**: entre reidentificación, sesgo y abuso de cuentas, ¿cuál es el más crítico en tu diseño y por qué?

---

## Entregables y evaluación (sugeridos)

* Documento breve (2–3 páginas) con tu **diseño de flujo** y controles.
* **Prototipo** de textos de consentimiento y panel de privacidad.
* **Métricas** de éxito a 12 meses (comprensión, adopción de 2FA, incidentes, disparidades del modelo).

> Criterios: claridad técnica y ética, viabilidad, y calidad de la comunicación.

---

## Mensaje final

La promesa se cumple cuando conviven datos mínimos y de calidad, modelos calibrados y explicables, seguridad proactiva y gobernanza visible. Así, el usuario gana **claridad y control**, la ciencia avanza con **evidencia reproducible** y la organización crece **sin perder la confianza**.

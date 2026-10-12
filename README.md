# Pedal

App web para el celular conectada a Intervals.icu, con un coach de IA (Claude) que planifica la semana, ajusta cada día según el RPE y manda los entrenamientos al Garmin.

## Uso

1. Abrir la app desde su dirección de GitHub Pages en el celular y elegir "Agregar a pantalla de inicio".
2. En **Ajustes**, cargar el ID de atleta y la clave de API de Intervals (Settings → Developer Settings).
3. En **Ajustes**, completar la **semana estándar** y **dónde entrena** (para el clima). Cada día combina casillas con sus horas: **Gimnasio** (el coach arma la rutina), **Bici libre** (por su cuenta o con el profe: el coach estima la carga con su historial), **Bici con Pedal Coach** (el coach arma la sesión y la manda al Garmin) y **Carrera** (carga estimada y preparación de los días previos). Sin nada tildado, es descanso.
4. En **Ajustes → Coach con IA**, cargar la clave de la API de Anthropic (platform.claude.com → Settings → API keys) y el contexto del atleta: objetivo, carreras, horas por semana, días disponibles y lesiones.

## Secciones

- **Hoy:** forma, fitness, fatiga, carga semanal, resumen del coach, próxima carrera y pronóstico del clima.
- **Modelo:** modelo de rendimiento de Banister ajustado a los datos del atleta (constantes propias de fitness y fatiga), validado contra el estándar 42/7 y usado por el coach cuando predice mejor.
- **Carreras:** registro con tipo, lugar, distancia, desnivel y prioridad (se carga en Intervals como RACE A/B/C); suma el clima del lugar y arma el historial por tipo con forma de llegada, carga previa y resultado.
- **Coach:** disponibilidad de la semana con cambios puntuales y ventana de planificación a elección; plan de martes a lunes (se arma los lunes), revisión diaria con ajustes, envío al Garmin vía el calendario de Intervals, aprendizajes del atleta e historial plan contra real.
- **Actividades:** últimas 8 semanas con análisis por sesión.
- **Plan:** calendario de Intervals de los próximos 14 días.
- **Bienestar:** HRV, FC en reposo, sueño y peso.

## Datos y claves

- Las claves se guardan solo en el navegador del teléfono. El código no contiene claves ni datos del atleta.
- La app llama directo a `intervals.icu` y a `api.anthropic.com`. A Anthropic viajan los datos de entrenamiento y bienestar, nunca la clave de Intervals.
- La memoria del coach (aprendizajes, historial y plan vigente) vive en el teléfono. **Ajustes → Memoria del coach** permite copiar un respaldo y restaurarlo.

## Estructura

Un único archivo, `index.html`, con HTML, CSS y JavaScript. No necesita servidor ni compilación.

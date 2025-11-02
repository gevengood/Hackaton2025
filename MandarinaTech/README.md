# Cruz Roja — MVP (Sabana Hack 2025)

Proyecto: Cruz_Roja_MVP  
Equipo: MandarinaTech

Grupo: 
Pablo Andres Ariza Hernandez
Juan Felipe Ruge
Jorge steven Doncel Bejarano
Esteban David Hernandez Parra

## Resumen
MVP web para la Seccional Cundinamarca - Soacha de la Cruz Roja Colombiana que fusiona mapas interactivos, predicción asistida por IA y material de prevención visual. Facilita la identificación de zonas en riesgo (verde/ámbar/rojo), guía a la población con pasos claros en caso de alerta y permite la gestión básica de formularios de voluntariado. Su objetivo es acelerar la toma de decisiones y mejorar la mitigación de desastres a nivel comunitario.

## Valor distintivo e innovación
- Integración de predicciones climáticas y heurísticas con una capa de IA que clasifica riesgo por zona y define color persistente en el mapa.  
- UX centrada en acciones: cuando la alerta es Alta (rojo) aparece contenido visual de prevención (imágenes + pasos) pensado para la lectura rápida y acción inmediata.  
- Persistencia local de predicciones por zona (localStorage) y comunicación sencilla entre componentes (eventos globales) para reactividad sin complejidad de backends pesados.  
- Digitalización de formularios de hojas para optimizar y ahorrar el tiempo y obtener persistencia de datos.

## Impacto social
- Reduce tiempo de reacción al comunicar visualmente riesgo y acciones concretas a la población.  
- Promueve comportamientos preventivos claros y accesibles (pasos con imágenes) durante emergencias.  
- Facilita coordinación rápida entre voluntarios y comunidades mediante códigos y formularios validados (demo), mejorando la trazabilidad de acciones.

## Características principales
- Mapa interactivo (Leaflet) con polígonos coloreados por probabilidad IA (rojo/ámbar/verde).  
- Panel de alertas con métricas (Población, IA%, AVCD, CMSR) y botón responsivo “Prevención” que abre una modal con pasos ilustrados.  
- Modal de prevención responsive con navegación entre pasos e imágenes (carpeta `Prevencion/`).  
- Pestaña "Voluntarios" que abre formularios HTML listos para imprimir/guardar en PDF y simulación de entrega con validación de código.  
- Proxy de IA (server/) para aislar credenciales y permitir fallback heurístico si el servicio IA no está disponible.

## Estructura del repositorio (resumen)
- src/ — frontend React + TypeScript (Vite).  
  - components/ — componentes UI (MapView, Header, LocationAlert, AdvcSection, CMRCSection, PreventionModal, etc.).  
  - Formulario(s): `src/Formularios/*.html` (formularios estáticos).  
  - Prevencion/ — imágenes numeradas para modal de prevención.  
- server/ — proxy para llamadas a la API de IA (gemini) y manejo de claves.  
- public/ — assets públicos (recomendado para desplegar formularios/imagenes).

## Requisitos y variables de entorno
- Node.js 18+ y npm.  
- Variables principales:
  - VITE_AI_PROXY_URL (por defecto `http://localhost:3001`)  
  - VITE_OWM_KEY (opcional, OpenWeatherMap API key para enriquecer predicciones)  
  - En `server/.env`: GEMINI_API_KEY o credenciales necesarias para el proveedor de IA (opcional; si falta se usa heurística local).

## Cómo ejecutar (desarrollo)
1. Instalar dependencias:
```bash
npm install
cd server && npm install
```
2. Levantar proxy IA (opcional, si quieres respuestas reales):
```bash
cd server
npm start
```
3. Levantar frontend:
```bash
cd /home/cyberteh/Proyectos/SabanaHack/Cruz_Roja_MVP(2)
npm run dev
```
4. Abrir `http://localhost:5173` y verificar que `VITE_AI_PROXY_URL` apunte al proxy si está en uso.

## Notas operativas
- Si el proxy IA no responde, la aplicación usa un fallback heurístico y muestra mensajes de error claros en la UI.  
- Para producción se recomienda servir los formularios e imágenes desde `public/` y proteger el proxy IA con autenticación y despliegue supervisado (pm2/systemd).

## Cómo contribuir
- Reporta issues, añade mejoras de accesibilidad y pruebas visuales.  
- Para agregar imágenes de prevención: colocarlas numeradas en `Prevencion/` y actualizar índices si se requiere otro orden.

## Licencia y contacto
- Proyecto de demostración para Sabana Hack 2025 — uso interno y educativo.  
- Contacto: equipo MandarinaTech.

---

Adicionalmente, el enlace al repositorio original es: https://github.com/gevengood/Sabana_Hack.git

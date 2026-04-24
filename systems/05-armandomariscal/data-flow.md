# Data Flow & Communication: Personal Brand & Portfolio Hub

## Communication Channels
- **GitHub API:** Fuente principal de datos para la generación de gráficos de actividad y estadísticas de lenguajes.
- **Metric Proxies:** Uso de servicios como `github-profile-summary-cards` y `github-readme-stats` para transformar metadatos de Git en representaciones visuales.
- **Internal Linkage:** El flujo de navegación dirige al reclutador/colaborador desde el README principal hacia arquitecturas específicas en repositorios como `chevrolet-tracker` o `sansar-tcg`.

## Event Flow (Actualización de Perfil)
1. **Trigger:** Un commit es realizado en cualquiera de los 7 repositorios destacados (ej. `jabberwocky`).
2. **Extraction:** GitHub actualiza el historial de contribuciones del usuario.
3. **Processing:** El API de `github-readme-activity-graph` procesa la frecuencia de commits.
4. **Visualization:** El README del perfil principal renderiza las nuevas métricas, reflejando el progreso en el "Activity Tracker" global del desarrollador.
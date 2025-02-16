# 🎵 TuneTwister

Bot de música para Discord con sistema multiidioma avanzado y arquitectura moderna.

## 📊 Flujos del Sistema

### Proceso de Inicio
```mermaid
graph TD
    A[Bot Invitado al Servidor] -->|Primera conexión| B[Buscar Canal del Sistema]
    B -->|Canal encontrado| C[Detectar Idioma del Servidor]
    C -->|Idioma Soportado| D[Mensaje: Idioma Detectado]
    C -->|Idioma no Soportado| E[Mensaje: Usando Inglés por Defecto]
    D --> F[Mensaje de Bienvenida]
    E --> F
    F --> G[Crear Configuración Servidor]
    G --> H[Bot Listo para Usar]
```

### Comando /play
```mermaid
graph TD
    A[/play URL] -->|Verificar| B{URL Válida?}
    B -->|No| C[Error: URL Inválida]
    B -->|Sí| D[Verificar Permisos]
    D -->|No| E[Error: Sin Permisos]
    D -->|Sí| F[Verificar Canal de Voz]
    F -->|No| G[Error: No en Canal]
    F -->|Sí| H[Cargar Audio]
    H --> I[Iniciar Reproducción]
    I --> J[Mostrar Embed Info]
```

### Comando /search
```mermaid
sequenceDiagram
    participant U as Usuario
    participant B as Bot
    participant YT as YouTube API
    
    U->>B: /search query
    B->>YT: Buscar (límite: 10)
    YT-->>B: Resultados
    B->>U: Embed con 10 resultados
    Note over U,B: Tiempo espera: 60s
    U->>B: Seleccionar número
    B->>U: Confirmar selección
    B->>B: Procesar como /play
```

### Panel de Control
```mermaid
graph TD
    A[/setup] -->|Verificar Admin| B{Es Admin?}
    B -->|No| C[Error: Sin Permisos]
    B -->|Sí| D[Crear Panel]
    D --> E[Botones de Control]
    E -->|▶️| F[Reproducir]
    E -->|⏸️| G[Pausar]
    E -->|⏹️| H[Detener]
    E -->|⏭️| I[Siguiente]
    E -->|🔊| J[Subir Volumen]
    E -->|🔉| K[Bajar Volumen]
```

## ✨ Características Completas

### 🎵 Sistema de Música
- **Reproducción**
  - YouTube URLs directas
  - Reproducción instantánea
  - Auto-reconexión
  - Control de volumen (0-200%)
  - Sistema anti-crash
  - Buffer adaptativo

- **Búsqueda**
  - Comando `/search` dedicado
  - 10 resultados de YouTube
  - Sistema de selección interactivo
  - Tiempo de expiración: 60 segundos
  - Vista previa de duración
  - Información del canal

- **Control de Reproducción**
  ```
  /play    - Reproducir música desde URL de YouTube
  /search  - Buscar y mostrar 10 resultados de YouTube
  /pause   - Pausar reproducción
  /resume  - Reanudar reproducción
  /stop    - Detener y limpiar cola
  /skip    - Saltar canción actual
  /volume  - Ajustar volumen
  ```

### 🌐 Sistema Multiidioma
- **Idiomas Soportados**
  - 32 idiomas oficiales de Discord
  - 3 idiomas regionales españoles
  - Sistema de fallback inteligente

- **Gestión de Idiomas**
  - Detección automática
  - Persistencia por servidor
  - Cambio en tiempo real
  - Traducciones contextuales

### ⚙️ Sistema de Control
- **Panel de Control**
  ```
  Botones interactivos:
  ▶️ - Reproducir/Reanudar
  ⏸️ - Pausar
  ⏹️ - Detener
  ⏭️ - Siguiente
  🔄 - Loop
  🔀 - Shuffle
  ```

- **Gestión de Permisos**
  - Control por roles
  - Restricciones por canal
  - Comandos administrativos

### 📊 Monitorización
- **Sistema de Logs**
  - Registro detallado
  - Rotación de archivos
  - Niveles de log configurables

- **Diagnósticos**
  ```
  /test    - Ejecutar diagnóstico
  /ping    - Verificar latencia
  /status  - Estado del sistema
  ```

## 🔧 Comandos Detallados

### Sistema de Música
| Comando | Descripción | Opciones |
|---------|-------------|----------|
| `/play` | Reproduce música desde URL | `url` |
| `/search` | Muestra 10 resultados de YouTube | `query` |
| `/queue` | Gestiona la cola | `page` |

### Administración
| Comando | Descripción | Permisos |
|---------|-------------|----------|
| `/setup` | Panel de control | ADMIN |
| `/language` | Cambiar idioma | ADMIN |
| `/config` | Configuración | ADMIN |

## 🛠️ Configuración Técnica

### Variables de Entorno
```env
BOT_TOKEN=tu_token
YOUTUBE_API_KEY=tu_api_key
DEFAULT_PREFIX=/
DEFAULT_LANGUAGE=es-ES
```

### Requisitos del Sistema
- Java 21+
- 512MB RAM mínimo
- Permisos Discord:
  - `VIEW_CHANNEL`
  - `SEND_MESSAGES`
  - `EMBED_LINKS`
  - `CONNECT`
  - `SPEAK`

## 📦 Instalación

```bash
git clone https://github.com/raw-community/TuneTwister.git
cd TuneTwister
mvn clean install
java -jar target/TuneTwister.jar
```

## 🤝 Contribuir

1. Fork el repositorio
2. Crea una rama (`git checkout -b feature/mejora`)
3. Commit tus cambios (`git commit -am 'Add: nueva característica'`)
4. Push a la rama (`git push origin feature/mejora`)
5. Abre un Pull Request

## 📜 Licencia

Este proyecto está licenciado bajo MIT - ver el archivo [LICENSE](LICENSE) para más detalles.

## 👥 Créditos

Desarrollado por Raw Community - Jaie55

## 📞 Soporte

- [Discord](https://discord.gg/tuservidor)
- [GitHub Issues](https://github.com/raw-community/TuneTwister/issues)
- [Documentación](https://github.com/raw-community/TuneTwister/wiki)

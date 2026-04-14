# 🤖 JARVIS IA LOCAL — Agente Autónomo Portable V.beta
para descargarlo aqui les dejo el enlace https://drive.google.com/file/d/1J364OFlpdbNwxpp3rri5NLMvzY3ReLui/view?usp=drive_link

> **Asistente de escritorio con inteligencia artificial 100% local, sin internet, sin instalación, sin APIs externas.**  
> Controla tu PC por voz o texto como si fuera JARVIS de Iron Man.

---

## ✨ ¿Qué hace esta IA?
*Adevertencia la Ia puede q funcione un poco lenta ya que al hacerla 100% portable hace que funcione no tan rapido (estoy trabajando en esto)
Es un agente autónomo que entiende órdenes en español y las ejecuta directamente en tu PC. Puedes hablarle o escribirle y él:

- Abre programas, carpetas y sitios web
- Controla el volumen, captura pantalla, mueve el mouse
- Reproduce música en YouTube
- Ejecuta comandos del sistema
- Apaga, reinicia o bloquea la PC
- Escribe texto, presiona teclas y hace clics automáticamente
- Recuerda el historial de conversaciones

Todo funciona **sin conexión a internet** (modo local) usando tu propio modelo de IA.

---

## 🧠 ¿Cómo funciona por dentro?

```
Tu voz / texto
      ↓
  asistente.py  ←→  Ollama (LLM local)
      ↓                    ↑
  Dispatcher          Modelfile (mi-ia)
   /       \
Sistema   Navegador
(PC)     (Chrome via Selenium)
```

1. El usuario habla o escribe una orden
2. `asistente.py` la envía a **Ollama** (motor de IA corriendo localmente)
3. Ollama responde con texto + **etiquetas de acción** invisibles como `[ABRIR_CALCULADORA]` o `[YOUTUBE_PLAY: duki]`
4. El dispatcher detecta las etiquetas y ejecuta la acción en el sistema
5. El texto visible (sin etiquetas) se muestra y se habla en voz alta

---

## 📁 Estructura del proyecto

```
INTELIGENCIA ARTIFICIAL DE SEBAS/
│
├── INICIAR_IA.bat              ← Doble clic para arrancar todo
│
├── MI_IA/
│   ├── SCRIPTS/
│   │   ├── asistente.py        ← Cerebro principal
│   │   ├── navegador.py        ← Control de Chrome (Selenium)
│   │   └── memoria_ia.txt      ← Historial de conversaciones
│   │
│   ├── MOTOR/
│   │   ├── ollama.exe          ← Motor de IA (portable)
│   │   └── chromedriver.exe    ← Driver de Chrome (portable)
│   │
│   └── PYTHON/                 ← Python portable con todas las librerías
│       └── Lib/site-packages/
│
├── MODELOS_DATOS/              ← Carpeta donde Ollama guarda el modelo
│   ├── blobs/                  ← Datos del modelo (archivos grandes)
│   └── manifests/              ← Índice del modelo
│
└── Modelfile                   ← Definición del modelo personalizado
```

---

## ⚡ Cómo usarlo (sin instalar nada)

### Requisito único
- Windows 10/11
- Google Chrome instalado (para funciones web)

### Pasos
1. **Descargar** la carpeta completa del proyecto
2. **Doble clic** en `INICIAR_IA.bat`
3. Elegir modo:
   - `[1] MODO RÁPIDO` → usa `llama3.2` (requiere internet la primera vez para descargarlo)
   - `[2] MODO LOCAL` → usa tu modelo `mi-ia` (100% offline)
4. Elegir entrada:
   - `[V]` → Por voz (micrófono)
   - `[T]` → Por texto (teclado)
5. ¡Hablar con la IA!

---

## 🎮 Comandos que entiende la IA

### 🌐 Navegación Web
| Ejemplo de orden | Acción |
|---|---|
| "Busca en Google cuando nació Bolívar" | Abre Google con la búsqueda |
| "Pon música de Duki en YouTube" | Abre YouTube y reproduce el primer video |
| "Abre Wikipedia sobre la Segunda Guerra Mundial" | Abre Wikipedia |
| "Busca en Maps el centro comercial más cercano" | Abre Google Maps |
| "Abre youtube.com" | Navega a cualquier URL |

### ⚙️ Control del Sistema
| Ejemplo de orden | Acción |
|---|---|
| "¿Qué hora es?" | Dice la hora actual |
| "¿Cuánta batería tengo?" | Muestra el nivel de batería |
| "¿Cuál es mi IP?" | Muestra la IP local |
| "Dime la resolución de pantalla" | Muestra resolución |
| "Muéstrame los procesos activos" | Lista programas corriendo |

### 🔊 Volumen
| Ejemplo de orden | Acción |
|---|---|
| "Sube el volumen" | Sube 5 niveles |
| "Baja el volumen 10" | Baja 10 niveles |
| "Silencia el sonido" | Silencia/activa |

### 💻 Abrir Aplicaciones
| Ejemplo de orden | Acción |
|---|---|
| "Abre la calculadora" | Abre calc.exe |
| "Abre el bloc de notas" | Abre notepad.exe |
| "Abre Chrome" | Abre Google Chrome |
| "Abre Paint" | Abre mspaint.exe |
| "Abre el administrador de tareas" | Abre taskmgr.exe |
| "Cierra chrome.exe" | Mata el proceso |

### 🖱️ Teclado y Mouse
| Ejemplo de orden | Acción |
|---|---|
| "Escribe Hola mundo" | Escribe el texto con el teclado |
| "Presiona Enter" | Simula tecla Enter |
| "Presiona Ctrl+S" | Ejecuta atajo de guardar |
| "Haz clic" | Clic en posición actual |
| "Haz clic en 500,300" | Clic en coordenadas X,Y |
| "Doble clic" | Doble clic |
| "Mueve el mouse a 800,400" | Mueve el cursor |
| "Scroll abajo" | Hace scroll hacia abajo |

### 📋 Portapapeles
| Ejemplo de orden | Acción |
|---|---|
| "Copia este texto: Hola" | Copia al portapapeles |
| "Pega" | Pega el portapapeles |
| "¿Qué hay en el portapapeles?" | Lee el contenido |

### 📂 Archivos y Carpetas
| Ejemplo de orden | Acción |
|---|---|
| "Crea una carpeta llamada Proyectos" | Crea carpeta en el escritorio |
| "Crea un archivo notas.txt con Hola" | Crea archivo en el escritorio |
| "Borra C:\ruta\archivo.txt" | Elimina el archivo |
| "Abre el explorador" | Abre el explorador de archivos |
| "Toma una captura de pantalla" | Guarda PNG en el escritorio |

### 🔋 Energía
| Ejemplo de orden | Acción |
|---|---|
| "Apaga la PC" | Apaga en 10 segundos |
| "Apaga en 60 segundos" | Apaga con temporizador |
| "Reinicia la PC" | Reinicia en 10 segundos |
| "Hiberna" | Pone en hibernación |
| "Bloquea la pantalla" | Bloquea Windows |
| "Cancela el apagado" | Cancela shutdown pendiente |

### 🛠️ Avanzado
| Ejemplo de orden | Acción |
|---|---|
| "Ejecuta ipconfig" | Corre cualquier comando CMD |
| "Espera 3 segundos" | Pausa la ejecución |
| "Borra la memoria" | Limpia el historial de chat |

---

## 🤖 El modelo de IA

El modelo base es **Meta Llama 3 8B Instruct** en formato GGUF cuantizado (Q4_K_M), corriendo localmente con **Ollama**.

- Sin conexión a internet después de la descarga inicial
- Corre en CPU (funciona sin GPU dedicada)
- 15.8 GB de RAM total — requiere al menos 8 GB disponibles
- Contexto de 4096 tokens
- Responde siempre en español y llama "Señor" al usuario

---

## 🔧 Librerías Python utilizadas

| Librería | Para qué |
|---|---|
| `requests` | Comunicarse con Ollama |
| `pyttsx3` | Síntesis de voz (TTS) en español |
| `SpeechRecognition` | Reconocimiento de voz (STT) |
| `pyautogui` | Control de mouse y teclado |
| `pyperclip` | Portapapeles |
| `selenium` | Control de Chrome |

> Todas estas librerías están incluidas en la carpeta `MI_IA/PYTHON/` — **no hay que instalar nada.**

---

## 📋 Requisitos del sistema

| Requisito | Mínimo |
|---|---|
| Sistema Operativo | Windows 10 / 11 |
| RAM | 8 GB disponibles |
| Almacenamiento | ~6 GB para el modelo |
| CPU | Cualquier procesador moderno |
| GPU | No requerida (opcional para acelerar) |
| Internet | Solo para modo rápido (primera descarga) |

---

## 🚀 Lo más especial del proyecto

> **Es 100% portable.** Copia la carpeta a cualquier USB o disco externo, llévala a otra PC con Windows, doble clic en el `.bat`, y funciona. No requiere instalar Python, Ollama, ni ninguna dependencia. Todo está dentro de la carpeta.

---

## 📌 Notas

- El modelo `mi-ia` es un modelo personalizado basado en Llama 3 8B. Si no está disponible, el sistema cambia automáticamente al modo internet con `llama3.2`.
- El historial de conversaciones se guarda en `MI_IA/SCRIPTS/memoria_ia.txt` y se puede borrar con el comando "borra la memoria".
- ChromeDriver debe coincidir con la versión de Google Chrome instalada en el sistema.

---

## 👤 Autor

**SEBAS** — IA Local primera versión completa, 2026  
Caracas, Venezuela 🇻🇪

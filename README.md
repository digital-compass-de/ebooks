# n8n-workflow-for-ebooks
| Reihenfolge | Schritt             | Tool                  |
| ----------- | ------------------- | --------------------- |
| 1           | Transkript laden    | yt-dlp                |
| 2           | Struktur erstellen  | OpenRouter (Claude)   |
| 3           | Übersetzen          | OpenRouter (Claude)   |
| 4           | **Review**          | Telegram + GitHub     |
| 5           | **Freigabe**        | Telegram Callback     |
| 6           | **Cover erstellen** | OpenRouter (DALL-E 3) |
| 7           | **PDF fertig**      | Pandoc                |


## Setup für VPS
- n8n Installation
### Pandoc + LaTeX installieren
sudo apt update && sudo apt install -y \
  texlive-xetex texlive-fonts-recommended pandoc

### Verzeichnis erstellen auf VPS
mkdir -p /tmp /output

### Github Setup
1. Repo erstellen (z.B. "ebooks")
2. Ordner "ebooks/" anlegen
3. Personal Access Token erstellen (Settings → Developer settings → Tokens)
    Berechtigungen: repo (Lese- und Schreibrechte)

## Nächste Schritte
- JSON in n8n importieren
- Environment Variables setzen
- Telegram-Bot erstellen
- Test mit einem Video

### Environment Variables
| Variable             | Beschreibung          |
| -------------------- | --------------------- |
| `OPENROUTER_API_KEY` | Für Claude + DALL-E   |
| `TELEGRAM_BOT_TOKEN` | Von @BotFather        |
| `TELEGRAM_CHAT_ID`   | Deine Chat-ID         |
| `GITHUB_TOKEN`       | Personal Access Token |
| `GITHUB_USER`        | Dein GitHub Username  |
| `GITHUB_REPO`        | Repository-Name       |

## Mögliche Anpassungen
| Schritt                | Modell            | Grund                        |
| ---------------------- | ----------------- | ---------------------------- |
| **Struktur erstellen** | **GPT-4**         | Deine Erfahrung: besser      |
| **Übersetzung**        | GPT-4 oder Claude | Testen, was besser           |
| **Cover**              | DALL-E 3          | Nur bei OpenRouter verfügbar |

### OpenRouter Modelle
```
// Für Struktur (GPT-4)
"model": "openai/gpt-4"

// Für Struktur (GPT-4 Turbo, schneller)
"model": "openai/gpt-4-turbo"

// Für Übersetzung (testen)
"model": "openai/gpt-4" 
// oder
"model": "anthropic/claude-3.5-sonnet"

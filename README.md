# 📥 Downloaden van MS Teams / SharePoint / Stream video's als deelnemer

Deze gids helpt je om video's van Microsoft Teams/SharePoint/Stream te downloaden, zelfs als je geen organisator bent van de meeting. We gebruiken hiervoor `yt-dlp` of `ffmpeg`.

---

## 🔎 Stap 1: Vind de downloadbare videolink (manifest)

1. Open je browser (werkt in Chrome, Edge en Firefox)
2. Ga naar [https://portal.office.com](https://portal.office.com) en log in
3. Navigeer naar de video die je wilt downloaden (bijv. via SharePoint of MS Stream)
4. Druk op `F12` om de ontwikkelaarstools te openen
5. Ga naar het tabblad **Network**
6. Zoek naar `videomanifest` in het filterveld
7. Druk op `F5` om de pagina opnieuw te laden
8. Start de video. Zodra deze begint met afspelen, verschijnt een URL die begint met `videomanifest?provider=...`
9. Rechtsklik op die regel en kies **Copy → Copy link address**
10. Plak deze URL in een teksteditor (zoals Notepad of VS Code)
11. Zoek in de URL naar: `index&format=dash`
12. **Verwijder alles wat ná `index&format=dash` komt**
13. Bewaar de ingekorte URL (meestal ±1000 tekens)

---

## 💾 Methode 1: Download met `yt-dlp`

### 🔧 Windows installatie

1. Download `yt-dlp.exe` van: [https://github.com/yt-dlp/yt-dlp/releases/latest](https://github.com/yt-dlp/yt-dlp/releases/latest)
2. Plaats het in een map, bijv. `C:\yt-dlp\`

### 🖥️ macOS installatie (via Homebrew)

```bash
brew install yt-dlp
```

### ▶️ Download de video

Open een terminal (Windows: CMD als administrator, macOS: Terminal) en typ:

```bash
yt-dlp "JE-INGEKORTE-URL" -o MijnVideo.mp4
```

---

## 🛠️ Methode 2: Download met `ffmpeg`

### 🔧 Windows installatie

1. Download een build van: [https://ffmpeg.org/download.html](https://ffmpeg.org/download.html)
2. Pak het ZIP-bestand uit naar bijvoorbeeld `C:\ffmpeg\bin\`

### 🖥️ macOS installatie (via Homebrew)

```bash
brew install ffmpeg
```

### ▶️ Download de video

Gebruik in je terminal:

```bash
ffmpeg -i "JE-INGEKORTE-URL" -codec copy MijnVideo.mp4
```

---

## 🧩 Veelvoorkomende fouten

| Foutmelding                             | Oplossing                                                              |
| --------------------------------------- | ---------------------------------------------------------------------- |
| `HTTP Error 500: Internal Server Error` | Controleer of je URL correct is en eindigt op `format=dash`            |
| `Unsupported URL` in yt-dlp             | Probeer ffmpeg in plaats van yt-dlp                                    |
| Video stopt tijdens downloaden          | Probeer de download opnieuw, of probeer een andere browser voor de URL |

---

## ✅ Voorbeeld van een correcte verkorte URL

```
https://germanywestcentral1-mediap.svc.ms/transform/videomanifest?provider=spo&...&part=index&format=dash
```

---

> 🧠 Tip: Werk je vaak met dit soort video's? Zet deze instructies in een snelkoppeling of script voor gemak.

# 📥 Downloading MS Teams / SharePoint / Stream Videos as a Participant

This guide helps you download videos from Microsoft Teams, SharePoint, or Stream — even if you're **not the organizer** of the meeting. We'll use either `yt-dlp` or `ffmpeg`.

---

## 🔎 Step 1: Get the video manifest URL

1. Open your browser (tested on Chrome, Edge, and Firefox)
2. Log in at [https://portal.office.com](https://portal.office.com)
3. Navigate to the video you want to download (via SharePoint or MS Stream)
4. Press `F12` to open Developer Tools
5. Go to the **Network** tab
6. Use the filter bar and type `videomanifest`
7. Press `F5` to reload the page
8. Start playing the video. A request should appear starting with `videomanifest?provider=...`
9. Right-click on that request → **Copy → Copy link address**
10. Paste the URL into a text editor (like Notepad or VS Code)
11. Find the text: `index&format=dash`
12. **Delete everything after `index&format=dash`**
13. Save the shortened URL (usually around 1,000 characters)

---

## 💾 Method 1: Download using `yt-dlp`

### 🔧 Installation on Windows

1. Download `yt-dlp.exe` from: [https://github.com/yt-dlp/yt-dlp/releases/latest](https://github.com/yt-dlp/yt-dlp/releases/latest)
2. Place it somewhere easy to access, e.g. `C:\yt-dlp\`

### 🖥️ Installation on macOS (using Homebrew)

```bash
brew install yt-dlp
```

### ▶️ Download the video

Open a terminal (Command Prompt as Admin on Windows or Terminal on macOS) and run:

```bash
yt-dlp "YOUR-SHORTENED-URL" -o MyVideo.mp4
```

---

## 🛠️ Method 2: Download using `ffmpeg`

### 🔧 Installation on Windows

1. Download a build from: [https://ffmpeg.org/download.html](https://ffmpeg.org/download.html)
2. Extract it to a location like: `C:\ffmpeg\bin\`

### 🖥️ Installation on macOS (using Homebrew)

```bash
brew install ffmpeg
```

### ▶️ Download the video

Run the following command in your terminal:

```bash
ffmpeg -i "YOUR-SHORTENED-URL" -codec copy MyVideo.mp4
```

---

## 🧩 Common Errors & Fixes

| Error Message                           | Solution                                                                  |
| --------------------------------------- | ------------------------------------------------------------------------- |
| `HTTP Error 500: Internal Server Error` | Check that the URL ends exactly with `format=dash`                        |
| `Unsupported URL` in yt-dlp             | Try downloading with ffmpeg instead                                       |
| Video freezes or fails to download      | Try reloading the page and copying the link again, or use another browser |

---

## ✅ Example of a Valid Shortened URL

```
https://germanywestcentral1-mediap.svc.ms/transform/videomanifest?provider=spo&...&part=index&format=dash
```

---

> 💡 Tip: If you do this often, consider writing a small shell or batch script to automate it.

source: https://www.reddit.com/user/Such-Necessary-9117/

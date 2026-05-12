# Marp Slides Starter

🚀 Progetto starter completo per creare presentazioni professionali con [Marp](https://marp.app/).

## ✨ Features

- 🎨 **Temi personalizzati versionati nel submodule** (Master, Alma, Mobility)
- 🔤 **Font professionali** (IBM Plex Sans/Mono, Sofia Sans)
- 📊 **Chart Vega-Lite** interattivi con fallback PDF
- 📐 **Layout flessibili** (colonne, cover, chapter, all-image)
- 📝 **Esempio completo** con 30+ slide demo
- ⚙️ **Pre-configurato** con VS Code settings e .marprc

## 🚀 Quick Start

### 1. Clona il progetto

```bash
git clone --recurse-submodules https://github.com/danielefadda/marp-slides-starter.git mio-progetto
cd mio-progetto
```

Lo starter resta bloccato alla versione del submodule clonata in quel momento. Aggiorna il puntatore solo quando vuoi adottare una nuova versione stabile del template.

### 2. Installa Marp per VS Code

Installa l'estensione [Marp for VS Code](https://marketplace.visualstudio.com/items?itemName=marp-team.marp-vscode)

### 3. Apri l'esempio

1. Apri `esempio.md` in VS Code
2. Premi **Cmd/Ctrl + K, V** per l'anteprima Marp
3. Esplora le 30+ slide di esempio

### 4. Crea la tua presentazione

Crea un nuovo file `.md` con:

```markdown
---
marp: true
theme: master
header: "Corso XYZ"
footer: "Lezione 01"
paginate: true
---

<!-- _class: cover -->

# Titolo Presentazione

<div class="authors">
  <div class="author-label">docente</div>
  <div class="author-name">Tuo Nome</div>
</div>

---

# Prima Slide

Il tuo contenuto qui...
```

## 📁 Struttura Progetto

```
mio-progetto/
├── .vscode/
│   └── settings.json      # Configurazione VS Code (temi, html)
├── .marprc.yml            # Configurazione per export CLI
├── esempio.md             # 30+ slide demo complete
├── README.md              # Questo file
├── QUICKSTART.md          # Guida rapida dettagliata
└── template/              # Git submodule (temi, font, js)
    ├── themes/
    │   ├── master.scss
  │   ├── alma.scss
  │   └── mobility.scss
    ├── assets/fonts/
    └── js/
```

Se vuoi lavorare sui temi, apri il submodule `template/` come progetto separato. Lo starter resta dedicato a chi scrive presentazioni.

## 🎨 Temi Disponibili

### Master (default)
- **Colori**: Blu #11296b, Rosso #de1f36
- **Font**: IBM Plex Sans/Mono
- **Stile**: Professionale, accademico

### Alma
- **Colori**: Giallo #f4dd4d, Nero
- **Font**: Sofia Sans
- **Stile**: Moderno, vivace

Per cambiare tema:
```yaml
---
theme: alma  # invece di master
---
```

## 📐 Classi Slide Principali

| Classe | Descrizione |
|--------|-------------|
| `cover` | Copertina a 2 colonne con autori |
| `chapter` | Separatore capitolo colorato |
| `title-slide` | Titolo centrato full-screen |
| `all-image` | Immagine background con overlay |
| `columns-2/3/4` | Layout a colonne |
| `small-text` | Testo ridotto per note |

Usa con: `<!-- _class: cover -->`

## 🔧 Export Presentazioni

### Da VS Code
1. Apri il file `.md`
2. **Cmd/Ctrl + K, V** per anteprima
3. Click su **"Export slide deck..."** nell'anteprima
4. Scegli formato: PDF, HTML, PPTX

### Da CLI

Se usi Marp CLI da terminale, puoi esportare anche da riga di comando con i comandi standard di Marp.

## 📊 Chart Vega-Lite (opzionale)

Per aggiungere chart interattivi, vedi **[QUICKSTART.md](QUICKSTART.md)** sezione Chart Vega-Lite.

## 🔄 Aggiornare il Template

Il template è importato come Git submodule ed e` pensato per restare stabile fino a un aggiornamento esplicito.

Per riallinearti alla versione registrata dal repository principale:

```bash
git submodule update --init --recursive
```

Per adottare una nuova versione del template in modo intenzionale:

```bash
cd template
git pull origin main
cd ..
git submodule update --remote template
git add template
git commit -m "Update template to latest version"
```

Per un flusso piu` dettagliato vedi [ADVANCED.md](ADVANCED.md).

## 💡 Tips

⚠️ **Apostrofi**: Usa virgolette doppie nel frontmatter  
```yaml
footer: "Lezione d'uso"  # ✅ OK
```

🔄 **Tema non carica**: Ricarica VS Code  
**Cmd+Shift+P** → "Developer: Reload Window"

📄 **Testa PDF**: Esporta sempre prima di condividere per verificare il risultato

## 📚 Documentazione

- **[QUICKSTART.md](QUICKSTART.md)** - Guida completa passo-passo
- **[ADVANCED.md](ADVANCED.md)** - Workflow avanzato per temi e manutenzione
- **[esempio.md](esempio.md)** - 30+ slide demo con tutti i layout
- **[template/README.md](template/README.md)** - Dettagli tecnici del template

## 🤝 Contribuire

Vuoi migliorare i temi o aggiungere funzionalità al template?

1. Apri il repository [template](template)
2. Lavora sui file in `template/themes/`
3. Segui le indicazioni in [ADVANCED.md](ADVANCED.md)
4. Apri una Pull Request nel repository [marp-template](https://github.com/danielefadda/marp-template)

## 📄 Licenza

**MIT License** - Libero per uso personale e commerciale

## 👨‍💻 Autore

**Daniele Fadda**  
Creato per il corso Data Visualization and Visual Analytics

---

**[Marp](https://marp.app/)** • **[Vega-Lite](https://vega.github.io/vega-lite/)** • **[IBM Plex](https://www.ibm.com/plex/)**

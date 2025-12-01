# Marp Slides - Quick Start

Guida completa per iniziare a creare presentazioni con questo template.

## 🚀 Setup (già fatto!)

Se hai clonato questo repository con `--recurse-submodules`, tutto è già configurato:

✅ VS Code settings (`.vscode/settings.json`)  
✅ Configurazione Marp CLI (`.marprc.yml`)  
✅ Template con temi e font (`template/`)  
✅ File esempio (`esempio.md`)

## 📝 Creare una Nuova Presentazione

### 1. Crea il file markdown

Crea `mia-lezione.md` nella root del progetto:

```markdown
---
marp: true
theme: master
header: "Nome del Corso"
footer: "Lezione 01 • A.A. 2024/2025"
paginate: true
---

<!-- _class: cover -->
<!-- _paginate: skip -->

<div>
  <h1>Titolo Presentazione</h1>
  <h2>Sottotitolo</h2>

  <div class="authors">
    <div class="author-label">docente</div>
    <div class="author-name">Nome Cognome</div>
    <br>
    <div class="author-label">università</div>
    <div class="author-name">Nome Università</div>
  </div>

  <div class="university">
    <strong>Nome Dipartimento</strong><br>
    Corso di Laurea<br>
    Anno Accademico: 2024/2025    
  </div>
</div>

<div class="cover-image">
  <img src="path/to/logo.png" alt="" style="width:60%">
</div>

---

# Prima Slide

Il tuo contenuto qui...

- Punto 1
- Punto 2
- Punto 3

---

# Seconda Slide

Altro contenuto...
```

### 2. Anteprima in VS Code

1. Apri `mia-lezione.md` in VS Code
2. Premi **Cmd/Ctrl + K, V**
3. Vedrai l'anteprima live sulla destra

### 3. Export PDF/HTML

**Da VS Code:**
- Click su **"Export slide deck..."** nell'anteprima
- Scegli il formato desiderato

**Da terminale:**
```bash
npx @marp-team/marp-cli mia-lezione.md -o mia-lezione.pdf
```

## 🎨 Layout e Classi

### Slide di Copertina

```markdown
<!-- _class: cover -->
<!-- _paginate: skip -->

<div>
  <h1>Titolo</h1>
  <div class="authors">...</div>
</div>
<div class="cover-image">
  <img src="..." alt="">
</div>
```

### Slide Capitolo

```markdown
<!-- _class: chapter -->
<!-- _paginate: skip -->

# Nome del Capitolo

Breve descrizione opzionale
```

### Slide Titolo Centrato

```markdown
<!-- _class: title-slide -->
<!-- _paginate: skip -->

# Titolo Grande Centrato
```

### Layout a Due Colonne

```markdown
<div class="columns-2">

<div>

**Colonna Sinistra**
- Contenuto 1
- Contenuto 2

</div>

<div>

**Colonna Destra**
- Contenuto A
- Contenuto B

</div>

</div>
```

### Layout a Tre Colonne

```markdown
<div class="columns-3">
<div>

**Prima**
Contenuto

</div>
<div>

**Seconda**
Contenuto

</div>
<div>

**Terza**
Contenuto

</div>
</div>
```

### Immagine Full-Screen

```markdown
<!-- _class: all-image -->

# Titolo Sovrapposto

![bg](path/to/image.jpg)
```

### Evidenziare Testo

```markdown
Questo è un testo con <mark>evidenziazione</mark> importante.
```

### Testo Piccolo

```markdown
<div class="small-text">

Questo testo apparirà più piccolo, utile per note o disclaimer.

</div>
```

## 📊 Chart Vega-Lite (avanzato)

### 1. Aggiungi script nel frontmatter

```markdown
---
marp: true
theme: master
---

<script src="https://cdn.jsdelivr.net/npm/vega@5.30.0"></script>
<script src="https://cdn.jsdelivr.net/npm/vega-lite@5.21.0"></script>
<script src="https://cdn.jsdelivr.net/npm/vega-embed@6.26.0"></script>
<script src="template/js/vega-insert-chart.js"></script>

<!-- resto della presentazione -->
```

### 2. Crea una specifica Vega-Lite

Crea `charts/vendite.json`:

```json
{
  "$schema": "https://vega.github.io/schema/vega-lite/v5.json",
  "data": {
    "values": [
      {"mese": "Gen", "vendite": 28},
      {"mese": "Feb", "vendite": 55},
      {"mese": "Mar", "vendite": 43}
    ]
  },
  "mark": "bar",
  "encoding": {
    "x": {"field": "mese", "type": "nominal", "axis": {"labelAngle": 0}},
    "y": {"field": "vendite", "type": "quantitative"}
  }
}
```

### 3. Inserisci nella slide

```markdown
# Vendite Mensili

<div class="columns-2">
<div>

**Analisi:**
- Crescita costante
- Picco a Febbraio
- Trend positivo

</div>
<div>

<div class="interactive-chart" id="vendite-chart"></div>
<div class="img-chart">
  <img src="charts/vendite.png" alt="Vendite mensili"/>
</div>

<script>
  insertChart('vendite-chart', './charts/vendite.json', '100%', '300px');
</script>

</div>
</div>
```

**Nota**: Il chart sarà interattivo su HTML, mentre su PDF verrà mostrata l'immagine statica.

## 🎨 Cambiare Tema

Nel frontmatter, cambia `theme`:

```yaml
---
theme: alma  # Giallo/nero, moderno
# oppure
theme: master  # Blu/rosso, classico (default)
---
```

## 💡 Tips & Tricks

### Apostrofi nel Footer

❌ **Errore:**
```yaml
footer: 'Lezione d'uso'  # Causa errore di parsing
```

✅ **Corretto:**
```yaml
footer: "Lezione d'uso"  # Usa virgolette doppie
```

### Nascondere Paginazione

Su una slide specifica:
```markdown
<!-- _paginate: skip -->
```

Globalmente nel frontmatter:
```yaml
paginate: false
```

### Dimensioni Immagini

```markdown
# Diverse dimensioni

![width:300px](image.jpg)
![w:50%](image.jpg)
![height:200px](image.jpg)
```

### Centrare Immagini

```markdown
![center](image.jpg)
![center w:400](image.jpg)
```

### Immagini Background

```markdown
![bg](image.jpg)                    # Full screen
![bg right](image.jpg)              # Metà destra
![bg left:40%](image.jpg)           # 40% sinistra
![bg opacity:0.3](image.jpg)        # Con trasparenza
```

### Tabelle

```markdown
| Colonna 1 | Colonna 2 | Colonna 3 |
|-----------|:---------:|----------:|
| Sinistra  | Centro    | Destra    |
| A         | B         | C         |
```

### Note Speaker (non visibili su slide)

```markdown
<!--
Queste note sono visibili solo in modalità presenter.
Usa per promemoria o dettagli extra.
-->
```

## 🔄 Aggiornare il Template

Quando ci sono nuove versioni del template:

```bash
git submodule update --remote template
git add template
git commit -m "Update template to latest version"
```

## 🐛 Troubleshooting

### Il tema non carica

1. Ricarica VS Code: **Cmd+Shift+P** → "Developer: Reload Window"
2. Verifica che il path in `.vscode/settings.json` sia corretto
3. Controlla che `template/` esista e contenga `themes/`

### L'anteprima non si aggiorna

- Salva il file (Cmd/Ctrl + S)
- Chiudi e riapri l'anteprima (Cmd/Ctrl + K, V)

### Errore "Theme not found"

Verifica il frontmatter:
```yaml
theme: master  # Non "Master" o "theme: master.scss"
```

### Export PDF non funziona

Installa Chromium o Chrome se richiesto:
```bash
npx @marp-team/marp-cli --version
# Seguire le istruzioni per installare il browser
```

## 📚 Prossimi Passi

1. **Esplora**: Apri `esempio.md` per vedere tutti i layout disponibili
2. **Sperimenta**: Modifica `esempio.md` per provare le varie classi
3. **Crea**: Inizia la tua prima presentazione!

## 🔗 Risorse Utili

- [Documentazione Marp](https://marp.app/)
- [Marpit Markdown](https://marpit.marp.app/markdown)
- [Vega-Lite Examples](https://vega.github.io/vega-lite/examples/)
- [Markdown Guide](https://www.markdownguide.org/)

## 📦 Repository

- **Template themes/fonts**: [marp-template](https://github.com/danielefadda/marp-template)
- **Questo starter**: [marp-slides-starter](https://github.com/danielefadda/marp-slides-starter)

---

**Domande?** Consulta il [README.md](README.md) o la [documentazione Marp](https://marp.app/)

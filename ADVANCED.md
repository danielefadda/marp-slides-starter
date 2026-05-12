# Advanced Workflow

Questa guida e` per chi vuole fare un uso avanzato dello starter o lavorare sui temi nel submodule `template/`.

## Obiettivo

Lo starter deve restare stabile per chi scrive presentazioni. Il submodule `template` contiene temi, font e utility ed e` il posto giusto per chi sviluppa o modifica l'aspetto grafico.

## Flusso consigliato

1. Clona il repository con i submodule.
2. Usa lo starter per creare la presentazione.
3. Apri `template/` separatamente solo se devi lavorare sui temi.
4. Aggiorna il puntatore del submodule nello starter solo quando vuoi pubblicare una nuova versione stabile.

```bash
git clone --recurse-submodules https://github.com/danielefadda/marp-slides-starter.git mio-progetto
cd mio-progetto
```

## Stabilita` dello starter

Per default lo starter resta fermo alla versione del submodule che hai clonato.

Se il submodule e` gia` presente e vuoi solo riallinearlo allo stato registrato dal repository principale:

```bash
git submodule update --init --recursive
```

Se invece vuoi aggiornare esplicitamente il submodule all'ultima versione disponibile nel suo remoto:

```bash
cd template
git pull origin main
cd ..
git add template
git commit -m "Update template submodule"
```

Usa questo flusso solo quando vuoi adottare davvero la nuova versione del template.

## Lavorare sui temi

1. Apri il repository `template/` in VS Code come progetto separato.
2. Modifica o aggiungi i file SCSS in `template/themes/`.
3. Mantieni la direttiva `@theme` nel file nuovo o modificato.
4. Aggiorna automaticamente la configurazione con il task `Marp: Sync themes from themes/`.
5. Se preferisci, puoi anche modificare manualmente `template/.vscode/settings.json`.

Nel template la lista dei temi viene tenuta sincronizzata in modo conservativo: lo script aggiunge i temi mancanti e non rimuove quelli gia` presenti.

## Creare una presentazione

1. Crea un nuovo file Markdown nella root dello starter.
2. Usa un tema disponibile, per esempio `master`, `alma` o `mobility`.
3. Scrivi il contenuto della presentazione.
4. Esporta o fai preview da VS Code.

## Buone pratiche

- Tieni il lavoro sui temi nel submodule, non nello starter.
- Non aggiornare il submodule senza una ragione precisa.
- Usa `esempio.md` solo come riferimento.
- Mantieni il file `.vscode/settings.json` dello starter semplice e orientato a chi crea slide.
- Aggiorna lo starter solo dopo aver validato il template nel repo `template`.

## Cose da evitare

- Non mescolare manutenzione dei temi e contenuti della presentazione nello stesso repo.
- Non cambiare il puntatore del submodule ad ogni modifica locale.
- Non usare il repository starter come se fosse il posto dove sviluppare temi.

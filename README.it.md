# SRIM 2013 su macOS Apple Silicon

[English](./README.md) | **Italiano**

Guida pratica per eseguire **SRIM 2013** su Mac con chip della **serie M** (M1/M2/M3/M4/M5).

Configurazione verificata con:
- **Sikarugir** (Template `1.0.11`)
- Engine **WS12WineCX24.0.7_7**
- macOS su architettura Apple Silicon (ARM64)

## Obiettivo
Avviare SRIM 2013 in modo stabile su Apple Silicon usando un wrapper Wine a 32-bit.

## Requisiti
- macOS (Apple Silicon)
- Sikarugir (1.0.11)
- Engine: `WS12WineCX24.0.7_7`
- Rosetta 2

> [!NOTE]
> Installazione Sikarugir tramite [homebrew](https://brew.sh/):
> 
> ```bash
> brew upgrade
> brew install --cask Sikarugir-App/sikarugir/sikarugir
> ```
>
> Installazione Rosetta 2:
>
>```bash
>  /usr/sbin/softwareupdate --install-rosetta --agree-to-license
> ```

## Download della repository

```bash
git clone https://github.com/tuo-username/nome-repo.git
cd nome-repo
```

## Impostazione formato decimale
SRIM non gestisce correttamente la virgola come separatore decimale.

1. Apri **Impostazioni di Sistema**.
2. Vai su **Generali > Lingua e zona**.
3. Imposta il formato numerico con separatore decimale `.` (punto).

Esempio corretto: `1,234,567.89` o `1 234 567.89`

## Installazione passo-passo

### 0) Download di SRIM
📥 [Scarica da qui](https://github.com/zosojack/SRIM-2013-Mac-Silicon/releases/latest/download/SRIM-2013-Std.zip) il file .zip, poi vai nella cartella Downloads/ e decomprimilo cliccandoci sopra.

### 1) Creazione del wrapper
1. Apri **Sikarugir Creator**;
2. Clicca Download Template;
3. Sotto 'No engine selected' clicca 'Change' e seleziona l'Engine `WS12WineCX24.0.7_7`;
4. Clicca **Create** e salva l'app con nome (es. `SRIM-2013`) in `/Applications/sikarugir/` (default).
5. Un prompt informa che l'app è stata creata, clicca 'Launch it'.

<img src="./screenshots/engine-selected.png" width="600">

### 2) Importazione di SRIM
1. Nel pannello **Configure**, clicca **Install Software > Copy a Folder Inside**;
2. Seleziona la cartella `SRIM-2013-Std` inclusa in questa repository;
3. Imposta l'eseguibile:

```text
C:/Program Files/SRIM-2013-Std/SRIM.exe
```

<div align="center">
  <table>
    <tr>
      <td align="center">
        <img src="screenshots/install-software.png" width="400" alt="Configurazione Engine">
        <br>
        <em>1. Install Software</em>
      </td>
      <td align="center">
        <img src="screenshots/copy-inside.png" width="400" alt="Winetricks VB6">
        <br>
        <em>2. Copy a Folder Inside</em>
	  </td>
      <td align="center">
        <img src="screenshots/seleziona-eseguibile.png" width="400" alt="Winetricks VB6">
        <br>
        <em>3. Seleziona eseguibile</em>
      </td>
    </tr>
  </table>
</div>

### 3) Setup interno SRIM
In alto, seleziona la tab **Tools** poi clicca su **Command Line (cmd)**. Nel terminale che si apre va digitato _manualmente_:

```bat
cd "C:\Program Files\SRIM-2013-Std\SRIM-Setup"
```
invia, quindi lancia:
```bat
"_SRIM-Setup (Right-Click).bat"
```

Quando compare il messaggio `END of SRIM setup`, chiudi il terminale.

### 4) Librerie aggiuntive
Torna al pannello **configure** e, in basso, clicca su **Winetricks**; nel pannello che si apre cerca `vb6run`, flaggalo, quindi clicca su **Run**, quando avrà terminato, clicca **Close**.

<div align="center">
  <table>
    <tr>
      <td align="center">
        <img src="screenshots/winetricks.png" width="400" alt="Configurazione Engine">
        <br>
        <em>1. Winetricks</em>
      </td>
      <td align="center">
        <img src="screenshots/flagga-vb6run.png" width="400" alt="Winetricks VB6">
        <br>
        <em>2. Flag vb6run e run</em>
      </td>
    </tr>
  </table>
</div>

### 5) Test Run
Cliccando su **Test Run** nel pannello di configurazione verrà lanciato SRIM. Se funziona tutto correttamente, chiudi pure il pannello di configurazione. D'ora in poi potrai lanciare SRIM-2013 come se fosse una normale app.


## Troubleshooting
- Se l'interfaccia risulta troppo piccola:
	- vai su **Tools > Wine Config > Graphics**
	- imposta i DPI a `120`

## Crediti
Ispirato alla [repository originale](https://github.com/antonio-padalino/SRIM-on-Mac) di Antonio Padalino e aggiornato per Apple Silicon/Sikarugir.
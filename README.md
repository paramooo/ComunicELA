<div align="center">
  <img src="imagenes/logo.png" alt="ComunicELA logo" width="160">
  <h1>ComunicELA</h1>
  <p><strong>AAC through gaze estimation and pictographic boards.</strong></p>
  <p>
    <img src="https://img.shields.io/badge/Python-3.10%20%7C%203.11%20%7C%203.12-3776AB?logo=python&logoColor=white" alt="Python 3.10, 3.11 and 3.12">
    <img src="https://img.shields.io/badge/Platform-Windows-0078D4?logo=windows11&logoColor=white" alt="Windows platform">
    <img src="https://img.shields.io/badge/License-GPLv3-3DA639" alt="GPLv3 licensed source code">
  </p>
</div>

## Overview

ComunicELA is an augmentative and alternative communication (AAC) desktop application designed to provide an accessible means of interaction for people with motor or speech impairments. Using a conventional camera, it turns gaze direction and blinking into actions within a visual, pictogram-based interface.

The system combines computer vision with a gaze-estimation model that can be retrained to suit individual needs. It enables navigation through communication boards, concept selection, message composition and speech output through Windows text-to-speech.

The core application runs locally and does not rely on external services. Google Gemini can optionally transform selected words into a natural, grammatically correct sentence before passing it to the speech synthesiser. Communication boards are editable, allowing the vocabulary to be extended or adapted without modifying the source code.

The complete analysis, design, implementation and evaluation of the system are available in the [ComunicELA technical report](ComunicELA.pdf).

<div align="center">
  <img src="imagenes/PantallaTablero.png" alt="ComunicELA pictographic communication board" width="72%">
  <br>
  <sub>Pictographic board used to compose and play messages.</sub>
</div>

## Key features

- Gaze- and blink-based interface control.
- Blink calibration.
- Model retraining for improved user adaptation.
- Sentence composition using pictograms.
- Message playback through Windows text-to-speech.
- Editable communication boards.
- Spanish, Galician and English interfaces and boards.
- Optional sentence correction and conjugation with Google Gemini.

---

## Getting started

### Requirements

- Windows 10 or 11 with Python 3.10/11/12.
- Standard webcam.
- Internet connection and Gemini API key (optional).

### Installation and execution

1. Create and activate a virtual environment from PowerShell in the project directory:

```powershell
python -m venv .venv
.\.venv\Scripts\Activate.ps1
```

2. Install the dependencies:

```powershell
python -m pip install --upgrade pip
python -m pip install -r requirements.txt
```

3. Start the application:

```powershell
python main.py
```

---

## Optional Gemini configuration

ComunicELA can use Google Gemini to convert a sequence of selected words into a more natural sentence before it is spoken. This integration is optional. Without an API key, the rest of the application continues to work normally.

### Obtain an API key

Generate a key in [Google AI Studio](https://aistudio.google.com/app/apikey).

### Configure the key in Windows

1. Open the Windows Start menu and search for **Environment Variables**.
2. Select **Edit the system environment variables**.
3. Select **Environment Variables**.
4. Under **User variables**, select **New**.
5. Enter `GOOGLE_API_KEY` as the variable name.
6. Paste the API key as its value and save the changes.
7. Close and reopen the application.

---

## Customising communication boards

Communication boards are defined in `.xlsx` files.

### Available files

| File | Language |
| --- | --- |
| `tableros/tableros_es_ES.xlsx` | Spanish |
| `tableros/tableros_gal_ES.xlsx` | Galician |
| `tableros/tableros_en_US.xlsx` | English |

Each worksheet represents a separate board. The first worksheet in the workbook is used as the initial board.

### Cell format

Each board cell uses two consecutive spreadsheet columns:

| Column | Content |
| --- | --- |
| First | Pictogram filename. |
| Second | Word or message displayed in the interface. |

The pictogram files shared by all languages are stored in `tableros/pictogramas`.

### Add or replace a pictogram

1. Copy the new image to `tableros/pictogramas`.
2. Open the board file you want to edit.
3. Enter the image filename in the first column of the cell.
4. Enter the visible label in the second column.
5. Save the workbook in `.xlsx` format.

### Links between boards

A cell is interpreted as a link when its label starts with `TAB. `. The complete label must exactly match another worksheet name in the same workbook. For example, `TAB. QUICK` opens the worksheet named `TAB. QUICK`.

> **Recommendation:** include a cell that returns to the first board on every other worksheet.

### Checks before saving

- Keep the initial board as the first worksheet.
- Preserve the two columns assigned to each board cell.
- Make sure image filenames include their extension and exactly match the files stored in the pictogram directory.
- Keep every `TAB. ...` link synchronised with its target worksheet name.

---

## Awards and recognition

- **Premio al Mejor TFG Aplicado** – Facultad de Informática, Universidade da Coruña (2025).  
- **Mención de Honor en los Premios CREAIMPACTO** – Uno de los tres mejores proyectos de España en la categoría Salud (2025).  
- **2º Premio al Mejor Trabajo de Fin de Grado** – Asociación Española para la Inteligencia Artificial (AEPIA) (2025).  
- **Premio al Mejor Trabajo de Fin de Estudios en Emprendimiento** – Categoría Ciencias de la Salud, Universidade da Coruña (2025).  
- **Premio ao Mellor Traballo Universitario con Licenza Libre** - GPUL, XVIII edición (2025).
- **Premio TalentPRO 2026** -  Categoría de Nuevas Tecnologías (2026)

---

## Media coverage

- [LinkedIn - Introducing ComunicELA](https://www.linkedin.com/posts/pabloparamotelle_introducing-comunicela-comunicela-activity-7253848414939955202-dNCy?utm_source=social_share_send&utm_medium=member_desktop_web&rcm=ACoAAByHYYkB_E_HDtRnYXUh-XtJ0k-h_0mzfnQ)
- [Fundación Universidade da Coruña - Carlota Vázquez e Pablo Páramo reciben o Décimo Premio ao mellor TFG aplicado 2023/24 durante a FepeFIC](https://www.fundacion.udc.es/noticia.asp?id=914&idioma=GA)
- [El Ideal Gallego - Un estudiante de la UDC, entre los tres mejores de España en los Premios CREAIMPACTO 2025](https://www.elidealgallego.com/articulo/a-coruna/estudiante-udc-entre-tres-mejores-espana-premios-creaimpacto-2025-5349103)  
- [El Ideal Gallego - Pablo Páramo | “La idea es que todos los pacientes con ELA puedan descargar el código, utilizarlo e incluso mejorarlo”](https://www.elidealgallego.com/articulo/a-coruna/pablo-paramo-idea-todos-pacientes-ela-puedan-descargar-codigo-utilizarlo-e-incluso-mejorarlo-5351524)  
- [UDC - Un estudante da UDC, entre os tres mellores de España nos Premios CREAIMPACTO 2025](https://www.udc.es/novas/Un-estudante-da-UDC-entre-os-tres-mellores-de-Espana-nos-Premios-CREAIMPACTO-2025/?fbclid=IwY2xjawLPagNleHRuA2FlbQIxMQABHmoErZkbHRHc8se3bh5jEwb2b_TUPh_Z2HtHwwYRcrfFSh6WLGRryYHJBKlq_aem_HIMF6ydyiBnKz8q-T7Z2Vw)  
- [Fundación UDC - Un estudiante de la UDC, entre los tres mejores de España en los Premios CREAIMPACTO 2025](https://www.fundacion.udc.es/site_noticia.asp?id=949&idioma=ES)
- [ABC - Un trabajo de fin de grado de la UDC sienta las bases para mejorar la comunicación de pacientes con ELA](https://www.abc.es/espana/galicia/trabajo-fin-grado-udc-sienta-bases-mejorar-20250701134827-nt.html?ref=https%3A%2F%2Fwww.google.com%2F)
- [El Español / Quincemil - Un estudiante de la Universidade da Coruña, entre los mejores de los Premios CREAIMPACTO](https://www.elespanol.com/quincemil/cultura/educacion/20250630/estudiante-universidade-da-coruna-mejores-premios-creaimpacto/1003743827602_0.html)  
- [La Opinión de A Coruña - Un alumno de la UDC, galardonado en Creaimpacto](https://www.laopinioncoruna.es/coruna/2025/06/30/alumno-udc-galardonado-creaimpacto-119226674.html)
- [Onda Cero - Podcast de Ciencia de Onda Cero en colaboración con la UDC](https://amp-ondacero-es.cdn.ampproject.org/c/s/amp.ondacero.es/emisoras/galicia/coruna/mas-de-uno/ciencia/udciencia-01072025_20250704686780d777c93072586743e6.html) 
- [Código Cero - Os Premios CreaImpacto recoñecen ao estudante Pablo Páramo (UDC) polo proxecto ComunicELA](https://codigocero.com/Os-Premios-CreaImpacto-reconecen-ao-estudante-Pablo-Paramo-UDC-polo-proxecto)  
- [CODDII - Un estudiante de Informática de la UDC, entre los tres mejores de España en los Premios CREAIMPACTO 2025](https://coddii.org/un-estudiante-de-informatica-la-udc-entre-los-tres-mejores-de-espana-en-los-premios-creaimpacto-2025)  
- [UDC - Acto de entrega dos Premios de Emprendemento da Universidade da Coruña no marco de UDC TALENTO](https://udc.es/gl/novas/Acto-de-entrega-dos-Premios-de-Emprendemento-da-Universidade-da-Coruna-no-marco-de-UDC-TALENTO/)
- [ABC - Los premios TalentPRO reconocen los cinco mejores trabajos universitarios de entre 500 propuestas de 65 universidades españolas](https://www.abc.es/sociedad/pulsera-detecta-crisis-epilepticas-scape-room-desinformacion-20260626141415-nt.html)
- [UDC - O Traballo de Fin de Grao do estudante da #UDC Pablo Páramo Telle sobre comunicación asistida en pacientes con #ELA foi recoñecido cunha mención de honra nos Premios CREAIMPACTO 2025](https://www.instagram.com/p/DLhhr-msgI6/?igsh=MWZjczkzODA3aDlzbQ==)
- [GPUL - XVIII edición do Premio ao TFG Libre](https://gpul.org/novas/2025/premio-tfg/)
- [ABC - Valeria González, Pablo Páramo, Marta Villegas, Manuel Alexander Fustamante y Leire Ochoaerrarte han sido galardonados en su tercera edición](https://www.abc.es/sociedad/premios-talentpro-vocento-u4impact-imagenes-20260626134511-ga.html)
- [UDC - O estudante da UDC Pablo Páramo Telle gaña o Premio TalentPRO 2026 na categoría de Novas Tecnoloxías](https://www.udc.gal/en/novas/O-estudante-da-UDC-Pablo-Paramo-Telle-gana-o-Premio-TalentPRO-2026-na-categoria-de-Novas-Tecnoloxias/)


---

## Licences and attribution

### Source code

The ComunicELA source code is distributed under the [GNU General Public License v3.0](LICENSE).

### Intellectual property registration

ComunicELA is registered as a computer program under registration entry `03/2025/362`. The Universidade da Coruña holds the exploitation rights.

### ARASAAC pictograms

Author: Sergio Palao · Source: [ARASAAC](https://arasaac.org/) · Licence: [CC BY-NC-SA 4.0](https://creativecommons.org/licenses/by-nc-sa/4.0/deed.en) · Owner: Government of Aragon, Spain.

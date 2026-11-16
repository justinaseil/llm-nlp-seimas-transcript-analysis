# Kalbos modelių taikymas Lietuvos Respublikos Seimo stenogramų analizei (2016–2020 ir 2020–2024 kadencijos)

Vilniaus universiteto Matematikos ir informatikos fakulteto, Duomenų mokslo studijų programos projektas (2026).

**Autoriai:** Justina Seiliūnaitė, Arnas Kazanavičius, Naglis Bražėnas
**Darbo vadovas:** Asist. dr. Andrius Buteikis

Pilnas darbas: [Atsisiųsti kursinį darbą (PDF)](https://github.com/justinaseil/llm-nlp-seimas-transcript-analysis/raw/refs/heads/main/docs/Kalbos_modeliu%CC%A8_taikymas_G13_kursinis.pdf)

## Apie projektą

Projekto tikslas – pritaikyti ir palyginti kalbos modelius, kurie leidžia Seimo posėdžių stenogramas:

1. Klasifikuoti į pagrindines temas (LitLatBERT – be papildomo mokymo ir papildomai apmokytas);
2. Išskirti svarbiausias frazes kiekvienai temai (TF–IDF, YAKE, KeyBERT);
3. Įvertinti emocinį toną (frazių kontekstai verčiami į anglų kalbą; VADER ir BERT).

ir palyginti 2016–2020 bei 2020–2024 m. kadencijas.

### Pagrindiniai rezultatai

- Papildomai apmokytas LitLatBERT tiksliausiai klasifikavo stenogramas į temas.
- TF–IDF ir YAKE pateikė lengviau interpretuojamas svarbiausias frazes.
- VADER geriausiai atspindėjo neutralų politinės kalbos pobūdį.
- Abiejose kadencijose daugiausia dėmesio skirta teisės, vidaus ir socialinės politikos klausimams; skirtumai išryškėjo ekonomikos ir energetikos temose. Svarbiausios frazės dažniausiai aptartos pozityvaus tono kontekstuose, skirtumai tarp kadencijų minimalūs.

## Analizės eiga

| Darbo dalis | Ataskaitos skyrius | Kas daroma |
|---|---|---|
| Pradinė analizė | 3.1 | Aprašomoji statistika, žodžių debesys, aktyviausi kalbėtojai |
| Duomenų apdorojimas | 3.2 | Skaidymas į skyrelius, teksto valymas (regex, stop words) |
| Neapmokyto modelio tekstų klasifikavimas | 4.1 | LitLatBERT embeddingai + kosinusinis panašumas su temų aprašais |
| Apmokyto modelio tekstų klasifikavimas | 4.2 | Klasterizavimas, temų žymėjimas, LitLatBERT fine-tuning, visų tekstų klasifikavimas |
| Svarbiausios frazės | 5 | TF–IDF, YAKE, KeyBERT |
| Kontekstų išgavimas | 6.1 | Sakinių konteksto išgavimas frazėms |
| Vertimas | 6.2 | Kontekstų vertimas į anglų kalbą |
| Sentimentai | 6.3–6.5 | VADER ir BERT sentimentai, metodų palyginimas |

## Naudoti modeliai

| Užduotis | Modelis / metodas |
|---|---|
| Klasifikavimas, KeyBERT embeddingai | `EMBEDDIA/litlat-bert` |
| Klasterizavimas | TF–IDF + K-vidurkiai |
| Svarbiausios frazės | TF–IDF, YAKE, KeyBERT |
| Vertimas LT → EN | `Helsinki-NLP/opus-mt-tc-big-lt-en` |
| Sentimentai | VADER (NLTK), `phanerozoic/BERT-Sentiment-Classifier` |
| Lemos (KeyBERT frazėms) | spaCy `lt_core_news_sm` |

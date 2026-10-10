# Zdalna zawartość MenuLab

Pliki są zgodne z obecnym parserem MenuLab (schema 1). Mod nadal korzysta tymczasowo z repozytorium Waypoints-Plus; te pliki są przygotowane do uzupełnienia przed przełączeniem źródła.

## Struktura

```text
remote/
├── links.json
├── about-ad.json
└── Assets/
    └── Banner.png   # dodaj własną grafikę
```

## links.json

Podmień przykładowe adresy `https://example.com/...` na docelowe linki HTTPS:

- `modrinth` — przycisk Modrinth.
- `curseForge` — przycisk CurseForge; zachowaj wielkie F w nazwie pola.
- `coffee` — przycisk Donate.
- `discord` — przyciski Discord w About i Support. Pusty tekst wyłącza oba przyciski.
- `source` — pole zgodności nadal wymagane przez parser. MenuLab nie pokazuje przycisku Source.

Pozostaw `schema: 1`. Poza opcjonalnym `discord` pola są wymagane; pozostałe adresy nie mogą być puste.

## about-ad.json

- `id` — identyfikator bannera; litery ASCII, cyfry, kropki, myślniki i podkreślenia, maksymalnie 64 znaki.
- `title.en`, `title.pl`, `text.en`, `text.pl` — tytuł i opis pokazywane zamiast grafiki, gdy nie jest dostępna.
- `targetUrl` — adres HTTPS otwierany po kliknięciu bannera.
- `imageUrl` — bezpośredni adres HTTPS do PNG/JPEG. Na razie pusty; uzupełnij po dodaniu grafiki.

Po przesłaniu `remote/Assets/Banner.png` użyj:
```text
https://raw.githubusercontent.com/Slogerski/Slogerski/main/remote/Assets/Banner.png
```

Grafika: maksymalnie 512 KiB, szerokość 16–2048 px, wysokość 16–1024 px i łącznie maksymalnie 294912 pikseli. Przykładowy format: 1112×248 px.
Dozwolone hosty grafiki: `raw.githubusercontent.com`, `cdn.modrinth.com`, `media.forgecdn.net`.
JSON: maksymalnie 32 KiB na plik.

## Adresy do podłączenia w modzie

```text
Baza:   https://raw.githubusercontent.com/Slogerski/Slogerski/main/remote/
Linki:  https://raw.githubusercontent.com/Slogerski/Slogerski/main/remote/links.json
Banner: https://raw.githubusercontent.com/Slogerski/Slogerski/main/remote/about-ad.json
```

About pobiera linki i dane bannera, Support tylko linki. Pozostałe zakładki nie uruchamiają pobierania.
Cache pozostaje w `config/menulab/cache/remote/` w instancji Minecrafta. Poprawne dane są ponownie sprawdzane po 10 minutach, z obsługą ETag i ponowień po błędach.

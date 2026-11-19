# Reto Náhuatl

A browser word game for learning Eastern Huasteca Nahuatl. Hear a word spoken by a native speaker, pick its meaning, and fill in a map of Mexico one state at a time. Get 32 in a row to complete the map.

It is the Nahuatl counterpart of *An Dúshlán*, an Irish-language game in the Fréamh project, and uses the same engine.

**Play:** open `index.html`, or `reto-nahuatl.html` directly. On GitHub Pages the game is at the site's root URL.

> **Status: prototype.** The recordings are used for testing only, pending permission from their owners (see [Audio and permissions](#audio-and-permissions)). The Spanish meanings are a draft awaiting a native-speaker check.

## How to play

- Each turn plays a Nahuatl word and shows it on screen, with two possible meanings.
- Pick the right one within 5 seconds. Use the mouse, a tap, the ↑ / ↓ keys, or 1 / 2.
- Each correct answer fills the next state on the map in green. A wrong answer or running out of time ends the run.
- 32 correct answers in a row (one for each of Mexico's 31 states and Mexico City) completes the map.

**Options on the start screen**

- **Order of the states:** alphabetical, north to south, south to north, population largest first, or population smallest first. The population orders show each state's 2020 census figure as it fills.
- **Answers:** Spanish or English. The choice is remembered on the device.
- **Modes:** *Solo*, or *Multijugador* for 2 to 6 players taking turns over 1 to 5 rounds. Scores add up across rounds, and a perfect run of 32 scores double (64).

No word repeats within a run. When a run ends, the correct answer is shown in both Spanish and English.

## Files

| File | What it holds |
| --- | --- |
| `index.html` | Front page. Redirects to the game. |
| `reto-nahuatl.html` | The game: screens, styles and logic. |
| `diccionario-nahuatl.js` | The word list. Each entry is `word: [Spanish, English, audio file]`. |
| `mapa-mexico.js` | The 32 state outlines as SVG paths, 2020 populations, and the fill orders. |

There is no build step and no dependencies. It is plain HTML and JavaScript and runs from any static host or straight from the folder.

## Running it locally

Download the folder and double-click `reto-nahuatl.html`. Keep all the files together. The audio streams from the dictionary's server, so sound needs an internet connection.

## Publishing on GitHub Pages

1. Push these files to the root of the repository.
2. In the repository, go to **Settings → Pages**.
3. Under **Build and deployment**, choose **Deploy from a branch**, pick `main` and `/ (root)`, and save.

The game appears at `https://<username>.github.io/<repository>/` within a minute or two.

## Editing the word list

Words live in `diccionario-nahuatl.js`:

```js
"tecolotl": ["tecolote, búho", "owl", "tecolotl.05088.a01.mp3"],
```

- The key is the word exactly as shown on screen, including vowel-length marks (macrons).
- Then the Spanish meaning, the English meaning, and the recording's file name on the dictionary server (`AUDIO_BASE`).
- Every meaning must be different from every other, so a wrong answer can never match the right one.

The game needs well over 32 words so runs don't repeat. It currently has 79.

When you change a script file, raise the `?v=` number on its `<script>` tag in `reto-nahuatl.html` (for example `?v=1` to `?v=2`) so browsers load the new copy and not a cached one.

## Language variety and spelling

The words are **Eastern Huasteca Nahuatl**, spoken in Veracruz, Hidalgo and San Luis Potosí. They use the IDIEZ spelling, which follows the ACK standard (Andrews, Campbell, Karttunen) and writes *hu* and *cu* where the SEP standard writes *w* and *k*. Long vowels are marked with macrons, as in the source dictionary.

## Sources and credits

- **Words, meanings and recordings:** [Online Nahuatl Dictionary](https://nahuatl.wired-humanities.org/), ed. Stephanie Wood (Wired Humanities Projects, College of Education, University of Oregon, 2000 to present), including modern Huasteca Nahuatl entries from the Instituto de Docencia e Investigación Etnológica de Zacatecas (IDIEZ).
- **Voices:** Eduardo de la Cruz Cruz, Ofelia Cruz Morales, and other Eastern Huasteca Nahuatl speakers recorded for the dictionary. Some recordings do not name their speaker yet.
- **Map:** [Natural Earth](https://www.naturalearthdata.com/) admin-1 boundaries (public domain), simplified for screen use.
- **Population:** INEGI, *Censo de Población y Vivienda 2020* (national total 126,014,024).
- **Spanish meanings:** draft translations from the dictionary's English and Nahuatl definitions, to be checked by a native speaker.

## Audio and permissions

The recordings belong to the Online Nahuatl Dictionary (© University of Oregon). The site has no open licence, so the game uses them for testing only while permission is requested. Before any public release:

- [ ] Written permission to use the recordings, and to host copies alongside the game
- [ ] Names for the speakers of the unattributed recordings, for the credits
- [ ] A native-speaker check of the word list and the Spanish meanings

## Licence

Not yet decided. The code is separate from the dictionary content and recordings, which are covered by the permissions above.

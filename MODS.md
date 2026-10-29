# Mody Claude Code w tym repo

Konfiguracja 9 modów z przewodnika „9 Claude Mods you need to try” (RoboNuggets).
Mody działają w terminalu Claude Code i w zakładce Code aplikacji desktopowej
(Claude Code 2.1.287+). Nie rysują się w sesjach w chmurze ani w rozszerzeniu VS Code.

> Mod nie jest w piaskownicy: działa z Twoimi uprawnieniami (pliki, procesy, sieć).
> Wszystkie poniższe pochodzą z publicznych repozytoriów wymienionych w tabeli.

## Co jest już skonfigurowane

`.claude/settings.json` deklaruje marketplace'y i włącza mody na poziomie projektu.
Po otwarciu repo w Claude Code i zaufaniu folderowi Claude Code zaproponuje ich instalację.

| #  | Mod              | Plugin                                       | Jak użyć                                   |
|----|------------------|----------------------------------------------|--------------------------------------------|
| 01 | Savvy Progress   | `savvy-progress@claude-kit`                  | `/agents-info` otwiera panel subagentów    |
| 02 | Claude Skins     | `skins@hellosverre-mods`                     | `/skin dracula`, `/skin noir`              |
| 03 | You Should Know  | `cc-plugin-you-should-know@builtin`          | działa sam, notki nad promptem             |
| 04 | Filetree         | `filetree@claude-code-filetree`              | najpierw `/tui fullscreen`, min. 110 kolumn |
| 05 | Cache Tax        | `cache-tax@claude-code-mods`                 | `/keepwarm 90m`, `/keepwarm off`           |
| 06 | Blast Radius     | `blast-radius@gtksklep-mods`                 | sam wstrzymuje `rm -rf`, force push itp.   |
| 07 | Reflect          | `reflect-mod@claude-reflect-marketplace`     | pasek „Save to CLAUDE.md” po poprawce      |
| 08 | Terminal Browser | `terminal-browser@terminal-browser`          | `/browser`                                 |
| 09 | Replay Theater   | `replay-theater@gtksklep-mods`               | `r` lub `/replay` po turze z edycjami      |

Źródła: [claude-kit](https://github.com/JohnnyVizz/claude-kit),
[claude-skins](https://github.com/hellosverre/claude-skins),
[claude-code-filetree](https://github.com/data-goblin/claude-code-filetree),
[claude-code-mods](https://github.com/karanb192/claude-code-mods) / [cache-tax](https://github.com/karanb192/cache-tax),
[claude-reflect](https://github.com/BayramAnnakov/claude-reflect),
[terminal-browser](https://github.com/zenbu-labs/terminal-browser),
[claude-code-playground](https://github.com/anthropics/claude-code-playground/tree/main/claude-code/mods).

## Jednorazowe kroki na Twoim komputerze

**Blast Radius i Replay Theater** (06, 09) to przykładowe mody Anthropic, skopiowane do
`.claude/mods/` (licencja Apache-2.0 w `.claude/mods/LICENSE`). Marketplace z folderu wymaga
ścieżki bezwzględnej, więc nie da się go zapisać we wspólnym `settings.json`. Uruchom raz
w katalogu głównym repo (zapisuje do `.claude/settings.local.json`, który nie trafia do gita):

```bash
claude plugin marketplace add ./.claude/mods --scope local
```

```bash
claude plugin install blast-radius@gtksklep-mods --scope local
```

```bash
claude plugin install replay-theater@gtksklep-mods --scope local
```

Blast Radius potrzebuje `bash`, `git`, `find` i `du`; na Windows uruchamiaj Claude Code z Git Bash.

**Terminal Browser** (08) działa tylko na macOS i Linuksie, w terminalu z grafiką kitty.
Potrzebuje też własnego programu:

```bash
brew install terminal-browser
```

albo bez Homebrew:

```bash
curl -fsSL https://terminal-browser.sh/install | bash
```

**Ustawienia modów.** Savvy Progress, Filetree i Terminal Browser mają opcjonalne ustawienia;
`/plugin configure <plugin>` w Claude Code pokazuje je i pozwala zmienić.

Po instalacji zacznij nową sesję albo wpisz `/reload-plugins`.

## Wyłączanie

Pojedynczy mod tylko dla siebie:

```bash
claude plugin disable cache-tax@claude-code-mods --scope local
```

Dla wszystkich: usuń wpis z `enabledPlugins` w `.claude/settings.json`.
Blast Radius i Replay Theater: `claude plugin uninstall <plugin>@gtksklep-mods --scope local`.

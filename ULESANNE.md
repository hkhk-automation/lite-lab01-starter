# Lab 01 — Esimene playbook · ülesanne

📘 **Loeng:** <https://hkhk-automation.github.io/devops-lite/week01/lecture/>
📖 **Praktikum:** <https://hkhk-automation.github.io/devops-lite/week01/lab/>
🏠 **Kodune õpe ja kodutöö:** <https://hkhk-automation.github.io/devops-lite/week01/homework/>

See fail on ülesande kirjeldus, seda ei pea muutma. Oma töö dokumenteerid failis **`README.md`**, mis on mall: täida see praktikumi dokumenteerimise osas. Kõik failid lähevad repo juurkausta. Playbookid ehitad ise.

---

## Enne alustamist: töökeskkond

Klassiarvuti on Windows, töö käib kooli Proxmoxi klastris sulle antud kolmes VM-is. **vm1 on sinu control node**, sealt haldad kõiki kolme.

1. Juhendajalt: vm1, vm2, vm3 IP-d, kasutajanimi, parool.
2. Ühendu vm1-ga: VS Code → Remote-SSH → *Connect to Host* → `<kasutaja>@<vm1-ip>` või PowerShellis `ssh <kasutaja>@<vm1-ip>`.
3. vm1-s kontrolli: `hostname`, `git --version`, `ansible --version`.
4. GitHubis loo fine-grained token (org `hkhk-automation`, *Contents: Read and write*), sest `git push` ei võta kontoparooli.
5. Klooni see repo vm1 kodukausta: `cd ~ && git clone <selle repo URL>`.

Täpsemalt: praktikumi osa **0 · Valmisolek**.

---

## Mis peab lõpuks repos olema

**Klassis (praktikum):**

| Fail | Kust |
|---|---|
| `halb.sh` | A2 |
| `inventory.ini` | A3, B |
| `bootstrap.yml` | A4, B |
| `logid/teine_jooks.txt` | A5 |
| `logid/kolm_masinat.txt` | B |
| `README.md` täidetud (nimi, soovitud olek, käivituskäsk, masinad, drift, peegeldus) | Dokumenteerimine |

**Kodus (kodune õpe ja kodutöö):**

| Fail | Kust |
|---|---|
| `markmed.md`, `vastused.md` | I, H6, IV |
| `admin.yml` + `logid/admin_teine_jooks.txt` | H1 |
| `hardening.yml` + `logid/hardening_teine_jooks.txt` | H2 |
| `baas.yml` + `logid/baas_teine_jooks.txt` | H3 |
| `raport.yml` + `raportid/` | H4 |
| `cron.yml` + `logid/cron_teine_jooks.txt` | H5 |
| `logid/drift_check.txt` | H6 |
| `oma/*.yml` + `oma/README.md` | III |
| `boonus.yml` | IV, vabatahtlik |

---

## Kontrollnimekiri (Issues ja tahvel)

Juhendaja avab kohtumise alguses su repo **Issues** alla kõik ülesanded eraldi issue'dena (sildid `klassitöö` ja `kodutöö`). Samad kaardid on kursuse tahvlil (GitHubi org `hkhk-automation` → Projects), vaade **Minu tööd**. Igas issue's on juhendi link, mida teha ja millal on valmis. Sule issue, kui osa on tehtud.

Kui jääd kinni: **Issues → New issue → Vajan abi**. Juhendaja saab teate.

---

## Kontroll (roheline = valmis)

Igal push'il jookseb automaatne kontroll, tulemust näed **Actions** vahelehel. Kokku 100 punkti: klassitöö 45, kodutöö 55.

| Kontroll | Punkte |
|---|---|
| K1–K5: klassi failid, README täidetud, süntaks, päris moodulid, `changed=0` ühel ja kolmel masinal | 45 |
| H1 `admin.yml`, H2 `hardening.yml` | 20 |
| H3 `baas.yml`, H4 `raport.yml`, H5–H6 `cron.yml` + drift | 21 |
| Märkmed, vastused (≥400 sõna), oma töö | 14 |

Tõendi salvestad nii:

```bash
ansible-playbook -i inventory.ini <fail>.yml | tee logid/<fail>_teine_jooks.txt
```

`changed=0` tuleb ainult siis, kui kõik on juba paigas. Seega salvesta **teine** jooks.

---

## Esitamine

```bash
git add . && git commit -m "Lab 01"
git push
```

Tähtaeg on kirjas Classroom 50-s. Pushida võid mitu korda, arvesse läheb viimane.

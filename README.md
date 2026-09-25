# Lab 01 — Esimene playbook

📘 **Loeng:** <https://hkhk-automation.github.io/devops-lite/week01/lecture/>
📖 **Praktikum:** <https://hkhk-automation.github.io/devops-lite/week01/lab/>
🏠 **Kodune õpe ja kodutöö:** <https://hkhk-automation.github.io/devops-lite/week01/homework/>

See on sinu esitusrepo. Kõik failid lähevad repo juurkausta. Playbookid ehitad ise.

---

## Mis peab lõpuks repos olema

**Klassis (praktikum):**

| Fail | Kust |
|---|---|
| `halb.sh`, `parem.sh` | A2 |
| `inventory.ini` | A3, B |
| `bootstrap.yml` | A4, B |
| `logid/teine_jooks.txt` | A5 |
| `logid/kolm_masinat.txt` | B |
| `README.md` (soovitud olek, käivituskäsk, drift, peegeldus) | Dokumenteerimine |

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

## Kontroll (roheline = valmis)

Igal push'il jookseb automaatne kontroll, tulemust näed **Actions** vahelehel. Kokku 100 punkti: klassitöö 45, kodutöö 55.

| Kontroll | Punkte |
|---|---|
| K1–K5: klassi failid, süntaks, päris moodulid, `changed=0` ühel ja kolmel masinal | 45 |
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

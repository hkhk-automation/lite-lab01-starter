# Lab 01 — Esimene playbook · ülesanne

**Loeng:** <https://hkhk-automation.github.io/devops-lite/week01/lecture/>
**Praktikum:** <https://hkhk-automation.github.io/devops-lite/week01/lab/>
**Kodune õpe ja kodutöö:** <https://hkhk-automation.github.io/devops-lite/week01/homework/>

See fail on ülesande kirjeldus, seda ei pea muutma. Oma töö dokumenteerid failis **`README.md`**, mis on mall: täida see praktikumi dokumenteerimise osas. Kõik failid lähevad repo juurkausta. Playbookid ehitad ise.

---

## Enne alustamist: töökeskkond

Töö käib kooli Proxmoxi klastris sulle antud kolmes **AlmaLinux 9** VM-is. **vm1 on sinu control node**, sealt haldad kõiki kolme.

1. Juhendajalt: vm1, vm2, vm3 IP-d, kasutajanimi, parool.
2. Ühendu vm1-ga (VS Code Remote-SSH või PowerShellis `ssh <kasutaja>@<vm1-ip>`). Vaheta kõigis kolmes masinas parool (`passwd`, igal pool sama uus parool) ja anna neile nimed (`sudo hostnamectl set-hostname vm1`, `vm2`, `vm3`).
3. Paigalda tööriistad: `sudo dnf install -y git ansible-core` ja `ansible-galaxy collection install ansible.posix:1.5.4`.
4. Loo vm1-s SSH-võti (`ssh-keygen -t ed25519`) ja lisa avalik võti GitHubi: **Settings → SSH and GPG keys**.
5. Klooni see repo SSH-ga: **Code → SSH** → `git clone git@github.com:hkhk-automation/<sinu-repo>.git`.

Täpselt samm-sammult: [Töökeskkond](https://hkhk-automation.github.io/devops-lite/keskkond/).

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

## Kontrollnimekiri (Issues ja projekt)

Su repo **Issues** all on selle nädala issue **Lab 01 · Esimene playbook**. Selles on kõik osad (klassitöö ja kodutöö) märkeruutudena koos juhendi linkidega. Märgi ruut, kui osa on tehtud. Kui kõik on tehtud, sulge issue. Sama issue on kursuse projektis (GitHubi org `hkhk-automation` → **Projects** → *ITS-25 Automatiseerimine*), vaade **Minu tööd**.

Kui jääd kinni: **Issues → New issue → Vajan abi**. Juhendaja saab teate.

---

## Kontroll

Igal push'il jookseb automaatne kontroll **Autograde** (vahekaart **Actions**). Loeb **punktisumma**, mitte värv: kuni kodutöö pole tehtud, on kontroll punane, ja see on ootuspärane. Kokku 100 punkti: klassitöö 45, kodutöö 55.

| Kontroll | Punkte |
|---|---|
| K1–K5: klassi failid, README täidetud, süntaks, päris moodulid, `changed=0` ühel ja kolmel masinal | 45 |
| H1 `admin.yml`, H2 `hardening.yml` | 20 |
| H3 `baas.yml`, H4 `raport.yml`, H5–H6 `cron.yml` + drift | 21 |
| Märkmed, vastused (≥150 sõna), oma töö | 14 |

Tõendi salvestad nii (failinimed on tabelis ülal):

```bash
ansible-playbook bootstrap.yml | tee logid/teine_jooks.txt          # A5
ansible-playbook bootstrap.yml --limit veeb | tee logid/kolm_masinat.txt   # B
ansible-playbook admin.yml | tee logid/admin_teine_jooks.txt        # H1, teised samamoodi
```

`changed=0` tuleb ainult siis, kui kõik on juba paigas. Seega salvesta **teine** jooks.

---

## Esitamine

```bash
git add . && git commit -m "Lab 01"
git push
```

Tähtaeg on kirjas Classroom 50-s. Pushida võid mitu korda, arvesse läheb viimane.

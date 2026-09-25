# Lab 01 — Esimene playbook

📖 **Praktikum:** <https://hkhk-automation.github.io/devops-lite/week01/lab/>
📘 **Loeng:** <https://hkhk-automation.github.io/devops-lite/week01/lecture/>

See on sinu esitusrepo. Kõik failid lähevad repo juurkausta. Playbooki ehitad laboris ise, task-haaval.

---

## Mis peab lõpuks repos olema

| Fail | Kust | Klassis / kodus |
|---|---|---|
| `halb.sh`, `parem.sh` | Osa 2 | klassis |
| `inventory.ini` | Osad 3 ja 9 | klassis |
| `bootstrap.yml` | Osad 4 ja 10 | klassis |
| `logid/teine_jooks.txt` | Osa 5 | klassis |
| `logid/kolm_masinat.txt` | Osa 10 | klassis |
| `README.md` | Osa 11: soovitud olek, käivituskäsk, mis triivis | klassis |
| `admin.yml` + `logid/admin_teine_jooks.txt` | Kodutöö 1 | kodus |
| `oma/*.yml` + `oma/README.md` | Kodutöö 2 | kodus |
| `vastused.md` | Kodutöö 3 | kodus |

`README.md` kirjutad Osa 11-s üle, see juhend jääb labori lehele alles.

---

## Kontroll (roheline = valmis)

Igal push'il jookseb automaatne kontroll, tulemust näed **Actions** vahelehel.

1. Klassi failid on olemas.
2. `bootstrap.yml` süntaks on korras.
3. `bootstrap.yml` kasutab päris mooduleid (`user`, `package`, `copy`, `service`), mitte `command`/`shell`-i.
4. `logid/teine_jooks.txt` näitab `changed=0`.
5. `logid/kolm_masinat.txt`: kolm masinat, kõigil `changed=0`, ükski pole `unreachable` ega `failed`.
6. Kodutöö: `admin.yml` süntaks on korras ja teine jooks on `changed=0`.
7. Kodutöö: `oma/` playbook + README ja `vastused.md` on olemas.

Tõendi salvestad nii, et jooksutad playbooki ja suunad väljundi faili, näiteks:

```bash
ansible-playbook -i inventory.ini bootstrap.yml | tee logid/teine_jooks.txt
```

`changed=0` tuleb ainult siis, kui kõik on juba paigas. Seega salvesta **teine** jooks, mitte esimene.

---

## Esitamine

```bash
git add . && git commit -m "Lab 01"
git push
```

Tähtaeg on kirjas Classroom 50-s. Pushida võid mitu korda, arvesse läheb viimane.

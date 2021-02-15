# Ansible Playbooks für Contao

Dieses Paket ist für die Reihe Contao mit Ansible verwalten.

Mehr dazu unter https://kirsten-roschanski.de/contao-kochbuch

### Motivation
Inzwischen habe ich gute 50 produktive Contao Installationen und dazu noch mal eine dreistellige Zahl an Installationen für Entwicklungen. Diese sollen/müssen regelmäßig aktualisiert werden, damit ich zum einen alle Sicherheitsupdates eingespielt bekommen und zum anderen damit ich die Weiterentwicklung mitbekomme. Darum habe ich nach einer automatischen Lösung gesucht , die meine tägliche Arbeit erleichtert und sich dabei in meinen bestehenden Workflow integriert. Daher setze ich auf Ansible, das ich bereits seit längerem dazu nutzen meine Server zu warten, pflegen und sogar zu installieren.

Nun also will und kann ich damit auch meine Contao-Installationen aufsetzen. Dang der Contao-Console und des Contao-Manager ist dieses ganz leicht zu realisieren gewesen. Schau es dir aber gerne selber an.

#### Voraussetzung
Voraussetzung ist, das man mit SSH auf den Server kommt und auf dem Server Python zur Verfügung steht. Auf dem Rechner muss Ansible installiert sein.


## Update von Contao
### Was macht dieses Playbook?

Es werden 5 Tasks abgearbeitet:
- Es wird die aktuelle Version ausgelesen und ausgegeben.
- Der Contao-Manager wird auf die aktuelle Version aktualisiert. Ausgabe über Update oder das er bereits aktuell ist.
- Contao-Installation wird aktualisiert.
- Die Datenbank wird aktualisiert (ohne löschen).
- Die nun aktuelle Version wird ausgelesen und ausgegeben.

### Wie führe ich das nun aus?

```bash
ansible-playbook -i customers/website-001.yml update_base.yml
```

## Basisinstallation von Contao
### Was macht dieses Playbook?

Es werden 19 Tasks abgearbeitet:

- Es wird geprüft ob bereits eine Installation vorhanden ist, eine composer.json existiert. Danach werden einige Schritte übersprungen.
- Das Verzeichnis web wird angelegt, falls es noch nicht existiert.
- Das Verzeichnis contao-manager wird angelegt, falls es noch nicht existiert.
- Die Konfiguration des Contao-Manager wird aus dem Template angelegt.
- Das Passwort für dem Contao-Manager-Benutzer wird lokal verschlüsselt.
- Das verschlüsselte Passwort für dem Contao-Manager-Benutzer wird in eine Variable geschrieben.
- Das Admin Benutzerkonto des Contao-Manager wird aus dem Template angelegt.
- Der Contao-Manager wird her runtergeladen.
- Die Composer Datei wird aus dem Template angelegt.
- Die Contao-Installation wird durchgeführt.
- Das Verzeichnis config wird angelegt, falls es noch nicht existiert. (ehemals app/config)
- Die Contao-Datenbank-Konfiguration wird aus dem Template angelegt.
- Das Passwort für das Install-Tool wird lokal verschlüsselt.
- Das verschlüsselte Passwort für das Install-Tool wird in eine Variable geschrieben.
- Die Contao-Konfig wird aus dem Template angelegt.
- Das Install-Tool wird aus Sicherheitsgründen gesperrt.
- In der Konfigurationsdatei hinterlegte Contao-Module werden installiert.
- Die Datenbank wird aktualisiert/angelegt.
- Für Contao ab 4.10 können wir auch die Backend-Benutzer direkt anlegen.

### Wie führe ich das nun aus?

```bash
ansible-playbook -i customers/website-001.yml install_base.yml
```


## Datenbank Backup
### Was macht dieses Playbook?

Es werden nur 2 Tasks abgearbeitet:

- Es wird ein Datenbankbackup in system/tmp erstellt.
- Der Datenbankdump wird auf die lokale Festplatte kopiert.


### Wie führe ich das nun aus?

```bash
ansible-playbook -i customers/website-001.yml datenbank_backup.yml
```


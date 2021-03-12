# Ansible Playbooks für Contao

Dieses Paket ist für die Reihe Contao mit Ansible verwalten.

Mehr dazu unter https://kirsten-roschanski.de/contao-kochbuch

### Motivation
Inzwischen habe ich gute 50 produktive Contao Installationen und dazu noch mal eine dreistellige Zahl an Installationen für Entwicklungen. Diese sollen/müssen regelmäßig aktualisiert werden, damit ich zum einen alle Sicherheitsupdates eingespielt bekommen und zum anderen damit ich die Weiterentwicklung mitbekomme. Darum habe ich nach einer automatischen Lösung gesucht , die meine tägliche Arbeit erleichtert und sich dabei in meinen bestehenden Workflow integriert. Daher setze ich auf Ansible, das ich bereits seit längerem dazu nutzen meine Server zu warten, pflegen und sogar zu installieren.

Nun also will und kann ich damit auch meine Contao-Installationen aufsetzen. Dang der Contao-Console und des Contao-Manager ist dieses ganz leicht zu realisieren gewesen. Schau es dir aber gerne selber an.

#### Voraussetzung
Voraussetzung ist, das man mit SSH auf den Server kommt und auf dem Server Python zur Verfügung steht. Auf dem Rechner muss Ansible installiert sein.

### Wie führe ich das nun aus?

```bash
ansible-playbook -i customers/INVENTORY.yml PLAYBOOK.yml
```

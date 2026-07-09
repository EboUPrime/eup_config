# eup_configurator

Leichtgewichtige YAML-Konfigurationsverwaltung mit verschachteltem
Dot-Notation-Zugriff (`config.mailer.host.value`).

## Installation

Lokal aus dem Projektordner:

```bash
pip install .
```

Für Entwicklung (editable install):

```bash
pip install -e .
```

## Verwendung

```python
from eup_configurator import Configurator

# Standardmäßig wird 'application.yaml' im Paketverzeichnis erwartet.
# Alternativ: eigenen Ordner angeben.
config = Configurator(config_file="application.yaml", base_dir="/pfad/zu/deinem/projekt")

# Verschachtelter Zugriff
print(config.mailer.host.value)

# Zugriff per Dot-Notation-Pfad
print(config.get_value("mailer.password"))

# Wert setzen und speichern
config.set_nested("mailer.password", "neues-passwort")

# Datenbankpfad ermitteln (Schlüssel unterhalb von 'database')
db_path = config.get_database_path("path")

# Konfiguration neu laden
config.reload()

# Alle bekannten Pfade auflisten
print(config.list_elements())
```


## Lizenz

MIT

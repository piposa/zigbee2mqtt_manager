Zigbee2MQTT Manager 1.1.0: lokale Korrekturen
===========================================

Patch:
  local-patches/zigbee2mqtt_manager-local-1.1.0-20261019.patch

Dieser kumulative Patch enthaelt alle lokalen Anpassungen fuer den
unveraenderten Integrationsstand 1.1.0:
  - Issue #5: ruhige Kartenaktualisierung ohne Scrollsprung
  - Offline-Anzeige: Z2M-Availability ist massgeblich
  - Issue #7: deaktivierte Geraete getrennt von Offline-Geraeten
  - Uebersicht: eigener HA-Sensor fuer deaktivierte Geraete

Die Kachel "Deaktiviert" im Dashboard "Z2M Manger" verwendet
sensor.womo_zigbee2mqtt_manager_zigbee2mqtt_deaktivierte_gerate.
Die Dashboard-Konfiguration ist in HA gespeichert und nicht Teil dieses
Integrationspatches.
Eine exportierte Vorlage liegt im Fork unter examples/z2m-manger-dashboard.json.

Der Fork-Quellcode enthaelt diese Aenderungen bereits. Den Patch nur auf den
unveraenderten Upstream-Stand 1.1.0 anwenden, nicht nochmals auf diesen Fork.

Die derzeitige Installation enthaelt den Patch bereits. Nach einer
Neuinstallation des unveraenderten Stands 1.1.0 als Benutzer pi:

  cd /opt/haos-docker
  sudo patch --dry-run --batch --forward -p0 < local-patches/zigbee2mqtt_manager-local-1.1.0-20261019.patch
  sudo patch --batch --forward -p0 < local-patches/zigbee2mqtt_manager-local-1.1.0-20261019.patch
  sudo docker restart homeassistant

HA braucht mehrere Minuten zum Starten; danach die Dashboard-Seite neu laden.
Den kumulativen Patch nicht zusammen mit den aelteren Einzelpatches fuer
Issue #5 oder Offline-Status anwenden. Bei einem fehlgeschlagenen Dry-Run
nicht --force verwenden, sondern den Patch fuer die neue Version anpassen.

Sicherungen der Originaldateien:
  config/zigbee2mqtt-manager-card.js.pre-issue5-20261019
  config/zigbee2mqtt-manager-init.py.pre-issue5-20261019
  config/zigbee2mqtt-manager-manager.py.pre-offline-20261019
  config/zigbee2mqtt-manager-sensor.py.pre-overview-20261019
  config/zigbee2mqtt-manager-strings.json.pre-overview-20261019
  config/zigbee2mqtt-manager-translations-de.json.pre-overview-20261019
  config/zigbee2mqtt-manager-translations-en.json.pre-overview-20261019
  config/zigbee2mqtt-manager-translations-nl.json.pre-overview-20261019

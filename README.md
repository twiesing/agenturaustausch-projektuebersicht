# Agentur-Tipps: Kundenprojekte im Überblick behalten

## Inhaltsverzeichnis

- [Uptime-Monitoring mit Gatus](#uptime-monitoring-mit-gatus)
    - [Use-Case](#use-case)
    - [Beschreibung](#beschreibung)
    - [Screenshots](#screenshots)
    - [Code-Beispiele](#code-beispiele)
- [Benachrichtigungen über Pushover](#benachrichtigungen-über-pushover)
    - [Use-Case](#use-case-1)
    - [Beschreibung](#beschreibung-1)
    - [Screenshots](#screenshots-1)
- [Website-Änderungen mit Changedetection erkennen](#website-änderungen-mit-changedetection-erkennen)
    - [Use-Case](#use-case-2)
    - [Beschreibung](#beschreibung-2)
    - [Screenshots](#screenshots-2)
- [Analytics mit Umami](#analytics-mit-umami)
    - [Use-Case](#use-case-3)
    - [Beschreibung](#beschreibung-3)
    - [Screenshots](#screenshots-3)
- [Automatisierungen mit n8n](#automatisierungen-mit-n8n)
    - [Use-Case](#use-case-4)
    - [Beschreibung](#beschreibung-4)
    - [Screenshots](#screenshots-4)
- [DNS-Records verwalten mit DNSControl](#dns-records-verwalten-mit-dnscontrol)
    - [Use-Case](#use-case-5)
    - [Beschreibung](#beschreibung-5)
    - [Code-Beispiele](#code-beispiele-1)
- [Cronjob-Monitoring mit Healthchecks](#cronjob-monitoring-mit-healthchecks)
    - [Use-Case](#use-case-6)
    - [Beschreibung](#beschreibung-6)
    - [Screenshots](#screenshots-5)
- [WP-CLI für WordPress-Management](#wp-cli-für-wordpress-management)
    - [Use-Case](#use-case-7)
    - [Beschreibung](#beschreibung-7)
    - [Code-Beispiele](#code-beispiele-2)
- [Passwörter verwalten mit Vaultwarden](#passwörter-verwalten-mit-vaultwarden)
    - [Use-Case](#use-case-8)
    - [Beschreibung](#beschreibung-8)
    - [Screenshots](#screenshots-6)

## Uptime-Monitoring mit Gatus

https://github.com/TwiN/gatus

### Use-Case

- Monitoring internen Dienste und aller Kundenwebsites im Intervall von 1 Minute.
- Prüfung, ob die Seite a) Status-Code 200 liefert, b) das gewünschte Suchwort gefunden wurde, c) die Auslieferung in unter 1000ms erfolgt und d) ob das Zeritifkat noch länger als 7 Tage gültig ist.
- Benachrichtigungen über Probleme per [Pushover](https://pushover.net/).
- Pflege der Konfiguration als YAML über ein Git-Repo mit automatischer Aktualisierung.

### Beschreibung

- **Konfiguration per YAML** – Überwachte Endpunkte lassen sich deklarativ definieren.
- **Vielfältige Checks** – HTTP (inkl. Keyword-Suche), JSON-Response, TCP, DNS-Records, TLS-Zertifikate u.v.m.
- **Flexible Benachrichtigungen** – Alerts via E-Mail, Slack, Webhook und viele weitere Integrationen.
- **Kundentaugliche Statusseiten** – Eigene, moderne Dashboards zur Darstellung der Verfügbarkeit.
- **Geplante Wartungsfenster** – Temporäre Downtimes ausblenden und Hinweise vermeiden.

### Screenshots

![Gatus Overview](/assets/gatus/overview.png)

![Gatus Overview](/assets/gatus/details.png)

### Code-Beispiele
```yaml
endpoints:
  - name: "hueske.digital: WordPress"
    url: "https://hueske.digital/?nocache"
    group: customers
    interval: 60s
    alerts:
      - type: pushover
    conditions:
      - "[STATUS] == 200"
      - "[RESPONSE_TIME] < 1000"
      - "[BODY] == pat(*Unsere Websites folgen 6 einfachen, aber wichtigen Prinzipien*)"
      - "[CERTIFICATE_EXPIRATION] > 168h"
```

## Benachrichtigungen über Pushover

https://pushover.net/

### Use-Case

- Jegliche Monitorings (Cronjobs, Website-Uptime, Changedetection) möchte ich  in einer App haben.
- Pro Tool eigener Channel, den ich mit meinem Bruder teile, um mich im Fall der Fälle nicht alleine um alles kümmern zu müssen.
- Verschiedene Prioritäts-Einstellungen je Channel bzw. Alert konfiguriert.

### Beschreibung

- Plattformübergreifend – Push-Nachrichten für iOS, Android, Desktop & Smartwatches.
- Einfache Integration – per HTTP-API oder individuelle E-Mail-Adresse.
- Channels & Gruppen – Nachrichten an Gruppen oder öffentliche Channels verteilen.
- Günstiges Modell – einmalig 5,99 € pro Plattform, kein Abo.
- Flexible Prioritäten – inkl. „Emergency“-Modus mit wiederholten Alerts.

### Screenshots

![Channel](/assets/pushover/channel.png)

## Website-Änderungen mit Changedetection erkennen

https://github.com/dgtlmoon/changedetection.io

### Use-Case

- Änderungen auf Websites überwachen, z. B. Release neuer PHP-Versionen oder Änderungen im Impressum von Dienstleistern.
- Check, ob extern eingebundene Inhalte problemlos laden oder APIs wie gewünscht antworten.

### Beschreibung

- Website-Änderungen im Blick – tracke jede Änderung auf beliebigen Webseiten.
- Selektives Monitoring – beobachte nur bestimmte Bereiche per CSS/XPath-Filter.
- Diff-Vergleich – Änderungen im Vorher-/Nachher-Vergleich darstellen. 
- Flexible Benachrichtigungen – E-Mail, Discord, Slack, Telegram & mehr. 
- Zeitgesteuerte Checks – automatische Prüfintervalle nach Wunsch.

### Screenshots

![Overview](/assets/changedetection/overview.png)

![Filter](/assets/changedetection/filter.png)

## Analytics mit Umami

### Use-Case

- Kunden wollen keinen nervigen Cookie-Banner auf ihren Websites.
- Einfaches, datenschutzkonformes & cookieless Besucher-Analytics, das jeder versteht.
- Share-Links für Kunden-Dashboards.

### Beschreibung

- Datenschutzfreundlich & Open Source – cookieless, DSGVO-ready & frei verfügbar.  
- Umfangreiche Website-Analysen – Seitenaufrufe, Referrer & Besucherquellen im Blick.  
- Echtzeit-Tracking – aktive Nutzer & Top-Seiten sofort sichtbar.  
- Individuelle Events – Klicks, Conversions & Formulare frei definieren.  
- Starke Filterfunktionen – Daten nach Segmenten & Bedingungen auswerten.  

### Screenshots

![Overview](/assets/umami/overview.png)

![Overview](/assets/umami/details.png)

## Automatisierungen mit n8n

### Use-Case

- Nutzung der [mittwald-API per Workflow-Automatisierung](https://github.com/wiesinghilker/n8n-nodes-mittwald): Monatlich alle Contributor-Ausgangsrechnungen (Stripe) per Mail versenden oder direkt ins Buchhaltungstool importieren.
- Formulare in WordPress per Webhook an N8N schicken und dort weiter verarbeiten, z. B. Eintragung in Newsletter-Listen von [Listmonk](https://github.com/knadh/listmonk).
- DIY-AI-Agents für Website-Chats.

### Beschreibung

- Visueller Workflow-Editor – per Drag & Drop komplexe Abläufe erstellen.  
- 400+ Integrationen – verbinde Apps, Dienste & APIs flexibel miteinander (darunter auch [mittwald](https://github.com/wiesinghilker/n8n-nodes-mittwald)).  
- Echtzeit-Automatisierung – Workflows reagieren sofort auf Events & Trigger (z. B. Webhooks oder Cron).  
- Mit Code erweiterbar – JavaScript oder Python direkt in Workflows nutzen.  
- AI-Integration – n8n verbinden mit OpenAI & [mittwald AI-Hosting](https://www.mittwald.de/mstudio/ai-hosting) für smarte Automatisierung.

### Screenshots

![Workflow](/assets/n8n/workflow.png)

## DNS-Records verwalten mit DNSControl

https://github.com/StackExchange/dnscontrol

### Use-Case

- Meine Domains nutzen alle Cloudflare DNS, da diese für verschiedenste Services (darunter auch mein [Lieblings-Proxy "caddy"](https://github.com/caddyserver/caddy)) eine gute API-Unterstützung bieten.
- DNS-Einträge, über alle Provider hinweg, liegen allesamt zentral in einem Git-Repository.
- Jeder Merge-Request prüft die gemachten Änderungen und überspielt diese nach Merge in den Cloudflare DNS-Server.
- Einfaches "Copy & Paste" beim Hinzufügen neuer Domains dank Templates und gute Nachvollziehbarkeit dank Git-Features wie Historie.

### Beschreibung

- **Infrastructure as Code für DNS** – Verwalte DNS-Zonen via einer deklarativ und kompiliere sie für viele DNS-Provider bzw. Registrar-Anbieter.  
- **Multi-Provider-Support** – Unterstützung für über 35 DNS-Provider (z. B. Cloudflare, Route 53, Hetzner, BIND) sowie diverse Registrar-Services.  
- **DNS-Compiler-Ansatz** – DNS-Konfigurationen werden in DNSControl konvertiert (IR), dann als Zone-Updates zu verschiedenen Anbietern übertragen.  
- **Import-/Export-Tools** – `convertzone`-Command konvertiert BIND-Zonefiles oder OctoDNS-Configs in die DNSControl-DSL (dnsconfig.js) für einfache Migrationen.  
- **CI/CD-freundlich & mehrfach plattformtauglich** – Lauffähig via Go-Binaries, Docker oder Homebrew; ideal kombinierbar mit GitHub Actions für Previews und automatische Deployments.  

### Code-Beispiele

`global.js`:
```javascript
var MITTWALD_SERVER01 = [
    ALIAS("@", "server01.meinedomain.de."),
    CNAME("*", "server01.meinedomain.de."),
]

var MITTWALD_MAILSERVER = [
    MX("@", 10, "mx1.agenturserver.de."),
    MX("@", 10, "mx2.agenturserver.de."),
    MX("@", 20, "mx3.agenturserver.de."),
    MX("@", 50, "mx4.agenturserver.de."),
    CNAME("autoconfig", "autoconfig.agenturserver.de."),
    SRV("_autodiscover._tcp", 0, 0, 443, "autodiscover.agenturserver.de."),
]

var MITTWALD_MAILSERVER_SPF = [
    TXT("agenturserver._domainkey", "\"v=DKIM1; k=rsa; p=MIGfMA0GCSqGSIb3DQEBAQUAA4GNADCBiQKBgQC3U8kqa4SiUlO5WBe8DwVPhhLNooNNe8VLEJ+9PbDHVeEw0O6mY2O6AvcqbnSeBO5Ac9Ix0RQzxe9krqSgWDR84IvROW/u4kMxELn+Q+Jy2QXYASbVWnYs4T6p1yIqBEgRfWDFnNtmRDvNFCAcRv2VkA0ykkRMq3u9E6FZTLMnGQIDAQAB\""),
    TXT("agenturserver2048._domainkey", "\"v=DKIM1; k=rsa; p=MIIBIjANBgkqhkiG9w0BAQEFAAOCAQ8AMIIBCgKCAQEA1BM9Prf00dhyP0i/fH0/k01oMSafqpl7biZMPjz/zxRJn+1YgSdeXt84NR3wZ5w+HWhtR27p1IEjchu179VOOyZ+xOte4owM+6FO7BVGnr/5IAlmRnC4fMvSeePdwun9fBExfkOroxwdEM4Y1+BqaSnpMT2xV6a2hRklymFzDkNQdmKrtm2AWSqg44iiMt3bu\" \"EtZ0/y5SSBNd41zJYsp7UdPO2fgzF+C5gJrpyKhTWGB9ELLK83cd2Vdb8N+CC1Oh62eybgsMt2iBmxgnYAwp1LdTuxxNFYT2gEOFGL5KE01WM0L0+KALhwDQBcGcSC7Eup855OI/v8F4YDTZ3NCgQIDAQAB\""),
    TXT("@", "\"v=spf1 include:agenturserver.de -all\""),
]
```

`examplede.js`:
```javascript
var DSP_CLOUDFLARE = NewDnsProvider("cloudflare");
var REG_NONE = NewRegistrar("none");

D("example.de", REG_NONE,
	DnsProvider(DSP_CLOUDFLARE),
	DefaultTTL(1),
	MITTWALD_SERVER01,
	MITTWALD_MAILSERVER,
	MITTWALD_MAILSERVER_SPF,
  CNAME("sentry", "example.sentry.io."),
	TXT("_dmarc", "\"v=DMARC1;  p=none; rua=mailto:823u823u82u823u32ijkadjskdn@dmarc-reports.cloudflare.net\""),
);
```
**Änderungen überprüfen:**

`dnscontrol preview`

**Änderungen ausrollen:**

`dnscontrol push`

```
CONCURRENTLY gathering 3 zone(s)
SERIALLY gathering 0 zone(s)
Waiting for concurrent gathering(s) to complete...DONE
******************** Domain: mittwald.de
******************** Domain: coolerblog.de
******************** Domain: example.de
1 correction (cloudflare)
#1: ± MODIFY example.de CNAME (sentry.example.de. proxy=false ttl=1) -> (example.sentry.io. proxy=false ttl=1) id=f5cb3824e77a3df8ebja0bddc266e68
SUCCESS!
Done. 1 correction.
```

## Cronjob-Monitoring mit Healthchecks

https://github.com/healthchecks/healthchecks

### Use-Case

- Warenwirtschafts-Exporte oder Backup-Cronjobs können einfach gemonitored werden.
- Erfolgt kein "Ping" in gewissem Zeitraum, dann bekomme ich via Pushover eine Benachrichtigung.
- Laufzeit und Ausgabe (z. B. Exit-Code oder Log) kann direkt mit werden.

### Beschreibung

- **Cron-Job-Monitoring** – Dead Man’s Switch: erwartet regelmäßige Pings, sonst Alarm.  
- **Flexibles Timing** – frei einstellbare Intervalle, Grace-Zeiten & Cron-Ausdrücke.  
- **Einsehbare Laufzeit** – langlaufende Prozesse sofort erkennen.
- **Integrationen** – Benachrichtigungen via E-Mail, Slack, Discord, Pushover, Webhooks u.v.m.  
- **Open Source** – Quelloffen, selbst hostbar oder als gehosteter Dienst nutzbar.  

### Screenshots

![Check](/assets/healthchecks/check.png)

## WP-CLI für WordPress-Management

https://wp-cli.org/de/

### Use-Case

- Zentrale Verwaltung einzelner bzw. aller WordPress-Instanzen über mehrere Hostinganbieter hinweg.
- Ausspielen von Konfigurationsänderungen, Updates oder Installation neuer Plugins (haben ein globales von unserer Agentur) mit einem Befehl.

### Beschreibung

- **Vollständige Admin-Alternative per CLI** – WP-CLI ermöglicht nahezu alle Aufgaben des WordPress-Backends, darunter Installation, Updates, Plugins, Themes, User-Management, Datenbankoperationen u.v.m. 
- **Ideal für Automatisierung & Bulk-Operationen** – Perfekt zu verwenden in Shell-Skripten oder CI/CD-Pipelines (z. B. GitHub Actions), um zeitsparende und wiederholbare Workflows zu erstellen. 
- **Multisite- und Core-Verwaltung** – Unterstützt WP-Core-Operationen (Installation, Updates), sowie Multisite-Management über entsprechende Befehle (`wp core`, `wp network`, `wp site`).  
- **Effizient & erweiterbar** – Klar strukturierte Parent- und Subcommands mit Tab-Completion (für Bash & Zsh), konsistentes Verhalten, Composability durch Pipes und CLI-Caching.
- **Einfacher Einstieg & flexible Installation** – Installation via Phar, Homebrew, Composer oder Docker möglich; danach standardisiert über `wp --info` installierbar und ausführbar.

### Code-Beispiele

`wp-cli.yml`:
```yaml
# Sites
@erlebnispark:
   ssh: tobias@hueske.digital@a-abc50@ssh.espelkamp.project.host
   path: /home/p-asdf12/html/erlebnispark-blocksy
@codefryx:
   ssh: tobias@hueske.digital@a-abc137@ssh.espelkamp.project.host
   path: /home/p-asdf99/html/wordpress-blocksy

# Alias
@all:
   - @erlebnispark
   - @codefryx
```

Plugin installieren:

`wp @all plugin install --force https://meinecooledomain.de/plugins/tools/asdf.zip`

Debug-Mode deaktivieren:

`wp @all config set WP_DEBUG false`

Datenbank exportieren:

`wp @all db export`


## Passwörter verwalten mit Vaultwarden

https://github.com/dani-garcia/vaultwarden

### Use-Case

- Passwörter sicher speichern und dank Organisationen einfach mit Geschäftspartnern teilen.
- Auto-Fill im Browser dank Chrome Extension.
- Zugangsdaten an Kunden per selbstlöschender Notiz Funktion an meine Kunden versenden.

### Beschreibung

- End-to-End-Verschlüsselung – volle Datenkontrolle beim Self-Hosting.  
- Kompatibel mit allen Bitwarden-Clients – Apps, Browser-Add-ons & Web-Vault.  
- Organisationen & Sharing – inkl. Collections, Rollen, Passwort-Teilen.  
- 2FA-Support – TOTP, WebAuthn, YubiKey, Duo u. v. m.  
- Alle Features kostenlos – keine versteckten Premium-Optionen.  

### Screenshots

![App](/assets/vaultwarden/app.png)

![Send](/assets/vaultwarden/send.png)

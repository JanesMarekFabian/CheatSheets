# IT Essentials Cheat Sheet
## Die wichtigsten Befehle und Tools für IT-Profis

### 🐧 Linux/Unix Befehle

#### Dateisystem & Navigation
```bash
# Navigation
cd /path/to/directory          # Verzeichnis wechseln
pwd                          # Aktuelles Verzeichnis anzeigen
ls -la                       # Dateien detailliert anzeigen
tree -L 2                    # Verzeichnisstruktur als Baum
find /path -name "*.txt"     # Dateien suchen
locate filename              # Dateien schnell finden

# Dateimanagement
cp -r source dest           # Verzeichnisse kopieren
mv oldname newname          # Umbenennen/Verschieben
rm -rf directory            # Verzeichnis löschen (VORSICHT!)
chmod 755 file              # Berechtigungen setzen
chown user:group file       # Besitzer ändern
```

#### System-Informationen
```bash
# System-Status
top                         # Prozesse in Echtzeit
htop                        # Verbesserte Prozess-Ansicht
ps aux                      # Alle laufenden Prozesse
df -h                       # Festplattenplatz
free -h                     # Arbeitsspeicher
uname -a                    # System-Informationen
lscpu                       # CPU-Informationen
```

#### Netzwerk
```bash
# Verbindungen
ping google.com             # Verbindung testen
nslookup domain.com         # DNS-Auflösung
dig domain.com              # DNS-Details
netstat -tulpn              # Offene Ports
ss -tulpn                   # Moderne Alternative zu netstat
curl -I website.com         # HTTP-Header
wget URL                    # Datei herunterladen
```

#### Text-Verarbeitung
```bash
# Dateien bearbeiten
vim file.txt                # Vim Editor
nano file.txt               # Nano Editor
cat file.txt                # Datei anzeigen
head -n 10 file.txt         # Erste 10 Zeilen
tail -f logfile.log         # Log-Datei verfolgen
grep "pattern" file.txt     # Text suchen
sed 's/old/new/g' file.txt  # Text ersetzen
awk '{print $1}' file.txt   # Text verarbeiten
```

### 🪟 Windows PowerShell

#### System-Verwaltung
```powershell
# System-Informationen
Get-ComputerInfo            # System-Details
Get-Process                 # Laufende Prozesse
Get-Service                 # Windows Services
Get-EventLog -LogName System # Event Logs
Get-WmiObject -Class Win32_LogicalDisk # Festplatten

# Netzwerk
Test-NetConnection google.com # Verbindung testen
Get-NetAdapter               # Netzwerk-Adapter
Get-NetIPConfiguration       # IP-Konfiguration
Resolve-DnsName google.com   # DNS-Auflösung
```

#### Dateisystem
```powershell
# Navigation
Get-ChildItem               # Dateien auflisten
Set-Location C:\Path        # Verzeichnis wechseln
New-Item -ItemType File     # Datei erstellen
Copy-Item -Recurse          # Verzeichnisse kopieren
Remove-Item -Recurse        # Löschen
```

### 🐳 Docker & Container

#### Container-Management
```bash
# Basis-Befehle
docker run -it ubuntu       # Container starten
docker ps                   # Laufende Container
docker ps -a                # Alle Container
docker images               # Images anzeigen
docker pull image:tag       # Image herunterladen
docker build -t name .      # Image erstellen
docker stop container_id    # Container stoppen
docker rm container_id      # Container löschen
```

#### Docker Compose
```bash
docker-compose up -d        # Services starten
docker-compose down         # Services stoppen
docker-compose logs         # Logs anzeigen
docker-compose exec service bash # In Service einsteigen
```

### 🔧 Git & Version Control

#### Basis-Workflow
```bash
# Repository
git init                    # Neues Repository
git clone URL               # Repository klonen
git remote -v               # Remote-Repositories anzeigen

# Änderungen
git add .                   # Alle Änderungen stagen
git add file.txt            # Spezifische Datei stagen
git commit -m "Message"     # Commit erstellen
git push origin main        # Änderungen pushen
git pull origin main        # Änderungen holen

# Branching
git branch                  # Branches anzeigen
git checkout -b new-branch  # Neuen Branch erstellen
git merge branch-name       # Branch mergen
git rebase main             # Rebase auf main
```

#### Erweiterte Git-Befehle
```bash
# History & Debugging
git log --oneline           # Commit-History
git diff                    # Änderungen anzeigen
git stash                   # Änderungen temporär speichern
git reset --hard HEAD~1     # Letzten Commit rückgängig
git cherry-pick commit-id   # Spezifischen Commit übernehmen
```

### ☁️ Cloud & DevOps

#### AWS CLI
```bash
# EC2
aws ec2 describe-instances  # Instanzen auflisten
aws ec2 start-instances --instance-ids i-1234567890abcdef0
aws ec2 stop-instances --instance-ids i-1234567890abcdef0

# S3
aws s3 ls                   # Buckets auflisten
aws s3 cp file.txt s3://bucket/ # Datei hochladen
aws s3 sync local/ s3://bucket/ # Verzeichnis synchronisieren
```

#### Kubernetes
```bash
# Pod-Management
kubectl get pods            # Pods anzeigen
kubectl describe pod name   # Pod-Details
kubectl logs pod-name       # Pod-Logs
kubectl exec -it pod-name bash # In Pod einsteigen

# Deployment
kubectl apply -f deployment.yaml # Deployment erstellen
kubectl scale deployment name --replicas=3 # Skalieren
kubectl delete deployment name   # Deployment löschen
```

### 🗄️ Datenbanken

#### SQL (MySQL/PostgreSQL)
```sql
-- Basis-Operationen
SELECT * FROM table_name;           -- Daten abrufen
INSERT INTO table VALUES (1, 'text'); -- Daten einfügen
UPDATE table SET column = 'value';    -- Daten aktualisieren
DELETE FROM table WHERE id = 1;       -- Daten löschen

-- Erweiterte Abfragen
SELECT * FROM table WHERE column LIKE '%pattern%';
SELECT COUNT(*) FROM table;
SELECT column, COUNT(*) FROM table GROUP BY column;
JOIN table1 ON table1.id = table2.foreign_id;
```

#### MongoDB
```javascript
// Basis-Operationen
db.collection.find()              // Alle Dokumente
db.collection.findOne()           // Ein Dokument
db.collection.insertOne({...})    // Dokument einfügen
db.collection.updateOne({...})    // Dokument aktualisieren
db.collection.deleteOne({...})    // Dokument löschen

// Erweiterte Abfragen
db.collection.find({field: {$regex: /pattern/}})
db.collection.aggregate([{$group: {_id: "$field", count: {$sum: 1}}}])
```

### 🐍 Python & Entwicklung

#### Package Management
```bash
# pip
pip install package          # Paket installieren
pip install -r requirements.txt # Aus Datei installieren
pip freeze > requirements.txt # Pakete exportieren
pip list                     # Installierte Pakete

# conda
conda create -n env python=3.9 # Umgebung erstellen
conda activate env            # Umgebung aktivieren
conda install package         # Paket installieren
conda env export > environment.yml # Umgebung exportieren
```

#### Virtual Environments
```bash
python -m venv venv          # Virtual Environment erstellen
source venv/bin/activate     # Aktivieren (Linux/Mac)
venv\Scripts\activate        # Aktivieren (Windows)
deactivate                   # Deaktivieren
```

### 🔍 Monitoring & Logging

#### System-Monitoring
```bash
# System-Metriken
iostat -x 1                  # I/O-Statistiken
vmstat 1                     # System-Aktivität
sar -u 1                     # CPU-Nutzung
iotop                       # I/O-Top-Prozesse

# Log-Analyse
journalctl -f                # System-Logs verfolgen
journalctl -u service        # Service-Logs
grep ERROR /var/log/syslog   # Fehler suchen
```

### 🔐 Security & Authentifizierung

#### SSH & Keys
```bash
# SSH-Verbindungen
ssh user@hostname            # SSH-Verbindung
ssh-keygen -t rsa -b 4096    # SSH-Key generieren
ssh-copy-id user@hostname    # Public Key kopieren
ssh -i key.pem user@host     # Mit privatem Key verbinden
```

#### SSL/TLS
```bash
# Zertifikate
openssl req -new -x509 -keyout server.key -out server.crt
openssl x509 -in cert.crt -text -noout # Zertifikat anzeigen
curl -I https://website.com  # SSL-Verbindung testen
```

### 📊 Performance & Profiling

#### CPU & Memory Profiling
```bash
# Performance-Tools
perf top                     # CPU-Profiling
valgrind --tool=memcheck ./program # Memory-Checker
strace -p PID                # System-Calls verfolgen
tcpdump -i eth0              # Netzwerk-Traffic
```

### 🔄 CI/CD & Automation

#### Jenkins/GitHub Actions
```yaml
# GitHub Actions Beispiel
name: CI/CD Pipeline
on: [push, pull_request]
jobs:
  test:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v2
      - name: Run tests
        run: npm test
```

### 📝 Nützliche Tools & Utilities

#### Text-Verarbeitung & Search
```bash
# JSON-Verarbeitung
jq '.field' file.json       # JSON parsen
cat file.json | jq '.[] | select(.status == "active")'

# CSV-Verarbeitung
csvkit --help               # CSV-Tools
in2csv data.xlsx > data.csv # Excel zu CSV
```

#### Network Tools
```bash
# Port-Scanning
nmap -p 80,443 hostname     # Ports scannen
nmap -sP 192.168.1.0/24    # Hosts im Netzwerk finden

# Traffic-Analyse
tcpdump -i any port 80      # HTTP-Traffic
wireshark                   # GUI für Traffic-Analyse
```

---

## 🎯 Quick Reference - Die häufigsten Befehle

### Für System-Administratoren:
1. `top` / `htop` - Prozesse überwachen
2. `df -h` - Festplattenplatz prüfen
3. `systemctl status service` - Service-Status
4. `journalctl -f` - Logs verfolgen
5. `netstat -tulpn` - Offene Ports

### Für Entwickler:
1. `git status` - Git-Status prüfen
2. `docker ps` - Container-Status
3. `kubectl get pods` - Kubernetes-Pods
4. `npm install` / `pip install` - Dependencies
5. `tail -f logfile.log` - Logs verfolgen

### Für DevOps:
1. `docker-compose up -d` - Services starten
2. `kubectl apply -f` - Kubernetes-Manifeste
3. `terraform plan` - Infrastructure-Code
4. `ansible-playbook` - Configuration Management
5. `curl -I` - HTTP-Status prüfen

---

## 📚 Zusätzliche Ressourcen

- **Linux**: `man command` für detaillierte Hilfe
- **Git**: [Git-SCM Book](https://git-scm.com/book)
- **Docker**: [Docker Documentation](https://docs.docker.com/)
- **Kubernetes**: [Kubernetes Documentation](https://kubernetes.io/docs/)

*Dieses Cheat Sheet wird regelmäßig aktualisiert und erweitert.*

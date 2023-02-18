# CI-CD_Project
Hintergrund 
Sie arbeiten seit 3 Monaten bei der Techstarter Cloud Solutions GmbH als Junior DevOps 
und bekommen Ihr erstes Projekt, was Sie selbst bewältigen müssen. Ihre Kollegen 
stehen Ihnen mit Rat und Tat zur Seite, umsetzen müssen Sie es jedoch allein.

Aufgabenüberblick 
Sie müssen zwei CI/CD Pipelines bauen, die Ihnen das komplette Wissen abverlangt. Die 
erste Pipeline soll via github Actions, Terraform und Ansible eine Infrastruktur
bereitstellen. Die zweite Pipeline soll via Jenkins Docker-Images bauen und releasen und 
deployen.

Die IaC-Pipeline soll zwei virtuelle Maschinen via Terraform in Azure bereitstellen und 
mittels Ansible konfigurieren. Beide VMs sollen idealerweise im gleichen Subnet 
arbeiten, via IPv4 öffentlich erreichbar sein und die entsprechenden Standard WebPorts freigeschaltet haben.
1. Virtuelle Maschine soll so nach dem Ausführen der pipeline eine komplette Jenkinsumgebung beinhalten:
     • Azure VM-Typ: Standard_B1s
     • Java
     • Jenkins
     • Nignix als reverse Proxy konfiguriert mit passendem Domainnamen
     o SSL ist nicht notwendig zu automatisieren
     • Docker mit docker-compose
2. Virtuelle Maschine soll so nach dem Ausführen der pipeline eine komplette Webserverumgebung beinhalten:
    • Azure VM-Typ: Standard_B2s
    • Nignix als reverse Proxy mit passendem Domainnamen
    o SSL ist nicht notwendig zu automatisieren
    • Docker mit docker-compose
    • Ein eigener Systembenutzer (bspw. deploy) der die Container starten / stoppen kann
    • (Jenkins Node)
    
Jenkins soll Pipelines für das Frontend und das Backend der Webapp beinhalten. Diese 
Pipelines sollen die entsprechenden Container bauen und in der dockerhub registry 
veröffentlichen. Nachdem release sollen die Container der Application mittels dockercompose 
oder docker direkt aktualisiert werden.
//Tipp: der Jenkins Agent kann auch auf dem Webserver installiert werden, um die Container dort zu starten.
Änderungen am Quellcode sollen automatisch die Pipeline auslösen und ausführen

Akzeptanz Kriterien 
- Änderungen am Terraform-Code aktualisiert automatisch die Infrastruktur via github actions
- Änderungen am Ansible-Code aktualisiert automatisch die Konfiguration der Infrastruktur 
via github actions
- Änderungen am Frontend-Code erstellt, released und deployed automatisch das Frondend 
via Jenkinspipeline
- Änderungen am Backend-Code erstellt, released und deployed automatisch das Backend via 
Jenkinspipelin

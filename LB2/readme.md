## Idee
Ursprüngich, hatte ich die Idee, eine Website zu erstellen, welche den Inhalt einer SQL Datenbanck darstellt. Da dies aber schon welche machen wollten, habe ich mich für einen Plex Server entschieden.

Plex ist ein Mediaserver, mit diesem, kann man Videos (Filme, Serien) oder auch Musik Online Verfügbar machen, dies über ein NAS einen Standalone oder über Dockercontainer. 

## Aufbau 
Meine Infrastruktur besteht aus einer Virtuellen Ubuntu Maschiene im TBZ Maas System und der Docker Umgebung. 
Um die Docker Umgebung Skalierbar zu gestalten, werden drei Ordner erstellt, 

Filme/ Serien

In diesen Ordnern werden alle Filme unud Serien welche auf dem Plex Server anschaubar sein sollten, abgespeichert. 

Config

Dies ist der Ordner für die Plex konfiguration

![Zeichnung2](https://user-images.githubusercontent.com/63262820/178158434-e346ccaf-31cf-4e89-a8fc-a5043d400442.png)

## Konfiguration
1. Ideen Sammeln auf Websiten 

https://computingforgeeks.com/how-to-run-plex-media-server-in-docker-containers/
https://hub.docker.com/r/linuxserver/plex
https://medium.com/@TechSquidTV/making-your-own-home-media-server-with-plex-and-docker-compose-techsquidtv-38a004257c66
2. Erstes zusammenschreiben eines Docker Compose Files nach der Anleitung eines YT Videos
3. Auftauchen des Ersten Errors (Siehe Probleme/1)

## Probleme

### 1.Mount error 
Zubeginn des Projektes (nachdem ich das Docker Compose file Geschrieben hatte) bekam ich das problem, dass beim starten des Docker Compose befels mir dieser Error (Siehe unten) angezeit wird. Habe keine Ahnung was das für ein Problem ist.

![image](https://user-images.githubusercontent.com/63262820/178159934-2b1179f0-b9e9-42d0-9a5b-aedda597b0e1.png)
#### Lösungsversuch 1
![image](https://user-images.githubusercontent.com/63262820/178335616-1ec8e9f7-80eb-4820-b0de-8a87907e7a8d.png)
#### Lösungsversuch 2
reboot :)

Analyse der Volumes (Teil des LV 2)
![image](https://user-images.githubusercontent.com/63262820/178340939-1bfcd237-e95a-4c57-8519-7b4259ea60d4.png)

---

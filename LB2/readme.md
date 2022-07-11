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
 
https://github.com/plexinc/pms-docker
https://computingforgeeks.com/how-to-run-plex-media-server-in-docker-containers/
https://hub.docker.com/r/linuxserver/plex
https://medium.com/@TechSquidTV/making-your-own-home-media-server-with-plex-and-docker-compose-techsquidtv-38a004257c66
2. Erstes zusammenschreiben eines Docker Compose Files nach der Anleitung eines YT Videos
3. Auftauchen des Ersten Errors (Siehe Probleme/1)
4. 1 h später ![image](https://user-images.githubusercontent.com/63262820/178344856-84eee1f8-794a-4497-8b09-4623a4641bb2.png)
OHA
5. Neues Problem siehe Problem 2
6. Doch kein Problem 
7. ![image](https://user-images.githubusercontent.com/63262820/178348124-95a1eaf6-4002-4375-86b1-8fd5bea9d52d.png)
Nun war ich an der Stelle an welcher ich die Info daten für den Plex server eingeben musste
8. Hinzufügen der Mediatheken ![image](https://user-images.githubusercontent.com/63262820/178348531-5dbc6808-4c99-4155-b990-3aac96f0b84c.png)
9. Fertig
####10. Upload eines Videos

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
Interessante Infos aus dem Inspect command
1. Der name des Projektes leitet sich aus dem Ordnernamen ab (Ahhhhha)
2. Ich habe die Docker Compose Version Falsch (1.0 statt 2.6.1)
3. Aussicht von docker heisst dieser "ordner" nicht plexmueller_filme sondern nur filme
4. Die Addressierung ist anders als in meinem Docker compose file ![image](https://user-images.githubusercontent.com/63262820/178341543-c0640268-a641-4ad2-a31a-e808bb4fdd61.png)
Ist dies die Lösung? 

Update: Nein war es nicht 

#### Lösungsversuch 3 / 21.35
Ich wollte mal kurz nochmals auf formfehler kontrollieren :) Ich hatte einen gefunden 

Das Problem war bei den Mount Paths der Volumes ich versuchete das Volume (auf dem host) namens config an den Mount point "mit dem Pfad x " anbinden. dies war falsch herum. 

Heisst: Falsch:"guest : host" Richtig:"host : guest"

![image](https://user-images.githubusercontent.com/63262820/178344198-958a24eb-ce14-4a74-897a-ad7b7a584b72.png)
![image](https://user-images.githubusercontent.com/63262820/178344213-82dc840f-c98e-4601-912b-62d7c34ad717.png)

---

### 2. kein Plex Media Server/ Warum??? 21.55
Ich hatte gerade den Plex Server aufgesetzt und es funktioniert super aber es siet nicht so aus wie erwartet, denn es ist ein detailierets abbild von plex.tv was ich nicht wollte. 
1. Was habe ich jetzt? 
![image](https://user-images.githubusercontent.com/63262820/178347956-a9c75a7a-5bd6-4f1d-a891-175fbe492786.png)

Doch das richtige hihihi

---


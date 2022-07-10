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

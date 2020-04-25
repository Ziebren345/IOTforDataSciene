# IOTforDataSciene

Als we een Data pipeline willen maken zijn er een aantal componenten voor nodig, namelijk een sensor, een proccessor, een netwerk en een cloud.
We zullen deze stap voor stap behandelen in dit project om zo een pipeline te kunnen creeren 

# Sensor
Voor dit project gebruiken wij een infrarood sensor, de RPI HC-SR501 om percies te zijn. We gebruiken deze omdat hij op het voltage van de Pi kan lopen en een digtal functie genereert die gelezen kan worden door node-red.

# Proccessor
Als proccessor gebruik ik een rasberry pi 3a+, dat komt omdat deze een goede prijs kwalieteit verhouding is en afdoende zal zijn voor dit project.

# Netwerk
Voor een verbinding met het internet gebruiken mijn eigen thuisnetwerk.

# Cloud
Als cloud gebruik ik Thingsspeak, omdat deze gratis is voor non-commerciele doeleinden, en deze veel support heeft op andere platformen.


# Stap 1
Als eerste moeten er een aantal dingen geinstaleerd en aangemaakt worden.
Voor de Pi moet je op Rasbarrian Node-Red downloaden. Deze is te vinden onder aanbevolen apps. Daarna moet je in Node-Red check of je de GPIO nodes hebt, zo ja moet je bij managne pallete thingspeak42 downloaden. deze zal de connectie met Thingspeak regelen. Als je de GPIO nodes nog niet heb moet je die ook eerst downloaden. Daarna moet je ook een account aanmaken voor Thingspeak.

# Stap 2
De tweede stap is verbinden van de sensor en deze via node red verbinden met thingspeak.

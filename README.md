# IOTforDataSciene

Als we een Data pipeline willen maken zijn er een aantal componenten voor nodig, namelijk een sensor, een proccessor, een netwerk en een cloud.
We zullen deze stap voor stap behandelen in dit project om zo een pipeline te kunnen creeren.
In de pipeline is het doel om het gebruik van een kamer te registeren. Dit doen wij met behulp van een infrarood bewgingssensor. Om vervolgens die kennis weer te kunnen toepassen in beheer van die kamer.

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
Voor de Pi moet je op Rasbarrian Node-Red downloaden. Deze is te vinden onder aanbevolen apps. Daarna moet je in Node-Red check of je de GPIO nodes hebt, zo ja moet je bij manange pallete, de node thingspeak downloaden. deze zal de connectie met Thingspeak regelen. Als je de GPIO nodes nog niet heb moet je die ook eerst downloaden. Daarna moet je ook een account aanmaken voor Thingspeak.

# Stap 2
De tweede stap is verbinden van de sensor en deze via node red verbinden met thingspeak.
![Foto van fysieke setup](https://github.com/Ziebren345/IOTforDataSciene/blob/master/WhatsApp%20Image%202020-04-25%20at%2012.20.14.jpeg)
Vervolgens moet je in node-red met de de GPIO node en Thingspeaknode een flow maken. Deze was voor dit project redelijk simpel.
Hij bestaat ook maar uit twee nodes.

# Stap 3
Vervolgens moet je eerst kijken welke dingen er moet aangepast worden in mijn versie van de code. Namelijk de Channel ID en de Write API key. Aangezien deze per channel op Thingsspeak veranderen. Ook kan je daarna kijken of de node het doet, als output moet je namelijk een 1 zien op de grafiek van thingspeak.

# Stap 4
Als laatste stap kun je de data die je nu verzamelt nog omzetten naar een betere manier van visalusatie, met behulp van matlab visualisations. Hierbij heb een code geschreven die de data per uur versimpelt en deze dan in een grafiek zet
```matlab
% Read traffic data for the past day from a ThingSpeak channel and 
% visualize hourly number of cars using the AREA function. 
 
   
% Channel ID to read data from 
readChannelID = 1046449; 
   
% Channel Read API Key   
% If your channel is private, then enter the read API 
% Key between the '' below:   
readAPIKey = '4WGEGHIDQO1Z3WXY'; 
   
% Read traffic data for the last 24 hours in a timetable, including 
% timestamps for each measurement 
movData = thingSpeakRead(readChannelID, 'Fields', [1], 'NumMinutes', 1440,...
                         'ReadKey', readAPIKey, 'Outputformat', 'Timetable');
   
% Compute the hourly average of the data 
avgMov = retime(movData, 'hourly', 'mean');
   
% Simplify the variables. Multiply by 240 to estimate the average number 
% of cars per hour from 15 second averages. 
Mov = avgMov.Test*240; 
 
  
% Plot the averaged data as an area plot. 
area(avgMov.Timestamps,[Mov]);
xlabel('Time');
ylabel('Average Movment per Hour');
legend({'Beweging'});
```
Wat dit als resultaat geeft.
![Foto van Grafiek](https://github.com/Ziebren345/IOTforDataSciene/blob/master/Plot.PNG)

# Ervaring
In dit project heb ik een aantal dingen geleerd over hoe mijn gebruik van computers anders is dan hoe de progammeurs dit doen, dit komt omdat ik zelf geen behoefte heb aan het coderen. Ik ben ook er fan van de uitspraak:"je hoeft het wiel geen twee uit te vinden". Dat komt omdat als ik iets van de computer gedaan wil krijgen ik niet zelf iets ga maken maar eerst ga kijken naar of iemand anders dit al heeft gedaan, of gedeeltelijk. Omdat ik zo moeite bespaar en niet hoef te programmeren.

Dit project heeft mij wel meer kennis gegeven van de IOT wereld omdat ik voor mijn project eerst onderzoek heb gedaan naar wat er allemaal onder IOT valt. En hoe ik dat het beste kon toepassen in mijn project. Ook heb wat geleerd over data, aangezien toen ik de dat binnenkreeg op thingspeak, het nog niet iets was waar veel waarde uitgelhaalt kon worden, en nadat ik deze data door matlab had gehaalt, echt informatie was geworden.


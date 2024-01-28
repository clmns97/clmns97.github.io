---
Autoren: Calugar Catalina Gabriela, Marquart John, Matanovic Patricia und Wollscheid Clemens
Kurs: 260.699 Projektentwicklung
Universität: Technische Universität Wien
Studienjahr: WS2023/24
---
# Dekabonisierung der Nemelkagasse 9

Das Ziel dieses Projekts ist es, verschiedene Möglichkeiten der Wärmeversorgung für ein Gebäude in der Nemelkagasse 9, 1110 Wien, zu visualisieren und zu vergleichen. Die Immobilie dient derzeit als Schule und verfügt über eine Nutzfläche von 2500 m². Untersucht wurden die Optionen der Versorgung durch Luft-Wasser-, Wasser-Wasser- und Sole-Wasser-Wärmepumpen sowie der Basisfall einer Versorgung durch Fernwärme. Dabei wurden die Wärmeversorgungssysteme hinsichtlich ihrer ökonomischen und ökologischen Auswirkungen verglichen.

## Webmap

Um das Projekt besser zu verorten, wurde eine Webmap auf Basis von Leaflet erstellt. Diese bildet zusätzlich das Potenzial für Erdwärme und Grundwasserwärme in Wien ab. Die Kartenerstellung erfolgte in QGIS, wobei die Gebäudeumrisse mit dem Plugin **[QuickOSM](https://github.com/3liz/QuickOSM)** bezogen wurden. Die Potenzialkarten für Erdwärme und thermische Grundwassernutzung wurden über den WFS-Server der Stadt Wien integriert und grafisch aufbereitet. Mit dem Plugin **[qgis2web](https://github.com/qgis2web/qgis2web)** wurde die Webmap anschließend generiert. Um die Benutzung zu vereinfachen und die Karte visuell zu verbessern, wurden Änderungen im HTML-Code vorgenommen, unter anderem durch die Integration einer vereinfachten Basemap von **[Stadia Maps](https://stadiamaps.com/explore-the-map/#style=alidade_smooth&map=14.44/59.43632/24.74273)**.

```html
L.tileLayer(
  "https://tiles.stadiamaps.com/tiles/alidade_smooth/{z}/{x}/{y}{r}.png",
  {
    maxZoom: 20,
    attribution:
      '&copy; <a href="https://stadiamaps.com/" target="_blank">Stadia Maps</a>, &copy; <a href="https://openmaptiles.org/" target="_blank">OpenMapTiles</a> &copy; <a href="https://www.openstreetmap.org/copyright" target="_blank">OpenStreetMap</a>',
  }
).addTo(map);
```

Die Webmap wurde auf der Website mittels eines iFrames wie folgt eingebunden:
```html
<iframe id="first_map" width="100%" height="500" title="Inline Frame Example" src="/maps/second_map/index.html"> </iframe>
```
## Diagramme

Die interaktiven Diagramme wurden mit der Dynamischen-Geometrie-Software **[Geogebra](https://www.geogebra.org/)** erstellt. Für jedes Diagramm wurde ein separates Projekt angelegt, das die relevanten Funktionsgraphen enthält.

### Kostenentwicklung

Die Modellierung der Kostenentwicklung basiert auf definierten Funktionen, wobei die Variablen für Strom- und Fernwärmepreis über Schieberegler angepasst werden können. Die Nutzfläche ist festgelegt, bietet aber zukünftig die Möglichkeit zur Anpassung. Die Projekte sind über verlinkte URLs (**[Kostenentwicklung](https://www.geogebra.org/m/j4stkc5m)** und **[CO&sup2; Äquivalente](https://www.geogebra.org/m/d47csuek)**) zugänglich. 

Fernwärme: $(0.3845*12*area+110*area*f)*x,~~~~~(0<x)$

Luft-Wasser-Wärmepumpe: 
$\begin{Bmatrix}
85*area+28*area*b*x ~~~~~:0<x<15~~ \\
85*area+28*area*b*x ~~~~~:15<x<30 \\
85*area+28*area*b*x ~~~~~:30<x<45 \\
\end{Bmatrix}$

Wasser-Wasser-Wärmepumpe: $145*area+19.6*area*b*x,~~~~~(0<x)$

Sole-Wasser-Wärmepumpe: $200*area+20.7*area*b*x,~~~~~(0<x)$

Die Einbindung der Diagramme erfolgt durch den Einsatz des Geogebra-Scripts im Header und einem entsprechenden Codeblock an der gewünschten Stelle auf der Webseite.
```html
<script src="https://www.geogebra.org/apps/deployggb.js"></script>
```

```html
<div id="ggb-element1"></div>
<script>
 	var params = {
  		appName: "classic",
  		autoHeight: true,
  		borderColor: "#92A2D6",
  		showResetIcon: true,
  		enableLabelDrags: false,
  		enableShiftDragZoom: false,
  		useBrowserForJS: false,
  		perspective: "G",
  		material_id: "j4stkc5m",
	};
    var ggbApplet1 = new GGBApplet(params, true);
        window.addEventListener("load", function () {
          ggbApplet1.inject("ggb-element1");
        });
</script>
```

### CO&sup2; Äquivalente

Auch das Diagramm für CO₂-Äquivalente wurde analog erstellt und beinhaltet Formeln, die die ökologischen Auswirkungen der verschiedenen Wärmeversorgungssysteme aufzeigen.

Fernwärme:$\frac{110*area*0.18*x}{1000},~~~~~(0<x)$

Luft-Wasser-Wärmepumpe: $\frac{28*area*0.227*x}{1000},~~~~~(0<x)$

Wasser-Wasser-Wärmepumpe: $\frac{19.6*area*0.227*x}{1000},~~~~~(0<x)$

Sole-Wasser-Wärmepumpe: $\frac{20.7*area*0.227*x}{1000},~~~~~(0<x)$

```html
<div id="ggb-element2"></div>
<script>
 	var params = {
  		appName: "classic",
  		autoHeight: true,
  		borderColor: "#92A2D6",
  		showResetIcon: true,
  		enableLabelDrags: false,
  		enableShiftDragZoom: false,
  		useBrowserForJS: false,
  		perspective: "G",
  		material_id: "d47csuek",
	};
    var ggbApplet2 = new GGBApplet(params, true);
        window.addEventListener("load", function () {
          ggbApplet2.inject("ggb-element2");
        });
</script>
```

### Annahmen

Die Annahmen zu den Wärmeversorgungssystemen, wie Jahresarbeitszahlen (JAZ) und Heizenergieverbrauch, sind in einer übersichtlichen Tabelle zusammengefasst.

| Wärmeversorgung | JAZ | Heizenergieverbrauch elektrisch | Konversationsfaktoren |
|----------|----------|----------|----------|
|Fernwärme|1|110 kWh/m²a|0,18 kg/kWh|
|Luft-Wasser-Wärmepumpe|3,9|28 kWh/m²a|0,23 kg/kWh|
|Sole-Wasser-Wärmepumpe|5,3|20,7 kWh/m²a|0,23 kg/kWh|
|Wasser-Wasser-Wärmepumpe|5,6|19,6 kWh/m²a|0,23 kg/kWh|

## Ausblick

Das Projekt bietet einen ersten Einstieg in das Thema "Dekabonisierung des Immobilinebestandes" anhand der Nemelkagasse 9 in 1110 Wien und erreichte das Ziel ein Visalisierungstool zu entwickeln, welches den Entscheidungstragenden die ökonomischen und ökologischen Auswirkungen einzelner Wärmeversorgungssysteme aufzeigt und Informationen zu den jeweiligen Systemen bereit stellt.

Die Erkentnisse und Umsetzungen der Projektgruppe können im nächsten Schritt von Interessierten genutz werden, um das Tool weiter zu entwickeln und interaktiver zu gestalten. Dies könnte weiterhin durch die Nutzung von Geogebra umgesetzt werden oder über andere Visualisierungstools wie **[Streamlit](https://streamlit.io/)** oder **[Chart.js](https://www.chartjs.org/)**. Die Potenziale des Tools liegen dabei in der Einbeziehung weiterer Faktoren zur genaueren Kostenabbildung. Möglichkeiten wären hier die Hinzunahme der Finanzierungskosten, variable Einstellung des Heizverbrauches, variable JAZs und Konversationsfaktoren sowie die Erweiterung um Photovoltaik zur Kosten- und CO²-Reduzierung.

## Quellen

- Stadt Wien (2023): Raus aus Gas, Wiener Wärme und Kälte 2040. Online Abrufbar unter: https://www.wien.gv.at/stadtentwicklung/energie/wissen/waerme-und-kaelte-2040.html (zuletzt abgerufen: 14.01.2024)
- Stadt Wien (2023 I): 100 Projekte Raus Gas. Online abrufbar unter: https://www.wien.gv.at/stadtentwicklung/energie/wissen/raus-aus-gas-vorzeigeprojekte.html (zuletzt abgerufen: 14.01.2024)
- Stadt Wien (2022): Wärmepumpen - der Dekarbonisierungsmotor im urbanen Bestand. Online abrufbar unter: https://www.wien.gv.at/kontakte/ma20/pdf/waermepumpe-leitfaden.pdf (zuletzt abgerufen: 14.01.2024)
- Stadt Wien (2014): Wärme! pumpen, zur energieeffizienten Wärmeversorgung. Online abrufbar unter: https://erneuerbare-energie.urbaninnovation.at/wp-content/uploads/2022/06/AC16333207.pdf (zuletzt abgerufen: 14.01.2024)
- Wimmer, Felix; DI Dr. Holzer, Peter (2020): Gebäudebestand gasfrei machen. Online abrufbar unter: https://www.klimaaktiv.at/dam/jcr:064e5746-6110-4857-8973-0a117cc9808d/Wien_Gebaeudebestand-gasfrei_2021-04.pdf (zuletzt abgerufen: 14.01.2024)
- Vaillant GmbH (2023): Die Vorteile & Nachteile von Wärmepumpen im Überblick. Online abrufbar unter: https://www.vaillant.ch/privatkunden/ratgeber-heizung/heiztechnologie-verstehen/warmepumpen/vorteile-nachteile-warmepumpe/ (zuletzt abgerufen: 14.01.2024)
- Wiegand, Dietmar (2015): Planen, bauen und betreiben im Kontext der Energiewende.
- Bundesministerium für Klimaschutz (2021): Ergebnisband Urbane Wärme und Kälte. Online abrufbar unter: https://nachhaltigwirtschaften.at/resources/sdz_pdf/schriftenreihe-2021-1-ergebnisband-urbane-waeme-kaelte.pdf (zuletzt abgerufen: 14.01.2024)

## Credits

- Icons: [Font Awesome](https://fontawesome.com/)
- Tamplate: [HTML5UP](https://html5up.net/)
- Other:
	- [jQuery](https://jquery.com/)
	- [Scrollex](https://github.com/ajlkn/jquery.scrollex)
	- [Responsive Tools](https://github.com/ajlkn/responsive-tools)
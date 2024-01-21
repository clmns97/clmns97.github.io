# Dekabonisierung der Nemelkagasse 9

Ziel dieses Projetes ist es die einzelnen Möglichkeiten zur Wärmeversorgung einer Immobilie in der Nemelkagasse 9 in 1110 Wien zu visualisieren und vergleichen. Die Immobilie wir derzeit als Schule genutzt und besitzt eine zu versorgende Nutzfläche von 2500 m2. Geprüft wurden die Möglichkeiten der Versorgung mit Luft-Wasser, Wasser-Wasser und Sole-Wasser Wärmepumpen sowie der Basecase mit einer Versorgung durch Fernwärme. Die einzelnen Wärmeversprgungen wurden dabei hinsichtlichs ihres ökonomischen als auch ökologischen Einflusses verglichen.

Zur beseren Verortung des Projektes wurde zudem eine Webmap auf Leafletbasis erstellt, welche zusätzlich die Möglichkeit bietet die Erdwärme- und Grundwasserwärme Potentiale der Stadt Wien abzubilden. Die Aufbereitung der Karte erfolgte 
QGIS unter zuhilfenahme des Plugins qgis2web. Auf der website selbst wurde die Webmap wiefolgt eingebunden.
```html
<iframe id="first_map" width="100%" height="500" title="Inline Frame Example" src="/maps/second_map/index.html"> </iframe>
``````

Die interaktiven Diagramme wurden mithilkfe des grafischen online Rechners Geogebra erstellt und manuell in die website eingebunden. 

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


Credits:

	Icons:
		Font Awesome (fontawesome.io)

	Other:
		jQuery (jquery.com)
		Scrollex (github.com/ajlkn/jquery.scrollex)
		Responsive Tools (github.com/ajlkn/responsive-tools)
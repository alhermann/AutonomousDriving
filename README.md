# AutonomousDriving
Simple Simulink 3D-world model for autonomous control systems testing.

Darauf achten, dass bei der Strassennode, der Node "Kopfsteinpflaster" sowie der Environmentnode die url's zu den hinterlegten Texturen angegeben sind (jeweils unter der "Shape/Texture" Node). Muss am Anfang angegeben bzw. geändert werden.

Die Strassentexturen sind etwas kantig geworden, falls es zu Problemen führt, kann ich es in Blender noch einmal verfeinern, probiert es einfach aus und sagt Bescheid.

Zur Zeit ist in der Lane Detection ein gierwinkelunabhängiges Template matching drin, zeigt jedoch in der Form nicht viel Wirkung und könnte auch weggelassen werden. Die Bildskalierung kann entsprechend angepasst werden, man muss jedoch darauf achten, dass die Dimensionen bei der Spurerkennung noch stimmen, die müssen dann theoretisch nochmals geändert werden.

Die Spurerkennung basiert auf einer Hough Transformation, RANSAC zeigt ähnliche Ergebnisse, brauchte jedoch längere Laufzeit, was sich aber vermutlich nach entsprechendem Parametersuchen aber beheben ließe. Hierfür wird das Eingangsbild in eine linke und rechte Hälfte geteilt und jeweils eine Fahrbahnerkennung durchgeführt, zusätzlich sind noch ein paar kleine Tricks drin, damit es etwas stabiler läuft.

Der PID-Regler basiert auf einem einfachen kinematischen Fahrradmodell (wenn man Daten für slip stiffnesses oder so hat kann man auch gerne komplexere Zustandraummodelle implementieren) und einem "pure pursuit" Ansatz. Dafür wird ein Pixelpunkt im Bild definiert, der zum Fahrzeug gehört, und ein Punkt auf der Fahrbahn und der Regler versucht, das Fahrzeug dahin zu lenken. Der Regler funktioniert auf einer Geraden relativ gut, auch in Kurven kann er teilweise auch noch gut funktionieren, jedoch ist die Performance und Stabilität stark abhängig von den Parametern und führt wohl im Allgemeinen nicht zu zufriedenstellenden Ergebnissen.
Interessant wäre es da wohl Regler wie die nach der Stanley Methode oder Potentialfeld State Feedback oder modellprädiktive Regler auszuprobieren. 

In der Simulation sollte das Fahrzeug einigermaßen stabil fahren, in einer Kurve aber, wo die Strassentexturen sich etwas ungünstig überlappen, fliegt das Fahrzeug gerne mal aus der Kurve. Man sieht aber trotzdem, dass eine Kurve zumindest durchfahren werden kann.

Als Fahrzeug ist zur Zeit der Camarro drin, ich hatte leider nichts kostenloses/lowpolyges/hübsches im Internet gefunden, kann man das aber sonst auch umtauschen.

Ansonsten sei vielleicht gesagt, dass die Steuerung in der 3D Umgebung etwas gewöhnungsbedürftig ist und die Nodes etwas verschachtelt werden können. 


Außerdem sind das VRML Koordinaten System und das Matlab Graphics Koordinaten System unterschiedlich! (Erstes Bild auf Google)

Wenn noch etwas sein sollte, sagt Bescheid!

Grüsse

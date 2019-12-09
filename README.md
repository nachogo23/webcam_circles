# webcam_circleis
Circle detection from online webcam images

L'algorítme de la Transformada de Hough és una tècnica d'analisisis d'imatges vírtuals que permet detectar figures geometriques simples que puguin ser expressades matemàticament de forma precissa. És una tècnica ampliament utilitzada en el camp de la visió per computació o l'analisis i el processat d'imatges. La tècnica va ser presentada i patentada al 1962 per Paul Hough. En un principi la tècnica s'utilitzava només per la detecció de rectes i més tard es va ampliar el seu ús per figures més complexes com cercles i el·lipses.

Per tenir una idea general de com funciona l'algorítme, podem fixar-nos en el cas de la detecció de rectes, doncs és el més simple. A la tranformada de Hough la idea principal es considerar les rectes pels seus paràmetres m i n (pendent i ordenada a l'origen) en comptes d'utilitzar els valors de x,y. Per rectes verticals però, els paràmetres m i n són indeterminats, per aquest motiu en general s'ulitzen les coordenades polars així a cada recta se li pot asiganr un parell (p, theta) únic. 

L'algoritme es basa en una matriu, anomenada acumulador, amb dimensions igual al número de paràmetres desconeguts de la equació que descriu la figura en questió. Pel cas d'una recta els paràmetres serien (m,n) o (p,theta) en coordenades polars.

En el cas aqui treballat per la detecció de cercles fent servir la Transformada de Hough, els paràmetres que es passen com a argument per la funció HoughCircles() són: MIN_RADIUS, MAX_RADIUS, MIN_CIRCLE_DIST, HOUGH_ACCUM_RESOLUTION, CANNY_EDGE_TH, HOUGH_ACCUM_TH.

Al repositori s'afegeixen algunes imatges a mode d'exemple per entendre l'influència dels paràmetres sobre la detecció de cercles.

MIN_RADIUS i MAX_RADIUS: determinen el radi mínim i màxim (en píxels) respectivament dels cercles que detectarà. Tunejant adequadament aquest paràmetre podem ser selectius amb les figures que volem identificar (imatge 1,2)

MIN_CIRCLE_DIST: Aquest paràmetre permet determinar la distància mínima que ha d'existir entre el centre de dos circumferencies per que ambdues siguin detectades. Si fem aquest paràmetre molt petit generarem falsos resultats, doncs detectarà varies vegades el mateix cercle (imatge 3). D'altra banda si fem aquest numero suficientment gran només podrem detectar una circumferencia en tota la imatge (imatge 4).

HOUGH_ACCUM_RESOLUTION: Resolució de l'acumulador de Hough, en termes de l'invers de la relació de resolució de la imatge.

CANNY_EDGE_TH: Limit del detector de cantonades (Canny algorithm). Si es fa molt gran el programa reconeixes cercles a molts punts, obtenim falsos resultats (iamtge 5).

HOUGH_ACCUM_TH: Límit de l'acumulador per decidir la detecció del centre. Si el numero és molt gran (1000) no es detecta cap cercle. Si el fixem al valor mínim (1) es dónen falsos resultats entorn al cercle real (imatge 6).

Instruccions

1. Fork del repositori al nostre espai de GitHub
2. Clone del repositori. Dins trobem l'arxiu CMakelists.txt, on es defineixen els paràmetres necesaaris per poder compilar, llibreries associades, nom de l'executable que es generarà, etc.
3. Dins del repo, afegim el directori "build" (mkdir build) i a l'interior executem "cmake .." (els ".." son per indicar que l'arxiu de config "CMakelists.txt" es troba al directori superior)
4. Seguidament dins de /build executem "make" per que es el compili el script en .cpp que es troba al directori /src. Obtenim un executable
5. Ja podem fer anar l'executable (./exe). Per fer anar l'executable cal estar dins del direcori on es troba. Si es fa al algún canvi al script cal tornar a repetir el proces per generar un nou executable.


Referencies:
http://homepages.inf.ed.ac.uk/rbf/HIPR2/hough.htm
http://wiki.ros.org/op3_ball_detector
https://en.wikipedia.org/wiki/Hough_transform



 

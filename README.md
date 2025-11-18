<h2><b>⚙ Projecte de shift left security</b></h2>

<ul>
    <li>En el primer commit, creo que fallaba la tabulación del archivo de workflow (por copiar del PDF)</li>
    <li>En el segundo, no estaba cambiada la URL del repo de Quay, por eso generó error al intentar subir</li>
    <li>Dockerfilebasic subió correctamente y se publicó en Quay con security scan == Passed</li>
    <li>Dockerfilevulerable encontró vulnerabilidades y no se subió</li>
    <li>Añadimos generación y análisis de SBOM</li>
    <li>Aunque hay varias vulnerabilidades Low y una Medium, el problema lo da con c-ares, que es una dependencia de curl, que es High (CVE-2025-31498). Según https://c-ares.org/vulns.html es un bug que se introdujo en v1.32.3 y leyendo la descripción, se indica que en 1.34.5 está parcheado</li>
    <li>No ha funcionado ya que parece que en los repositorios de Alpine 3.20, la versión con la vulnerabilidad es la más reciente disponible, por lo que debemos plantear usar una Alpine más reciente. Se ha probado con la 3.22</li>
    <li>Parece que ahora todo bien, sigue estando una medium y varias low pero se ha solucionado la high que se pedía</li>
    <li>Se añaden en el yaml del workflow para subir SBOM al git</li>
    <li>El nuevo step da un error e indica que hay que hacer git config del emial y usuario, se prueba de nuevo</li>
    <li>Vuelve a dar error, ahora se indica que el workflow no tiene permiso de escritura en el git. Desde settings >> actions del repo, se concede permiso de escritura al workflow</li>
</ul>

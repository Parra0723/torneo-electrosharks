# Torneo FIFA 2v2 · ElectroSharks

Página para organizar un torneo de FIFA 2v2 en PS5 con 3 consolas: 16, 20 o 24 dúos, grupos de 4 y luego cuartos, semis, tercer puesto y final.

## Links

Cambia `USUARIO` y `REPO` por los tuyos.

| Para | Link |
|---|---|
| Jugadores (buscan su dúo, ven los partidos en vivo, las tablas y la llave) | `https://USUARIO.github.io/REPO/` |
| Pantalla grande (televisor o proyector) | `https://USUARIO.github.io/REPO/#pantalla` |
| Ayudantes (celular) | `https://USUARIO.github.io/REPO/#ayudante` |
| Organizador | `https://USUARIO.github.io/REPO/#organizar` |
| Inscripciones y pagos (FIFA y Rocket League) | `https://USUARIO.github.io/REPO/inscripciones.html` |

## Inscripciones (`inscripciones.html`)

Lleva quién se inscribió, en qué torneo, con qué dúo, cuánto pagó y cómo (dólares o bolívares). Los datos se guardan **solo en el navegador donde la abres**, no en Firebase ni en este repositorio, así que nadie más los ve.

- Para pasar los datos a otro teléfono o computadora: *Ajustes → Descargar copia de seguridad* en el primero y *Recuperar una copia de seguridad* en el otro.
- Descarga una copia de vez en cuando: si se borran los datos del navegador, se pierden.

La pantalla grande se ajusta sola al tamaño del televisor o proyector, sin barras de desplazamiento. Ábrela en pantalla completa (F11).

## Durante el torneo (panel del organizador)

- **Cambiar un partido:** si un dúo llega tarde o no está, toca *Cambiar* en su consola y elige otro partido para jugar en ese momento. El que no se jugó pasa a la hora del partido elegido. Solo aparecen partidos posibles (nadie juega dos veces en el mismo turno) y avisa si un dúo jugaría dos turnos seguidos. Ayudantes, pantalla y jugadores lo ven al instante, y se puede deshacer mientras esos partidos no hayan empezado.
- **Atraso:** si van tarde en general, suma minutos y todas las horas pendientes se corren.
- **Calendario en PDF:** *Compartir calendario en PDF* (en el panel y en Calendario) arma un PDF con los grupos, todos los partidos con hora y consola, los resultados que ya haya y las reglas. En el celular abre el menú de compartir para mandarlo por WhatsApp; en la computadora lo descarga. En *Mi dúo* está el PDF con el horario de un solo dúo.

## Archivos

- `index.html`: toda la página del torneo.
- `inscripciones.html`: inscripciones y pagos.
- `assets/`: logo, íconos de la pestaña, la imagen que aparece al compartir el link y el logo de los PDF.
- `config.js`: los datos de tu proyecto de Firebase. **Es lo único que tienes que editar.**
- `firestore.rules`: reglas de seguridad para pegar en Firebase (con tus claves).

## Conectar Firebase (una sola vez, unos 10 minutos)

GitHub Pages solo muestra la página. Los resultados se guardan en Firebase (gratis para un torneo así).

1. Entra a https://console.firebase.google.com con una cuenta de Google y crea un proyecto (puedes desactivar Google Analytics).
2. **Authentication** → Comenzar → pestaña *Sign-in method* → activa **Anónimo**.
3. **Firestore Database** → Crear base de datos → elige una ubicación cercana (por ejemplo `us-east1`) → modo de producción.
4. En Firestore, pestaña **Reglas**: borra lo que hay, pega el contenido de `firestore.rules` con tus claves en lugar de `CLAVE_AYUDANTES` y `CLAVE_ORGANIZADOR`, y toca **Publicar**.
5. **Configuración del proyecto** (el engranaje) → *Tus apps* → ícono web `</>` → registra la app (sin Hosting) → copia los valores de `firebaseConfig`.
6. Pega esos valores en `config.js` en GitHub (abre el archivo → lápiz → pega → *Commit changes*).
7. **Authentication** → Configuración → *Dominios autorizados* → agrega `USUARIO.github.io`.

Listo: abre el link del organizador, escribe la clave de organizador y crea el torneo.

## Claves

- **Clave de ayudantes:** se la das a quienes van a cargar resultados. Escriben su nombre y la clave una sola vez en su celular.
- **Clave de organizador:** solo para ti. Permite crear el torneo, cambiar el atraso, corregir resultados y ver el registro.
- Las claves viven solo en las reglas de Firebase, no en este repositorio. Para cambiarlas, edita las reglas y publícalas de nuevo.
- Para sacar a todos los ayudantes que ya entraron, borra la colección `ayudantes` en Firestore.

## Probar sin Firebase

Si `config.js` no está configurado, la página ofrece **Probar en este dispositivo**: funciona completa, pero los datos se guardan solo en ese navegador.

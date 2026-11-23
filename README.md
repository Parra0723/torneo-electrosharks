# Torneo FIFA 2v2 · ElectroSharks

Página para organizar un torneo de FIFA 2v2 en PS5 con 3 consolas: 16, 20 o 24 dúos, grupos de 4 y luego cuartos, semis, tercer puesto y final.

## Links

Cambia `USUARIO` y `REPO` por los tuyos.

| Para | Link |
|---|---|
| Pantalla grande (también para los jugadores) | `https://USUARIO.github.io/REPO/#pantalla` |
| Ayudantes (celular) | `https://USUARIO.github.io/REPO/#ayudante` |
| Organizador | `https://USUARIO.github.io/REPO/#organizar` |

## Archivos

- `index.html`: toda la página.
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

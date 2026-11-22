# Hogar

Web para organizar las tareas de casa, el menú semanal y las listas de la compra.

Dirección: https://jontxu06.github.io/public/hogar/

Mientras Firebase no esté configurado, la web funciona en **modo prueba**: los datos se guardan solo en el móvil donde la abras. Así se puede probar todo antes.

## Conectar Firebase (una sola vez)

1. Entra en https://console.firebase.google.com con tu cuenta de Google y crea un proyecto (por ejemplo `hogar`). Google Analytics no hace falta.
2. **Authentication** → Comenzar → Método de acceso → **Google** → Habilitar → Guardar.
3. **Authentication** → Configuración → Dominios autorizados → Agregar dominio → `jontxu06.github.io`.
4. **Firestore Database** → Crear base de datos → elige una ubicación de Europa (por ejemplo `europe-west1`) → modo producción.
5. **Firestore Database** → Reglas → borra lo que haya, pega el contenido de `firestore.rules` y pulsa **Publicar**.
6. Configuración del proyecto (rueda dentada) → General → Tus apps → icono `</>` (web) → ponle un nombre → Registrar. Copia el bloque `firebaseConfig`.
7. En `index.html` busca la línea `const FIREBASE_CONFIG = null;` y cámbiala por tu configuración:

```js
const FIREBASE_CONFIG = {
  apiKey: "...",
  authDomain: "....firebaseapp.com",
  projectId: "...",
  storageBucket: "...",
  messagingSenderId: "...",
  appId: "..."
};
```

Puede quedar público en GitHub sin problema: lo que protege los datos son las reglas del paso 5.

## Primer uso

- **Entra tú el primero**: la primera persona que entra crea el grupo y queda como administradora.
- Los demás entran con Google y quedan pendientes. Tú los aceptas en **Ajustes** (la rueda de arriba muestra un número rojo cuando hay solicitudes).
- Si el único administrador sale del grupo, otra persona pasa a serlo al azar.

Los datos del modo prueba no se pasan a Firebase; son solo para probar.

# DevNG Chat

Este proyecto es una aplicación de chat implementada enteramente en JavaScript, diseñada para que los alumnos practiquen conceptos básicos de JavaScript y la manipulación dinámica del DOM sin el uso de librerías externas (excepto FontAwesome para iconos).

---

## ¿Qué se implementó?

- **Generación Dinámica del DOM:**  
  Se creó toda la interfaz (pantalla de login, área de chat, contenedores, botones, etc.) usando `document.createElement` y estilos aplicados a través de la propiedad `style`.

- **Conexión con el Servidor:**  
  El chat se conecta al servidor en `https://chat.devng.online/chats` mediante peticiones `GET` y `POST` para leer y escribir mensajes.

- **Pantalla de Login:**  
  Si no se encuentra un usuario en `localStorage`, se muestra una pantalla de login que solicita al usuario su nombre. Una vez ingresado, se guarda en `localStorage` y se despliega la interfaz del chat.

- **Límite de Caracteres y Envío de Mensajes:**  
  Los mensajes se limitan a 140 caracteres y se muestra un contador en tiempo real. Los mensajes se pueden enviar tanto haciendo clic en el botón como presionando la tecla "Enter" (sin Shift).

- **Auto-Refresh y Preservación del Scroll:**  
  La lista de mensajes se actualiza automáticamente cada 5 segundos. Si el usuario está al final del chat, el scroll se preserva para mostrar los nuevos mensajes sin interrumpir la experiencia.

- **Detección y Previsualización de Contenido:**  
  - **Imágenes:** Se detectan enlaces que contienen “.jpeg” o se reciben datos en formato data URL, y se muestran usando un elemento `<img>`.
  - **Páginas Web:** Se detectan enlaces a páginas web y se muestra una preview utilizando un elemento `<object>` (sin usar iframes).

- **Cambio de Tema (Claro/Oscuro):**  
  El usuario puede cambiar entre un tema claro y uno oscuro. La preferencia se guarda en `localStorage` para que se recuerde en futuras visitas.

- **Manejo de Errores de Conexión:**  
  Si no se puede conectar al servidor (por problemas de red o si el servidor está caído), se muestra un mensaje de error intermitente en el centro del área de mensajes.

- **Uso de Async/Await y Deconstrucción:**  
  Las funciones asíncronas para enviar y obtener mensajes utilizan `async/await` de forma semánticamente correcta y se emplea la deconstrucción para extraer propiedades de los objetos de mensajes.

- **Animaciones:**  
  Se implementaron animaciones para:
  - La aparición de elementos (efecto fade + slide).
  - El mensaje de error, que parpadea utilizando la animación `blink`.

---

## ¿Cómo se implementó el Chat?

1. **Estilos y Animaciones:**  
   Se creó un `<style>` dinámicamente en el `<head>` que define los estilos globales, animaciones para el fondo, la aparición de elementos y el parpadeo de mensajes de error.

2. **Interfaz de Usuario:**  
   Toda la interfaz se genera mediante JavaScript. Se crean contenedores para el login y el chat, se establecen estilos con `document.createElement` y se organizan utilizando flexbox.

3. **Gestión del Usuario:**  
   Al iniciar la aplicación, se verifica si `localStorage` contiene un usuario. Si no es así, se muestra la pantalla de login. Una vez ingresado el usuario, se almacena en `localStorage` y se carga la interfaz del chat.

4. **Comunicación con el Servidor:**  
   Se utilizan llamadas a `fetch()` para:
   - **Obtener Mensajes:** La función `getMessages()` hace una petición GET al servidor y muestra los mensajes en la interfaz.
   - **Enviar Mensajes e Imágenes:** Las funciones `sendMessage()` y `sendImage()` realizan peticiones POST para enviar datos al servidor.

5. **Control de Errores y Timeout:**  
   En las funciones de envío y obtención de mensajes se usan bloques try…catch para capturar errores de conexión. Cuando ocurre un error, se limpia el área de mensajes y se muestra un mensaje de error intermitente en el centro.

6. **Interactividad y Animaciones:**  
   Se añadió la funcionalidad para enviar mensajes con el botón o al presionar Enter, y se aplican animaciones para mejorar la experiencia de usuario. Además, se implementa el cambio entre temas claro y oscuro, que se guarda en `localStorage`.

---

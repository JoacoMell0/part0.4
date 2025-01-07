```mermaid
sequenceDiagram
    browser->>server: POST https://studies.cs.helsinki.fi/exampleapp/new_note
    activate server
    server-->>browser: HTTP 302 response (Redirect to /exampleapp/notes)
    deactivate server

    Note right of browser: The browser follows the redirect and sends a new GET request

    browser->>server: GET https://studies.cs.helsinki.fi/exampleapp/notes
    activate server
    server-->>browser: HTML document
    deactivate server

    browser->>server: GET https://studies.cs.helsinki.fi/exampleapp/main.css
    activate server
    server-->>browser: the CSS file
    deactivate server

    browser->>server: GET https://studies.cs.helsinki.fi/exampleapp/main.js
    activate server
    server-->>browser: the JavaScript file
    deactivate server

    browser->>server: GET https://studies.cs.helsinki.fi/exampleapp/data.json
    activate server
    server-->>browser: [{ "content": "HTML is easy", "date": "2023-1-1" }, ... ]
    deactivate server

    Note right of browser: The browser processes the retrieved data<br>and renders the notes dynamically


```
---

### **Explicación del flujo en el diagrama:**

1. **Envío del formulario**:
   - El navegador envía una solicitud `POST` al servidor con los datos del formulario.
   - El servidor responde con un código de estado `302` indicando una redirección.

2. **Redirección**:
   - El navegador sigue automáticamente la redirección y envía una solicitud `GET` a la URL proporcionada (`/exampleapp/notes`).

3. **Carga de recursos de la página**:
   - Se generan tres solicitudes adicionales para obtener los recursos necesarios: `main.css`, `main.js` y `data.json`.

4. **Procesamiento de los datos**:
   - El navegador utiliza los datos obtenidos (`data.json`) para renderizar dinámicamente las notas.

---

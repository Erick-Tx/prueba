```mermaid
sequenceDiagram
    participant Usuario as User
    participant Navegador as Browser
    participant Servidor as Server

    Note over Usuario, Navegador: El usuario accede a la aplicación de notas

    Navegador->>Servidor: GET /notes
    activate Servidor
    Servidor-->>Navegador: HTML document
    deactivate Servidor

    Navegador->>Servidor: GET /main.css
    activate Servidor
    Servidor-->>Navegador: CSS file
    deactivate Servidor

    Navegador->>Servidor: GET /main.js
    activate Servidor
    Servidor-->>Navegador: JavaScript file
    deactivate Servidor

    Navegador->>Servidor: GET /data.json
    activate Servidor
    Note right of Servidor: Servidor prepara datos JSON
    Servidor-->>Navegador: JSON data
    deactivate Servidor

    Note over Usuario, Navegador: Usuario decide agregar una nueva nota

    Usuario->>Navegador: Input new note
    Navegador->>Servidor: POST /new_note {note content}
    activate Servidor
    Note right of Servidor: Servidor procesa la nueva nota
    Servidor-->>Navegador: Confirmación
    deactivate Servidor

    Navegador->>Servidor: GET /data.json (nuevamente para actualizar)
    activate Servidor
    Servidor-->>Navegador: JSON data actualizado
    deactivate Servidor

    Note over Navegador: Navegador actualiza la vista con la nueva nota

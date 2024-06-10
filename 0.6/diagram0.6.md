//0.6 Posting a new note (SPA)

sequenceDiagram
    participant browser
    participant server

    Note right of broser: 

    browser->>server: POST https://studies.cs.helsinki.fi/exampleapp/new_note_spa
    activate server
    server-->>browser: 201 created
    deactivate server


    Note right of browser: The 201 Created status code means that the request was successfully fulfilled and resulted in one or possibly multiple new resources being created. In this case, the server just response with one HTML, this HTML has its content manipulated by JS when is executed in the browser.
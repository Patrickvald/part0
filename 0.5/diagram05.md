//0.5 Opening web page (SPA)

sequenceDiagram
    participant browser
    participant server

    Note right of broser: the process is quite similar to get the HTML document and their notes. Nevertheless, posting a new note will have several differences, we will see that in exercise 0.6

    browser->>server: GET https://studies.cs.helsinki.fi/exampleapp/spa
    activate server
    server-->>browser: HTML document
    deactivate server

    browser->>server: GET https://studies.cs.helsinki.fi/exampleapp/main.css
    activate server
    server-->>browser: the css file
    deactivate server

    browser->>server: GET https://studies.cs.helsinki.fi/exampleapp/spa.js
    activate server
    server-->>browser: the JavaScript file
    deactivate server

    Note right of browser: Now the browser starts executing the JS code that fetches the JSON from the server with the different notes.

    browser->>server: GET https://studies.cs.helsinki.fi/exampleapp/data.json
    activate server
    server-->>browser: [{ "content": "j", "date": "2024-06-10T08:06:04.768Z" }, ... ]
    deactivate server

    Note right of browser: The browser executes the callback function that renders the notes

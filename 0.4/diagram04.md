//0.4 Posting a new note

sequenceDiagram
    participant browser
    participant server

    browser->>server: POST https://studies.cs.helsinki.fi/exampleapp/new_note
    activate server
    server-->>browser:response 302, URL found 
    desactivate server
    Note right of browser: Our browser searchs this URL to post the new note, the server responses with a 302, the url was found. Next, the browser will do a get request to get the HTML document.

    browser->>server: GET https://studies.cs.helsinki.fi/exampleapp/notes
    activate server
    server-->>browser: HTML document
    deactivate server

    browser->>server: GET https://studies.cs.helsinki.fi/exampleapp/main.css
    activate server
    server-->>browser: the css file
    deactivate server

    browser->>server: GET https://studies.cs.helsinki.fi/exampleapp/main.js
    activate server
    server-->>browser: the JavaScript file
    deactivate server

    Note right of browser: Now the browser starts executing the JS code that fetches the JSON from the server with the different notes.

    browser->>server: GET https://studies.cs.helsinki.fi/exampleapp/data.json
    activate server
    server-->>browser: [{ "content": "save", "date": "2024-06-10T07:44:30.586Z" }, ... ]
    deactivate server

    Note right of browser: The browser executes the callback function that renders the notes

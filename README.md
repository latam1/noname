# noname
Alice quiere comprar un libro que Bob tiene en venta, Alice y Bob no se conocen, y viven en países diferentes, bajo jurisdicciones y regulaciones distintas:

```mermaid
sequenceDiagram
Alice-x+ Bob: $ 8.906.000,89
Note left of Alice: para Alice<br/>cualquier cosa<br/>puede salir mal<br/>oh no ~~$%&!!#%%^^&
Bob-x- Alice: "Los Evangelios de Enrique el León"
Note right of Bob: para Bob<br/>Cualquier cosa <br/>puede salir mal<br/>oh no ~~$%&!!#%%^^&

```

buscan una agencia de asentamiento "settlement", un agente de liquidación,  que cumpla funciones de intermediario para garantizar un "cierre rápido" y "efectivo" de la operación bajo una jurisdicción relativamente segura, y ellos acuerdan operar con “Rodolfo cerrajería y agencia de asentamientos 24/7” ubicado en Suiza

```mermaid
sequenceDiagram
Alice->>Rodolfo: $ 8.906.000,89
Rodolfo-->>Bob: Tengo custodia del dinero todo OK
Bob->>Alice: "Los Evangelios de Enrique el León"
Alice-->>Rodolfo: recibí "Los Evangelios de Enrique el León" todo OK
Rodolfo->>Bob: $ 8.816.940,88
```

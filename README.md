# sistema de intercambio mediado tradicional
Alice quiere comprar un libro que Bob tiene en venta, Alice y Bob no se conocen, y viven en países diferentes, bajo jurisdicciones distintas:

```mermaid
sequenceDiagram
box Purple
actor Alice
end
box Purple
actor Bob
end
Alice-) Bob: $ 8.906.000,89
Note left of Alice: para Alice<br/>cualquier cosa<br/>puede salir mal<br/>oh no ~~$%&!!#%%^^&
Bob-) Alice: "Los Evangelios de Enrique el León"
Note right of Bob: para Bob<br/>Cualquier cosa <br/>puede salir mal<br/>oh no ~~$%&!!#%%^^&

```

buscan una agencia de asentamiento "settlement", un agente de liquidación,  que cumpla funciones de intermediario para garantizar un "cierre rápido" y "efectivo" de la operación bajo una jurisdicción relativamente segura, y ellos acuerdan operar con “Rodolfo cerrajería y agencia de asentamientos 24/7” ubicado en Suiza


```mermaid
sequenceDiagram
box Purple
actor Alice
end
actor Rodolfo
box Purple
actor Bob
end
Alice-)Rodolfo: $ 8.906.000,89
Note over Rodolfo,Bob: ---> Bob ya recibí el dinero 
Bob-)Alice: "Los Evangelios <br/>de Enrique el León"
Note over Alice,Rodolfo: ---> Rodolfo ya recibí <br/>Los Evangelios de Enrique el León
Rodolfo-)Bob: $ 8.816.940,88

```

Las condiciones generales establecidas para este contrato ["ESCROW"](https://www.hispacolex.com/blog/civil-mercantil/que-es-el-contrato-de-escrow/) son las siguientes: 

- Alice se compromete en enviar el monto acordado para iniciar el proceso
- Bob se compromete en completar la entrega del libro a alice en un periodo de 7 días, a partir del momento que los fondos estén bajo la custodia de Rodolfo
`Alice + Bob = via normal, sin marco temporal, pueden ejecutar el contrato cuando ellos quieran`

- Después de 7 días te inciar el contrato con el deposito de Alice a Rodolfo y si Bob no ha logrado cumplir con su parte del contrato, Rodolfo puede ejecutar el contrato con cualquiera de las dos partes, o con Alice para devolver el dinero o con Bob para completar el contrato considerando cual de las partes incumplió con el contrato. ```despues de 7 dias: o Alice + Rodolfo o Bob + Rodolfo```

# sistema de intercambio mediado con esquemas de firmas digitales y contratos de bitcoin
Es posible realizar el mismo contrato de manera expedita con bitcoin si se incluye algun mecanismo de clasificación "rating" para con todas las partes, siguiendo el mismo modelo de los mercados [OTC](https://www.bbva.com/es/que-son-los-mercados-over-the-counter-otc/)


```mermaid
graph TD
A[Contrato de Bitcoin] --> B("via Normal:<br/>+firma_digital_Alice<br/>+firma_digital_Bob") 
A --> C[via Disputa:]   
C --> D("despues_de_7_dias<br/>+firma_digital_Rodolfo<br/>+firma_digital_Bob")
C --> E("despues_de_7_dias<br/>+firma_digital_Rodolfo<br/>+firma_digital_Alice")
```

[Ejemplo](https://mempool.space/testnet/address/tb1pyp9uxlkukvlrq5px5rqzl03ks88e9me3kvjzkqg5lkfe4vht0ktq8sj37p) del contrato:

flujo:
1. El ofertante `Bob` genera una oferta de bien o servicio mediante la interfaz de usuario y describe las condiciones especificas de la operacion siguiendo el protocolo definido en [NIP15](https://github.com/nostr-protocol/nips/blob/master/15.md) o un clon personalizado. 
2. El comprador `Alice` propone un acuerdo de compra previamente discutido entre las dos partes, envía la información del acuerdo al mediador `Rodolfo`, para que el mismo genere el contrato digital.
3.  `Rodolfo` genera el contrato digital con la información de `Alice` y `Bob`
4.  `Alice` envía los fondos al contrato y marca su compromiso como ejecutado
5.  `Bob` crea una orden / solicitud  para usar los fondos enviados al contrato
6.  `Rodolfo` verifica que la orden generada por `Bob` sea correcta generando los pagos necesarios o compromisos a las partes involucradas, si todo está OK `Rodolfo` firma digitalmente el contrato y lo envía  a las partes.
7.  `Bob` verifica la firma digital de `Rodolfo` e inicia con el cumplimiento de su compromiso "bien o servicio", al dar por culminado su participación, marca como finalizado y notifica a las partes

en este punto el contrato puede derivar en dos ramas:

8.1. `Alice` firma el contrato digital y lo devuelve firmado a `Bob` para su firma y distribución en la red de bitcoin "vía Normal". [EJEMPLO](https://mempool.space/testnet/tx/4e4e558a0de1c5a462c1f370c6bd4b599e52139fe6df344aa86aa9792b954a5d) de una ejecucion de este tipo realizada por el equipo

o

8.2. `Alice` no firma el contrato digital y después de 7 días `Rodolfo` debe dar una resolución con los contratos derivados de la "vía Disputa", sea con `Alice` para retornar los fondos o con `Bob` para dar cumplimiento con el contrato. [EJEMPLO](https://mempool.space/testnet/tx/fb1992fc1cc5bdcef81b003d32454440581cc4afba55cbbfa0981dc0d5ab17c2) de una ejecucion de este tipo realizada por el equipo


*Para este material educativo no se toman en cuenta todos los factores que modifican los incentivos de las partes a operar de manera saludable, así como las variables temporales y la cantidad de contratos secundarios derivados o de ejecución por via "Disputa".
*`Rodolfo` no tienen que ser 1 sola entidad, pueden ser un esquema de firmas digitales diferentes a 1 firma, por ejemplo 2-de-3 firmas o 3-de-5 firmas o partes
*el canal/medio de comunicación para intercambio de información no tiene por que ser centralizado

-el desafío más evidente es la interfaz de usuario, no es un wallet no necesita almacenar llaves de bitcoin con fondos, pero sí debe poder realizar firmas digitales compatibles con [bip340-342-350](https://github.com/bitcoin/bips/blob/master/bip-0340.mediawiki), manejar nativamente las primitivas de bitcoin, generación de llaves, serialización de transacciones etc  . . ., [bip-327](https://github.com/bitcoin/bips/blob/master/bip-0327.mediawiki), nostr [nip1-5](https://github.com/nostr-protocol/nips/blob/master/01.md) para comunicación, [nip15](https://github.com/nostr-protocol/nips/blob/master/15.md) publicación de ofertas. (Kotlin, Java ideal)  

# aquiSeVendenLibros.com
En pro de identificar un posible producto mínimo viable, realizar estudios de mercado, capitalizar talento local, talento remoto etc . . se propone la siguiente prueba de concepto "especifica" en donde se podrá abstraer la complejidad de un sistema de carácter general, descentralizado y resiliente.

POC: una página web donde poder vender y comprar libros de manera expedita y segura, usando un esquema de firmas digitales, un contrato de bitcoin definido para este fin de la siguiente manera; un contrato digital que requiere 2 firmas digitales de 2 posibles firmas digitales (2-de-2) y que con el tiempo deriva en un contrato digital que requiere 2 firmas de 3 posibles firmas digitales (2-de-3)   

- dado un conjunto de [vendedores](https://github.com/nostr-protocol/nips/blob/master/15.md#event-30017-create-or-update-a-stall) de libros: (V1, V2, . . . Vn) donde
  v1 = libros de tecnología
  v2 = novelas
  * de no poseer ninguna operación previa los vendedores deben hacer un deposito de garantía por un tiempo establecido o limitar las operaciones a rangos específicos de valor máximo de operación 50$ que se incrementa en función de las operaciones realizadas. Antecedentes de lo anterior se pueden observar en [Bitcoin-OTCs](https://www.bitcoin.com/otc/), localbitcoins, [hodlhodl](https://hodlhodl.com/) y cualquier otra plataforma de intercambios p2p donde compradores y vendedores son considerados no confiables. #TODO definir el sistema de rating aquí!
  * del precio final de venta de cada libro; el 0.5% es enviado al mediador al finalizar cualquier operacion
 
- un conjunto de [compradores](https://github.com/nostr-protocol/nips/blob/master/05.md#mapping-nostr-keys-to-dns-based-internet-identifiers): (C1, C2, ... Cn)
  C1 = casual
  C2 = recurrente
  * el comprador debe colocar en garantia el monto completo + 0.5% en el contrato 
  * el 0.5% es enviado al mediador al dar por finalizada cualquier operacion 

- un mediador : M1
  * debe grarantizar la operatividad del sistema por el 1% del valor total de las operaciones finalizadas
 
- los fondos en garantia "el dinero del comprador en bitcoin o algun asset estable*=)" no necesariamente deben ser el activo transado por una de las partes, el comprador puede completar su parte del acuerdo con haciendo una transferencia bancaria local y el vendedor al confirmar el pago por otra via, puede liberar los fondos del comprador nuevamente al origen -1%, ejemplo una compania de logistica que resulta tambien aporta liquidez en bitcoin a una de las partes para realizar un operacion para con la plataforma a la hora de comprar un libro extremadamente raro.

- para la prueba de concepto el monto valor en garantia sera "el pago", si bien esto no es eficiente usando bitcoin directamente, se deben incluir cadenas secundarias como Liquid y sus "Colored Coins",


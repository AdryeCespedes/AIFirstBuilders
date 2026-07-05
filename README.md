# PRD-001: SIRCIP — Gestionador del nuevo regimen SIRCIP de percepciones de Ingresos Brutos bajo Convenio Multilateral

## Contexto y Problema
Se precisa desarrollar una nueva aplicación que permita manejar el cálculo de percepciones de Ingresos Brutos, en clientes bajo Convenio Multilateral, según el nuevo regimen SIRCIP (Sistema Informático de Recaudación, Control e Información de Percepciones), que es un sistema desarrollado por la Comisión Arbitral (COMARB) para unificar, centralizar y estandarizar el régimen de percepciones de Ingresos Brutos bajo Convenio Multilateral, 
El sistema publica un padrón por contribuyente en forma mensual. Actualmente oara realizar el cálculo hay que consultar manualmente dicho padrón por CUIT en la página correspondiente y según la respuesta, evaluarla según unas determinadas reglas para disponer finalmente en qué provincias, que alícuota hay que aplicar y si hay sobretasas, para finalmente calcular el importe de las percepciones de ingresos brutos a facturar al cliente.
Se precisa automatizar tanto la obtención de dicho padrón que puede ser muy grande con millones de registros y almacenarlo de forma que pueda ser consultado rápidamente, automatizar la obtención a partir de un CUIT, una fecha, un importe facturado y un código de provincia de entrega, la lista de provincias, alicuotas, tipo e importes de percepciones de ingresos brutos a aplicar. 
El archivo tiene un formato .TXT y una estructura informada en un documento de diseño de registro disponible.
También hay documentos que explican en función del contenido del padrón como se calculan dichos importes de percepciones.

Personas:
Administrador del padrón: Es la persona encargada de descargar el padrón del Portal Federal Tributario cuando está disponbile e importarlo en el nuevo sistema.
Usuario facturador: Es la persona que está facturando a un cliente y que tiene que calcular los importes de percepciones de ingresos brutos para dicho cliente.

## Objetivos
Calcular de forma correcta las percepciones de ingresos brutos a un cliente en convenio multilateral, según la provincia de entrega del comprobante a facturar y hacerlo de forma rápida.

## Requerimientos Funcionales
- RF-01: Un usuario debe poder loguearse en el sistema con nombre de usuario y contraseña y el sistema tiene que poder administrar dos tipos de usuario Administradores y simples usuarios, sin RBAC configurable. Los usuarios están dados de alta inicialmente en una base de datos.
- RF-02: El sistema debe permitir que un usuario con role de Administrador pueda importar el padrón, que será un archivo con formato .txt desde una ubicación en el disco de la computadora. Debe poder indicarse el mes y año para el cual se está importando dicho padrón y debe quedar registro de la fecha de importación, el período, el usuario y cantidad de registros importados.
- RF-03: El sistema debe poder a partir de una serie de reglas indicadas y la información del padrón, obtener a partir de un CUIT, una fecha, un importe facturado y una provincia de entrega calcular que importe de percepciones de ingresos brutos, de qué tipo y a qué provincias hay que facturar al cliente. Esto se implementará con una API que devolverá una lista de impuestos a facturar.
- RF-04: Para CUIT que no estén en el padrón del período indicado, el sistema no tiene que calcular percepciones de ingresos brutos.
- RF-05: Si el período indicado para el cálculo de las percepciones no está importado en el sistema la API debe devolver un error de padrón inexistente para el cálculo.
- RF-05: Si la importación del padrón genera algún error debe quedar registro del error, del usuario importador, el período y la fecha de importación.
- RF-06: El padrón importado de un período, debe poder eliminarse.

## Requerimientos No Funcionales
- RNF-01: La importación del padrón debe realizarse en tiempos menores al minuto.
- RNF-02: Las contraseñas deben almacenarse con hash seguro (bcrypt/argon2), nunca en texto plano; la sesión expira tras 24 h de inactividad.
- RNF-03: El cálculo de las percepciones debe tener un 0% de error.
- RNF-04: El cálculo de las percepciones no puede demorar más de 30 segundos.

## Criterios de Aceptación
- AC-01 (RF-01): Dado <contexto>, cuando <acción>, entonces <resultado medible>.

## Fuera de Alcance
- No hay una página de registración de usuarios.
- No puede realizarse varias veces la importación de un padrón de un período, dicho de otra forma no hay importación parcial o modificación de un padrón importado. Para volver a importarlo primero hay que eliminarlo y luego volver a importarlo.

## Riesgos y Dependencias
- Riesgo: No se detecta.
- Dependencia: SQLLite para almacenar los usuarios.

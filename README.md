# PRD-001: SIRCIP — Gestionador del nuevo regimen SIRCIP de percepciones de Ingresos Brutos bajo Convenio Multilateral

## Contexto y Problema
Se precisa desarrollar una nueva aplicación que permita manejar el cálculo de percepciones de Ingresos Brutos, en clientes bajo Convenio Multilateral, según el nuevo regimen SIRCIP (Sistema Informático de Recaudación, Control e Información de Percepciones), que es un sistema desarrollado por la Comisión Arbitral (COMARB) para unificar, centralizar y estandarizar el régimen de percepciones de Ingresos Brutos bajo Convenio Multilateral, 
El sistema publica un padrón por contribuyente en forma mensual. Actualmente oara realizar el cálculo hay que consultar manualmente dicho padrón por CUIT en la página correspondiente y según la respuesta, evaluarla según unas determinadas reglas para disponer finalmente en qué provincias, que alícuota hay que aplicar y si hay sobretasas, para finalmente calcular el importe de las percepciones de ingresos brutos a facturar al cliente.
Se precisa automatizar tanto la obtención de dicho padrón que puede ser muy grande con millones de registros y almacenarlo de forma que pueda ser consultado rápidamente, automatizar la obtención a partir de un CUIT, un importe facturado y un código de provincia de entrega, la lista de provincias, alicuotas, tipo e importes de percepciones de ingresos brutos a aplicar. 
El archivo tiene un formato .TXT y una estructura informada en un documento de diseño de registro disponible.
También hay documentos que explican en función del contenido del padrón como se calculan dichos importes de percepciones.

Personas:
Administrador del padrón: Es la persona encargada de descargar el padrón del Portal Federal Tributario cuando está disponbile e importarlo en el nuevo sistema.
Usuario facturador: Es la persona que está facturando a un cliente y que tiene que calcular los importes de percepciones de ingresos brutos para dicho cliente.

## Objetivos
Calcular de forma correcta las percepciones de ingresos brutos a un cliente en convenio multilateral, según la provincia de entrega del comprobante a facturar y hacerlo de forma rápida.

## Requerimientos Funcionales
- RF-01: El sistema debe <una acción, verbo imperativo>.
- RF-02: ...

## Requerimientos No Funcionales
- RNF-01: <cualidad con número: "< 3 s p95", "≥ 85%">.

## Criterios de Aceptación
- AC-01 (RF-01): Dado <contexto>, cuando <acción>, entonces <resultado medible>.

## Fuera de Alcance
- <Lo que explícitamente NO entra.>

## Riesgos y Dependencias
- Riesgo: <qué puede salir mal> → mitigación: <cómo lo cubrís>.
- Dependencia: <de qué depende para funcionar>.

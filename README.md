# Control de Almacén de Obra

App de almacén de obra en un solo archivo (`index.html`): kardex valorizado (promedio ponderado), ingresos, salidas con vale, compras con cuadro comparativo, varios almacenes, varias obras y préstamos/transferencias entre obras. Funciona sin internet.

**Aquí solo está la app, vacía.** Los datos de cada obra se guardan en el teléfono de quien la usa y nunca se suben a este repositorio.

## Uso en el celular
1. Abrir el enlace de GitHub Pages de este repositorio (Chrome en Android, Safari en iPhone).
2. Menú → **Agregar a pantalla de inicio**.
3. Para pasar datos de otra versión: en la versión anterior **Más → Respaldo completo**, y en esta **Más → Importar respaldo…**.

## Varias empresas (v7)
**Más → Empresa → Nueva empresa.** Cada empresa es un espacio separado en el teléfono: sus obras, préstamos entre obras, reportes, respaldos y archivo de Drive no se mezclan con los de otra empresa. Los datos que ya tenías quedan en la primera empresa.

## Sincronizar con Google Drive (v7)
1. Ya está hecho para este repositorio. Solo si publicas la app en otra dirección: en [console.cloud.google.com](https://console.cloud.google.com): crear un proyecto, activar **Google Drive API**, configurar la pantalla de consentimiento (tipo *Externo*, agregar los correos que la usarán como *usuarios de prueba*) y crear un **ID de cliente OAuth** de tipo *Aplicación web* con el origen autorizado `https://americomirandao.github.io`.
2. En la app: **Más → Google Drive** → **Sincronizar con Google Drive** (desde la v10 el ID de cliente ya viene incluido; no hay que pegarlo).
3. En otro teléfono: **Sincronizar** → elegir el archivo de la empresa.

La app usa el permiso `drive.file`: solo ve los archivos que ella misma creó en tu Drive. Cada empresa tiene su archivo (`AlmacenCalc - <empresa>.json`). Si dos teléfonos cambian datos sin sincronizar, la app avisa del conflicto y deja elegir; antes de traer datos de Drive descarga un respaldo de lo que había en el teléfono.

## Seguridad (v8)
La página trae una política de seguridad (CSP) que solo permite su propio código y el de Google (para Drive). Los respaldos y archivos de Drive se validan antes de cargarse; si alguno trae datos manipulados, la app lo rechaza.

## Cambios de la v12
- El kardex se calcula por orden de fecha (antes, por orden de registro): un ingreso con fecha atrasada entra en su lugar y el costo promedio se recalcula. No se puede registrar una salida o traslado con una fecha en la que no había saldo. Si datos antiguos quedan con saldo negativo en alguna fecha, la cabecera lo avisa.
- Los códigos internos de cada registro ya no pueden repetirse al crear varios a la vez (catálogo base, recepción de una OC con varios ítems).
- No se puede anular un ingreso, devolución o traslado si el saldo quedaría negativo: primero hay que anular las salidas posteriores.
- No se aceptan precios negativos (ingresos y cotizaciones).
- Los CSV exportan las cantidades con hasta 4 decimales, igual que en pantalla.
- La app queda guardada para abrir sin internet desde la primera visita, y trae ícono propio para instalarla en el teléfono.

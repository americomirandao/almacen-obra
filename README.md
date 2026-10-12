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
1. Una sola vez, en [console.cloud.google.com](https://console.cloud.google.com): crear un proyecto, activar **Google Drive API**, configurar la pantalla de consentimiento (tipo *Externo*, agregar los correos que la usarán como *usuarios de prueba*) y crear un **ID de cliente OAuth** de tipo *Aplicación web* con el origen autorizado `https://americomirandao.github.io`.
2. En la app: **Más → Google Drive** → pegar el ID de cliente → **Sincronizar con Google Drive**.
3. En otro teléfono: mismo ID de cliente → **Sincronizar** → elegir el archivo de la empresa.

La app usa el permiso `drive.file`: solo ve los archivos que ella misma creó en tu Drive. Cada empresa tiene su archivo (`AlmacenCalc - <empresa>.json`). Si dos teléfonos cambian datos sin sincronizar, la app avisa del conflicto y deja elegir; antes de traer datos de Drive descarga un respaldo de lo que había en el teléfono.

## Seguridad (v8)
La página trae una política de seguridad (CSP) que solo permite su propio código y el de Google (para Drive). Los respaldos y archivos de Drive se validan antes de cargarse; si alguno trae datos manipulados, la app lo rechaza.

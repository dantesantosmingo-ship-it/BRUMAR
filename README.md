# BRUMAR · Gestión integral

Proyecto iniciado el 28/10/2026 para un comercio de venta de pescado.

## Estado actual

Base técnica inicial: pantalla de bienvenida, navegación entre los módulos previstos y comunicación entre HTML y Apps Script. Las secciones muestran su alcance propuesto; todavía no registran operaciones.

Pendiente: relevar los procesos reales, definir datos y permisos, implementar las operaciones y probarlas con el negocio. No hay conexión a una planilla, datos de clientes, envíos de avisos ni una implementación publicada en Google.

## Tecnología

- HTML, CSS y JavaScript para una interfaz adaptable a computadora y celular.
- Google Apps Script (`.gs`) para las reglas y automatizaciones del servidor.
- Google Sheets como propuesta inicial de almacenamiento, sujeta al volumen y la cantidad de usuarios.
- Zona horaria inicial: `America/Argentina/Buenos_Aires`.

Las pantallas y los servicios se ampliarán por módulo. La interfaz llama al servidor con `google.script.run`; las validaciones y autorizaciones de futuras operaciones deberán ejecutarse en el servidor.

## Archivos

```text
src/
  appsscript.json    Configuración de Apps Script
  Config.gs         Identidad y catálogo de módulos previstos
  Code.gs           Entrada web y carga de fragmentos HTML
  Application.gs    Información inicial que recibe la interfaz
  Index.html        Estructura de la pantalla
  Styles.html       Estilos
  JavaScript.html   Navegación y comunicación con el servidor
docs/
  ALCANCE_Y_PROCESOS.md
scripts/
  preview.mjs       Genera una vista local sin conexión a Google
  verify.mjs        Comprueba sintaxis y contrato inicial del servidor
```

## Vista local

Desde esta carpeta, con Node.js instalado:

```powershell
node scripts/verify.mjs
node scripts/preview.mjs
```

Abrir `preview/Index.html` en un navegador. Esta vista utiliza el mismo catálogo del servidor y muestra explícitamente que es una vista local. No guarda datos.

## Probar en Apps Script

1. Crear un proyecto nuevo en [Google Apps Script](https://script.google.com/).
2. Crear los archivos `.gs` y HTML de `src/` con sus mismos nombres y contenidos. En el editor de Google se ingresa el nombre sin la extensión.
3. En Configuración del proyecto, mostrar `appsscript.json` y copiar el manifiesto de `src/`.
4. Usar **Implementar → Probar implementaciones → Aplicación web**. Esta prueba está destinada a los editores del proyecto.
5. Verificar que el indicador cambie a **Conectado a Apps Script** y que las secciones sean navegables.

Esta base expone únicamente información general del proyecto. Antes de incorporar datos comerciales, definir quién podrá acceder y cómo se comprobarán sus permisos. El modelo de identidad debe decidirse según la cuenta y la modalidad de ejecución de la aplicación; no asumir que el correo del visitante siempre estará disponible.

## Próximo trabajo

Relevar primero un pedido real, desde que llega hasta su entrega y cobro. A partir de ese ejemplo se definirán los estados, las cantidades, el momento de afectar stock y los documentos relacionados. Ver [alcance y procesos](docs/ALCANCE_Y_PROCESOS.md).

## Referencias técnicas

- [Aplicaciones web de Apps Script](https://developers.google.com/apps-script/guides/web).
- [Separación de HTML, CSS y JavaScript](https://developers.google.com/apps-script/guides/html/best-practices).
- [Comunicación con funciones del servidor](https://developers.google.com/apps-script/guides/html/communication).
- [Identidad y disponibilidad del correo del usuario](https://developers.google.com/apps-script/reference/base/session).
- [Cuotas de ejecución y de servicios](https://developers.google.com/apps-script/guides/services/quotas). La viabilidad del almacenamiento y las automatizaciones se evaluará con el volumen real de BRUMAR.

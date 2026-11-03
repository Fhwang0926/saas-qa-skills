# SaaS Web QA Skill

[한국어](README.md) | [English](README.en.md) | [日本語](README.ja.md) | [Tiếng Việt](README.vi.md) | Español | [Português](README.pt.md) | [Français](README.fr.md) | [Deutsch](README.de.md) | [Italiano](README.it.md)

Una sola skill para revisar el funcionamiento de sitios web y servicios SaaS, sus interfaces adaptables y su accesibilidad. Adapta de forma selectiva procesos de las skills públicas de Anthropic, Vercel, Microsoft y otras fuentes de QA. Incluye instrucciones y listas de comprobación, pero no instala las skills originales ni sus herramientas.

Según la solicitud, también ayuda a planificar QA según el riesgo, comprobar API, revisar pruebas existentes de Playwright o Cypress e investigar fallos. Consulta las [fuentes y el alcance](skills/saas-web-qa/references/sources.md).

Las revisiones autenticadas distinguen el rol y espacio de trabajo autorizados, las listas y filtros pertinentes y el alcance de la comprobación de persistencia. Las sesiones de navegador separadas aún pueden compartir datos del servidor.

En el QA por perfiles, diez usuarios simulados recorren el sitio en un navegador real. Cuando sea posible, subagentes independientes recopilan hallazgos y capturas; si se solicitan correcciones, se repiten los recorridos. Consulta el [procedimiento](skills/saas-web-qa/references/persona-journeys.md).

## Flujo de QA

- **Diagnosticar, corregir y volver a comprobar:** Tanto en QA general como por perfiles, si se solicitan correcciones, se solucionan los problemas dentro del alcance y se vuelve a comprobar el comportamiento original cuando el servicio en ejecución haya incorporado los cambios. Si no es posible, se indica el motivo y lo no verificado.
- **Recorridos separados:** Si se solicitan varias funciones, se define un punto de entrada y un criterio de éxito para cada recorrido. El QA por perfiles registra cada resultado por separado y, para cada problema, cuántos perfiles pudieron evaluar el paso y cuántos lo encontraron. Se ordena por frecuencia y se destacan aparte los problemas graves.
- **Antes y después del inicio de sesión:** Si el inicio de sesión está bloqueado pero existe una sesión autorizada, se pueden comprobar por separado las funciones autenticadas. No se declara que el recorrido completo e ininterrumpido haya tenido éxito.

## Skills públicas de QA y prácticas incorporadas

Se han adaptado de forma selectiva los flujos de las siete skills o colecciones siguientes en una sola `saas-web-qa`. No se incluyen ni instalan los paquetes originales, sus reglas completas, scripts o herramientas. Consulta los enlaces y el alcance en [fuentes](skills/saas-web-qa/references/sources.md).

| Skill o colección pública | Práctica incorporada |
| --- | --- |
| Anthropic `webapp-testing` | Inspección de páginas renderizadas antes de comprobar acciones y resultados. |
| Vercel `web-design-guidelines` | Revisión de UI, usabilidad, interacción y accesibilidad. |
| Microsoft `playwright-cli` | Flujos de interacción con el navegador y automatización. |
| `qa-skills` | Planificación basada en riesgos, QA exploratorio, comprobación de API e informes de defectos. |
| `e2e-skills` | Revisión de la calidad de pruebas E2E existentes e investigación de fallos. |
| TestDino `playwright-skill` | Pruebas de navegador con la configuración Playwright existente del proyecto. |
| `cypress-agent-skill` | Pruebas de navegador con la configuración Cypress existente del proyecto. |

## Pedir a un agente que instale y ejecute la skill

Envía una petición como esta a tu agente de programación. El repositorio debe estar publicado en GitHub y ser accesible para el agente.

```text
Instala la skill saas-web-qa de https://github.com/Fhwang0926/saas-qa-skills
en el proyecto actual, lee sus instrucciones y realiza el siguiente QA.
Si ya está instalada, comprueba que admite la tarea solicitada antes de usarla.

Objetivo: página de inicio de sesión del proyecto actual
Alcance: diseño en escritorio y móvil, inicio de sesión y accesibilidad
```

Para instalarla sin hacer QA, solicita solo la instalación. Puede que el agente necesite una sesión nueva para detectarla; si puede leer los archivos instalados, puede seguir las instrucciones en la sesión actual.

### Instrucciones para agentes

1. Identifica el proyecto y el agente y lee las instrucciones del usuario y del proyecto. Si `saas-web-qa` ya está instalada, lee `SKILL.md` y las referencias pertinentes y comprueba que admiten la tarea; no supongas que es la versión actual por el nombre. Reutilízala si es suficiente. Si falta una función, comprueba la fuente accesible de este repositorio, la procedencia de la instalación y los cambios locales; actualiza según las reglas sin sobrescribir trabajo que no pueda reemplazarse de forma segura. Si actualizar no es seguro, usa directamente las instrucciones de la fuente cuando sea posible. Informa si no hay acceso o falta la función.
2. Si hace falta instalarla, ejecuta el comando siguiente en el proyecto de destino. Si no hay selección interactiva y conoces el agente, selecciona solo ese agente; para Codex, añade `--agent codex -y`. No añadas `-g` salvo que se solicite instalación global. Respeta los permisos y las normas de herramientas del entorno.
3. Comprueba el resultado y la ruta de instalación; lee `SKILL.md` y los archivos necesarios de `references/`. Si no aparece registrada pero los archivos son legibles, sigue sus instrucciones directamente. Si solo se pidió instalar, no realices QA.
4. Prioriza el servicio en ejecución y el navegador disponible. Respeta las reglas del usuario y del proyecto sobre compilaciones, pruebas, inicio de servidores, bases de datos y servicios externos. Si faltan herramientas o acceso, informa del bloqueo y del trabajo realizado; no declares éxito sin pruebas.

## Instalación directa

Una vez publicado el repositorio, ejecuta este comando en el proyecto de destino. Se requiere Node.js 22.20 o posterior; selecciona el agente cuando se solicite.

```bash
npx skills add Fhwang0926/saas-qa-skills --skill saas-web-qa
```

Para instalar desde una copia local, sustituye la ruta por la ubicación real:

```bash
npx skills add /path/to/saas-qa-skills --skill saas-web-qa
```

Por defecto, la instalación se limita al proyecto. Añade `-g` para instalar globalmente. Reinicia el agente si necesita volver a detectar la skill.

## Uso

```text
$saas-web-qa Revisa la página de inicio de sesión en escritorio y móvil e informa de los problemas reproducibles.
```

### Diagnosticar, corregir y volver a comprobar en una petición

```text
$saas-web-qa Revisa el servicio en ejecución con diez perfiles de usuario simulados.
Usa subagentes separados cuando sea posible y comprueba en un navegador real
las páginas públicas y las funciones principales con una cuenta autorizada.
Captura los puntos confusos o bloqueantes e indica, para cada problema, cuántos
perfiles llegaron al paso y cuántos lo encontraron. Corrige los problemas
confirmados en conjunto, repite los recorridos en condiciones comparables
e informa de lo resuelto y lo pendiente.
```

La skill proporciona instrucciones; no incluye navegador, Playwright, aplicación en ejecución ni cuentas. Las comprobaciones reales requieren el entorno y los permisos adecuados. Prevalecen las reglas del usuario y del proyecto.

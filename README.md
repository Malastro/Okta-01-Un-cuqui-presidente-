# Okta 01 — Un presidente, unos privilegios y un Cuqui descontrolado

## 1. Descripción del proyecto

Este laboratorio está inspirado en el primer episodio de la segunda temporada de *La que se avecina*: **«Un soltero, un yogur con fibra y un nuevo presidente»**.

Tras la salida de Javi Maroto de la presidencia de Mirador de Montepinar, Amador Rivas decide presentar su candidatura y termina convirtiéndose en el nuevo presidente de la comunidad. Maite Figueroa celebra entusiasmada su ascenso a primera dama, mientras Leo Romaní continúa desempeñando las funciones de vicepresidente.

Sin embargo, el cambio de presidencia trae consigo un problema que nadie había previsto: la gestión de los cargos y las responsabilidades de los vecinos sigue dependiendo de registros manuales que no siempre se actualizan correctamente.

Javi continúa figurando como presidente, Amador todavía aparece como un propietario más y algunos vecinos conservan pertenencias a grupos que ya no les corresponden. Ante semejante descontrol, Enrique Pastor propone modernizar la administración de Mirador de Montepinar S. L. mediante la implantación de **Okta Identity Cloud** como plataforma centralizada de gestión de identidades.

El objetivo de este laboratorio es configurar y validar un sistema de gestión de usuarios basado en **Okta Universal Directory**, utilizando atributos personalizados para representar los cargos de la comunidad y reglas dinámicas (*Group Rules*) para automatizar las pertenencias a grupos.

A través del relevo entre Javi y Amador, se comprobará cómo una modificación en los atributos de un usuario puede provocar una actualización automática de su pertenencia a los grupos correspondientes, sin necesidad de gestionar manualmente cada asignación.

También se analizará el comportamiento de las reglas ante cambios de cargo y excepciones, verificando los resultados mediante la consola de administración de Okta y los eventos registrados en **System Log**.

El laboratorio permitirá aplicar conceptos fundamentales de *Identity and Access Management (IAM)*, especialmente la administración centralizada de identidades, la gestión de atributos y la automatización de asignaciones basadas en información del perfil.

**Escenario ficticio:** Mirador de Montepinar S. L., donde Amador Rivas acaba de descubrir que convertirse en presidente es mucho más fácil que conseguir que los vecinos reconozcan sus nuevas responsabilidades. Y donde, gracias a Okta, al menos los grupos de usuarios estarán mejor organizados que las juntas de propietarios.

## 2. Objetivos técnicos

El propósito de este laboratorio es implementar un sistema de asignación automática de grupos en Okta a partir de los atributos de los usuarios, simulando un cambio de responsabilidades dentro de Mirador de Montepinar.

Para ello, se establecen los siguientes objetivos:

1. **Personalizar Universal Directory:** crear el atributo `cargoVecinal` para representar los cargos de los vecinos dentro de la comunidad.
2. **Automatizar la pertenencia a grupos:** configurar reglas dinámicas que incorporen a presidentes y vicepresidentes al grupo `Junta de Gobierno`.
3. **Gestionar cambios de responsabilidad:** simular el relevo de Javi Maroto por Amador Rivas sin modificar manualmente las pertenencias.
4. **Comprobar las limitaciones de las reglas:** observar qué ocurre cuando dos usuarios tienen simultáneamente el cargo de presidente.
5. **Auditar los cambios:** utilizar System Log para identificar y verificar los eventos de incorporación y eliminación de miembros.
6. **Evitar efectos sobre configuraciones existentes:** mantener separado el grupo `Junta de Gobierno` del grupo `Junta`, que ya dispone de una política de inscripción de autenticadores.

## 3. Entorno y tecnologías utilizadas

El laboratorio se ha desarrollado en un entorno **Okta Integrator Free Plan**, utilizando la consola de administración para gestionar las identidades de los vecinos de Mirador de Montepinar.

### Tecnologías y funcionalidades

| Tecnología | Aplicación en el laboratorio |
|---|---|
| Okta Identity Cloud | Plataforma de gestión de identidades. |
| Universal Directory | Administración de usuarios y atributos de perfil. |
| Custom Attributes | Creación del atributo `cargoVecinal`. |
| Okta Groups | Organización de los miembros de la Junta de Gobierno. |
| Group Rules | Asignación y retirada automática de usuarios según su cargo. |
| System Log | Auditoría de los cambios de pertenencia a grupos. |

### Identidades utilizadas

| Usuario | Cargo inicial | Cargo final |
|---|---|---|
| Javier Maroto | Presidente | ExPresidente |
| Amador Rivas | Propietario | Presidente |
| Leonardo Romaní | Vicepresidente | Vicepresidente |
| Enrique Pastor | Propietario | Propietario |

### Grupos y reglas

Se creó el grupo `Junta de Gobierno` para gestionar automáticamente la pertenencia de los vecinos que ocupan cargos de responsabilidad.

Se configuraron dos reglas:

- **Presidencia de Montepinar:** incorpora al grupo a los usuarios cuyo atributo `cargoVecinal` sea `Presidente`.
- **Vicepresidencia de Montepinar:** incorpora al grupo a los usuarios cuyo atributo `cargoVecinal` sea `Vicepresidente`.

El grupo `Junta`, existente de prácticas anteriores, se mantuvo sin modificaciones porque tenía asociada una política de inscripción de autenticadores que exigía Okta Verify y contraseña.

De esta forma, las pruebas de automatización se realizaron sin modificar los requisitos de autenticación del grupo original.

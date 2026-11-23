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

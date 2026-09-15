<div align="center">

# Avalon

### Un PC Windows 10/11 x64. Varios escritorios independientes.

Convierte un único equipo Windows 10/11 x64 en varias instancias de escritorio accesibles de forma independiente, cada una con su propia pantalla, entrada, audio, aplicaciones y conexión de streaming remoto.

**Un host. Varias instancias.**

[English](README.md) · [简体中文](README-zh-CN.md)

</div>

---

## ¿Qué es Avalon?

Avalon es una plataforma de streaming de escritorio multisesión para Windows 10/11 x64.

En lugar de limitar un PC a un único escritorio interactivo, Avalon permite que la misma máquina aloje varias instancias independientes de Windows al mismo tiempo.

Cada instancia puede tener sus propios:

- sesión de escritorio de Windows
- monitor virtual
- resolución y frecuencia de actualización
- flujo de entrada
- flujo de audio
- aplicaciones y juegos
- conexión remota mediante Moonlight

Esto permite que un único PC potente se comporte de forma parecida a varios ordenadores accesibles a distancia, sin tener que ejecutar una máquina virtual completa para cada usuario.

---

## ¿Cómo se ve en la práctica?

Imagina un PC Windows 10/11 x64 ejecutando tres instancias de Avalon:

```text
                Windows 10/11 x64 Host
                       │
                ┌──────┴──────┐
                │    Avalon    │
                └──────┬──────┘
                       │
         ┌─────────────┼─────────────┐
         │             │             │
         ▼             ▼             ▼
    Instance 01    Instance 02    Instance 03
         │             │             │
         ▼             ▼             ▼
     Moonlight      Moonlight      Moonlight
        TV            Tablet         Laptop
```

Cada cliente se conecta a su propio escritorio de Windows.

Las instancias funcionan en paralelo sin compartir el mismo escritorio, cursor del ratón, salida de audio ni sesión de aplicaciones.

---

## ¿Por qué Avalon?

Las herramientas tradicionales de escritorio remoto suelen estar diseñadas alrededor de un usuario controlando un solo escritorio.

Las máquinas virtuales proporcionan un aislamiento fuerte, pero también añaden sistemas operativos adicionales, consumo de memoria, almacenamiento, complejidad de GPU y costes de administración.

Avalon adopta otro enfoque.

Combina sesiones de Windows, pantallas virtuales, procesos de streaming independientes y gestión centralizada del ciclo de vida para que varios escritorios interactivos puedan coexistir en un único host Windows 10/11 x64.

La complejidad permanece dentro de Avalon. Para el usuario, el flujo es sencillo:

```text
Crear una instancia
        ↓
Configurar pantalla y emparejamiento
        ↓
Abrir Moonlight
        ↓
Conectar
```

---

## Capacidades principales

### Varias instancias independientes

Ejecuta varias sesiones de escritorio de Windows en el mismo host al mismo tiempo.

Cada instancia se comporta como un entorno de escritorio interactivo independiente.

### Streaming independiente

Cada instancia dispone de su propio contexto de streaming y puede recibir una conexión independiente desde un cliente Moonlight.

Un televisor puede conectarse a una instancia mientras una tableta u otro ordenador se conecta simultáneamente a otra.

### Pantalla independiente

Cada instancia puede utilizar su propia configuración de pantalla virtual, incluida la resolución y la frecuencia de actualización.

Avalon gestiona el entorno de pantalla sin exigir un monitor físico para cada instancia.

### Entrada independiente

El teclado y el ratón se enrutan a la sesión de Windows correspondiente en lugar de compartirse entre todas las instancias.

A medida que evoluciona la pila de entrada, Avalon está diseñado para avanzar hacia un aislamiento de dispositivos cada vez más completo por instancia.

### Audio independiente

Cada instancia utiliza su propia ruta de audio de sesión de Windows, por lo que distintos usuarios pueden escuchar aplicaciones o juegos diferentes sin mezclar simplemente el audio entre instancias.

### Gestión del ciclo de vida de las sesiones

Avalon crea y mantiene las sesiones por sí mismo.

No es necesario mantener conectado permanentemente un cliente RDP externo solo para que una instancia siga activa.

### Administración web

Todas las instancias se administran desde una única interfaz web.

Las operaciones habituales incluyen:

- crear y eliminar instancias
- iniciar y detener instancias
- configurar resolución y frecuencia de actualización
- emparejar clientes Moonlight
- revisar el estado de las conexiones
- consultar diagnósticos
- administrar ajustes del host

El uso cotidiano no requiere trabajar con la línea de comandos.

---

## Diseñado para Moonlight

Avalon mantiene la experiencia de streaming de Moonlight que ya conoces.

Puedes seguir utilizando Moonlight en dispositivos como:

- Windows
- Linux
- macOS
- Android
- iOS / iPadOS
- Android TV
- televisores inteligentes y dispositivos de streaming compatibles con Moonlight

Avalon cambia la organización del lado del host; no obliga a aprender un cliente de streaming completamente nuevo.

---

## Casos de uso

### Juegos en casa

Convierte un único PC gaming en varios entornos de juego independientes para distintas personas de la misma casa.

Una persona puede jugar desde el televisor del salón mientras otra se conecta a otra instancia desde una consola portátil o un portátil.

### Varias cuentas y varias instancias

Ejecuta aplicaciones, cuentas o sesiones de juego diferentes en entornos de Windows separados dentro de la misma máquina.

### Estación de trabajo remota

Utiliza un escritorio potente como varios espacios de trabajo remotos accesibles de forma independiente.

### Pruebas y desarrollo

Mantén varias sesiones de Windows para pruebas de software, automatización, compatibilidad o entornos de usuario aislados.

### Homelab y autoalojamiento

Utiliza un equipo Windows de alto rendimiento como host de computación remota multiusuario administrado de forma centralizada.

---

## Cómo funciona Avalon

Avalon coordina internamente varias capas del sistema:

```text
Web Management
      │
      ▼
Avalon Control Service
      │
      ▼
Windows Sessions
Virtual Displays
Streaming Processes
Input / Audio Routing
      │
      ▼
Moonlight Clients
```

Los usuarios normales no necesitan conocer estos detalles de implementación.

Creas una instancia; Avalon prepara la sesión, la pantalla, el entorno de streaming y su ciclo de vida; después te conectas.

---

## Modelo de aislamiento

Avalon proporciona **aislamiento a nivel de sesión de Windows**.

Cada instancia tiene su propia sesión de Windows, escritorio, aplicaciones, pantalla, ruta de entrada y ruta de audio.

Sin embargo, las instancias de Avalon **no son máquinas virtuales completas**.

Siguen compartiendo:

- la misma instalación de Windows del host
- el mismo kernel
- la misma CPU física
- la misma GPU física
- los mismos recursos de hardware del host

Por ello, Avalon no debe considerarse una frontera de seguridad equivalente a una VM.

Su objetivo es el streaming multiusuario y multiescritorio eficiente, no la virtualización completa del hardware.

---

## Estado actual

Avalon se encuentra actualmente en fase **Alpha**.

La arquitectura, la interfaz de administración, la capa de compatibilidad y la pila de dispositivos siguen evolucionando.

Durante esta fase pueden aparecer:

- cambios incompatibles
- compatibilidad de hardware incompleta
- cambios de interfaz
- casos límite relacionados con controladores y sesiones
- funciones cuyo comportamiento cambie antes de la versión estable

Avalon todavía no debería utilizarse como infraestructura crítica de producción.

Las pruebas, los registros, los informes de errores reproducibles y la experiencia de uso real son especialmente valiosos en esta etapa.

---

## Plataforma

Objetivo actual:

```text
Windows 10 x64 / Windows 11 x64
```

Avalon está diseñado específicamente alrededor del modelo de escritorio, sesiones y gráficos de Windows.

La compatibilidad con otros sistemas operativos de host no es actualmente un objetivo principal del proyecto.

---

## Rendimiento

El rendimiento real del streaming depende de muchos factores, entre ellos:

- GPU
- compatibilidad del codificador
- controlador gráfico
- resolución
- frecuencia de actualización
- códec
- calidad de red
- capacidad de decodificación del cliente
- número de instancias simultáneas

Avalon no garantiza una resolución, una frecuencia de actualización, un modo HDR o un número concreto de instancias simultáneas en todos los sistemas.

La documentación de compatibilidad se irá ampliando a medida que aumente el alcance de las pruebas.

---

## Filosofía del proyecto

Avalon parte de una idea sencilla:

> Un PC potente no debería estar limitado siempre a una pantalla, un escritorio y un usuario.

El host puede ser una sola máquina. Las experiencias que se ejecutan sobre ella no tienen por qué ser una sola.

---

## Desarrollo

Este README se mantiene como introducción estable al producto Avalon.

Para consultar el progreso de desarrollo en tiempo real y los mensajes del proyecto, revisa [devlog.md](https://github.com/AvalonStream/AvalonStream/blob/main/devlog.md).

Para informar de errores, hacer preguntas o proponer funciones, utiliza [GitHub Issues](https://github.com/AvalonStream/AvalonStream/issues).

---

<div align="center">

### Avalon

**Un host. Varias instancias.**

</div>

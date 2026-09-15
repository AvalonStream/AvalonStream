# Avalon

### Un PC Windows 10/11 x64. Varios escritorios independientes.

Avalon convierte un host Windows 10/11 x64 en múltiples instancias de escritorio accesibles de forma independiente. Cada instancia puede tener su propia sesión de Windows, pantalla virtual, entrada, audio, aplicaciones, juegos y conexión Moonlight.

**Un host. Varias instancias.**

[English](README.md)

[Registro de desarrollo y comentarios](https://github.com/AvalonStream/AvalonStream/blob/main/devlog.md) · [Issues / errores y solicitudes](https://github.com/AvalonStream/AvalonStream/issues)

---

## ¿Qué es Avalon?

Avalon es una plataforma de streaming de escritorio multisesión para Windows 10/11 x64. En lugar de dedicar todo el PC a un único escritorio interactivo, permite ejecutar varias instancias independientes de Windows en el mismo host sin necesitar una máquina virtual completa para cada usuario.

---

## Funciones principales

- Varias instancias independientes de Windows en un solo host
- Un contexto de streaming dedicado para cada instancia
- Pantalla virtual, resolución y frecuencia de actualización por instancia
- Rutas independientes de teclado, ratón y audio de sesión
- Avalon mantiene el ciclo de vida de la sesión sin dejar conectado un cliente RDP externo
- Creación, emparejamiento, estado y diagnóstico desde la Web
- Moonlight sigue siendo el cliente para teléfonos, tabletas, televisores y PCs

---

## Cómo funciona

Crea una instancia, elige la configuración de pantalla y empareja el cliente. Avalon prepara la sesión de Windows, la pantalla virtual, el contexto de streaming y el ciclo de vida; después te conectas con Moonlight.

```text
Windows 10/11 x64 Host
        │
      Avalon
        │
 ┌──────┼──────┐
 ▼      ▼      ▼
Instance 01  Instance 02  Instance 03
 │      │      │
 ▼      ▼      ▼
Moonlight  Moonlight  Moonlight
```

---

## Diseñado para Moonlight

Avalon cambia el lado del host, no el cliente que ya conoces. Moonlight puede seguir utilizándose en Windows, Linux, macOS, Android, iOS/iPadOS, Android TV y otros dispositivos compatibles.

---

## Casos de uso habituales

- Juegos en casa: distintas personas usan instancias diferentes al mismo tiempo
- Múltiples cuentas y cargas de trabajo multiinstancia
- Varios puestos remotos sobre un único PC potente
- Pruebas, automatización y entornos de compatibilidad
- Homelab y computación remota autoalojada

---

## Modelo de aislamiento

Avalon ofrece aislamiento a nivel de sesión de Windows, no aislamiento completo de máquina virtual. Las instancias tienen escritorios, aplicaciones, pantallas, entrada y audio separados, pero comparten Windows, kernel, CPU, GPU y hardware físico del host. No debe tratarse como un límite de seguridad equivalente a una VM.

---

## Plataforma y rendimiento

Avalon está dirigido a Windows 10 y Windows 11 de 64 bits. La resolución, frecuencia, códecs, HDR y número de instancias simultáneas dependen de la GPU, los controladores, el codificador, la red y el hardware del cliente.

---

## Estado del proyecto

Avalon se encuentra actualmente en fase Alpha. La interfaz, la compatibilidad y los componentes de bajo nivel siguen evolucionando, por lo que pueden producirse cambios incompatibles y casos límite específicos de hardware.

---

## Desarrollo y comentarios

Este README es la presentación estable del producto. Las novedades de desarrollo en tiempo real y las indicaciones para dejar mensajes se mantienen en un registro de desarrollo separado.

- [Registro de desarrollo y comentarios](https://github.com/AvalonStream/AvalonStream/blob/main/devlog.md)
- [Issues / errores y solicitudes](https://github.com/AvalonStream/AvalonStream/issues)

**Un host. Varias instancias.**

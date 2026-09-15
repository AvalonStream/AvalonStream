# Avalon

### Um PC Windows 10/11 x64. Vários desktops independentes.

O Avalon transforma um host Windows 10/11 x64 em várias instâncias de desktop acessíveis de forma independente. Cada instância pode ter sua própria sessão do Windows, monitor virtual, entrada, áudio, aplicativos, jogos e conexão Moonlight.

**Um host. Várias instâncias.**

[English](README.md)

[Log de desenvolvimento e feedback](https://github.com/AvalonStream/AvalonStream/blob/main/devlog.md) · [Issues / bugs e sugestões](https://github.com/AvalonStream/AvalonStream/issues)

---

## O que é o Avalon?

Avalon é uma plataforma de streaming de desktop multissessão para Windows 10/11 x64. Em vez de dedicar todo o PC a um único desktop interativo, várias instâncias independentes do Windows podem funcionar lado a lado no mesmo host sem exigir uma máquina virtual completa por usuário.

---

## Principais recursos

- Várias instâncias independentes do Windows em um host
- Contexto de streaming dedicado por instância
- Monitor virtual, resolução e taxa de atualização por instância
- Caminhos independentes de teclado, mouse e áudio da sessão
- Avalon mantém o ciclo de vida da sessão sem exigir um cliente RDP externo conectado
- Criação, pareamento, status e diagnóstico via Web
- Moonlight continua sendo o cliente em celulares, tablets, TVs e PCs

---

## Como funciona

Crie uma instância, escolha as configurações de exibição e faça o pareamento do cliente. O Avalon prepara a sessão do Windows, o monitor virtual, o contexto de streaming e o ciclo de vida; depois basta conectar pelo Moonlight.

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

## Projetado para Moonlight

O Avalon muda o lado do host, não o cliente que você já conhece. O Moonlight continua funcionando em Windows, Linux, macOS, Android, iOS/iPadOS, Android TV e outros dispositivos compatíveis.

---

## Casos de uso comuns

- Jogos em casa: pessoas diferentes usam instâncias diferentes ao mesmo tempo
- Múltiplas contas e cargas multi-instância
- Várias estações remotas em um único PC potente
- Testes, automação e ambientes de compatibilidade
- Homelab e computação remota auto-hospedada

---

## Modelo de isolamento

O Avalon oferece isolamento no nível de sessão do Windows, não isolamento completo de máquina virtual. As instâncias têm desktops, aplicativos, telas, entrada e áudio separados, mas compartilham Windows, kernel, CPU, GPU e hardware físico do host. Não deve ser tratado como uma barreira de segurança equivalente a uma VM.

---

## Plataforma e desempenho

O Avalon é voltado para Windows 10 e Windows 11 de 64 bits. Resolução, taxa de atualização, codecs, HDR e quantidade de instâncias simultâneas dependem da GPU, drivers, codificador, rede e hardware do cliente.

---

## Status do projeto

O Avalon está atualmente em Alpha. Interface, compatibilidade e componentes de baixo nível continuam evoluindo, portanto mudanças incompatíveis e casos específicos de hardware são esperados.

---

## Desenvolvimento e feedback

Este README é a apresentação estável do produto. Atualizações de desenvolvimento em tempo real e orientações de mensagens ficam em um registro de desenvolvimento separado.

- [Log de desenvolvimento e feedback](https://github.com/AvalonStream/AvalonStream/blob/main/devlog.md)
- [Issues / bugs e sugestões](https://github.com/AvalonStream/AvalonStream/issues)

**Um host. Várias instâncias.**

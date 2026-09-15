<div align="center">

# Avalon

### Um PC Windows 10/11 x64. Vários desktops independentes.

Transforme uma única máquina Windows 10/11 x64 em várias instâncias de desktop acessíveis de forma independente, cada uma com sua própria tela, entrada, áudio, aplicativos e conexão de streaming remoto.

**Um host. Várias instâncias.**

[English](README.md) · [简体中文](README-zh-CN.md)

</div>

---

## O que é o Avalon?

Avalon é uma plataforma de streaming de desktop multissessão para Windows 10/11 x64.

Em vez de limitar um PC a um único desktop interativo, o Avalon permite que a mesma máquina hospede várias instâncias independentes do Windows simultaneamente.

Cada instância pode ter seus próprios:

- sessão de desktop do Windows
- monitor virtual
- resolução e taxa de atualização
- fluxo de entrada
- fluxo de áudio
- aplicativos e jogos
- conexão remota via Moonlight

Assim, um único PC potente pode se comportar mais como vários computadores acessíveis remotamente, sem exigir uma máquina virtual completa para cada usuário.

---

## Como isso funciona na prática?

Imagine um PC Windows 10/11 x64 executando três instâncias do Avalon:

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

Cada cliente se conecta ao seu próprio desktop do Windows.

As instâncias funcionam lado a lado sem compartilhar o mesmo desktop, cursor do mouse, saída de áudio ou sessão de aplicativos.

---

## Por que Avalon?

Ferramentas tradicionais de área de trabalho remota geralmente são projetadas em torno de um usuário controlando um único desktop.

Máquinas virtuais resolvem bem o isolamento, mas também adicionam sistemas operacionais extras, consumo de memória, uso de armazenamento, complexidade de GPU e custo de administração.

O Avalon segue outra abordagem.

Ele combina sessões do Windows, telas virtuais, processos de streaming independentes e gerenciamento centralizado de ciclo de vida para permitir que vários desktops interativos coexistam em um único host Windows 10/11 x64.

A complexidade fica dentro do Avalon. Para o usuário, o fluxo é simples:

```text
Criar uma instância
        ↓
Configurar tela e pareamento
        ↓
Abrir o Moonlight
        ↓
Conectar
```

---

## Recursos principais

### Várias instâncias independentes

Execute várias sessões de desktop do Windows no mesmo host ao mesmo tempo.

Cada instância funciona como seu próprio ambiente de desktop interativo.

### Streaming independente

Cada instância possui seu próprio contexto de streaming e pode ser conectada de forma independente por um cliente Moonlight.

Uma TV pode se conectar a uma instância enquanto um tablet ou outro computador se conecta simultaneamente a outra.

### Tela independente

Cada instância pode usar sua própria configuração de tela virtual, incluindo resolução e taxa de atualização.

O Avalon gerencia o ambiente de exibição sem exigir um monitor físico para cada instância.

### Entrada independente

Teclado e mouse são encaminhados para a sessão do Windows correta, em vez de serem compartilhados entre todas as instâncias.

À medida que a pilha de entrada evolui, o Avalon é projetado para avançar em direção a um isolamento de dispositivos cada vez mais completo por instância.

### Áudio independente

Cada instância usa seu próprio caminho de áudio da sessão do Windows, permitindo que usuários diferentes ouçam aplicativos ou jogos diferentes sem simplesmente misturar o áudio entre as instâncias.

### Gerenciamento do ciclo de vida das sessões

O Avalon cria e mantém as sessões por conta própria.

Não é necessário manter um cliente RDP externo conectado apenas para preservar uma instância ativa.

### Gerenciamento via Web

Todas as instâncias são administradas por uma única interface Web.

Operações típicas incluem:

- criar e remover instâncias
- iniciar e parar instâncias
- configurar resolução e taxa de atualização
- parear clientes Moonlight
- consultar o estado das conexões
- visualizar diagnósticos
- gerenciar configurações do host

O uso cotidiano não exige linha de comando.

---

## Projetado para Moonlight

O Avalon preserva a experiência de streaming do Moonlight que você já conhece.

Você pode continuar usando Moonlight em dispositivos como:

- Windows
- Linux
- macOS
- Android
- iOS / iPadOS
- Android TV
- Smart TVs e dispositivos de streaming compatíveis com Moonlight

O Avalon muda a organização do host; ele não obriga o usuário a aprender um cliente de streaming completamente novo.

---

## Casos de uso

### Jogos em casa

Transforme um único PC gamer em vários ambientes de jogo independentes para diferentes pessoas na mesma casa.

Uma pessoa pode jogar na TV da sala enquanto outra se conecta a outra instância por um portátil ou notebook.

### Múltiplas contas e instâncias

Execute aplicativos, contas ou sessões de jogos diferentes em ambientes Windows separados na mesma máquina.

### Estação de trabalho remota

Use um desktop potente como vários espaços de trabalho remotos acessíveis de forma independente.

### Testes e desenvolvimento

Mantenha várias sessões do Windows para testes de software, automação, compatibilidade ou ambientes de usuário isolados.

### Homelab e self-hosting

Use uma máquina Windows de alto desempenho como host de computação remota multiusuário gerenciado centralmente.

---

## Como o Avalon funciona

O Avalon coordena internamente várias camadas do sistema:

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

O usuário comum não precisa compreender esses detalhes de implementação.

Você cria uma instância; o Avalon prepara a sessão, a tela, o ambiente de streaming e o ciclo de vida; depois você se conecta.

---

## Modelo de isolamento

O Avalon oferece **isolamento no nível de sessão do Windows**.

Cada instância possui sua própria sessão do Windows, desktop, aplicativos, tela, caminho de entrada e caminho de áudio.

Porém, instâncias do Avalon **não são máquinas virtuais completas**.

Elas ainda compartilham:

- a mesma instalação do Windows do host
- o mesmo kernel
- a mesma CPU física
- a mesma GPU física
- os mesmos recursos de hardware do host

Portanto, o Avalon não deve ser tratado como uma fronteira de segurança equivalente a uma VM.

Seu objetivo é streaming multiusuário e multidesktop eficiente, não virtualização completa de hardware.

---

## Estado atual

O Avalon está atualmente em fase **Alpha**.

A arquitetura, a interface de gerenciamento, a camada de compatibilidade e a pilha de dispositivos continuam evoluindo.

Nesta fase, podem ocorrer:

- mudanças incompatíveis
- compatibilidade de hardware incompleta
- mudanças de interface
- casos extremos envolvendo drivers e sessões
- comportamentos de recursos que ainda podem mudar antes da versão estável

O Avalon ainda não deve ser usado como infraestrutura crítica de produção.

Testes, logs, relatórios de bugs reproduzíveis e feedback de uso real são especialmente valiosos neste estágio.

---

## Plataforma

Alvo atual:

```text
Windows 10 x64 / Windows 11 x64
```

O Avalon foi projetado especificamente em torno do modelo de desktop, sessões e gráficos do Windows.

Suporte a outros sistemas operacionais de host não é atualmente um objetivo principal do projeto.

---

## Desempenho

O desempenho real de streaming depende de muitos fatores, incluindo:

- GPU
- suporte de encoder
- driver gráfico
- resolução
- taxa de atualização
- codec
- qualidade da rede
- capacidade de decodificação do cliente
- quantidade de instâncias simultâneas

O Avalon não garante uma resolução, taxa de atualização, modo HDR ou número específico de instâncias simultâneas em todos os sistemas.

A documentação de compatibilidade será ampliada conforme os testes crescerem.

---

## Filosofia do projeto

O Avalon parte de uma ideia simples:

> Um PC potente não deveria estar permanentemente limitado a uma tela, um desktop e um usuário.

O host pode ser uma única máquina. As experiências executadas sobre ele não precisam ser únicas.

---

## Desenvolvimento

Este README é mantido como a introdução estável ao produto Avalon.

Para atualizações de desenvolvimento em tempo real e mensagens do projeto, consulte [devlog.md](https://github.com/AvalonStream/AvalonStream/blob/main/devlog.md).

Para relatar bugs, fazer perguntas ou sugerir recursos, use [GitHub Issues](https://github.com/AvalonStream/AvalonStream/issues).

---

<div align="center">

### Avalon

**Um host. Várias instâncias.**

</div>

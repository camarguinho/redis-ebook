# Introdução

## O que é Redis

Redis (Remote Dictionary Server) é uma solução de armazenamento em memória, de código aberto, que pode ser usada como banco de dados, cache e message broker. Ele é conhecido por sua alta performance e suporte a diversas estruturas de dados.

## Para que serve

Redis é amplamente utilizado para:
- Armazenamento em cache para melhorar a performance de aplicações.
- Gerenciamento de sessões em aplicações web.
- Implementação de filas e sistemas de mensagens.
- Contadores e rankings em tempo real.

## Arquitetura Geral

Redis utiliza um modelo single-threaded, onde todas as operações são executadas em uma única thread. Ele armazena os dados em memória, com opções de persistência para disco.

## Casos de Uso Comuns

- **Cache**: Reduz a latência de acesso a dados frequentemente utilizados.
- **Pub/Sub**: Implementação de sistemas de mensagens em tempo real.
- **Filas**: Gerenciamento de tarefas assíncronas.
- **Sessões**: Armazenamento de sessões de usuários em aplicações web.

---

[Próximo capítulo: Conceitos Básicos](02-conceitos-basicos.md)
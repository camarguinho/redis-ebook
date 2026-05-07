# Conceitos Básicos

## Estruturas de Dados

Redis suporta diversas estruturas de dados:
- **Strings**: Valores simples, como "chave:valor".
- **Hashes**: Estruturas semelhantes a objetos JSON.
- **Lists**: Listas ordenadas de strings.
- **Sets**: Conjuntos não ordenados de strings únicas.
- **Sorted Sets**: Conjuntos ordenados com pontuações associadas.

## Modelo Single-threaded

Redis utiliza um modelo single-threaded, o que significa que todas as operações são executadas em uma única thread. Isso simplifica o design e evita problemas de concorrência, mas exige atenção ao desempenho de comandos.

## Memória e Persistência

Redis armazena os dados em memória para alta performance. Ele oferece dois mecanismos principais de persistência:
- **RDB (Redis Database)**: Snapshots periódicos dos dados.
- **AOF (Append-Only File)**: Log de operações para recriar o estado.

## TTL, Expiração e Políticas de Eviction

- **TTL (Time to Live)**: Define um tempo de vida para as chaves.
- **Expiração**: Chaves podem ser configuradas para expirar automaticamente.
- **Eviction**: Quando a memória está cheia, Redis aplica políticas como LRU (Least Recently Used) para remover chaves.

---

[Capítulo anterior: Introdução](01-introducao.md) | [Próximo capítulo: Problemas que o Redis Resolve](03-problemas-que-o-redis-resolve.md)
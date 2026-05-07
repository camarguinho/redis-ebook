# Limitações do Redis

## Onde Não Usar

Redis não é ideal para:
- Armazenamento de dados críticos sem persistência adequada.
- Consultas complexas ou relacionais.
- Cenários com grandes volumes de dados que excedem a memória disponível.

## Riscos de Perda de Dados

Redis pode perder dados em cenários como:
- Falhas antes de persistir no disco.
- Configuração inadequada de persistência (RDB ou AOF).

## Impacto de Memória

Redis armazena todos os dados em memória, o que pode ser caro em termos de custo e capacidade.

## Limitações Arquiteturais

- Modelo single-threaded pode ser um gargalo em workloads intensivos.
- Gerenciamento de clusters pode ser complexo.

---

[Capítulo anterior: Problemas que o Redis Resolve](03-problemas-que-o-redis-resolve.md) | [Próximo capítulo: Erros Comuns e Como Corrigir](05-erros-comuns.md)
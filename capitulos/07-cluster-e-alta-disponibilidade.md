# Cluster e Alta Disponibilidade

## Sentinel

Redis Sentinel fornece alta disponibilidade monitorando instâncias e realizando failover automático.

Configuração básica:
```bash
sentinel monitor mymaster 127.0.0.1 6379 2
sentinel auth-pass mymaster senha
```

## Cluster Mode

Redis Cluster permite sharding automático e replicação.

Criação de cluster:
```bash
redis-cli --cluster create 127.0.0.1:7000 127.0.0.1:7001 127.0.0.1:7002 --cluster-replicas 1
```

## Sharding

Distribui dados entre múltiplos nós para escalabilidade horizontal.

## Replicação

Redis suporta replicação mestre-escravo para redundância de dados.

## Failover

Em caso de falha, o Sentinel ou Cluster realiza failover automático para uma réplica.

## Modo Replicação

No modo de replicação, o Redis suporta replicação mestre-escravo para redundância de dados.

Exemplo de configuração:
```java
Jedis jedis = new Jedis("127.0.0.1", 6379); // Mestre
jedis.slaveof("127.0.0.1", 6380); // Configura o escravo
```

---

[Capítulo anterior: Redis com Java](06-redis-com-java.md) | [Próximo capítulo: Segurança](08-seguranca.md)

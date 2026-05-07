# Redis com Java

## Configuração de Clientes

### Jedis

Exemplo de configuração:
```java
Jedis jedis = new Jedis("localhost", 6379);
jedis.auth("senha");
```

### Lettuce

Exemplo de configuração:
```java
RedisClient redisClient = RedisClient.create("redis://localhost:6379");
StatefulRedisConnection<String, String> connection = redisClient.connect();
```

### Spring Data Redis

Exemplo de configuração:
```java
@Bean
public RedisTemplate<String, Object> redisTemplate(RedisConnectionFactory connectionFactory) {
    RedisTemplate<String, Object> template = new RedisTemplate<>();
    template.setConnectionFactory(connectionFactory);
    return template;
}
```

### Jedis com Pool de Conexões

Para ambientes de produção, é recomendado usar um pool de conexões:
```java
JedisPool pool = new JedisPool(new JedisPoolConfig(), "localhost");
try (Jedis jedis = pool.getResource()) {
    jedis.set("chave", "valor");
    String valor = jedis.get("chave");
}
```

### Lettuce com Programação Reativa

Lettuce suporta programação reativa para aplicações modernas:
```java
RedisClient redisClient = RedisClient.create("redis://localhost:6379");
RedisReactiveCommands<String, String> commands = redisClient.connect().reactive();
commands.set("chave", "valor").subscribe();
commands.get("chave").subscribe(valor -> System.out.println("Valor: " + valor));
```

### Spring Data Redis com Serializadores

Para evitar problemas com objetos complexos, configure serializadores:
```java
@Bean
public RedisTemplate<String, Object> redisTemplate(RedisConnectionFactory connectionFactory) {
    RedisTemplate<String, Object> template = new RedisTemplate<>();
    template.setConnectionFactory(connectionFactory);
    template.setKeySerializer(new StringRedisSerializer());
    template.setValueSerializer(new GenericJackson2JsonRedisSerializer());
    return template;
}
```

## Exemplos Práticos

### Cache
```java
jedis.set("chave", "valor");
String valor = jedis.get("chave");
```

### Pub/Sub
```java
jedis.publish("canal", "mensagem");
```

### Streams
```java
Map<String, String> message = new HashMap<>();
message.put("campo", "valor");
jedis.xadd("stream", StreamEntryID.NEW_ENTRY, message);
```

---

[Capítulo anterior: Erros Comuns e Como Corrigir](05-erros-comuns.md) | [Próximo capítulo: Cluster e Alta Disponibilidade](07-cluster-e-alta-disponibilidade.md)
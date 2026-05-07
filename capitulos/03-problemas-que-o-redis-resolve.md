# Problemas que o Redis Resolve

## Cache

Redis é amplamente utilizado como cache para armazenar dados frequentemente acessados, reduzindo a latência e a carga em bancos de dados tradicionais.

Exemplo em Java (Jedis):
```java
Jedis jedis = new Jedis("localhost");
jedis.set("chave", "valor");
String valor = jedis.get("chave");
```

## Rate Limiting

Redis pode ser usado para implementar limites de taxa (rate limiting) em APIs.

Exemplo:
```java
long requests = jedis.incr("user:123:requests");
if (requests > 100) {
    System.out.println("Limite excedido");
}
```

## Filas e Pub/Sub

Redis suporta filas e sistemas de mensagens em tempo real com Pub/Sub.

Exemplo:
```java
// Publicador
jedis.publish("canal", "mensagem");

// Assinante
jedis.subscribe(new JedisPubSub() {
    @Override
    public void onMessage(String channel, String message) {
        System.out.println("Recebido: " + message);
    }
}, "canal");
```

## Fluxo de Pub/Sub

```plaintext
+-----------+       +-----------+       +-----------+
| Publisher | ----> |   Redis   | ----> | Subscriber |
+-----------+       +-----------+       +-----------+
```

Neste fluxo, o Publisher envia mensagens para um canal no Redis, que as distribui para os Subscribers inscritos.

## Sessões

Redis é usado para armazenar sessões de usuários em aplicações web.

## Locks Distribuídos

Redis pode implementar locks distribuídos para sincronização entre sistemas.

Exemplo:
```java
String lockKey = "lock";
String lockValue = UUID.randomUUID().toString();
boolean locked = jedis.setnx(lockKey, lockValue) == 1;
if (locked) {
    jedis.expire(lockKey, 30); // Expiração do lock

    // Liberação do lock com Lua script
    String script = "if redis.call('get', KEYS[1]) == ARGV[1] then " +
                    "return redis.call('del', KEYS[1]) " +
                    "else return 0 end";
    jedis.eval(script, Collections.singletonList(lockKey), Collections.singletonList(lockValue));
}
```

## Streams

Redis Streams permite o processamento de dados em tempo real.

Exemplo de escrita:
```java
Map<String, String> message = new HashMap<>();
message.put("campo", "valor");
jedis.xadd("stream", StreamEntryID.NEW_ENTRY, message);
```

Exemplo de leitura:
```java
List<Map.Entry<String, List<StreamEntry>>> entries = jedis.xread(
    XReadParams.xReadParams().count(1).block(0),
    new StreamEntryID("0-0"), "stream"
);
for (Map.Entry<String, List<StreamEntry>> entry : entries) {
    System.out.println("Stream: " + entry.getKey());
    for (StreamEntry streamEntry : entry.getValue()) {
        System.out.println("ID: " + streamEntry.getID());
        System.out.println("Campos: " + streamEntry.getFields());
    }
}
```

---

[Capítulo anterior: Conceitos Básicos](02-conceitos-basicos.md) | [Próximo capítulo: Limitações do Redis](04-limitacoes-do-redis.md)
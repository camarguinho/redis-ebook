# Segurança

## Autenticação

Redis suporta autenticação básica com senhas configuradas no arquivo `redis.conf`:
```conf
requirepass senha
```

## TLS

Redis suporta conexões seguras com TLS. Configuração básica:
```conf
tls-cert-file /etc/redis/tls/redis.crt
tls-key-file /etc/redis/tls/redis.key
tls-ca-cert-file /etc/redis/tls/ca.crt
tls-auth-clients yes
```

## Configurações Essenciais

- **Proteja o Redis com firewalls**: Restrinja o acesso à porta 6379.
- **Desative comandos perigosos**: Use `rename-command` para desativar comandos como `FLUSHALL`.
- **Habilite autenticação**: Sempre configure uma senha forte.

---

[Capítulo anterior: Cluster e Alta Disponibilidade](07-cluster-e-alta-disponibilidade.md) | [Próximo capítulo: Monitoramento](09-monitoramento.md)
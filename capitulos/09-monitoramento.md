# Monitoramento

## Métricas Importantes

- **Uso de memória**: Monitore o uso com `INFO memory`.
- **Latência**: Use `LATENCY DOCTOR` para identificar problemas.
- **Comandos lentos**: Identifique com `SLOWLOG`.

## Logs

Configure logs no arquivo `redis.conf`:
```conf
logfile /var/log/redis/redis.log
loglevel notice
```

## Alertas

Use ferramentas como Prometheus e Grafana para configurar alertas baseados em métricas do Redis.

## Capacity Planning

Planeje capacidade com base em:
- **Uso de memória**.
- **Taxa de crescimento de dados**.
- **Carga esperada de leitura/escrita**.

---

[Capítulo anterior: Segurança](08-seguranca.md) | [Próximo capítulo: Guia de Certificação](10-guia-de-certificacao.md)
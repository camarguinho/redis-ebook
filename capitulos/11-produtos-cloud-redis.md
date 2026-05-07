[Capítulo anterior: Guia de Certificação](10-guia-de-certificacao.md)

# Produtos Cloud Baseados em Redis

## Introdução

Redis é uma tecnologia amplamente utilizada em soluções de armazenamento em memória, e sua flexibilidade permite que seja integrada em diversos cenários. Este capítulo explora os serviços baseados em Redis oferecidos por Azure e AWS. Além disso, apresentamos um desenho arquitetural ASCII para ilustrar um cenário real de uso eficiente do Redis em cloud.

---

## Produtos Cloud Baseados em Redis

### Azure Cache for Redis
- **Descrição**: Serviço gerenciado de Redis oferecido pela Microsoft Azure.
- **Recursos**:
  - Alta disponibilidade com réplicas.
  - Integração com outros serviços Azure, como Azure Functions.
  - Suporte a Redis Enterprise para funcionalidades avançadas.

### Amazon ElastiCache for Redis
- **Descrição**: Serviço gerenciado de Redis oferecido pela AWS.
- **Recursos**:
  - Suporte a sharding automático.
  - Failover automático para alta disponibilidade.
  - Integração com serviços AWS, como Lambda e DynamoDB.

### Comparação
| Recurso                  | Azure Cache for Redis | Amazon ElastiCache for Redis |
|--------------------------|-----------------------|------------------------------|
| Alta Disponibilidade     | Sim                   | Sim                          |
| Sharding Automático      | Não                   | Sim                          |
| Integração com Serviços  | Azure Functions       | AWS Lambda                   |

---

## Desenho Arquitetural

Abaixo está um exemplo de arquitetura eficiente utilizando Redis em cloud:

```plaintext
+-------------------+       +-------------------+       +-------------------+
|   Frontend Web    | ----> |   Redis Cache     | ----> |   Banco de Dados   |
+-------------------+       +-------------------+       +-------------------+
        |                        |                            |
        v                        v                            v
+-------------------+   +-------------------+       +-------------------+
| Azure Functions   |   | AWS Lambda        |       |   Backup em S3    |
+-------------------+   +-------------------+       +-------------------+
```

### Explicação
1. **Frontend Web**: Envia requisições para o Redis Cache para dados frequentemente acessados.
2. **Redis Cache**: Atua como camada intermediária para reduzir a latência e aliviar a carga no banco de dados.
3. **Banco de Dados**: Armazena dados persistentes.
4. **Azure Functions e AWS Lambda**: Processam eventos e atualizam o Redis Cache e o banco de dados.
5. **Backup em S3**: Garante a persistência dos dados críticos.

---

[Capítulo anterior: Guia de Certificação](10-guia-de-certificacao.md)
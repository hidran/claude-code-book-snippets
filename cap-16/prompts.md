# Capitolo 16 — Deploy su AWS con CloudFormation

## 🔁 Genera CloudFormation per uno stack applicativo

```
Genera un template CloudFormation YAML per un'applicazione [NOME] con:
- Stack: [backend in Node.js/Python/Java] + [frontend in React/Vue/Angular]
- Database: [MySQL/PostgreSQL/MongoDB] gestito su RDS (o DocumentDB)
- Regione AWS: [eu-west-1/us-east-1/...]
- Deployment target: ECS Fargate per il backend, S3 + CloudFront per il frontend
- Ambienti: dev, staging, prod tramite Parameters

Il template deve includere:
- VPC con 2 subnet pubbliche (ALB) e 2 private (ECS, RDS) in 2 AZ
- Security group con least privilege (ECS → RDS solo su porta DB)
- IAM execution role per ECS con accesso a Secrets Manager e S3
- ECR repository per l'immagine Docker
- CloudWatch log groups per ogni container
- Outputs: ALBDnsName, CloudFrontDomainName, EcrRepositoryUri

Output: infra/cloudformation.yaml. Aggiungi commenti inline per le sezioni
non ovvie (es. perché quel DependsOn, perché quella policy IAM).
```

Adatta `[NOME]`, lo stack, il database e la regione al tuo progetto.

# Postagem no Linkedin

[BLOG] Como criar uma pipeline CI/CD para o GitHub Actions e testar localmente?

O uso de pipeline é util para automatizar o processo de deploy, executar testes automatizados, agendar tarefas, fazer verificação de segurança e muitos outros. Quase tudo que queira executar de forma automática, da para fazer com uma pipeline.

Nesse blog post, mostro:

- Criação de um container
- Criação de um job para CI
- Criação de um job para build e push da imagem Docker
- Criação de um aletar via Telegram em caso de sucesso e de falha da pipeline
- Como usar o Act para simular o GitHub Actions localmente

O arquivo completo da pipeline pode ser vista [aqui](https://github.com/deirofelippe/agenda-telefonica/blob/main/.github/workflows/backend.yaml).

#cicd #githubactions #act #docker #devops

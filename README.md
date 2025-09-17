# 📘 Desafio – AWS Step Functions  

## 🚀 Descrição do Desafio  
Este laboratório teve como objetivo **consolidar o aprendizado sobre workflows automatizados com AWS Step Functions**. Este desafio faz parte do Bootcamp Santander Code Girls - 2025. 
Foram criados dois modelos de orquestração, utilizando serviços da AWS de forma integrada:  

1. **Mapa Distribuído com S3** – processamento paralelo de múltiplos objetos de dados.  
2. **Padrão de Retorno de Chamada com SQS** – coordenação assíncrona via callback pattern.  

O entregável é este repositório, que reúne anotações, códigos e prints das execuções, servindo como **guia de estudos e referência para futuras implementações**.  

---

## 🎯 Objetivos de Aprendizagem  
Ao concluir este desafio, consegui:  

- ✔️ Aplicar na prática os conceitos de Step Functions.  
- ✔️ Documentar os processos técnicos de forma clara e estruturada.  
- ✔️ Utilizar o GitHub como ferramenta de compartilhamento e versionamento de documentação técnica.  
- ✔️ Integrar serviços da AWS como **Lambda, S3, DynamoDB, SQS e SNS** em workflows automatizados.  

---

## 🛠️ Modelos Criados  

### 🔹 1. Mapa Distribuído com S3
- **Descrição:** Este workflow demonstra como processar múltiplos arquivos armazenados em um bucket S3 usando o recurso *Distributed Map*.  
- **Serviços usados:** S3, Lambda, DynamoDB, CloudWatch, Step Functions, CloudFormation.  
- **Fluxo realizado:**  
  1. O Step Functions lista os objetos dentro de um prefixo no bucket S3.  
  2. Cada objeto é processado em paralelo.  
  3. Métricas são enviadas para o CloudWatch.  
  4. Um resumo é armazenado no DynamoDB.  
  5. Por fim, uma função Lambda gera o relatório agregado.

## 📸 Prints da Execução

- **Bucket S3 criado para os arquivos**  
<img width="1920" height="1080" alt="Bucket" src="https://github.com/user-attachments/assets/06afe26d-e73c-41e2-8a06-5dafde10e748" />

- **Implantação da pilha via CloudFormation**  
<img width="1920" height="1080" alt="CloudFormation" src="https://github.com/user-attachments/assets/1415c40b-0041-4c2e-acc7-fc1f8704c043" />

- **Máquina de estado criada (Distributed Map)**  
<img width="1920" height="1080" alt="Máquina de estado" src="https://github.com/user-attachments/assets/5a8ea2d7-07d5-428b-b144-89099713bc72" />

- **Execução com êxito**  
<img width="1920" height="1080" alt="Execução com êxito" src="https://github.com/user-attachments/assets/6ae599a4-fc6f-417e-8eef-8bf65e61a633" />

- **Função Lambda configurada**  
<img width="1920" height="1080" alt="Função Lambda" src="https://github.com/user-attachments/assets/41775081-e44d-4a22-8cfb-4ac065312bdb" />

- **Tabela DynamoDB criada** 
<img width="1920" height="1080" alt="Tabela DynamoDB" src="https://github.com/user-attachments/assets/76062655-7ac9-476c-99c0-25fbf17bf053" />

- **Logs no CloudWatch**  
<img width="1920" height="1080" alt="Logs no CloudWatch" src="https://github.com/user-attachments/assets/0cc308a0-d2ae-482c-8129-3edb41d11ae2" />

---

### 🔹 2. Padrão de Retorno de Chamada com SQS  
- **Descrição:** Este workflow demonstra o uso do *callback pattern*, onde o Step Functions pausa a execução até receber a resposta de um serviço externo.  
- **Serviços usados:** SQS, Lambda, SNS, Step Functions.  
- **Fluxo realizado:**  
  1. O Step Functions envia uma mensagem para a fila SQS.  
  2. Um Lambda consome a mensagem e executa o processamento.  
  3. O Lambda responde ao Step Functions com sucesso ou falha via `SendTaskSuccess` ou `SendTaskFailure`.  
  4. O fluxo continua e publica uma notificação no tópico SNS. 

## 📸 Prints da Execução  

- **Criação da State Machine (Máquina de estado)** 
<img width="1920" height="1080" alt="State Machine" src="https://github.com/user-attachments/assets/7b847627-f515-4c59-ad80-282bec193e6c" />

- **Execução em andamento**  
<img width="1920" height="1080" alt="Execução em andamento" src="https://github.com/user-attachments/assets/8abf4e62-1739-4f47-9a24-896f31a49bf2" />

- **Execução com êxito**  
<img width="1920" height="1080" alt="Execução com sucesso" src="https://github.com/user-attachments/assets/23b9e5ca-d3cd-4972-82cd-74b8822b45d9" />

- **Tópico SNS criado**  
<img width="1920" height="1080" alt="Tópico SNS criado" src="https://github.com/user-attachments/assets/a747d520-97c2-4fa7-921f-7c2b6c33dd2b" />

- **Filas SQS criadas**  
 <img width="1920" height="1080" alt="Filas SQS criadas" src="https://github.com/user-attachments/assets/14ea1de0-e936-44e4-811c-9e06e56425c6" />

- **Função Lambda integrada**  
<img width="1920" height="1080" alt="Função Lambda integrada" src="https://github.com/user-attachments/assets/2ccc1710-7188-453b-b701-e37969765868" />


## 📌 Insights e Aprendizados

- O Distributed Map é ideal para paralelismo em larga escala, processando milhares de arquivos simultaneamente.

- O Callback Pattern permite criar workflows resilientes e assíncronos, integrando sistemas externos de forma confiável.

- A visualização gráfica do Step Functions facilita o debug e o entendimento dos fluxos.

- Documentar cada passo no GitHub ajuda a consolidar o aprendizado e servir de referência futura.
---

## 📖 Referências  
- [AWS Step Functions – Distributed Map](https://docs.aws.amazon.com/step-functions/latest/dg/concepts-distributed-map.html)  
- [AWS Step Functions – Callback Pattern com SQS](https://docs.aws.amazon.com/step-functions/latest/dg/callback-task-sample-sqs.html)  

---

## ✨ Autora

**Ingrid Moitinho**

* LinkedIn: [LinkedIn](https://www.linkedin.com/in/ingridmoitinho/)
* GitHub: [GitHub](https://github.com/ingridmoitinho)
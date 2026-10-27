# Implementação de Stack com AWS CloudFormation

Este repositório contém a documentação técnica, anotações de estudo e modelos (templates) utilizados durante a criação e implementação da minha primeira **Stack no AWS CloudFormation**. O objetivo deste projeto é consolidar conceitos de **Infraestrutura como Código (IaC)** no ambiente Amazon Web Services (AWS).

---

## 📌 Objetivos

- **Prática de IaC:** Automatizar o aprovisionamento de recursos na AWS utilizando ficheiros declarativos (YAML/JSON).
- **Documentação Técnica:** Organizar insights, comandos e arquitetura implementada para consultas futuras.
- **Controlo de Versão:** Manter os modelos e a documentação versionados via Git/GitHub.

---

## 🛠️ Tecnologias e Serviços Utilizados

- **AWS CloudFormation:** Serviço de gestão e automação de infraestrutura declarativa.
- **Amazon EC2 / VPC:** (Ajuste para os recursos criados no seu laboratório, ex: Instância EC2, Security Group, S3, etc.)
- **YAML / JSON:** Linguagem declarativa utilizada para definir a stack.
- **AWS Management Console / AWS CLI:** Interface de criação e gestão de eventos da stack.

---

## 🏗️ Estrutura do Template CloudFormation

O ficheiro do template (`templates/ec2-stack.yaml`) declara as seguintes secções principais:

```yaml
AWSTemplateFormatVersion: '2010-09-09'
Description: 'Minha primeira Stack CloudFormation - Lab Prático'

Parameters:
  InstanceType:
    Type: String
    Default: t2.micro
    AllowedValues:
      - t2.micro
      - t3.micro
    Description: 'Tipo da instância EC2'

Resources:
  MyEC2Instance:
    Type: 'AWS::EC2::Instance'
    Properties:
      InstanceType: !Ref InstanceType
      ImageId: 'ami-0c55b159cbfafe1f0' # Substituir pela AMI correspondente da região

Outputs:
  InstanceId:
    Description: 'ID da Instância EC2 criada'
    Value: !Ref MyEC2Instance

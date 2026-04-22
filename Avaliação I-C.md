# Avaliação Prática – Programação para Web (Java + Spring Boot + JPA + MySQL)

## Enunciado

Você deverá desenvolver uma API utilizando **Java com Spring Boot, JPA e MySQL**, simulando um sistema de **agendamento de consultas**. O sistema permitirá o cadastro de pacientes, médicos e o registro de consultas, incluindo validações de horário e cálculo do valor total da consulta, quando aplicável.

A entrega consiste no desenvolvimento do **backend completo** com as funcionalidades descritas abaixo.

---

## Funcionalidades

1. **Cadastro de Pacientes**
2. **Cadastro de Médicos**
3. **Registro de Consultas**

Cada consulta deve conter:

* Um paciente
* Um médico
* Data e hora da consulta
* Status da consulta
* Valor da consulta
* Observação (opcional)

---

## Tecnologias obrigatórias

* Java + Spring Boot
* Spring Web
* Spring Data JPA
* MySQL
* Utilização de DTOs (`record` recomendado)
* Camadas bem definidas: **Controller, Service, Repository, Entity, DTO**

---

## Critérios de Avaliação (Total: 10,0 pontos)

| Critério                                                           |    Peso |
| ------------------------------------------------------------------ | ------: |
| CRUD completo e funcional de uma entidade (Paciente ou Médico)     | 5,0 pts |
| Registro funcional de uma consulta com validações corretas         | 2,0 pts |
| Criação de todos os models e seus relacionamentos                  |  1,0 pt |
| Uso de DTOs organizados e bem estruturados                         |  1,0 pt |
| Camada de serviço com regras de negócio aplicadas corretamente     |  1,0 pt |


---

## Regras de Negócio

* Não deve ser permitido agendar consulta para **data/hora no passado**.
* Um médico **não pode possuir duas consultas no mesmo horário**.
* Um paciente **não pode possuir duas consultas no mesmo horário**.
* O status da consulta deve ser informado no momento do cadastro. Exemplos:
  * `AGENDADA`
  * `REALIZADA`
  * `CANCELADA`
* O valor da consulta deve ser maior que zero.
* Os dados da consulta devem ser retornados no DTO de resposta.

---

## Sugestão de Entidades

<img width="704" height="273" alt="image" src="https://github.com/user-attachments/assets/07afb0a7-e493-4608-ac7c-0f78a79459ec" />


---

## Exemplos de Requisições em JSON

### Paciente – Criar (POST)

```json
{
  "name": "João da Silva",
  "email": "joao@email.com",
  "cpf": "123.456.789-00"
}
```

### Médico – Criar (POST)

```json
{
  "name": "Dra. Mariana Souza",
  "specialty": "Cardiologia",
  "crm": "CRM12345"
}
```

### Consulta – Criar (POST)

```json
{
  "patientId": 1,
  "doctorId": 1,
  "appointmentDate": "2026-05-10T14:30:00",
  "status": "AGENDADA",
  "price": 250.00,
  "notes": "Paciente retornará com exames."
}
```

### Consulta – Resposta (GET)

```json
{
  "id": 1,
  "patient": {
    "id": 1,
    "name": "João da Silva",
    "cpf": "123.456.789-00"
  },
  "doctor": {
    "id": 1,
    "name": "Dra. Mariana Souza",
    "specialty": "Cardiologia",
    "crm": "CRM12345"
  },
  "appointmentDate": "2026-05-10T14:30:00",
  "status": "AGENDADA",
  "price": 250.00,
  "notes": "Paciente retornará com exames."
}
```

---

## Entrega

* Suba o projeto no **GitHub pessoal** e compartilhe o link.
* O repositório deve conter:

  * Código-fonte organizado (`Controller`, `Service`, `Repository`, `Entity`, `DTO`)
  * `README.md` com instruções para rodar o projeto
  * Exemplos dos endpoints testados
---


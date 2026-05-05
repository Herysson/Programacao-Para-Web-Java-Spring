# Camada de Serviço

## ✅ O que é a Camada de Serviço?

A **camada de serviço** (ou *Service Layer*) é responsável por implementar **as regras de negócio** da aplicação. Ela atua como **ponte entre o controller e o repositório**, organizando melhor o código e separando responsabilidades.

- **Controller:** recebe as requisições HTTP e repassa os dados.
- **Service:** aplica lógica de negócio (validações, cálculos, etc.).
- **Repository:** acessa o banco de dados.

> 🧠 *Regra de negócio* é qualquer lógica importante para o funcionamento correto da aplicação. Ex: "um usuário só pode ter no máximo 3 telefones cadastrados".

---

## 🧩 Estrutura no seu projeto

No seu repositório `UserPhoneAPI`, temos as entidades `User` e `Phone`, e suas respectivas camadas de serviço:

📁 `src/main/java/com/example/userphone/service`

- `UserService.java`
- `PhoneService.java`

---

## 👨‍🏫 Vamos olhar o `UserService`

```java
@Service
public class UserService {
    private final UserRepository userRepository;

    public UserService(UserRepository userRepository) {
        this.userRepository = userRepository;
    }

    public List<User> getAllUsers() {
        return userRepository.findAll();
    }

    public User createUser(User user) {
        return userRepository.save(user);
    }

    public Optional<User> getUserById(Long id) {
        return userRepository.findById(id);
    }

    public void deleteUser(Long id) {
        userRepository.deleteById(id);
    }
}
```

---

## 🔍 Explicação por partes

| Método                | O que faz                                                                 |
|-----------------------|---------------------------------------------------------------------------|
| `getAllUsers()`       | Busca todos os usuários no banco.                                         |
| `createUser(user)`    | Salva um novo usuário.                                                    |
| `getUserById(id)`     | Busca um usuário específico pelo ID.                                      |
| `deleteUser(id)`      | Deleta um usuário com base no ID.                                         |

---

## 🧠 Onde entra a "regra de negócio"?

No seu repositório, os serviços ainda estão **bastante diretos**, sem regras complexas. Mas **caso você queira** adicionar uma regra, por exemplo:

> ❗ *"Um usuário não pode ser criado com e-mail repetido."*

Você adicionaria essa lógica **dentro do `UserService`**, antes de salvar:

```java
public User createUser(User user) {
    if (userRepository.existsByEmail(user.getEmail())) {
        throw new IllegalArgumentException("E-mail já está em uso!");
    }
    return userRepository.save(user);
}
```

---

## 📌 Como utilizar a camada de serviço

No `UserController`, veja como a camada de serviço é usada:

```java
@RestController
@RequestMapping("/users")
public class UserController {
    private final UserService userService;

    public UserController(UserService userService) {
        this.userService = userService;
    }

    @GetMapping
    public List<User> getAllUsers() {
        return userService.getAllUsers();
    }

    @PostMapping
    public User createUser(@RequestBody User user) {
        return userService.createUser(user);
    }

    // outros endpoints...
}
```

🔄 O controller **chama o serviço**, e o serviço **chama o repositório**.

---

## 🧪 Benefícios da Camada de Serviço

✅ Centraliza regras de negócio  
✅ Facilita testes unitários  
✅ Diminui a responsabilidade do controller  
✅ Melhora a organização do projeto

---


## 🛠️ Atividade – Implementando Regras de Negócio na Camada de Serviço

### 🎯 Objetivo:
Compreender o papel da **camada de serviço** em uma aplicação Spring Boot, através da implementação de **regras de negócio** no projeto `UserPhoneAPI`.

---

### 📂 Repositório base:
[https://github.com/Herysson/UserPhoneAPI](https://github.com/Herysson/UserPhoneAPI)

---

### 🛠️ Tarefas:

Implemente **as seguintes regras de negócio** na camada de serviço:

---

### ✅ 1. Um usuário pode ter no máximo **3 telefones** cadastrados
- **O que fazer:** Antes de salvar um novo telefone, verifique quantos telefones o usuário já tem.

### ✅ 2. Validar o **DDD** do telefone
- **O que fazer:** O DDD deve estar entre 11 e 99. Verifique antes de salvar o telefone.

### ✅ 3. Não permitir **e-mails repetidos** para usuários
- **O que fazer:** Antes de salvar um novo usuário, verificar se o e-mail já existe.

---

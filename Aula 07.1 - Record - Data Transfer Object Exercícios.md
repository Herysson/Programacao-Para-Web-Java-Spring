# 🎓 Classes `record` em Java


Compreender o uso de classes do tipo `record` em Java e aplicá-las corretamente no desenvolvimento de APIs REST, especialmente no contexto de DTOs. Utilizaremos como base o projeto `UserPhoneAPI`.

---

## 📚 1. O que é uma classe `record`?

Introduzido oficialmente no **Java 16**, um `record` é um tipo especial de classe em Java voltado para **armazenar dados de forma imutável e concisa**.

### 🧩 Características principais:
- Imutável por padrão (sem `setters`);
- Gera automaticamente:
  - Construtor com todos os atributos;
  - `getters`;
  - `toString()`, `equals()` e `hashCode()`;
- Ideal para **DTOs**, **valores de retorno de métodos**, e **camada de comunicação entre sistemas**.

---

## 🧾 2. Sintaxe Básica

```java
public record UserDTO(Long id, String name, String email) {}
```

Esse `record` equivale a:

```java
public final class UserDTO {
    private final Long id;
    private final String name;
    private final String email;

    public UserDTO(Long id, String name, String email) {
        this.id = id;
        this.name = name;
        this.email = email;
    }

    public Long id() { return id; }
    public String name() { return name; }
    public String email() { return email; }

    // toString, equals, hashCode...
}
```

---

## 🛠️ 3. Aplicando no Projeto `UserPhoneAPI`

### 🗂️ Estrutura de Entidades:

```java
@Entity
public class User {
    private Long id;
    private String name;
    private String email;
    private List<Phone> phones;
}

@Entity
public class Phone {
    private Long id;
    private String number;
    private String type;
}
```

### 📤 DTOs com `record`:

```java
public record PhoneDTO(Long id, String number, String type) {}

public record UserDTO(Long id, String name, String email, List<PhoneDTO> phones) {}
```

#### ✅ Use `record` para:
- **Isolar a lógica de domínio da lógica de apresentação**;
- Facilitar **serialização** com frameworks como Jackson;
- Simplificar o uso de padrões REST;

---

## 🔄 4. Mapeamento de dados - (Entidade) <--> (record)

O mapeamento de dados é o processo de converter objetos de um tipo para outro, geralmente entre a entidade do sistema (modelo usado internamente, como uma classe JPA) e um DTO representado por um record (modelo usado para comunicação externa, como entrada/saída de dados em APIs REST).

---

### 🔧 Mapeamento Manual (padrão):

```java
public class UserMapper {
    public static UserDTO toDTO(User user) {
        List<PhoneDTO> phones = user.getPhones().stream()
            .map(p -> new PhoneDTO(p.getId(), p.getNumber(), p.getType()))
            .toList();

        return new UserDTO(user.getId(), user.getName(), user.getEmail(), phones);
    }

    public static User toEntity(UserRequestDTO dto) {
        User user = new User();
        user.setName(dto.name());
        user.setEmail(dto.email());
        user.setPassword(dto.password()); // supondo que essa seja tratada
        return user;
    }
}
```

#### `toDTO(User user)`

Este método converte uma **entidade `User`** (normalmente vinda do banco de dados) em um **DTO `UserDTO`** que será retornado para o cliente.

```java
public static UserDTO toDTO(User user) {
```
🔹 Método estático que retorna um `UserDTO`, recebendo como parâmetro um `User` (entidade).

```java
    List<PhoneDTO> phones = user.getPhones().stream()
        .map(p -> new PhoneDTO(p.getId(), p.getNumber(), p.getType()))
        .toList();
```
🔹 Aqui estamos convertendo a **lista de `Phone` (entidade)** do usuário em uma lista de **`PhoneDTO`**:

- `user.getPhones()` → pega os telefones do usuário.
- `.stream()` → cria um stream para processar os dados funcionalmente.
- `.map(...)` → mapeia cada `Phone` para um `PhoneDTO`, passando os dados do telefone (`id`, `number`, `type`) para o construtor do `record`.
- `.toList()` → coleta todos os resultados mapeados e os transforma em uma nova lista de `PhoneDTO`.

```java
    return new UserDTO(user.getId(), user.getName(), user.getEmail(), phones);
}
```
🔹 Cria e retorna um novo `UserDTO` com os dados do usuário e a lista de telefones já convertida.


#### `toEntity(UserRequestDTO dto)`

Este método faz o caminho inverso: converte um **DTO de entrada** (geralmente vindo do corpo da requisição HTTP) em uma **entidade `User`**.

```java
public static User toEntity(UserRequestDTO dto) {
```
🔹 Método estático que retorna um `User`, recebendo um `UserRequestDTO` (record usado para entrada de dados, com `name`, `email`, `password`).

```java
    User user = new User();
```
🔹 Cria uma nova instância de `User` (entidade JPA que será salva no banco).

```java
    user.setName(dto.name());
    user.setEmail(dto.email());
    user.setPassword(dto.password()); // supondo que essa seja tratada
```
🔹 Define os valores da entidade `User` usando os dados do DTO.

- `dto.name()` → usa os métodos de acesso do `record`, que têm o mesmo nome dos campos.
- Aqui, o `password` é tratado diretamente — em uma aplicação real, normalmente seria criptografado antes de salvar.

```java
    return user;
}
```
🔹 Retorna a entidade preenchida, pronta para ser salva no repositório.

---

**💡 Resumo Visual**

| Função                  | Direção             | Objetivo                              |
|------------------------|---------------------|----------------------------------------|
| `toDTO(User)`          | Entidade → DTO      | Preparar os dados para envio ao cliente |
| `toEntity(UserRequestDTO)` | DTO → Entidade      | Preparar os dados para salvar no banco |


---


✅ **Vantagens**:
- Controle total do que é mapeado.
- Simples e direto.

❌ **Desvantagens**:
- Muito código repetitivo.
- Pode ficar difícil de manter em sistemas grandes.

---

### 🤖 2. **MapStruct (Framework de Mapeamento Automático)** 💡

#### O que é?
[**MapStruct**](https://mapstruct.org/) é um framework que **gera automaticamente o código de mapeamento** em tempo de compilação, baseado em interfaces e anotações.

#### Exemplo:

```java
@Mapper(componentModel = "spring")
public interface UserMapper {
    UserDTO toDTO(User user);
    User toEntity(UserRequestDTO dto);
}
```

Ele gera automaticamente as implementações no momento da compilação.

#### Gradle/Maven:
Adicione no `pom.xml`:

```xml
<dependency>
    <groupId>org.mapstruct</groupId>
    <artifactId>mapstruct</artifactId>
    <version>1.5.5.Final</version>
</dependency>
<annotationProcessorPaths>
    <path>
        <groupId>org.mapstruct</groupId>
        <artifactId>mapstruct-processor</artifactId>
        <version>1.5.5.Final</version>
    </path>
</annotationProcessorPaths>
```

✅ **Vantagens**:
- Reduz 90% do código repetitivo.
- Performance excelente (gerado em tempo de compilação).

❌ **Desvantagens**:
- Exige configuração inicial.
- Requer build com suporte a *annotation processing* (como Maven ou Gradle).

---

### 🔄 3. **ModelMapper (Reflexão)**

[**ModelMapper**](http://modelmapper.org/) é uma biblioteca que usa **reflexão em tempo de execução** para mapear objetos automaticamente.

#### Exemplo:

```java
ModelMapper modelMapper = new ModelMapper();
UserDTO dto = modelMapper.map(user, UserDTO.class);
```

✅ **Vantagens**:
- Pouquíssimo código.
- Rápido de implementar.

❌ **Desvantagens**:
- Menor performance (usa reflexão).
- Dificuldade para depurar erros.
- Não recomendado para produção em sistemas grandes.

---

### 🔥 4. **Lombok com Builders (para criar DTOs)**

Você pode usar `@Builder` com Lombok para facilitar o preenchimento de DTOs em mapeamento manual:

```java
@Getter
@Builder
public class UserDTO {
    private Long id;
    private String name;
    private String email;
}
```

Uso:

```java
UserDTO dto = UserDTO.builder()
    .id(user.getId())
    .name(user.getName())
    .email(user.getEmail())
    .build();
```

---

### ✅ Qual abordagem escolher?

| Cenário                        | Recomendação            |
|-------------------------------|--------------------------|
| Projeto pequeno/simples       | Mapeamento manual        |
| Projeto médio/grande          | MapStruct                |
| Protótipos/testes rápidos     | ModelMapper              |
| Precisa de controle total     | Manual ou MapStruct com customização |
| Quer evitar boilerplate       | MapStruct + record       |

---

# Data Transfer Object - DTO 

## 📦 O que é um DTO?

DTO significa **Data Transfer Object**, ou seja, **Objeto de Transferência de Dados**.

Ele é usado para:
- **Levar dados de um lugar para outro**, geralmente entre o **controller** e o **cliente (ex: front-end)**.
- **Evitar enviar entidades completas (modelos do banco)**, protegendo dados sensíveis ou evitando problemas de estrutura.
- **Facilitar o controle sobre o que entra e sai da API**.

---

## 🧩 Por que usar DTOs?

Imagine que sua entidade `User` tenha um campo chamado `senha`. Você não quer que isso seja retornado na resposta da API.  
Ou imagine que você quer exibir o nome do usuário **e os telefones formatados** juntos em uma única resposta. O DTO resolve isso!

---

## 🛠️ Estrutura no seu repositório

No repositório `UserPhoneAPI`, temos um exemplo de organização dos DTOs:

📁 `src/main/java/com/example/userphone/dto`

- `UserDTO.java`
- `PhoneDTO.java`

Esses DTOs são usados para transferir apenas os dados que você quer que **entrem** ou **saiam** da sua API.



### 👀 Exemplo prático: `UserDTO.java`

```java
public record UserDTO(Long id, String name, String email) {
}
```

Esse `record` representa apenas os dados que você quer expor de um `User`.

🔒 Repare que **não tem senha aqui** — isso protege a aplicação de retornar dados sensíveis.

---

## 🧭 Como utilizar um DTO na prática

1. **No Controller**, você usa o DTO para **receber ou retornar** dados.
2. **No Service**, você pode converter a entidade para DTO e vice-versa.


### 🔁 Exemplo de conversão: Entidade → DTO

```java
public UserDTO convertToDTO(User user) {
    return new UserDTO(user.getId(), user.getName(), user.getEmail());
}
```


### 🧍 Exemplo no `UserController`

```java
@GetMapping
public List<UserDTO> getAllUsers() {
    return userService.getAllUsers()
                      .stream()
                      .map(user -> new UserDTO(user.getId(), user.getName(), user.getEmail()))
                      .toList();
}
```

Aqui o controller **não retorna o `User` diretamente**, mas sim o `UserDTO`.

---

## ✏️ Exemplo com DTO de entrada (criação de usuário)

Você pode ter um DTO separado para entrada, ex:

```java
public record CreateUserDTO(String name, String email, String password) {}
```

E no controller:

```java
@PostMapping
public UserDTO createUser(@RequestBody CreateUserDTO dto) {
    User user = new User();
    user.setName(dto.name());
    user.setEmail(dto.email());
    user.setPassword(dto.password()); // só uso interno!

    return userService.createUser(user);
}
```

---

## 🧠 Benefícios de usar DTOs

| Vantagem | Descrição |
|---------|-----------|
| 🔐 Segurança | Evita expor dados sensíveis |
| 📦 Organização | Separa claramente entrada e saída |
| 🎯 Clareza | Define o que exatamente será transferido |
| 🔄 Flexibilidade | Permite compor objetos com dados de múltiplas fontes |

---

## 🛠️ Exercícios Práticos — `record`, DTOs e Mapeamento em Java
Entender e aplicar o uso de **DTOs** para melhorar a organização, segurança e clareza na troca de dados entre o back-end e os consumidores da API.

### 📂 Repositório base:
[https://github.com/Herysson/UserPhoneAPI](https://github.com/Herysson/UserPhoneAPI)

### 📚 Contexto Geral
Você está desenvolvendo uma API REST para gerenciamento de usuários e seus telefones. A estrutura utiliza `record` para criar DTOs e separa claramente entidades (modelo de dados JPA) das representações que trafegam pela API.


#### 🔹 **Exercício 1: Criar DTO de saída (`PhoneDTO`)**

**Objetivo:** garantir que apenas dados relevantes e seguros do telefone sejam enviados ao cliente.


#### 🔹 **Exercício 2: Criar DTO de entrada (`CreatePhoneDTO`)**

**Objetivo:** representar os dados recebidos para criação de um novo telefone, sem expor ou depender da entidade JPA.

#### 🔹 **Exercício 3: Criar classe de mapeamento (`PhoneMapper`)**

**Objetivo:** realizar a conversão entre DTOs e entidades seguindo boas práticas.

#### 🔹 **Exercício 4: Atualizar o `PhoneController`**

**Objetivo:** aplicar os DTOs criados para entrada e saída nos endpoints da API.

#### 🔹 **Exercício 5: Adaptar o cadastro de usuário (`UserService`)**

**Objetivo:** permitir o cadastro de um novo usuário com múltiplos telefones (DTOs de entrada).

#### 🔹 **Exercício 6: Comentar e justificar**

**Objetivo:** refletir sobre as decisões arquiteturais.

#### 🔹 **Exercício 7 (Avançado): Criar mapeamento reverso para update**

**Objetivo:** preparar a aplicação para receber dados de atualização com segurança.

---

## ✅ Dicas e Boas Práticas Reforçadas

- **Nunca exponha entidades JPA diretamente nos controllers.**
- **Sempre use DTOs para entrada e saída de dados.**
- **Separe claramente os `record DTOs` de entrada (Request) e saída (Response/DTO).**
- **Use classes auxiliares para mapeamento, mantendo controllers limpos.**
- **Prefira imutabilidade: `record` é ideal para isso.**
---

## ✅ Recomendação de nomenclatura padrão de DTO's (limpa e descritiva)

### Para DTOs de **entrada**:
- Prefira **nomear com `Request`** + ação ou contexto:
  - `CreateUserRequestDTO`
  - `UpdatePhoneRequestDTO`
  - `LoginRequestDTO`

### Para DTOs de **saída**:
- Prefira `ResponseDTO`, ou só `DTO` se for genérico:
  - `UserResponseDTO` (para detalhado)
  - `UserDTO` (se for padronizado e usado em várias saídas)
  - `PhoneResponseDTO`

## 🛡️ Vantagens dessa abordagem:
- **Clareza:** Fica claro se o DTO é para *entrada* ou *saída*.
- **Escalabilidade:** Fácil criar diferentes versões (ex: `Create`, `Update`, `List`, `Detail`).
- **Organização:** Evita confusões ao ler serviços com múltiplas operações.

---

## 📚 Referências – Formato IEEE

[1] Oracle, "Records", *The Java® Language Specification*, Java SE 16 Edition. [Online]. Available: https://docs.oracle.com/en/java/javase/16/language/records.html

[2] J. Bloch, *Effective Java*, 3rd ed. Addison-Wesley, 2018.

[3] M. Fowler, "Data Transfer Object," *Patterns of Enterprise Application Architecture*. [Online]. Available: https://martinfowler.com/eaaCatalog/dataTransferObject.html

[4] MapStruct, "MapStruct Reference Guide", [Online]. Available: https://mapstruct.org/documentation/stable/reference/html/

[5] Spring.io, "Building a RESTful Web Service", [Online]. Available: https://spring.io/guides/gs/rest-service/

[6] R. C. Martin, *Clean Architecture: A Craftsman's Guide to Software Structure and Design*, 1st ed. Prentice Hall, 2017.

[7] Oracle, "8.10 Record Types," *The Java Language Specification*, Java SE 16. [Online]. Available: https://docs.oracle.com/javase/specs/jls/se16/html/jls-8.html#jls-8.10



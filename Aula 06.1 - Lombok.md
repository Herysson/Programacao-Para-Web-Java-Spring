
# Lombok
O Project Lombok é uma biblioteca Java que se popularizou por oferecer uma solução elegante para reduzir e simplificar o código boilerplate (repetitivo) em aplicações Java. Utilizando uma série de anotações customizadas, o Lombok automatiza a geração de métodos comumente usados em classes de dados, como getters, setters, métodos de construção, `toString()`, `hashCode()`, e `equals()`. Essa automação não só torna o código mais limpo e legível, mas também diminui o tempo de desenvolvimento e a possibilidade de erros, uma vez que reduz a quantidade de código manualmente escrito.

<div align="center">
    
![Sem título](https://github.com/Herysson/Spring-Backend-CRUD/assets/7634437/355dcd31-eee6-4d9c-ab45-5a20cb916bc9)

</div>

### Principais Anotações do Lombok

- **`@Getter` / `@Setter`**: Essas duas anotações são usadas para gerar automaticamente os métodos getters e setters para os campos de uma classe. Podem ser aplicadas tanto a nível de classe para afetar todos os campos, quanto a nível de campo individual.

- **`@NoArgsConstructor`, `@RequiredArgsConstructor`, e `@AllArgsConstructor`**: Essas anotações são utilizadas para gerar diferentes tipos de construtores automaticamente. `@NoArgsConstructor` cria um construtor sem argumentos; `@RequiredArgsConstructor` gera um construtor com um parâmetro para cada campo final e cada campo não final marcado com `@NonNull`; `@AllArgsConstructor` gera um construtor com um parâmetro para cada campo da classe.

- **`@ToString`**: É usada para gerar automaticamente uma implementação do método `toString()` 

- **`@EqualsAndHashCode`**: Gera implementações dos métodos `equals(Object other)` e `hashCode()` baseadas nos campos da classe, facilitando a comparação entre instâncias.

- **`@Data`**: É uma das anotações mais poderosas do Lombok, combinando várias outras anotações em uma. Ela gera automaticamente getters para todos os campos, setters para todos os campos não finais, e implementações adequadas de `toString`, `equals`, e `hashCode`. Além disso, se aplicável, gera um construtor que inicializa campos finais e campos não finais marcados com `@NonNull`.

- **`@Value`**: É similar a `@Data`, mas para criação de objetos imutáveis. Todos os campos são final por padrão, e são gerados apenas getters e não setters.

- **`@Builder`**: Implementa o padrão Builder para a criação de objetos de forma mais controlada, permitindo a inicialização de objetos com código mais legível e manutenível.

- **`@Slf4j`**: Facilita a criação de logs ao inserir automaticamente um logger SLF4J na classe.


O Lombok é integrado durante o processo de compilação, o que significa que o código gerado por suas anotações não aparece explicitamente no código fonte. Isso mantém o código fonte limpo e focado na lógica de negócios, enquanto o bytecode gerado contém todos os métodos e construtores necessários. Para utilizar o Lombok, é necessário adicionar a sua dependência ao projeto e configurar a IDE para reconhecer as anotações do Lombok, garantindo que o código gerado seja corretamente compilado e disponível no ambiente de desenvolvimento.

O uso do Lombok em projetos Java modernos é uma prática comum que ajuda desenvolvedores a focar mais na lógica do negócio e menos na escrita de código repetitivo, promovendo assim a eficiência e a qualidade no desenvolvimento de software.


## @Getter e @Setter

- `@Getter`: Esta anotação é usada para gerar automaticamente o método getter para um campo. O método gerado será público e retornará o valor do campo.
- `@Setter`: Semelhante ao `@Getter`, mas para gerar automaticamente o método setter para um campo. O método setter será público, retornará void e permitirá a modificação do valor do campo.

Essas anotações podem ser aplicadas tanto no nível da classe, o que afeta todos os campos relevantes, quanto no nível de campos individuais, permitindo controle granular sobre quais campos devem ter getters e setters.

**Exemplo de Uso**

Suponha que temos uma classe `User` com campos para id, nome, e-mail e telefone. Aqui está como você pode usar `@Getter` e `@Setter` do Lombok para gerar automaticamente os métodos de acesso e modificação para esses campos.


```java
import lombok.Getter;
import lombok.Setter;

@Getter
@Setter
public class User {
    private Long id;
    private String name;
    private String email;
    private String phone;
}
```

Neste exemplo, as anotações `@Getter` e `@Setter` aplicadas na classe `User` instruirão o Lombok a gerar automaticamente métodos getter e setter públicos para todos os quatro campos (`id`, `name`, `email`, `phone`). Isso elimina a necessidade de escrevê-los manualmente.

**Código Java Vanilla Equivalente**

Sem o Lombok, teríamos que implementar manualmente cada método getter e setter, resultando no seguinte código:

```java
public class User {
    private Long id;
    private String name;
    private String email;
    private String phone;

    public Long getId() {
        return id;
    }

    public void setId(Long id) {
        this.id = id;
    }

    public String getName() {
        return name;
    }

    public void setName(String name) {
        this.name = name;
    }

    public String getEmail() {
        return email;
    }

    public void setEmail(String email) {
        this.email = email;
    }

    public String getPhone() {
        return phone;
    }

    public void setPhone(String phone) {
        this.phone = phone;
    }
}
```

O Lombok reduz significativamente a quantidade de código boilerplate necessário, tornando o código mais 
limpo e mais fácil de entender e manter. Isso não apenas economiza tempo durante a fase de desenvolvimento inicial, mas também 
simplifica as modificações futuras ao reduzir o risco de erros ao adicionar ou modificar campos na classe.


## @NoArgsConstructor, @RequiredArgsConstructor e @AllArgsConstructor

As anotações `@NoArgsConstructor`, `@RequiredArgsConstructor`, e `@AllArgsConstructor` do Lombok oferecem uma forma concisa de gerar diferentes tipos de construtores em classes Java, reduzindo o código boilerplate associado à criação de construtores manuais. Cada uma dessas anotações serve a um propósito específico na geração automática de construtores, facilitando o desenvolvimento e a manutenção de código.

### `@NoArgsConstructor`

Gera um construtor sem argumentos. É particularmente útil para classes que requerem um construtor vazio, seja por exigências de uma framework ou por necessidade de inicialização padrão.

### `@RequiredArgsConstructor`

Cria um construtor apenas com os campos finais e os campos marcados como `@NonNull` que não são inicializados no ponto de declaração. Este construtor garante que todos os atributos essenciais de uma instância da classe sejam inicializados.

### `@AllArgsConstructor`

Gera um construtor com um argumento para cada campo na classe. Isso é útil quando você quer criar uma instância de uma classe e inicializar todos os seus campos em uma única chamada de construtor.

**Exemplo de Uso na Classe `User`**

Considere uma classe `User` com campos `id`, `name`, `email`, e `phone`, onde `id` é um campo final (simulando uma situação em que o `id` é atribuído uma única vez), `email` é um campo obrigatório (marcado com `@NonNull` para demonstrar `@RequiredArgsConstructor`), e os outros campos são opcionais.

```java
import lombok.NoArgsConstructor;
import lombok.RequiredArgsConstructor;
import lombok.AllArgsConstructor;
import lombok.NonNull;

@NoArgsConstructor
@RequiredArgsConstructor
@AllArgsConstructor
public class User {
    private final Long id; // Final field for @RequiredArgsConstructor example
    @NonNull private String email; // Non-null field for @RequiredArgsConstructor
    private String name;
    private String phone;
}
```

**Como os Construtores são Gerados**

- **@NoArgsConstructor** geraria o seguinte construtor:

  ```java
  public User() {
  }
  ```

- **@RequiredArgsConstructor** geraria um construtor que inicializa `id` (por ser final) e `email` (por ser marcado com `@NonNull`):

  ```java
  public User(final Long id, @NonNull String email) {
      this.id = id;
      this.email = email;
  }
  ```

- **@AllArgsConstructor** geraria um construtor que inicializa todos os campos:

  ```java
  public User(final Long id, String email, String name, String phone) {
      this.id = id;
      this.email = email;
      this.name = name;
      this.phone = phone;
  }
  ```

**Código Java Vanilla Equivalente**

Sem o Lombok, você teria que manualmente implementar cada um desses construtores, aumentando o código boilerplate e potencialmente introduzindo erros manuais.

```java
public class User {
    private final Long id;
    private String email;
    private String name;
    private String phone;

    public User() {
    }

    public User(final Long id, String email) {
        this.id = id;
        this.email = email;
    }

    public User(final Long id, String email, String name, String phone) {
        this.id = id;
        this.email = email;
        this.name = name;
        this.phone = phone;
    }
}
```

## `@ToString`

- Por padrão, a anotação `@ToString` incluirá o nome da classe e todos os campos não estáticos na saída do `toString()`.
- É possível customizar o comportamento da anotação, excluindo certos campos ou incluindo apenas campos específicos, além de outras opções como chamar `toString()` de superclasses.
- A anotação também permite configurar se os nomes dos campos devem ser incluídos na saída do `toString()`, o que pode melhorar a legibilidade.

**Exemplo de Uso na Classe `User`**

Vamos aplicar a anotação `@ToString` à nossa classe `User` para incluir todos os campos na saída do método `toString()`, exceto o campo `password`, assumindo que este campo seja sensível e não deva ser exposto em logs ou depurações.

```java
import lombok.ToString;

@ToString(exclude="password")
public class User {
    private Long id;
    private String name;
    private String email;
    private String phone;
    private String password; // Campo sensível, excluído do toString
}
```

**Como o Método `toString()` é Gerado**

Com a anotação `@ToString(exclude="password")`, o Lombok geraria automaticamente um método `toString()` semelhante ao seguinte:

```java
@Override
public String toString() {
    return "User(id=" + this.id + ", name=" + this.name + ", email=" + this.email + ", phone=" + this.phone + ")";
}
```

Isso fornece uma representação em `String` do objeto `User` que inclui todos os campos exceto `password`, conforme especificado.

**Código Java Vanilla Equivalente**

Sem o uso do Lombok, você teria que implementar manualmente o método `toString()` da seguinte forma:

```java
@Override
public String toString() {
    return "User{" +
           "id=" + id +
           ", name='" + name + '\'' +
           ", email='" + email + '\'' +
           ", phone='" + phone + '\'' +
           '}';
}
```

Note que, na implementação manual, é preciso cuidar explicitamente de não incluir o campo `password` para proteger a sensibilidade dos dados, tal como feito automaticamente pelo Lombok com a opção `exclude`.

A anotação `@ToString` do Lombok, portanto, não apenas economiza tempo e esforço ao evitar a necessidade de escrever este código boilerplate manualmente, mas também oferece flexibilidade e segurança ao permitir a exclusão de campos sensíveis ou desnecessários da representação de string do objeto.

Quando modificamos o atributo `phone` na classe `User` para ser uma lista de objetos do tipo `Phone`, a anotação `@ToString` do Lombok se torna ainda mais útil, especialmente ao lidar com coleções. Ela nos permite criar representações em string não apenas dos objetos `User`, mas também dos objetos contidos em suas coleções de maneira fácil e intuitiva.

Neste cenário, `@ToString` automaticamente incluirá a representação em string da lista de objetos `Phone` na saída de `toString()` do `User`. Isso é especialmente útil para visualizar rapidamente os dados contidos em coleções dentro de objetos.

Suponha que temos uma classe `Phone` com atributos como `type` e `number`. Sem precisar fazer nenhuma configuração adicional em `Phone`, a anotação `@ToString` em `User` cuidará de chamar o método `toString()` em cada objeto `Phone` da lista, agregando suas representações em string à representação do `User`.

**Alterando a classe User**

Agora, modificamos a classe `User` para incluir uma lista de `Phone`:

```java
import lombok.ToString;
import java.util.List;

@ToString(exclude="password")
public class User {
    private Long id;
    private String name;
    private String email;
    private List<Phone> phones; // Lista de objetos Phone
    private String password; // Campo sensível, excluído do toString

    // Construtores, Getters e Setters omitidos para brevidade
}
```

**Como o Método `toString()` é Gerado para User**

Com a anotação `@ToString(exclude="password")`, o Lombok geraria um método `toString()` para `User` que inclui a representação em string da lista de `Phone`, parecido com isto:

```java
@Override
public String toString() {
    return "User(id=" + this.id + ", name=" + this.name + ", email=" + this.email + ", phones=" + this.phones + ")";
}
```

Se `User` tivesse, por exemplo, dois telefones, a saída de `toString()` poderia se parecer com:

```
User(id=1, name=John Doe, email=johndoe@example.com, phones=[Phone(type=Mobile, number=123456789), Phone(type=Home, number=987654321)])
```

**Código Java Vanilla Equivalente**

Sem Lombok, a implementação manual envolveria a criação de loops ou chamadas de método para concatenar a representação em string de cada `Phone` na lista, algo assim:

```java
@Override
public String toString() {
    String phonesString = phones.stream()
                                 .map(Phone::toString)
                                 .collect(Collectors.joining(", "));
    return "User{" +
           "id=" + id +
           ", name='" + name + '\'' +
           ", email='" + email + '\'' +
           ", phones=[" + phonesString + ']' +
           '}';
}
```

A abordagem do Lombok simplifica significativamente esse processo, gerando automaticamente a representação em string adequada para coleções e seus objetos contidos, facilitando a visualização e depuração dos estados dos objetos.

A anotação `@EqualsAndHashCode` do Lombok é usada para gerar automaticamente as implementações dos métodos `equals(Object other)` e `hashCode()` em classes Java. Esses métodos são cruciais para comparar instâncias de objetos não apenas por sua referência, mas por seu conteúdo, e são essenciais para o uso correto de coleções como `HashSet` e `HashMap`.

## `@EqualsAndHashCode`

- **Por padrão**, `@EqualsAndHashCode` inclui todos os campos não estáticos da classe para calcular a igualdade e o hash code. No entanto, você pode customizar isso excluindo campos específicos ou incluindo apenas campos selecionados.
- **`callSuper`**: Por padrão, `@EqualsAndHashCode` não chama `equals` e `hashCode` da superclasse. Se sua classe estende outra classe e você quer incluir os campos da superclasse nas comparações e cálculos de hash, você deve configurar `callSuper = true`.
- **Cuidados**: Ao usar `@EqualsAndHashCode`, especialmente com `callSuper = true`, é importante garantir que a superclasse também tenha implementações corretas de `equals` e `hashCode`, para evitar comportamentos inesperados.


Vamos expandir a classe `User`, agora considerando a importância de `equals` e `hashCode` para a lista de objetos `Phone`. Decidimos incluir todos os campos na geração de `equals` e `hashCode`, exceto o campo `password`, por ser sensível.

```java
import lombok.EqualsAndHashCode;

@EqualsAndHashCode(exclude = {"password"})
public class User {
    private Long id;
    private String name;
    private String email;
    private List<Phone> phones; // Lista de objetos Phone
    private String password; // Excluído de equals e hashCode
}
```

** Como os Métodos `equals` e `hashCode` são Gerados**

Com a configuração `@EqualsAndHashCode(exclude = {"password"})`, o Lombok geraria implementações de `equals` e `hashCode` que consideram os campos `id`, `name`, `email`, e `phones` para determinar a igualdade e o hash code de objetos `User`, mas ignorariam o campo `password`.

**Código Java Vanilla Equivalente**

Sem o Lombok, a implementação manual de `equals` e `hashCode` para a classe `User`, excluindo o campo `password`, poderia se parecer com isto:

```java
import java.util.Objects;

public class User {
    private Long id;
    private String name;
    private String email;
    private List<Phone> phones;
    private String password;

    @Override
    public boolean equals(Object o) {
        if (this == o) return true;
        if (o == null || getClass() != o.getClass()) return false;
        User user = (User) o;
        return Objects.equals(id, user.id) &&
               Objects.equals(name, user.name) &&
               Objects.equals(email, user.email) &&
               Objects.equals(phones, user.phones);
    }

    @Override
    public int hashCode() {
        return Objects.hash(id, name, email, phones);
    }
}
```

Este código compara `User` objetos baseando-se em seus `id`, `name`, `email`, e `phones` campos, mas ignora o `password` campo tanto em `equals` quanto em `hashCode`, assegurando que a sensibilidade dos dados seja mantida, enquanto ainda permite uma comparação significativa e operações de hashing baseadas no conteúdo real do objeto `User`.

A anotação `@EqualsAndHashCode` simplifica significativamente este processo, gerando automaticamente essas implementações críticas e frequentemente complexas, reduzindo o potencial para erros e inconsistências no código.

## `@Data`

A anotação `@Data` do Lombok é uma das anotações mais poderosas e convenientes oferecidas pela biblioteca, pois combina uma série de outras anotações importantes em uma única declaração. Usar `@Data` em uma classe automaticamente fornece:

- **Métodos `getter` para todos os campos**
- **Métodos `setter` para todos os campos não finais**
- **Um método `toString` adequado que inclui todos os campos, exceto os marcados com `@ToString.Exclude`**
- **Implementações adequadas dos métodos `equals` e `hashCode` que usam todos os campos relevantes, exceto os marcados com `@EqualsAndHashCode.Exclude`**
- **Um construtor `requiredArgsConstructor` que inicializa todos os campos finais, bem como os campos não finais marcados com `@NonNull`, garantindo que não sejam nulos**

Essa anotação é particularmente útil para classes de dados (Data Transfer Objects, DTOs, e entidades de persistência), simplificando a criação e manutenção ao eliminar a necessidade de escrever manualmente esse código repetitivo.

**Exemplo de Uso na Classe `User`**

Considerando a classe `User` com uma lista de objetos `Phone` e um campo sensível `password` que não queremos incluir nos métodos `toString`, `equals` e `hashCode`, podemos usar a anotação `@Data` para gerar automaticamente a maior parte do código necessário para esta classe:

```java
import lombok.Data;
import lombok.NonNull;
import java.util.List;

@Data
public class User {
    private Long id;
    private String name;
    @NonNull
    private String email;
    private List<Phone> phones;
    private transient String password; // Usando 'transient' para excluí-lo de @Data geração
}
```

Neste exemplo, todos os campos exceto `password` serão incluídos nos métodos `toString`, `equals` e `hashCode` gerados. O campo `password` é marcado como `transient` para indicar que ele deve ser excluído. Note que `@NonNull` é usado em `email`, o que faz com que o construtor gerado exija esse campo como um parâmetro e que uma verificação nula seja adicionada ao setter correspondente.

**Como o Código Gerado se Parece**

Embora o código gerado não seja visível no arquivo fonte, o comportamento seria similar a este:

```java
import java.util.List;
import java.util.Objects;

public class User {
    private Long id;
    private String name;
    private String email;
    private List<Phone> phones;
    private String password; // Incluído para o exemplo, mas tipicamente excluído

    public User(String email) {
        this.email = Objects.requireNonNull(email, "email cannot be null");
    }

    // Getters
    public Long getId() {
        return id;
    }

    public String getName() {
        return name;
    }

    public String getEmail() {
        return email;
    }

    public List<Phone> getPhones() {
        return phones;
    }

    public String getPassword() {
        return password;
    }

    // Setters
    public void setId(Long id) {
        this.id = id;
    }

    public void setName(String name) {
        this.name = name;
    }

    public void setEmail(String email) {
        this.email = email;
    }

    public void setPhones(List<Phone> phones) {
        this.phones = phones;
    }

    public void setPassword(String password) {
        this.password = password;
    }

    // toString
    @Override
    public String toString() {
        return "User{" +
               "id=" + id +
               ", name='" + name + '\'' +
               ", email='" + email + '\'' +
               ", phones=" + phones +
               ", password='" + password + '\'' +
               '}';
    }

    // equals
    @Override
    public boolean equals(Object o) {
        if (this == o) return true;
        if (o == null || getClass() != o.getClass()) return false;
        User user = (User) o;
        return Objects.equals(id, user.id) &&
               Objects.equals(name, user.name) &&
               Objects.equals(email, user.email) &&
               Objects.equals(phones, user.phones) &&
               Objects.equals(password, user.password);
    }

    // hashCode
    @Override
    public int hashCode() {
        return Objects.hash(id, name, email, phones, password);
    }
}
```

**Benefícios do Uso de `@Data`**

- **Redução significativa de boilerplate**: O código necessário para getters, setters, `toString`, `equals`, e `hashCode` é gerado automaticamente.
- **Código mais limpo e focado**: Com a redução de boilerplate, o código torna-se mais legível e fácil de manter, permitindo que os desenvolvedores se concentrem na lógica de negócios.
- **Consistência**: As implementações de `equals` e `hashCode` geradas garantem consistência em como os objetos são comparados e armazenados em coleções, evitando bugs comuns relacionados a esses métodos.

Utilizar `@Data` é uma prática recomendada para classes de modelo em aplicações Java, especialmente quando se deseja manter o código enxuto e manutenível.

## `@Value`

A anotação `@Value` do Lombok é usada para indicar que uma classe é imutável e deve ter todos os seus campos considerados finais. Essa anotação gera automaticamente os métodos `getter` para todos os campos, marca todos os campos como `final`, e também gera implementações adequadas dos métodos `toString`, `equals`, e `hashCode`, semelhante à anotação `@Data`, mas com a semântica de imutabilidade. Além disso, `@Value` gera um construtor que aceita todos os campos como argumentos, facilitando a criação de instâncias de objetos imutáveis.

**Benefícios da Imutabilidade**

- **Segurança de Thread**: Objetos imutáveis são naturalmente thread-safe, pois o estado de um objeto imutável não pode ser alterado após sua criação.
- **Menor Complexidade**: Ao trabalhar com objetos imutáveis, você não precisa se preocupar com mudanças de estado, o que simplifica o raciocínio sobre o código.
- **Prevenção de Bugs**: A imutabilidade reduz a possibilidade de bugs relacionados a mudanças inesperadas de estado.

**Exemplo de Uso na Classe `User`**

Vamos aplicar a anotação `@Value` na nossa classe `User`, transformando-a em uma classe imutável. Consideraremos que todos os campos, incluindo a lista de telefones, devem ser imutáveis. Nota: Para garantir a imutabilidade completa, a lista de `Phone` deve ser encapsulada de forma imutável no construtor ou usando uma coleção imutável diretamente.

```java
import lombok.Value;
import java.util.Collections;
import java.util.List;

@Value
public class User {
    Long id;
    String name;
    String email;
    List<Phone> phones; // A imutabilidade completa requer coleções imutáveis

    // O campo password foi removido para simplificar o exemplo,
    // considerando as melhores práticas de segurança.
}
```

**Como o Código Gerado se Parece**

O Lombok gera o seguinte comportamento para a classe `User`:

- Todos os campos são marcados como `final`.
- São gerados métodos `getter` para todos os campos.
- Um construtor que aceita todos os campos como argumentos é gerado.
- São gerados `toString`, `equals`, e `hashCode` que incluem todos os campos.

**Código Java Vanilla Equivalente**

Sem o Lombok, a classe `User` imutável precisaria ser escrita manualmente, incluindo todos os aspectos mencionados:

```java
import java.util.Collections;
import java.util.List;
import java.util.Objects;

public final class User {
    private final Long id;
    private final String name;
    private final String email;
    private final List<Phone> phones;

    public User(Long id, String name, String email, List<Phone> phones) {
        this.id = id;
        this.name = name;
        this.email = email;
        this.phones = Collections.unmodifiableList(phones); // Garantindo a imutabilidade da lista
    }

    public Long getId() {
        return id;
    }

    public String getName() {
        return name;
    }

    public String getEmail() {
        return email;
    }

    public List<Phone> getPhones() {
        return phones;
    }

    @Override
    public boolean equals(Object o) {
        if (this == o) return true;
        if (!(o instanceof User)) return false;
        User user = (User) o;
        return Objects.equals(id, user.id) &&
               Objects.equals(name, user.name) &&
               Objects.equals(email, user.email) &&
               Objects.equals(phones, user.phones);
    }

    @Override
    public int hashCode() {
        return Objects.hash(id, name, email, phones);
    }

    @Override
    public String toString() {
        return "User{" +
               "id=" + id +
               ", name='" + name + '\'' +
               ", email='" + email + '\'' +
               ", phones=" + phones +
               '}';
    }
}
```

Este exemplo mostra como a anotação `@Value` do Lombok pode ser usada para simplificar a criação de classes imutáveis em Java, eliminando a necessidade de codificar manualmente construtores, getters, e métodos `toString`, `equals`, e `hashCode`, mantendo o código conciso e fácil de manter.

### **Referências:**

Lombok [projectlombok.org](https://projectlombok.org/features/)

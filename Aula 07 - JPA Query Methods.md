# JPA Query Methods

Os Métodos de Consulta JPA, no contexto do Spring Data JPA, representam uma abordagem poderosa e flexível para a criação de consultas de banco de dados, permitindo aos desenvolvedores definir métodos de consulta em interfaces de repositório com nomes que o Spring Data JPA interpreta automaticamente para gerar as consultas SQL ou JPQL correspondentes. Essa funcionalidade elimina a necessidade de escrever explicitamente a maioria das consultas, facilitando o foco no desenvolvimento de funcionalidades ao invés de detalhes de implementação de banco de dados.

## Como Funcionam os Métodos de Consulta

Os métodos de consulta seguem uma convenção de nomenclatura específica que o Spring Data JPA entende e traduz em consultas reais. Por exemplo, um método chamado `findByLastName(String lastName)` em um repositório relacionado a uma entidade `Person` resultará em uma consulta que busca todas as pessoas com o sobrenome especificado. O Spring Data JPA suporta uma ampla gama de palavras-chave que permitem definir critérios de seleção, ordenação, limitação de resultados, e muito mais.

##Tipos de Métodos de Consulta

1. **Consulta por Derivação de Nome de Método**: Como descrito, o Spring Data JPA interpreta o nome do método e cria uma consulta.
2. **Consulta por Anotação**: Usando a anotação `@Query`, é possível definir explicitamente a consulta JPQL ou SQL, oferecendo mais flexibilidade para casos complexos.
3. **Consulta Nomeada**: JPA permite definir consultas nomeadas na entidade que podem ser referenciadas por um nome simples nos métodos de repositório.

Os Métodos de Consulta JPA simplificam a interação com o banco de dados em aplicações Java, abstraindo a complexidade das consultas e promovendo um desenvolvimento mais ágil e focado no domínio da aplicação. Com suporte para uma ampla gama de operações de consulta através de convenções de nomenclatura intuitivas ou anotações, eles são uma ferramenta essencial no ecossistema Spring Data JPA.

# JPQL
JPQL, ou Java Persistence Query Language, é uma linguagem de consulta orientada a objetos usada para realizar consultas contra entidades gerenciadas dentro do contexto da Java Persistence API (JPA). Inspirada na sintaxe do SQL, a JPQL é projetada para abstrair a complexidade das consultas diretas ao banco de dados, permitindo que os desenvolvedores se concentrem nas entidades e suas relações conforme definido no modelo de domínio da aplicação, ao invés de tabelas e colunas específicas do banco de dados.

### Características Principais da JPQL:

- **Orientada a Objetos**: JPQL trabalha diretamente com classes e propriedades de objetos, e não com tabelas e colunas, facilitando a realização de consultas em um contexto de programação orientada a objetos.
- **Independência de Banco de Dados**: As consultas JPQL são independentes de banco de dados, significando que o mesmo código JPQL pode ser executado em diferentes bancos de dados sem a necessidade de alteração.
- **Sintaxe Familiar**: Para quem já conhece SQL, a JPQL apresenta uma curva de aprendizado suave, pois sua sintaxe é muito semelhante à do SQL, com algumas extensões para suportar operações orientadas a objetos.

### Exemplos de Uso da JPQL:

Um exemplo simples de uma consulta JPQL seria buscar todos os objetos de uma entidade `Person`:

```java
SELECT p FROM Person p
```

Este código seleciona todas as instâncias de `Person` no banco de dados. Ao contrário do SQL, que opera em tabelas e colunas, a JPQL opera em entidades e suas propriedades.

Para um exemplo mais complexo, considere a necessidade de buscar pessoas com uma certa idade mínima, juntando-se a outra entidade, digamos, `Address`:

```java
SELECT p FROM Person p WHERE p.age >= :minAge AND p.address.city = :city
```

Aqui, `:minAge` e `:city` são parâmetros que podem ser vinculados na hora da execução da consulta, proporcionando flexibilidade e segurança contra injeção de SQL.


Embora a JPQL ofereça poderosas abstrações e independência de banco de dados, ela tem suas limitações, especialmente em casos de consultas extremamente complexas ou quando o desempenho é uma preocupação crítica. Em tais situações, pode ser necessário recorrer a consultas nativas SQL ou a outras estratégias de otimização.

A JPQL é uma ferramenta essencial no arsenal de desenvolvedores JPA, permitindo a criação de consultas de banco de dados de forma mais intuitiva e alinhada com o paradigma da orientação a objetos.

# Consulta por Derivação de Nome de Método

No Spring Data JPA, a consulta a partir de nomes de métodos é um recurso poderoso que permite aos desenvolvedores criar consultas de banco de dados de forma intuitiva, apenas pela definição de métodos nas interfaces do repositório. Esses métodos são automaticamente interpretados pelo Spring Data JPA, que gera as consultas SQL correspondentes com base nos nomes dos métodos. Isso elimina a necessidade de escrever consultas explícitas para operações de banco de dados comuns, simplificando significativamente o desenvolvimento.

Vamos utilizar a classe `User` que você forneceu como exemplo para explicar como isso funciona:

```java
import javax.persistence.*;
import java.util.List;

@Entity
public class User {

    @Id
    @GeneratedValue(strategy = GenerationType.IDENTITY)
    private Long id;

    private String name;

    private String email;

    @OneToMany(mappedBy = "user", cascade = CascadeType.ALL, fetch = FetchType.LAZY)
    private List<Phone> phones;
}
```

Para usar a consulta a partir de nomes de métodos com essa classe, você primeiro cria uma interface de repositório que estende `JpaRepository` ou um de seus pais, como `Repository` ou `CrudRepository`. Essa interface inclui métodos definidos com nomes que seguem as convenções de nomenclatura do Spring Data JPA para expressar consultas.

### Exemplo de Interface de Repositório para `User`

```java
import org.springframework.data.jpa.repository.JpaRepository;

public interface UserRepository extends JpaRepository<User, Long> {

    // Encontra um usuário pelo nome
    List<User> findByName(String name);
    
    // Encontra um usuário pelo email
    User findByEmail(String email);
    
    // Encontra usuários por um trecho do nome
    List<User> findByNameContaining(String name);
    
    // Encontra usuários com email específico e ordena pelo nome
    List<User> findByEmailOrderByNomeAsc(String email);
}
```

### Como Funcionam as Consultas a Partir de Nomes de Métodos

1. **Prefixo**: Métodos de consulta começam com prefixos como `find...By`, `read...By`, `query...By`, `count...By`, e `get...By`. Depois do `By`, você pode adicionar critérios de consulta. O Spring Data JPA ignora o prefixo em termos de execução da consulta, mas ele é importante para a legibilidade.

2. **Critérios de Consulta**: Após o `By`, você adiciona condições de propriedades dos objetos de domínio. Por exemplo, `findByName` traduz-se numa consulta que busca usuários pelo campo `name`. Você pode adicionar condições complexas usando `And` e `Or`.

3. **Operadores de Consulta**: São suportadas várias operações dentro do nome do método, como `Containing`, `Between`, `LessThan`, `GreaterThan` etc., que permitem definir critérios mais detalhados para as consultas.

4. **Parâmetros do Método**: Os parâmetros dos métodos são passados para a consulta na ordem em que aparecem no nome do método.

### Observações

- **Simplicidade e Redução de Boilerplate**: Não é necessário escrever consultas SQL ou JPQL manualmente para operações simples de busca.
- **Facilidade de Manutenção**: Mudanças nas consultas muitas vezes podem ser feitas apenas ajustando os nomes dos métodos.
- **Integração Profunda**: Funciona bem com outras funcionalidades do Spring Data JPA, como paginação e ordenação.
- **Limitações em Consultas Complexas**: Para consultas muito complexas, pode ser necessário recorrer a `@Query` com JPQL ou SQL nativo, ou usar a API Criteria.
- **Nomenclatura**: À medida que a complexidade dos critérios de consulta aumenta, os nomes dos métodos podem se tornar longos e menos legíveis.

A tabela a seguir descreve as palavras-chave suportadas para JPA e o que um método contendo essa palavra-chave se traduz:
Aqui está a sua tabela organizada de maneira mais clara e formatada:

| Palavra Chave       | Exemplo                              | JPQL Correspondente                                                              |
|---------------------|--------------------------------------|----------------------------------------------------------------------------------|
| `Distinct`          | `findDistinctByLastnameAndFirstname` | `select distinct ... where x.lastname = ?1 and x.firstname = ?2`                 |
| `And`               | `findByLastnameAndFirstname`         | `… where x.lastname = ?1 and x.firstname = ?2`                                   |
| `Or`                | `findByLastnameOrFirstname`          | `… where x.lastname = ?1 or x.firstname = ?2`                                    |
| `Is`, `Equals`      | `findByFirstname`,`findByFirstnameIs`,`findByFirstnameEquals` | `… where x.firstname = ?1`                      |
| `Between`           | `findByStartDateBetween`             | `… where x.startDate between ?1 and ?2`                                          |
| `LessThan`          | `findByAgeLessThan`                  | `… where x.age < ?1`                                                             |
| `LessThanEqual`     | `findByAgeLessThanEqual`             | `… where x.age <= ?1`                                                            |
| `GreaterThan`       | `findByAgeGreaterThan`               | `… where x.age > ?1`                                                             |
| `GreaterThanEqual`  | `findByAgeGreaterThanEqual`          | `… where x.age >= ?1`                                                            |
| `After`             | `findByStartDateAfter`               | `… where x.startDate > ?1`                                                       |
| `Before`            | `findByStartDateBefore`              | `… where x.startDate < ?1`                                                       |
| `IsNull`, `Null`    | `findByAge(Is)Null`                  | `… where x.age is null`                                                          |
| `IsNotNull`, `NotNull` | `findByAge(Is)NotNull`              | `… where x.age is not null`                                                      |
| `Like`              | `findByFirstnameLike`                | `… where x.firstname like ?1`                                                    |
| `NotLike`           | `findByFirstnameNotLike`             | `… where x.firstname not like ?1`                                                |
| `StartingWith`      | `findByFirstnameStartingWith`        | `… where x.firstname like ?1` (parameter bound with appended `%`)                |
| `EndingWith`        | `findByFirstnameEndingWith`          | `… where x.firstname like ?1` (parameter bound with prepended `%`)               |
| `Containing`        | `findByFirstnameContaining`          | `… where x.firstname like ?1` (parameter bound wrapped in `%`)                   |
| `OrderBy`           | `findByAgeOrderByLastnameDesc`       | `… where x.age = ?1 order by x.lastname desc`                                    |
| `Not`               | `findByLastnameNot`                  | `… where x.lastname <> ?1`                                                       |
| `In`                | `findByAgeIn(Collection<Age> ages)`  | `… where x.age in ?1`                                                            |
| `NotIn`             | `findByAgeNotIn(Collection<Age> ages)`| `… where x.age not in ?1`                                                       |
| `True`              | `findByActiveTrue()`                 | `… where x.active = true`                                                        |
| `False`             | `findByActiveFalse()`                | `… where x.active = false`                                                       |
| `IgnoreCase`        | `findByFirstnameIgnoreCase`          | `… where UPPER(x.firstname) = UPPER(?1)`                                         |

Note que os placeholders como `?1`, `?2` são substituídos pelos parâmetros passados para o método em sua ordem de aparição. A sintaxe exata do JPQL pode variar ligeiramente com base nas especificações exatas e na implementação do JPA utilizada. Esta tabela oferece uma visão geral básica e as palavras-chave podem ser combinadas para criar consultas mais complexas e específicas.

# Consulta por Anotação

A consulta por anotação no Spring Data JPA é realizada através do uso da anotação `@Query`, que permite definir explicitamente uma consulta em JPQL (Java Persistence Query Language) ou SQL nativo diretamente no método de um repositório. Essa abordagem fornece uma flexibilidade significativa, permitindo a implementação de consultas complexas que podem não ser facilmente expressas através da derivação de nomes de métodos.

## `@Query`

Vamos considerar a classe `User` fornecida, que tem relacionamentos com outras entidades, como `Phone`. Suponha que queremos encontrar usuários pelo nome e trazer também os telefones associados de forma otimizada. Podemos fazer isso utilizando a anotação `@Query` para definir uma consulta JPQL que faça o "fetch join" dos telefones na mesma consulta, evitando o problema N+1 em operações de leitura.

Primeiro, definiríamos um repositório para a entidade `User`:

```java
import org.springframework.data.jpa.repository.JpaRepository;
import org.springframework.data.jpa.repository.Query;
import org.springframework.stereotype.Repository;

import java.util.List;

@Repository
public interface UserRepository extends JpaRepository<User, Long> {
    
    @Query("SELECT u FROM User u JOIN FETCH u.phones WHERE u.name = :name")
    List<User> findUsersByNameWithPhones(String name);
}
```

Neste exemplo, a anotação `@Query` define uma consulta JPQL que seleciona usuários (`u`) da entidade `User` e junta (`JOIN FETCH`) a entidade `phones` associada para carregar os telefones na mesma operação de banco de dados. A consulta é parametrizada para buscar por um nome específico (`:name`), que é passado como argumento para o método `findUsersByNameWithPhones`.

A consulta `"SELECT u FROM User u JOIN FETCH u.phones WHERE u.name = :name"` faz o seguinte:

- `SELECT u FROM User u`: Seleciona entidades `User`.
- `JOIN FETCH u.phones`: Realiza um "fetch join" na coleção `phones` de cada usuário, o que significa que os telefones serão carregados na mesma consulta, evitando múltiplas chamadas ao banco de dados para carregar os telefones de cada usuário separadamente.
- `WHERE u.name = :name`: Filtra os usuários pelo nome fornecido como parâmetro.

Esse método é particularmente útil quando você tem operações de leitura que precisam otimizar a carga de relacionamentos ou quando a consulta envolve lógica que vai além das capacidades da derivação de nome de método.

### Usando a expressão `LIKE`

O exemplo fornecido demonstra como usar a expressão `LIKE` em uma consulta JPQL personalizada no Spring Data JPA para buscar entidades `User` cujo `firstname` termina com um certo padrão especificado. Contudo, há um pequeno erro de sintaxe na consulta, pois os caracteres de percentagem (`%`) usados com `LIKE` para especificar padrões de correspondência devem estar dentro da string de consulta ou concatenados dinamicamente aos parâmetros da consulta. Vou corrigir esse erro na explicação e fornecer o exemplo correto.

Quando você quer buscar registros baseados em padrões parciais, como nomes que começam, terminam ou contêm uma certa substring, você usa o operador `LIKE` junto com `%` (que representa qualquer sequência de caracteres) em SQL ou JPQL. Aqui está como você pode corrigir e usar esse conceito corretamente:

```java
public interface UserRepository extends JpaRepository<User, Long> {

  @Query("select u from User u where u.firstname like CONCAT('%', ?1)")
  List<User> findByFirstnameEndsWith(String firstname);
}
```

Neste exemplo corrigido, a função `CONCAT('%', ?1)` é usada para concatenar dinamicamente o caractere de percentagem ao início do valor do parâmetro `firstname`. Isso cria um padrão que casa com qualquer `firstname` que termine com o string fornecido ao método. Por exemplo, se você passar `son` como parâmetro, a consulta buscará por usuários cujo nome seja algo como `Jackson`, `Mason`, etc.

- **`select u from User u`**: Esta parte da consulta seleciona todas as entidades `User`. `u` é um alias que representa a instância de `User` na consulta.

- **`where u.firstname like CONCAT('%', ?1)`**: Aqui, especifica-se a condição para filtrar os resultados. `u.firstname` deve terminar com o valor fornecido no parâmetro `firstname`. O operador `LIKE` é utilizado com `%` no início do valor para indicar que qualquer sequência de caracteres antes do valor especificado é aceitável. A função `CONCAT` é usada para unir `%` com o valor do parâmetro `?1`, que é o `firstname` passado para o método.

Esse método de consulta é bastante flexível e poderoso, permitindo filtragens baseadas em padrões de string complexos. No entanto, é importante notar que o uso excessivo de `LIKE` com padrões muito abertos (especialmente no início da string) pode afetar o desempenho, pois pode impedir o uso eficiente de índices pelo banco de dados. Além disso, certifique-se de que o valor do parâmetro não inclua o caractere `%`, a menos que você esteja ciente das implicações, pois isso pode ampliar significativamente o conjunto de resultados retornados.

### Native Queries
O uso de consultas nativas no Spring Data JPA permite que você execute consultas SQL diretamente no banco de dados, sem a necessidade de converter a consulta para a linguagem de consulta JPQL do JPA. Isso pode ser especialmente útil quando você precisa utilizar recursos específicos do banco de dados ou quando a consulta que você precisa executar não pode ser facilmente expressa ou otimizada através de JPQL.

No exemplo abaixo, utilizamos a anotação `@Query` para definir uma consulta nativa. O atributo `nativeQuery` é configurado como `true` para indicar que a consulta especificada é uma consulta SQL nativa, em vez de uma consulta JPQL.

**Exemplo**

```java
import org.springframework.data.jpa.repository.JpaRepository;
import org.springframework.data.jpa.repository.Query;

public interface UserRepository extends JpaRepository<User, Long> {

  @Query(value = "SELECT * FROM users WHERE email = ?1", nativeQuery = true)
  User findByEmailAddress(String emailAddress);
}
```

**Elementos Chave da Anotação `@Query` com `nativeQuery=true`:**

- **`@Query(value = "SELECT * FROM users WHERE email = ?1", nativeQuery = true)`**: Define a consulta SQL nativa que será executada. O `value` contém a consulta SQL nativa propriamente dita. `nativeQuery = true` sinaliza para o Spring Data JPA que esta é uma consulta SQL nativa e não uma consulta JPQL.

- **`User findByEmailAddress(String emailAddress);`**: Este é o método do repositório que você chama para executar a consulta definida. Quando chamado, ele executa a consulta SQL nativa especificada na anotação `@Query` usando o `emailAddress` fornecido como parâmetro para substituir o `?1` na consulta. O método retorna um objeto `User` correspondente ao endereço de email fornecido.

**OBS:**

- **Portabilidade**: O uso de consultas nativas pode afetar a portabilidade do seu aplicativo entre diferentes bancos de dados, pois as consultas podem utilizar sintaxes ou funcionalidades específicas de um determinado sistema de banco de dados.

- **Manutenção**: Consultas SQL nativas embutidas no código podem ser mais difíceis de manter e entender, especialmente para consultas complexas, em comparação com a abordagem mais declarativa de consultas JPQL ou do uso de métodos de consulta derivados do nome do método no Spring Data JPA.

Sempre avalie a necessidade e as implicações de usar consultas nativas em relação às alternativas disponíveis antes de optar por essa abordagem.

### Sort

No Spring Data JPA, o objeto `Sort` é usado para adicionar critérios de ordenação às consultas. Isso permite definir a direção da ordenação (ascendente ou descendente) e os atributos pelos quais os resultados devem ser ordenados. O exemplo fornecido demonstra como utilizar o `Sort` em consultas JPQL personalizadas para ordenar os resultados com base em diferentes critérios.

**Exemplo**

```java
import org.springframework.data.domain.Sort;
import org.springframework.data.jpa.repository.JpaRepository;
import org.springframework.data.jpa.repository.Query;
import java.util.List;

public interface UserRepository extends JpaRepository<User, Long> {

  @Query("select u from User u where u.lastname like ?1%")
  List<User> findByAndSort(String lastname, Sort sort);

  @Query("select u.id, LENGTH(u.firstname) as fn_len from User u where u.lastname like ?1%")
  List<Object[]> findByAsArrayAndSort(String lastname, Sort sort);
}
```

### Uso das Consultas com Ordenação

1. **Ordenar por `firstname` (nome):**
   ```java
   repo.findByAndSort("lannister", Sort.by("firstname"));
   ```
   Ordena os usuários cujo sobrenome começa com "lannister" pelo nome em ordem ascendente (padrão).

2. **Ordenar pela length (comprimento) de `firstname` usando JPQL:**
   ```java
   repo.findByAndSort("stark", Sort.by("LENGTH(firstname)"));
   ```
   Este caso não funcionará diretamente como esperado, pois o Spring Data JPA `Sort` não suporta expressões de função diretamente em sua sintaxe. Seria necessário usar uma abordagem diferente, como `JpaSort.unsafe`, para casos como este.

3. **Ordenar pela length (comprimento) de `firstname` usando `JpaSort.unsafe`:**
   ```java
   repo.findByAndSort("targaryen", JpaSort.unsafe("LENGTH(firstname)"));
   ```
   Permite ordenação por expressões ou funções específicas não suportadas diretamente pelo `Sort`, como a função `LENGTH` do SQL. `unsafe` indica que você está usando uma string literal para definir o critério de ordenação, o que pode ser necessário para funções ou operações específicas do banco de dados.

4. **Ordenação em consultas que retornam arrays:**
   ```java
   repo.findByAsArrayAndSort("bolton", Sort.by("fn_len"));
   ```
   Ordena os resultados (arrays de objetos, onde cada objeto inclui o `id` do usuário e o comprimento do nome) pelo alias `fn_len` (comprimento do nome) definido na consulta.

**OBS:**

- A ordenação no Spring Data JPA é flexível e pode ser facilmente aplicada a consultas, tanto para entidades completas quanto para arrays de valores específicos.

- Para critérios de ordenação complexos ou específicos do banco de dados (como funções), pode ser necessário usar `JpaSort.unsafe()`. Isso deve ser feito com cuidado, pois a injeção direta de strings na ordenação pode levar a vulnerabilidades se os valores não forem devidamente validados ou sanitizados.

- Usar `Sort.by("LENGTH(firstname)")` diretamente (como no exemplo 2) não é suportado pelo `Sort` padrão e foi listado para demonstrar o ponto. Na prática, para ordenar por expressões como esta, você precisaria recorrer ao `JpaSort.unsafe()`.

Este exemplo demonstra a flexibilidade e o poder do Spring Data JPA em lidar com ordenações em consultas, permitindo ajustes finos na forma como os dados são retornados e apresentados.

# Consulta Nomeada `@NamedQuery`

A anotação `@NamedQuery` é uma forma de definir consultas de forma estática diretamente na entidade JPA, o que permite a centralização da lógica de consulta dentro da classe de domínio a que pertence. Essas consultas nomeadas são carregadas em tempo de inicialização e podem ser referenciadas por um nome simples nos repositórios.

Fazendo uso de `@NamedQuery`, vamos definir uma consulta que busca usuários pelo email. Modificaremos a classe `User` para incluir uma consulta nomeada que realiza essa operação.

```java
import javax.persistence.*;
import java.util.List;

@Entity
@NamedQuery(
    name = "User.findByEmail",
    query = "SELECT u FROM User u WHERE u.email = :email"
)
public class User {

    @Id
    @GeneratedValue(strategy = GenerationType.IDENTITY)
    private Long id;

    private String name;

    private String email;

    @OneToMany(mappedBy = "user", cascade = CascadeType.ALL, fetch = FetchType.LAZY)
    private List<Phone> phones;

    // Getters and setters
}
```

Neste exemplo, a anotação `@NamedQuery` define uma consulta com o nome `"User.findByEmail"`, que pode ser utilizada para buscar um usuário pelo seu email. O parâmetro `:email` na consulta será substituído pelo valor fornecido ao executar a consulta.

**Referenciando a Consulta Nomeada no Repositório**

Para utilizar a consulta nomeada definida na classe `User`, referenciamo-la em um método no repositório `UserRepository`:

```java
import org.springframework.data.jpa.repository.JpaRepository;
import org.springframework.stereotype.Repository;

import java.util.Optional;

@Repository
public interface UserRepository extends JpaRepository<User, Long> {
    
    Optional<User> findByEmail(String email);
}
```

Embora este exemplo específico possa ser realizado diretamente através da convenção de nomenclatura do Spring Data JPA, consultas nomeadas são especialmente úteis para consultas mais complexas ou quando se deseja centralizar a definição da consulta na classe de entidade. A vantagem de usar `@NamedQuery` é que a consulta é validada em tempo de inicialização da aplicação, o que pode ajudar a identificar erros mais cedo no ciclo de desenvolvimento.

## XML Named Query

Utilizar definições de consultas nomeadas (`Named Queries`) em XML é uma alternativa à anotação `@NamedQuery` no código Java e permite definir consultas fora das classes de entidade. Essa abordagem é útil para manter as consultas separadas do código das entidades, facilitando a organização e a manutenção, especialmente em aplicações maiores ou quando se deseja evitar a alteração das classes de entidade.

1. **Criar o Arquivo XML de Mapeamento**: Este arquivo contém as definições das consultas nomeadas. O arquivo deve ser colocado no classpath da aplicação, comumente dentro do diretório `src/main/resources/META-INF`.

2. **Definir a Consulta Nomeada no XML**: Você especifica as consultas dentro do arquivo XML usando a sintaxe apropriada para mapeamento JPA.

3. **Referenciar o Arquivo XML no `persistence.xml`**: Assegure-se de que o arquivo de mapeamento XML está listado no arquivo `persistence.xml` para que seja reconhecido pela JPA.


Supondo que temos a classe `User` já definida, vamos criar uma consulta nomeada para buscar usuários pelo email utilizando XML.

1. **Criar o Arquivo de Mapeamento XML**:

   Arquivo `orm.xml` dentro de `src/main/resources/META-INF`:

   ```xml
   <?xml version="1.0" encoding="UTF-8"?>
   <entity-mappings xmlns="http://java.sun.com/xml/ns/persistence/orm"
                    xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
                    xsi:schemaLocation="http://java.sun.com/xml/ns/persistence/orm
                    http://java.sun.com/xml/ns/persistence/orm_2_0.xsd"
                    version="2.0">
   
       <named-query name="User.findByEmail">
           <query><![CDATA[SELECT u FROM User u WHERE u.email = :email]]></query>
       </named-query>
   
   </entity-mappings>
   ```

2. **Atualizar o `persistence.xml` para Incluir o Arquivo de Mapeamento**:

   No arquivo `persistence.xml`, referencie o `orm.xml` para que as consultas nomeadas definidas nele sejam reconhecidas pela JPA:

   ```xml
   <persistence-unit name="yourPersistenceUnit">
       <mapping-file>META-INF/orm.xml</mapping-file>
       <!-- Outras configurações -->
   </persistence-unit>
   ```

3. **Usar a Consulta Nomeada no Repositório**:

   No repositório `UserRepository`, você pode referenciar a consulta nomeada da mesma forma que faria com uma consulta definida com a anotação `@NamedQuery`:

   ```java
   import org.springframework.data.jpa.repository.JpaRepository;
   import org.springframework.stereotype.Repository;

   import java.util.Optional;

   @Repository
   public interface UserRepository extends JpaRepository<User, Long> {
       
       Optional<User> findByEmail(String email);
   }
   ```

Ao executar a aplicação, o JPA carrega as consultas nomeadas do arquivo XML, e elas podem ser utilizadas nos repositórios da mesma maneira que as consultas nomeadas definidas através de anotações. Esta abordagem mantém as consultas organizadas e separadas do código das entidades, facilitando a manutenção e promovendo a separação de responsabilidades.

## QueryRewriter

Em contextos específicos, como ao usar o Spring Data JPA, um `QueryRewriter` pode ser uma classe personalizada que modifica ou ajusta dinamicamente a consulta antes de ser executada. Isso pode ser útil para adicionar filtros, condições ou modificações baseadas em contexto que não são conhecidas em tempo de compilação.

Primeiramente, é importante notar que a funcionalidade de `queryRewriter` descrita não é parte padrão do Spring Data JPA até o meu último conhecimento. O exemplo dado parece sugerir uma funcionalidade customizada ou hipotética que não é diretamente suportada pelo Spring Data JPA como uma funcionalidade pronta para uso. Contudo, podemos imaginar um cenário e criar um exemplo conceptual baseado nessa ideia.

1. **Definindo a Interface do Repositório**

```java
import org.springframework.data.jpa.repository.JpaRepository;
import org.springframework.data.jpa.repository.Query;
import java.util.List;

public interface MyRepository extends JpaRepository<User, Long> {

    @Query(value = "SELECT original_user_alias.* FROM SD_USER original_user_alias WHERE original_user_alias.some_column = ?1",
            nativeQuery = true)
    List<User> findByNativeQuery(String param);

    @Query(value = "SELECT original_user_alias FROM User original_user_alias WHERE original_user_alias.someProperty = ?1",
            nativeQuery = false)
    List<User> findByNonNativeQuery(String param);
}
```
2. **Criando a Classe `QueryRewriter`**

Como a ideia de um `QueryRewriter` não é uma funcionalidade padrão, vamos conceituar uma classe que poderia atuar como um. Essa classe teria o propósito de modificar a consulta de acordo com os parâmetros fornecidos ou o contexto de execução.

```java
import javax.persistence.Query;

public class MyQueryRewriter {

    public String rewriteQuery(String originalQuery, Object... params) {
        // Lógica para reescrever a consulta baseada em parâmetros ou contexto
        // Por exemplo, adicionando uma condição extra se um parâmetro específico for não nulo
        if (params != null && params.length > 0 && params[0] != null) {
            return originalQuery + " AND additional_condition = '" + params[0] + "'";
        }
        return originalQuery;
    }
}
```

3. **Integrando o `QueryRewriter` com o Repositório**

Dada a natureza hipotética do `queryRewriter` em `@Query`, a integração desse reescritor com o repositório seria um processo customizado, possivelmente envolvendo o uso de um `EntityManager` para criar e executar a consulta dinamicamente dentro de um método de serviço ou repositório.

```java
import javax.persistence.EntityManager;
import javax.persistence.PersistenceContext;
import java.util.List;

public class MyService {

    @PersistenceContext
    private EntityManager entityManager;

    public List<User> findByNativeQueryWithRewriting(String param) {
        MyQueryRewriter rewriter = new MyQueryRewriter();
        String rewrittenQuery = rewriter.rewriteQuery("SELECT original_user_alias.* FROM SD_USER original_user_alias WHERE original_user_alias.some_column = ?1", param);

        Query query = entityManager.createNativeQuery(rewrittenQuery, User.class);
        query.setParameter(1, param);

        return query.getResultList();
    }
}
```

# Expressões SpEL

Spring Expression Language (SpEL) é uma poderosa ferramenta de expressão de linguagem que pode ser usada em vários contextos dentro do ecossistema Spring, incluindo Spring Data JPA. No contexto do Spring Data JPA, SpEL pode ser utilizado dentro das anotações `@Query` para adicionar flexibilidade às consultas, permitindo, por exemplo, referenciar dinamicamente o nome da entidade em uma consulta JPQL.

**Exemplo Explicado**


```java
import org.springframework.data.jpa.repository.JpaRepository;
import org.springframework.data.jpa.repository.Query;
import java.util.List;

public interface UserRepository extends JpaRepository<User, Long> {

  @Query("select u from #{#entityName} u where u.lastname = ?1")
  List<User> findByLastname(String lastname);
}
```

- **`#{#entityName}`**: Esta é uma expressão SpEL que referencia o nome da entidade JPA gerenciada por este repositório. No caso do `UserRepository`, `#{#entityName}` será resolvido para `User`, que é a entidade gerenciada pelo repositório.

- **`select u from #{#entityName} u where u.lastname = ?1`**: Esta consulta JPQL busca todas as instâncias de `User` (`#{#entityName}`) onde o campo `lastname` corresponde ao valor passado como parâmetro para o método `findByLastname`. O `?1` é um placeholder para o primeiro parâmetro do método.

Enquanto o uso de SpEL em consultas oferece grande flexibilidade, é importante utilizá-lo com cuidado para evitar complexidade desnecessária ou impactos na performance. O uso de expressões dinâmicas pode tornar as consultas mais difíceis de entender e manter se usadas indiscriminadamente. Portanto, avalie cuidadosamente a necessidade e o impacto de usar SpEL em suas consultas JPA.

Neste exemplo, `MyService` usaria `EntityManager` para executar a consulta reescrita manualmente, mostrando como uma funcionalidade de reescrita de consulta poderia ser implementada em um nível alto. Note que este exemplo é puramente ilustrativo e requer adaptação para casos de uso reais e integração com o Spring Data JPA ou qualquer framework de persistência usado.

# Views

No Spring Data JPA, é possível criar uma projeção baseada em uma view do banco de dados usando a anotação `@Immutable` do Hibernate para indicar que a entidade é imutável, ou seja, não deve ser modificada. Isso é particularmente útil quando você quer trabalhar com dados que são o resultado de uma consulta complexa ou agregação e não pretende alterá-los, apenas lê-los. Usar `@Immutable` garante que o Hibernate não tente propagar mudanças dessa entidade para o banco de dados, o que é ideal para trabalhar com views.

### Exemplo de Criação de uma View no Banco de Dados

Suponha que temos uma tabela `User` no banco de dados, e queremos criar uma view `user_summary` que contém um resumo dos dados dos usuários. A view poderia ser criada diretamente no banco de dados com um SQL como:

```sql
CREATE VIEW user_summary AS
SELECT id, CONCAT(firstname, ' ', lastname) AS fullname, email
FROM users;
```

### Mapeando a View no Spring Data JPA

Após criar a view no banco de dados, você pode mapeá-la em uma entidade JPA no seu aplicativo Spring. Usaremos a anotação `@Immutable` para indicar que esta entidade representa uma view imutável:

```java
import org.hibernate.annotations.Immutable;
import javax.persistence.Entity;
import javax.persistence.Id;

@Entity
@Immutable
public class UserSummary {

  @Id
  private Long id;
  private String fullname;
  private String email;

  // Getters
}
```

- **`@Entity`**: Marca a classe como uma entidade JPA, permitindo que ela seja usada para operações de banco de dados.

- **`@Immutable`**: Especifica que a entidade é imutável. O Hibernate não tentará fazer nenhuma alteração (INSERT, UPDATE ou DELETE) nesta entidade. Isso é particularmente útil para mapear views do banco de dados, onde as alterações não são aplicáveis.

- **Campos da Classe**: Os campos `id`, `fullname`, e `email` correspondem às colunas da view `user_summary`. O campo `id` é marcado com `@Id` para indicar que é a chave primária da entidade.

- A entidade `UserSummary` é uma projeção somente leitura dos dados na view `user_summary`. Qualquer tentativa de alteração será ignorada, o que é consistente com o comportamento esperado de uma view.

- Essa abordagem é útil para otimizar consultas de leitura e trabalhar com dados agregados sem a necessidade de carregar entidades completas ou executar operações complexas em memória.

- Lembre-se de que a criação e manutenção das views é feita fora do contexto do Spring Data JPA, diretamente no banco de dados ou por meio de scripts de migração.

Usar a anotação `@Immutable` com entidades que representam views do banco de dados é uma prática recomendada para garantir a integridade dos dados e a clareza da arquitetura do seu aplicativo.

## @Subselect

Para utilizar `@Subselect`, você define a subconsulta SQL dentro da anotação em uma classe de entidade. Esta entidade se comportará como se fosse mapeada para uma view, mas a "view" é definida apenas no nível da aplicação, não existindo como uma entidade no banco de dados.

Aqui está um exemplo de como você pode usar `@Subselect`:

```java
import org.hibernate.annotations.Immutable;
import org.hibernate.annotations.Subselect;
import javax.persistence.Entity;
import javax.persistence.Id;

@Entity
@Immutable
@Subselect("SELECT id, CONCAT(firstname, ' ', lastname) AS fullname, email FROM users")
public class UserSummary {

  @Id
  private Long id;
  private String fullname;
  private String email;

  // Getters e setters
}
```

Embora `@Subselect` possa simular o comportamento de uma view no nível da aplicação, ela não substitui a criação de views no banco de dados quando isso é necessário ou mais apropriado para a situação. A escolha entre usar `@Subselect` ou uma view de banco de dados depende de vários fatores, incluindo requisitos de performance, complexidade da consulta, e se a consulta precisa ser reutilizada fora da aplicação.

# Stored Procedure

A introdução da anotação `@Procedure` na especificação JPA 2.1 ampliou significativamente o suporte à integração com Stored Procedures diretamente de dentro das aplicações Java. Com `@Procedure`, você pode declarar metadata de uma Stored Procedure em um método de repositório, facilitando a invocação de procedimentos armazenados no banco de dados de maneira declarativa e reduzindo a necessidade de boilerplate code para executar tais operações.

## @Procedure

Para utilizar a anotação `@Procedure`, você geralmente a aplica a um método dentro de um repositório do Spring Data JPA. O Spring Data JPA usa essa anotação para mapear o método do repositório a uma Stored Procedure específica no banco de dados.

Aqui está um exemplo de como você pode usar `@Procedure` para invocar uma Stored Procedure que retorna o nome de um usuário baseado no seu ID:

**1. Definir a Stored Procedure no Banco de Dados**

Suponha que temos a seguinte Stored Procedure no MySQL:

```sql
CREATE PROCEDURE GetUserById(IN userId INT, OUT userName VARCHAR(100))
BEGIN
    SELECT name INTO userName FROM users WHERE id = userId;
END
```

Esta Stored Procedure, chamada `GetUserById`, aceita um `id` de usuário como parâmetro de entrada e define um parâmetro de saída `userName` com o nome do usuário correspondente.

**2. Declarar a Stored Procedure no Repositório JPA**

```java
import org.springframework.data.jpa.repository.JpaRepository;
import org.springframework.data.jpa.repository.query.Procedure;
import org.springframework.stereotype.Repository;

@Repository
public interface UserRepository extends JpaRepository<User, Long> {

    @Procedure(name = "GetUserById")
    String getUserById(Integer id);
}
```

- **@Procedure**: Esta anotação é aplicada a um método no repositório. `name` é opcional se o nome do método segue a convenção de nomenclatura que o Spring Data pode associar automaticamente à Stored Procedure. Caso contrário, você pode especificar explicitamente o nome da Stored Procedure usando o atributo `name`.

- **Retorno e Parâmetros**: O tipo de retorno do método e os parâmetros devem corresponder ao esperado pela Stored Procedure. No exemplo acima, esperamos que a Stored Procedure retorne um `String`, que é o nome do usuário.

Este mecanismo fornece uma maneira simples e poderosa de trabalhar com Stored Procedures dentro da camada de persistência de uma aplicação Spring, aproveitando a abstração fornecida pelo Spring Data JPA. É importante notar que, embora a anotação `@Procedure` facilite a invocação de Stored Procedures, as próprias Procedures ainda precisam ser definidas e criadas no banco de dados, separadamente do código da aplicação.

# Referências de Conteúdo

Este documento fornece referências para os conceitos e funcionalidades discutidos, relacionados ao JPA, Hibernate, e Spring Data JPA, especialmente focando no uso de Stored Procedures e consultas.

## JPA e Hibernate

- [Java Persistence API (JPA) 2.1 Specification](https://jakarta.ee/specifications/persistence/2.1/)
- [Hibernate User Guide](https://docs.jboss.org/hibernate/orm/current/userguide/html_single/Hibernate_User_Guide.html)

## Spring Data JPA

- [Spring Data JPA - Referência Oficial](https://docs.spring.io/spring-data/jpa/docs/current/reference/html/)
- [Spring Data Repositories](https://docs.spring.io/spring-data/data-commons/docs/current/reference/html/#repositories)

## Consultas e Stored Procedures

- [Spring Data JPA - Consultas](https://docs.spring.io/spring-data/jpa/docs/current/reference/html/#jpa.query-methods)
- [Usando @Query para Consultas JPQL e Native](https://docs.spring.io/spring-data/jpa/docs/current/reference/html/#jpa.query-methods.at-query)
- [Invocando Stored Procedures com @Procedure](https://docs.spring.io/spring-data/jpa/docs/current/reference/html/#jpa.stored-procedures)

## Exemplos e Tutoriais

- [Accessing Data with JPA - Tutorial Spring](https://spring.io/guides/gs/accessing-data-jpa/)
- [Using Stored Procedures in Spring Data JPA](https://www.baeldung.com/spring-data-jpa-stored-procedures)

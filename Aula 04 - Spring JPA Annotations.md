# **Spring JPA Annotations** 

## **O que é JPA?**
JPA, que significa Java Persistence API, não é uma ferramenta ou framework por si só; 
em vez disso, ele fornece um conjunto de conceitos e diretrizes que implementam diretamente 
como gerenciar dados relacionais em aplicativos Java. Metadados de anotações são fornecidos 
pelo JPA para definir uma relação entre objetos e bancos de dados relacionais.

## **O que é Annotation**
A anotação é uma informação suplementar sobre o programa. Os desenvolvedores usam anotações 
para informar o JPA.

## **JPA Annotations**
As anotações JPA são usadas no mapeamento de objetos Java para tabelas de banco de dados. 
O Hibernate é a biblioteca ORM mais popular que utiliza as especificações JPA e fornece algumas 
anotações adicionais. As anotações podem ser adicionadas ao código-fonte e permitidas a serem 
retidas pelo JVM em tempo de execução.

<div align="center">
    
![Principais Annotations](https://miro.medium.com/v2/resize:fit:1400/format:webp/1*Z91sIw81eeIsjEnLEtseaQ.jpeg)

</div>

Essas são algumas das anotações mais comumente usadas em JPA/Hibernate e suas respectivas funções:

- `@Id`: Indica que o campo anotado é a chave primária da entidade.
- `@GeneratedValue`: Especifica a estratégia de geração de valores para a chave primária automaticamente.
- `@Table`: Permite definir informações adicionais sobre a tabela associada à entidade.
- `@Entity`: Marca a classe como uma entidade persistente.
- `@Column`: Permite definir informações adicionais sobre a coluna associada ao campo.
- `@Transient`: Indica que o campo não deve ser persistido no banco de dados.
- `@Temporal`: Especifica o tipo de dado temporal (data, hora etc.) de um campo de data/hora.
- `@Embedded`: Marca um campo como embutido, ou seja, parte de outra entidade.
- `@Embeddable`: Marca uma classe como embutível, ou seja, pode ser parte de outra entidade.
- `@ElementCollection`: Mapeia uma coleção de tipos básicos ou embeddables.
- `@OneToMany`: Estabelece uma relação de um-para-muitos entre duas entidades.
- `@ManyToOne`: Estabelece uma relação de muitos-para-um entre duas entidades.
- `@ManyToMany`: Estabelece uma relação muitos-para-muitos entre duas entidades.
- `@OneToOne`: Estabelece uma relação um-para-um entre duas entidades.
- `@Lob`: Indica que o campo contém um objeto grande (Large Object), como um blob ou clob.
- `@JoinColumn`: Permite definir informações adicionais sobre a coluna que é usada para a junção de entidades em relacionamentos.

Essas anotações são essenciais para mapear entidades Java para tabelas de banco de dados e 
para definir o comportamento de persistência.

## **@Id**
A anotação `@Id` é usada em Java para marcar um campo como a chave primária de uma entidade. 
Geralmente é utilizada em conjunto com um framework ORM (Object-Relational Mapping) como o Hibernate, 
que mapeia objetos Java para tabelas de banco de dados relacionais.

A anotação `@Id` pode ser usada com vários parâmetros para especificar detalhes sobre a chave primária. 
Aqui está um exemplo de como a anotação @Id pode ser usada com parâmetros:

``` java
@Entity
@Table(name = "students")
public class Student {
    @Id
    @GeneratedValue(strategy = GenerationType.IDENTITY)
    @Column(name = "id")
    private Long id;
    // other fields and methods
}
```
## **@Generated**
A anotação ``@GeneratedValue`` é usada em Java para gerar automaticamente valores para colunas de chave primária 
em uma tabela de banco de dados. Esta anotação é tipicamente usada em conjunto com a anotação ``@Id`` para indicar 
que um campo específico é a chave primária para uma tabela.

A anotação ``@GeneratedValue`` pode receber um dos quatro parâmetros:

- ``strategy``: Este parâmetro especifica a estratégia a ser usada para gerar a chave primária. Existem quatro estratégias disponíveis: AUTO, IDENTITY, SEQUENCE, TABLE e UUID.
  - `GenerationType.IDENTITY:` Essa estratégia delega a geração da chave primária para o banco de dados. Normalmente é usado com colunas de identidade auto-incrementáveis em bancos de dados relacionais.
  - `GenerationType.AUTO`: Essa estratégia permite ao provedor JPA escolher a melhor estratégia de geração de chave primária com base no banco de dados subjacente.
  - `GenerationType.SEQUENCE:` Essa estratégia é usada para chaves primárias que são geradas por uma sequência no banco de dados. Isso é comum em bancos de dados como Oracle, onde você define uma sequência separada para gerar valores únicos.
  - `GenerationType.TABLE:` Essa estratégia envolve a criação de uma tabela especial no banco de dados para rastrear os valores de chave primária.
  - `GenerationType.UUID` é utilizada para gerar valores de chave primária usando identificadores universais únicos (UUIDs). Um UUID é um valor único de 128 bits que é gerado de acordo com algoritmos específicos e que é garantido ser único em um determinado contexto.
- ``generator``: Este parâmetro especifica o nome do gerador a ser usado para gerar a chave primária.

Aqui está um exemplo de como usar a anotação ``@GeneratedValue`` com o parâmetro ``strategy``:

``` java
@Entity
public class User {
    @Id
    @GeneratedValue(strategy = GenerationType.IDENTITY)
    private Long id;

    private String username;
    private String password;
    // other fields and methods omitted for brevity
}
```

Neste exemplo, a classe ``User`` representa uma tabela em um banco de dados. O campo id é marcado com a anotação ``@Id`` para indicar que é a chave primária da tabela. A anotação ``@GeneratedValue`` também é aplicada ao campo id com o parâmetro ``strategy`` definido como ``GenerationType.IDENTITY``. Isso significa que o banco de dados gerará um valor único para a chave primária de cada nova linha adicionada à tabela, usando uma coluna de identidade.

## **@Table**
A anotação ``@Table`` é usada em Java para especificar os detalhes da tabela do banco de dados que uma determinada entidade (classe) deve ser mapeada. Esta anotação pode ser usada para especificar o nome da tabela, seu esquema, catálogo, índices e outros detalhes específicos do banco de dados.

A anotação ``@Table`` pode receber os seguintes parâmetros:

- ``name``: Este parâmetro especifica o nome da tabela do banco de dados que a entidade deve ser mapeada. Se não especificado, o nome padrão é o nome da classe da entidade.
- ``schema``: Este parâmetro especifica o nome do esquema (banco de dados) ao qual a tabela pertence.
- ``catalog``: Este parâmetro especifica o nome do catálogo (banco de dados) ao qual a tabela pertence.
- ``uniqueConstraints``: Este parâmetro é usado para especificar uma ou mais restrições únicas na tabela.
- ``indexes``: Este parâmetro é usado para especificar um ou mais índices na tabela.

Aqui está um exemplo de como usar a anotação ``@Table`` com o parâmetro ``name``:

```java
@Entity
@Table(name = "users")
public class User {
    @Id
    @GeneratedValue(strategy = GenerationType.IDENTITY)
    private Long id;

    private String username;
    private String password;
    // outros campos e métodos omitidos por brevidade
}
```

Neste exemplo, a classe ``User`` representa uma tabela em um banco de dados. A anotação ``@Table`` também é aplicada à classe com o parâmetro ``name`` definido como "users". Isso significa que a classe ``User`` será mapeada para uma tabela do banco de dados chamada "users".

## **@Entity**

A anotação ``@Entity`` é usada em Java para marcar uma classe como uma classe de entidade, o que significa que ela deve ser mapeada para uma tabela de banco de dados. Esta anotação é tipicamente usada em conjunto com outras anotações, como ``@Table`` e ``@Id``.

Aqui está um exemplo de como usar a anotação ``@Entity``:

```java
@Entity(name = "User")
@Table(name = "users")
public class User {
    @Id
    @GeneratedValue(strategy = GenerationType.IDENTITY)
    private Long id;

    private String username;
    private String password;
    // outros campos e métodos omitidos por brevidade
}
```

Neste exemplo, a classe ``User`` representa uma tabela em um banco de dados. A anotação ``@Entity`` é aplicada à classe para indicar que ela deve ser mapeada para uma tabela de banco de dados.

<sub> 
Obs. nome da tabela será "users". Isso é especificado pela anotação @Table(name = "users"). A anotação @Entity(name = "User") define o nome da entidade como "User", mas isso é apenas uma convenção para referenciar a entidade em consultas JPQL ou em outros contextos do JPA. 
</sub>

## **@Column**

A anotação ``@Column`` é usada em Java para especificar os detalhes de uma coluna específica em uma tabela de banco de dados que um campo deve ser mapeado. Esta anotação pode ser usada para especificar o nome da coluna, seu tipo de dados, comprimento, precisão, escala e outros detalhes específicos do banco de dados.

A anotação ``@Column`` pode receber os seguintes parâmetros:

- ``name``: Este parâmetro especifica o nome da coluna do banco de dados que o campo deve ser mapeado. Se não especificado, o nome padrão é o nome do campo.
- ``nullable``: Este parâmetro especifica se a coluna pode conter valores nulos ou não.
- ``unique``: Este parâmetro especifica se a coluna deve conter valores únicos ou não.
- ``length``: Este parâmetro especifica o comprimento máximo da coluna (para colunas de string).
- ``precision``: Este parâmetro especifica a precisão da coluna (para colunas numéricas).
- ``scale``: Este parâmetro especifica a escala da coluna (para colunas numéricas).
- ``insertable``: Este parâmetro especifica se a coluna deve ser incluída em declarações de inserção SQL ou não.
- ``updatable``: Este parâmetro especifica se a coluna deve ser incluída em declarações de atualização SQL ou não.

Aqui está um exemplo de como usar a anotação ``@Column`` com os parâmetros ``name`` e ``nullable``:

```java
@Entity
@Table(name = "users")
public class User {
    @Id
    @GeneratedValue(strategy = GenerationType.IDENTITY)
    private Long id;

    @Column(name = "username", nullable = false)
    private String username;

    @Column(name = "password", nullable = false)
    private String password;
    // outros campos e métodos omitidos por brevidade
}
```

Neste exemplo, a classe ``User`` representa uma tabela em um banco de dados. A anotação ``@Entity`` é aplicada à classe para indicar que ela deve ser mapeada para uma tabela de banco de dados. A anotação ``@Table`` também é aplicada à classe com o parâmetro ``name`` definido como "users". Os campos username e password são marcados com a anotação ``@Column`` com o parâmetro ``name`` definido como "username" e "password", respectivamente. O parâmetro ``nullable`` é definido como false para ambas as colunas, o que significa que elas não podem conter valores nulos. Isso significa que os campos username e password serão mapeados para colunas não nulas na tabela "users" no banco de dados.

## **@Transient**
A anotação ``@Transient`` é usada em Java para indicar que um campo não deve ser persistido no banco de dados. Isso significa que o campo não será mapeado para uma coluna do banco de dados e seu valor não será armazenado no banco de dados.

A anotação ``@Transient`` não recebe nenhum parâmetro. Simplesmente é usada para marcar um campo como transitório.

Aqui está um exemplo de como usar a anotação ``@Transient``:

```java
@Entity
@Table(name = "users")
public class User {
    @Id
    @GeneratedValue(strategy = GenerationType.IDENTITY)
    private Long id;

    @Column(name = "username", nullable = false)
    private String username;

    @Column(name = "password", nullable = false)
    private String password;

    @Transient
    private String confirmPassword;
    // outros campos e métodos omitidos por brevidade
}
```

Neste exemplo, a classe ``User`` representa uma tabela em um banco de dados. A anotação ``@Entity`` é aplicada à classe para indicar que ela deve ser mapeada para uma tabela de banco de dados. A anotação ``@Table`` também é aplicada à classe com o parâmetro ``name`` definido como "users". Os campos username e password são marcados com a anotação ``@Column`` para indicar que devem ser persistidos no banco de dados.

O campo confirmPassword é marcado com a anotação ``@Transient`` para indicar que não deve ser persistido no banco de dados. Este campo é apenas utilizado para fins de validação e não deve ser armazenado no banco de dados. Quando o objeto User é salvo no banco de dados, o campo confirmPassword será ignorado.

Note que os campos marcados com ``@Transient`` não são serializados por padrão, então eles não serão incluídos em representações JSON ou XML do objeto, a menos que sejam explicitamente incluídos.

<sub>
Em SQL isto pode representar um atributo derivado (calculado / adquirido com base em outros atributos)
</sub>

## **@Temporal**

A anotação ``@Temporal`` é usada em Java para especificar o tipo de uma coluna temporal de banco de dados ou de um campo Java. É utilizada para indicar como um valor de data, hora ou timestamp deve ser armazenado ou recuperado do banco de dados.

A anotação ``@Temporal`` recebe um único parâmetro, value, que especifica o tipo do campo temporal. O parâmetro value pode assumir os seguintes valores:

- ``TemporalType.DATE``: Este valor é usado para indicar que o campo representa apenas uma data, sem nenhuma informação de hora.
- ``TemporalType.TIME``: Este valor é usado para indicar que o campo representa apenas uma hora, sem nenhuma informação de data.
- ``TemporalType.TIMESTAMP``: Este valor é usado para indicar que o campo representa um timestamp, que inclui tanto a data quanto a hora.

Aqui está um exemplo de como usar a anotação ``@Temporal`` com o parâmetro value:

```java
@Entity
@Table(name = "events")
public class Event {
    @Id
    @GeneratedValue(strategy = GenerationType.IDENTITY)
    private Long id;

    @Column(name = "event_date")
    @Temporal(TemporalType.DATE)
    private Date eventDate;

    @Column(name = "event_time")
    @Temporal(TemporalType.TIME)
    private Date eventTime;

    @Column(name = "event_timestamp")
    @Temporal(TemporalType.TIMESTAMP)
    private Date eventTimestamp;
    // outros campos e métodos omitidos por brevidade
}
```

Neste exemplo, a classe ``Event`` representa uma tabela em um banco de dados. A anotação ``@Entity`` é aplicada à classe para indicar que ela deve ser mapeada para uma tabela de banco de dados. A anotação ``@Table`` também é aplicada à classe com o parâmetro ``name`` definido como "events".

O campo eventDate é marcado com a anotação ``@Temporal`` com o parâmetro value definido como ``TemporalType.DATE``. Isso indica que o campo eventDate representa apenas uma data, sem nenhuma informação de hora.

O campo eventTime é marcado com a anotação ``@Temporal`` com o parâmetro value definido como ``TemporalType.TIME``. Isso indica que o campo eventTime representa apenas uma hora, sem nenhuma informação de data.

O campo eventTimestamp é marcado com a anotação ``@Temporal`` com o parâmetro value definido como ``TemporalType.TIMESTAMP``. Isso indica que o campo eventTimestamp representa um timestamp, que inclui tanto a data quanto a hora.

## **@Embedded**

A anotação ``@Embedded`` é usada em Java para indicar que uma entidade possui um objeto incorporado. Isso significa que os campos do objeto incorporado devem ser mapeados para colunas na tabela do banco de dados da entidade pai.

Aqui está um exemplo de como usar a anotação ``@Embedded``:

```java
@Entity
@Table(name = "employees")
public class Employee {
    @Id
    @GeneratedValue(strategy = GenerationType.IDENTITY)
    private Long id;

    @Column(name = "name")
    private String name;

    @Embedded
    private Address address;
    // outros campos e métodos omitidos por brevidade
}
```

```java
@Embeddable
public class Address implements Serializable {
    private String street;
    private String city;
    private String state;
    private String zipCode;
    // construtores, getters e setters omitidos por brevidade
}
```

Neste exemplo, a classe ``Employee`` representa uma tabela em um banco de dados. A anotação ``@Entity`` é aplicada à classe para indicar que ela deve ser mapeada para uma tabela de banco de dados. A anotação ``@Table`` também é aplicada à classe com o parâmetro ``name`` definido como "employees".

O campo address é marcado com a anotação ``@Embedded`` para indicar que é um objeto incorporado. O parâmetro ``@AttributeOverrides`` é usado para especificar o mapeamento dos campos do objeto Address para as colunas do banco de dados.

Neste caso, os campos street, city, state e zipCode do objeto Address são mapeados para as colunas address_street, address_city, address_state e address_zip_code da tabela employees, respectivamente. Isso substitui os mapeamentos de coluna padrão especificados na classe Address.

Note que a classe Address em si não precisa ser anotada com nenhuma anotação especial, já que é um objeto incorporado.

<sub>
Em SQL isto é representado como um atributo composto
</sub>

## **@Embeddable**

A anotação ``@Embeddable`` é usada em Java para indicar que uma classe é uma classe incorporável. Uma classe incorporável é uma classe cujas instâncias são armazenadas como parte dos dados de outra entidade. A anotação ``@Embeddable`` é tipicamente usada para anotar uma classe que é usada como um componente dentro de outra entidade.

A anotação ``@Embeddable`` não recebe nenhum parâmetro. Aqui está um exemplo de como usar a anotação ``@Embeddable``:

No Exemplo anterior, a classe ``Address`` é marcada com a anotação ``@Embeddable`` para indicar que é uma classe incorporável. A classe ``Address`` contém campos para o endereço de rua, cidade, estado e código postal.

A anotação ``@Embeddable`` é usada para indicar ao provedor JPA que as instâncias da classe ``Address`` devem ser incorporadas aos dados de outra entidade. O provedor JPA mapeia os campos da classe ``Address`` para colunas na mesma tabela que a entidade pai. A entidade pai usaria a anotação ``@Embedded`` para especificar que contém uma instância da classe ``Address``.

No exemplo demonstrado acima, a classe ``Employee`` contém uma instância da classe ``Address`` como um campo. A anotação ``@Embedded`` é usada para indicar que o objeto ``Address`` está incorporado dentro do objeto ``Employee``. O provedor JPA mapeia os campos da classe ``Address`` para colunas na mesma tabela que a entidade ``Employee``.

<sub>
Quando uma classe implementa a interface Serializable, ela indica que os objetos dessa classe podem ser serializados e desserializados. Isso permite que os objetos sejam armazenados em arquivos, transmitidos pela rede ou passados entre diferentes partes de um programa Java.
</sub>

## **@ElementCollection**
A anotação ``@ElementCollection`` é usada em Java para indicar que uma coleção de valores simples ou objetos incorporáveis deve ser persistida em uma tabela separada. A anotação ``@ElementCollection`` é utilizada para definir um relacionamento um-para-muitos entre uma entidade e uma coleção de tipos de valores ou tipos incorporáveis.

A anotação ``@ElementCollection`` aceita vários parâmetros opcionais:

- ``fetch``: é usado em mapeamentos de relacionamento de entidades JPA (Java Persistence API) para determinar como os dados associados a um relacionamento devem ser recuperados do banco de dados. Ele define a estratégia de carregamento dos dados relacionados quando a entidade principal é carregada.

    -`FetchType.LAZY`: Com `FetchType.LAZY`, os dados associados ao relacionamento são carregados sob demanda, ou seja, somente quando são explicitamente acessados pela primeira vez. Essa é a opção mais comum para relacionamentos de muitos para um (`@ManyToOne`) e um para um (`@OneToOne`).

    -`FetchType.EAGER`: Com `FetchType.EAGER`, os dados associados ao relacionamento são carregados imediatamente junto com a entidade principal. Isso significa que os dados associados são carregados automaticamente quando a entidade principal é recuperada do banco de dados. Isso pode resultar em grandes quantidades de dados sendo carregados desnecessariamente e é geralmente evitado, a menos que seja necessário.
- ``targetClass``: Especifica a classe dos elementos da coleção. Isso só é necessário se a coleção não for definida usando genéricos.

Aqui está um exemplo de como usar a anotação ``@ElementCollection``:

```java
@Entity
@Table(name = "orders")
public class Order {
    @Id
    @GeneratedValue(strategy = GenerationType.IDENTITY)
    private Long id;

    @Column(name = "customer_name")
    private String customerName;

    @ElementCollection(fetch = FetchType.LAZY)
    @CollectionTable(name = "order_items", joinColumns = @JoinColumn(name = "order_id"))
    @OrderColumn(name = "item_order")
    private List<String> items;
    // outros campos e métodos omitidos por brevidade
}
```

Neste exemplo, a classe Order representa uma tabela em um banco de dados. A anotação ``@Entity`` é aplicada à classe para indicar que ela deve ser mapeada para uma tabela de banco de dados. A anotação ``@Table`` também é aplicada à classe com o parâmetro ``name`` definido como "orders".

O campo items é marcado com a anotação ``@ElementCollection`` para indicar que é uma coleção de valores simples a serem persistidos em uma tabela separada. O parâmetro ``fetch`` é definido como LAZY, o que significa que a coleção será carregada apenas quando acessada pela primeira vez.

A anotação ``@CollectionTable`` é usada para especificar o nome da tabela que será usada para armazenar os elementos da coleção. Neste caso, o nome da tabela é definido como "order_items", e uma coluna de junção é definida com o nome "order_id". Esta coluna de junção será usada para mapear os elementos da coleção para a entidade pai.

A anotação ``@OrderColumn`` é usada para especificar o nome da coluna que será usada para armazenar a ordem dos elementos na coleção. Neste caso, o nome da coluna é definido como "item_order".

Observe que o campo items é uma simples List<String> neste exemplo. Se você quiser usar uma coleção de objetos incorporáveis ​​em vez disso, precisaria definir uma classe separada para os objetos incorporáveis ​​e anotar a classe com a anotação ``@Embeddable``. Você poderia então definir uma coleção de objetos incorporáveis ​​na classe Order e marcá-la com a anotação ``@ElementCollection``.

<sub>
Em SQL isto pode ser representado como um atributo multivalorado
</sub>

## **@OneToMany**
A anotação ``@OneToMany`` é usada em Java para definir um relacionamento um-para-muitos entre duas entidades. Geralmente é usada quando uma entidade possui uma coleção de outras entidades.

A anotação ``@OneToMany`` aceita vários parâmetros:

- ``targetEntity``: Especifica a classe da entidade de destino. Isso só é necessário se a entidade de destino não for especificada usando genéricos.
- ``mappedBy``: Especifica o nome do atributo na entidade de destino que mapeia para a chave primária da entidade proprietária.
- ``cascade``: Especifica as operações de cascata a serem aplicadas à entidade de destino.
    - `CascadeType.ALL`: Indica que todas as operações de persistência (persist, remove, merge, refresh, detach) feitas na entidade pai devem ser aplicadas às entidades filhas.
    - `CascadeType.PERSIST`: Indica que a operação de persistência (persist) feita na entidade pai deve ser aplicada às entidades filhas.
    - `CascadeType.REMOVE`: Indica que a operação de remoção (remove) feita na entidade pai deve ser aplicada às entidades filhas.
    - `CascadeType.MERGE`: Indica que a operação de merge (merge) feita na entidade pai deve ser aplicada às entidades filhas.
    - `CascadeType.REFRESH`: Indica que a operação de refresh (refresh) feita na entidade pai deve ser aplicada às entidades filhas.
    - `CascadeType.DETACH`: Indica que a operação de detach (detach) feita na entidade pai deve ser aplicada às entidades filhas.     
- ``fetch``: Especifica a estratégia de busca a ser usada para a entidade de destino.
- ``orphanRemoval``: É usado para remover automaticamente entidades filhas quando elas não são mais referenciadas pela entidade pai.

Aqui está um exemplo de como usar a anotação ``@OneToMany``:

```java
@Entity
@Table(name = "users")
public class User {
    @Id
    @GeneratedValue(strategy = GenerationType.IDENTITY)
    private Long id;

    @Column(name = "username")
    private String username;

    @OneToMany(mappedBy = "user", cascade = CascadeType.ALL, orphanRemoval = true)
    private List<Address> addresses;
    // outros campos e métodos omitidos por brevidade
}
```

```java
@Entity
@Table(name = "addresses")
public class Address {
    @Id
    @GeneratedValue(strategy = GenerationType.IDENTITY)
    private Long id;

    @Column(name = "street")
    private String street;

    @Column(name = "city")
    private String city;

    @Column(name = "state")
    private String state;

    @ManyToOne
    @JoinColumn(name = "user_id")
    private User user;
    // outros campos e métodos omitidos por brevidade
}
```

Neste exemplo, a classe User representa uma tabela em um banco de dados. A anotação ``@Entity`` é aplicada à classe para indicar que ela deve ser mapeada para uma tabela de banco de dados. A anotação ``@Table`` também é aplicada à classe com o parâmetro ``name`` definido como "users".

O campo addresses é marcado com a anotação ``@OneToMany`` para indicar que representa uma coleção de objetos Address, sendo que cada objeto Address possui uma referência a um único objeto User. O parâmetro mappedBy é definido como "user", o que indica que o mapeamento é feito através do campo user na classe Address.

O parâmetro cascade é definido como CascadeType.ALL, o que indica que todas as alterações feitas na entidade User devem ser propagadas também para as entidades Address. O parâmetro orphanRemoval é definido como true, o que significa que quaisquer objetos Address que não sejam mais referenciados por um objeto User serão automaticamente excluídos.

A classe Address também representa uma tabela no banco de dados. Ela tem um campo user marcado com a anotação ``@ManyToOne``, o que indica que cada objeto Address está associado a um único objeto User. A anotação JoinColumn é usada para especificar o nome da coluna na tabela addresses que mapeia para a chave primária da tabela users.

## **@ManyToOne**

A anotação ``@ManyToOne`` é usada em Java para definir um relacionamento muitos-para-um entre duas entidades. Geralmente é usada quando uma entidade possui uma referência a outra entidade.

A anotação ``@ManyToOne`` aceita vários parâmetros:

- ``targetEntity``: Especifica a classe da entidade de destino. Isso só é necessário se a entidade de destino não for especificada usando genéricos.
- ``cascade``: Especifica as operações de cascata a serem aplicadas à entidade de destino.
- ``fetch``: Especifica a estratégia de busca a ser usada para a entidade de destino.
- ``optional``: Especifica se a associação é opcional ou obrigatória. Por padrão, é opcional.
- 
Neste exemplo anteriormente citado, a classe Order representa uma tabela em um banco de dados. A anotação ``@Entity`` é aplicada à classe para indicar que ela deve ser mapeada para uma tabela de banco de dados. A anotação ``@Table`` também é aplicada à classe com o parâmetro ``name`` definido como "orders".

O campo customer é marcado com a anotação ``@ManyToOne`` para indicar que representa uma referência a um objeto Customer, sendo que cada objeto Order tem uma referência a um único objeto Customer. A anotação JoinColumn é usada para especificar o nome da coluna na tabela orders que mapeia para a chave primária da tabela customers.

A classe Customer também representa uma tabela no banco de dados. Ela tem um campo orders marcado com a anotação ``@OneToMany``, o que indica que cada objeto Customer tem uma coleção de objetos Order associados a ele. O parâmetro mappedBy é definido como "customer", o que indica que o mapeamento é feito através do campo customer na classe Order.

O parâmetro cascade é definido como CascadeType.ALL, o que indica que todas as alterações feitas na entidade Customer devem ser propagadas também para as entidades Order. O parâmetro orphanRemoval é definido como true, o que significa que quaisquer objetos Order que não sejam mais referenciados por um objeto Customer serão automaticamente excluídos. O parâmetro fetch é definido como FetchType.LAZY, o que significa que o objeto Customer será carregado de forma preguiçosa quando for acessado pela primeira vez.

## **@OneToOne**
A anotação ``@OneToOne`` é usada em Java para definir um relacionamento um-para-um entre duas entidades. Geralmente é usada quando uma entidade tem uma referência a outra entidade e essa relação é um-para-um.

A anotação ``@OneToOne`` aceita vários parâmetros:

- ``targetEntity``: Especifica a classe da entidade de destino. Isso só é necessário se a entidade de destino não for especificada usando genéricos.
- ``cascade``: Especifica as operações de cascata a serem aplicadas à entidade de destino.
- ``fetch``: Especifica a estratégia de busca a ser usada para a entidade de destino.
- ``optional``: Especifica se a associação é opcional ou obrigatória. Por padrão, é opcional.
- ``mappedBy``: Especifica o campo na entidade de destino que mapeia de volta para a entidade de origem. Isso é usado em relacionamentos bidirecionais.
- ``orphanRemoval``: É usado para remover automaticamente entidades filhas quando elas não são mais referenciadas por sua entidade pai.

Aqui está um exemplo de como usar a anotação ``@OneToOne``:

```java
@Entity
@Table(name = "users")
public class User {
    @Id
    @GeneratedValue(strategy = GenerationType.IDENTITY)
    private Long id;

    @Column(name = "username")
    private String username;

    @Column(name = "password")
    private String password;

    @OneToOne(mappedBy = "user", cascade = CascadeType.ALL, orphanRemoval = true, fetch = FetchType.LAZY)
    private UserProfile userProfile;
    // outros campos e métodos omitidos por brevidade
}
```

```java
@Entity
@Table(name = "user_profiles")
public class UserProfile {
    @Id
    @GeneratedValue(strategy = GenerationType.IDENTITY)
    private Long id;

    @Column(name = "first_name")
    private String firstName;

    @Column(name = "last_name")
    private String lastName;

    @OneToOne(fetch = FetchType.LAZY)
    @JoinColumn(name = "user_id")
    private User user;
    // outros campos e métodos omitidos por brevidade
}
```

Neste exemplo, a classe User representa uma tabela em um banco de dados. A anotação ``@Entity`` é aplicada à classe para indicar que ela deve ser mapeada para uma tabela de banco de dados. A anotação ``@Table`` também é aplicada à classe com o parâmetro ``name`` definido como "users".

O campo userProfile é marcado com a anotação ``@OneToOne`` para indicar que representa uma referência a um objeto UserProfile, sendo que cada objeto User tem uma referência a um único objeto UserProfile. O parâmetro ``mappedBy`` é usado para especificar o campo na classe UserProfile que mapeia de volta para a classe User.

A classe UserProfile também representa uma tabela no banco de dados. Ela tem um campo user marcado com a anotação ``@OneToOne``, o que indica que cada objeto UserProfile tem uma referência a um único objeto User associado a ele. A anotação JoinColumn é usada para especificar o nome da coluna na tabela user_profiles que mapeia para a chave primária da tabela users.

O parâmetro cascade é definido como CascadeType.ALL, o que indica que todas as alterações feitas nas entidades User ou UserProfile devem ser propagadas também para a outra entidade. O parâmetro ``orphanRemoval`` é definido como true, o que significa que qualquer objeto UserProfile que não seja mais referenciado por um objeto User será automaticamente excluído. O parâmetro fetch é definido como FetchType.LAZY, o que significa que o objeto UserProfile será carregado de forma preguiçosa quando for acessado pela primeira vez.

## **@ManyToMany**

A anotação `@ManyToMany` é usada em Java para definir um relacionamento muitos-para-muitos entre duas entidades. Isso significa que uma entidade pode estar associada a várias instâncias de outra entidade e vice-versa.

A anotação `@ManyToMany` aceita vários parâmetros:

- `targetEntity`: Especifica a classe da entidade de destino. Isso só é necessário se a entidade de destino não for especificada usando genéricos.
- `mappedBy`: Especifica o nome do atributo na entidade de destino que mapeia para o relacionamento inverso.
- `cascade`: Especifica as operações de cascata a serem aplicadas à entidade de destino.
- `fetch`: Especifica a estratégia de busca a ser usada para a entidade de destino.

Aqui está um exemplo de como usar a anotação `@ManyToMany`:

```java
@Entity
@Table(name = "students")
public class Student {
    @Id
    @GeneratedValue(strategy = GenerationType.IDENTITY)
    private Long id;

    @Column(name = "name")
    private String name;

    @ManyToMany
    @JoinTable(
        name = "student_course",
        joinColumns = @JoinColumn(name = "student_id"),
        inverseJoinColumns = @JoinColumn(name = "course_id")
    )
    private Set<Course> courses = new HashSet<>();
    // outros campos e métodos omitidos por brevidade
}
```

```java
@Entity
@Table(name = "courses")
public class Course {
    @Id
    @GeneratedValue(strategy = GenerationType.IDENTITY)
    private Long id;

    @Column(name = "name")
    private String name;

    @ManyToMany(mappedBy = "courses")
    private Set<Student> students = new HashSet<>();
    // outros campos e métodos omitidos por brevidade
}
```

Neste exemplo, temos duas entidades: `Student` e `Course`. A anotação `@ManyToMany` é aplicada ao campo `courses` na classe `Student` e ao campo `students` na classe `Course`, indicando que existe uma relação muitos-para-muitos entre essas entidades.

A anotação `@JoinTable` é usada para definir a tabela de associação que armazena os relacionamentos entre `Student` e `Course`. O parâmetro `name` especifica o nome da tabela de associação, `joinColumns` especifica a coluna na tabela de associação que faz referência à chave primária de `Student`, e `inverseJoinColumns` especifica a coluna que faz referência à chave primária de `Course`.

Com essa configuração, é possível associar vários cursos a um estudante e vários estudantes a um curso, estabelecendo assim um relacionamento muitos-para-muitos entre essas entidades.

## **@Lob**

A anotação ``@Lob`` é usada em Java para mapear um campo ou propriedade para uma coluna de objeto grande (LOB) em um banco de dados. Geralmente é usada quando o tamanho dos dados a serem armazenados excede o tamanho máximo de um tipo de coluna padrão, como uma coluna VARCHAR ou TEXT.

A anotação ``@Lob`` não possui parâmetros, mas pode ser usada em conjunto com outras anotações para especificar propriedades adicionais, como o nome e o tipo da coluna.

Aqui está um exemplo de como usar a anotação ``@Lob``:

```java
@Entity
@Table(name = "products")
public class Product {
    @Id
    @GeneratedValue(strategy = GenerationType.IDENTITY)
    private Long id;
     
    @Column(name = "name")
    private String name;

    @Column(name = "description")
    @Lob
    private String description;
    // outros campos e métodos omitidos por brevidade
}
```

Neste exemplo, a classe Product representa uma tabela em um banco de dados. A anotação ``@Entity`` é aplicada à classe para indicar que ela deve ser mapeada para uma tabela de banco de dados. A anotação ``@Table`` também é aplicada à classe com o parâmetro ``name`` definido como "products".

O campo description é marcado com a anotação ``@Lob`` para indicar que representa uma coluna de objeto grande no banco de dados. A anotação ``@Column`` também é aplicada ao campo com o parâmetro ``name`` definido como "description". Por padrão, o tipo de coluna para um campo anotado com ``@Lob`` é BLOB para dados binários ou CLOB para dados de caractere, dependendo do tipo Java do campo. No entanto, isso pode ser substituído usando o parâmetro ``columnDefinition`` da anotação ``@Column``.

Neste exemplo, o campo description é do tipo String, então o tipo de coluna padrão CLOB é usado. Se o campo description fosse do tipo byte[], o tipo de coluna padrão BLOB seria usado em vez disso.

Observe que nem todos os bancos de dados suportam colunas LOB, então o comportamento da anotação ``@Lob`` pode variar dependendo do banco de dados usado. Além disso, colunas LOB podem ter tamanhos máximos diferentes dependendo do banco de dados e do tipo de coluna sendo usado.

## **@JoinColumn**

A anotação `@JoinColumn` no JPA é usada para definir a coluna que deve ser utilizada como chave estrangeira para mapear um relacionamento entre duas entidades. Geralmente é utilizada em conjunto com as anotações `@ManyToOne`, `@OneToMany` e `@OneToOne` para especificar a coluna que deve ser usada como chave estrangeira para o relacionamento.

A anotação `@JoinColumn` fornece diversos parâmetros que podem ser utilizados para personalizar o comportamento do mapeamento:

- `name`: Especifica o nome da coluna de chave estrangeira na tabela que mantém o relacionamento. Se este parâmetro não for especificado, o JPA utilizará o nome da coluna de chave primária da entidade referenciada.
- `referencedColumnName`: Especifica o nome da coluna de chave primária na entidade referenciada. Se este parâmetro não for especificado, o JPA utilizará o nome da coluna de chave primária da entidade referenciada.
- `nullable`: Especifica se a coluna de chave estrangeira pode conter valores nulos. Se este parâmetro for definido como `true`, a coluna de chave estrangeira pode conter valores nulos. Se for definido como `false`, a coluna de chave estrangeira não pode conter valores nulos.
- `unique`: Especifica se a coluna de chave estrangeira deve ser única. Se este parâmetro for definido como `true`, a coluna de chave estrangeira deve ser única. Se for definido como `false`, a coluna de chave estrangeira não precisa ser única.
- `insertable`: Especifica se a coluna de chave estrangeira deve ser incluída em instruções SQL INSERT geradas pelo JPA. Se este parâmetro for definido como `true`, a coluna de chave estrangeira será incluída em instruções INSERT. Se for definido como `false`, a coluna de chave estrangeira não será incluída em instruções INSERT.
- `updatable`: Especifica se a coluna de chave estrangeira deve ser incluída em instruções SQL UPDATE geradas pelo JPA. Se este parâmetro for definido como `true`, a coluna de chave estrangeira será incluída em instruções UPDATE. Se for definido como `false`, a coluna de chave estrangeira não será incluída em instruções UPDATE.

```java
@Entity
@Table(name = "employees")
public class Employee {
    @Id
    @GeneratedValue(strategy = GenerationType.IDENTITY)
    private Long id;

    @ManyToOne
    @JoinColumn(name = "department_id", nullable = false)
    private Department department;
    // outros campos e métodos omitidos por brevidade
}
```

```java
@Entity
@Table(name = "departments")
public class Department {
    @Id
    @GeneratedValue(strategy = GenerationType.IDENTITY)
    private Long id;
    @OneToMany(mappedBy = "department")
    private List<Employee> employees;
    // outros campos e métodos omitidos por brevidade
}
```

Neste exemplo, as classes `Employee` e `Department` representam tabelas em um banco de dados. A classe `Employee` possui um relacionamento muitos para um com a classe `Department`, que é representado pelo campo `department`. A anotação `@ManyToOne` é aplicada ao campo para indicar o relacionamento.

A anotação `@JoinColumn` também é aplicada ao campo `department` com o parâmetro `name` definido como "department_id", que especifica o nome da coluna de chave estrangeira na tabela `employees`. O parâmetro `nullable` é definido como `false`, o que especifica que a coluna de chave estrangeira não deve permitir valores nulos.

A classe `Department` também possui um relacionamento um para muitos com a classe `Employee`, que é representado pelo campo `employees`. A anotação `@OneToMany` é aplicada ao campo com o parâmetro `mappedBy` definido como "department", que especifica que o relacionamento é mapeado pelo campo `department` na classe `Employee`.

## **srping.jpa.hibernate.dll-auto**

A propriedade `spring.jpa.hibernate.ddl-auto` é usada para controlar o comportamento de criação e atualização de tabelas pelo Hibernate em um ambiente Spring Boot. Aqui estão as opções disponíveis para essa propriedade:

`validate`: A opção validate faz com que o Hibernate valide o esquema do banco de dados, mas não faça nenhuma alteração nele. Isso significa que o Hibernate não criará, alterará ou excluirá tabelas.

`update`: A opção update faz com que o Hibernate atualize o esquema do banco de dados conforme necessário para se adequar às entidades mapeadas. Isso significa que o Hibernate criará novas tabelas, colunas e restrições conforme necessário, mas **não excluirá ou modificará** as tabelas existentes.

`create`: A opção create faz com que o Hibernate crie o esquema do banco de dados do zero a partir das entidades mapeadas. Isso significa que o Hibernate criará todas as tabelas, colunas e restrições necessárias, **descartando qualquer esquema existente no banco de dados.**

`create-drop`: A opção create-drop faz com que o Hibernate **crie o esquema do banco de dados ao iniciar a aplicação e o descarte ao encerrar a aplicação.** Isso é útil principalmente para **ambientes de desenvolvimento e testes**, onde você deseja que o banco de dados seja recriado a cada reinicialização da aplicação.

`none`: A opção none desabilita completamente a funcionalidade de criação e atualização automática do esquema do banco de dados pelo Hibernate. Isso significa que o Hibernate não fará nenhuma alteração no esquema do banco de dados, e cabe ao desenvolvedor garantir que o esquema do banco de dados esteja em sincronia com as entidades mapeadas.

## **spring.datasource.url**
Para configurar a URL do banco de dados em uma aplicação Spring Boot, você pode definir a propriedade `spring.datasource.url` no arquivo `application.properties`.

Aqui está um exemplo de como configurar a URL do banco de dados em `application.properties`:

```properties
spring.datasource.url=jdbc:mysql://localhost:3306/meu_banco_de_dados
```

Neste exemplo:

- `jdbc:mysql://` é o prefixo que indica que você está usando o driver JDBC do MySQL.
- `localhost:3306` é o endereço do servidor de banco de dados MySQL e o número da porta.
- `meu_banco_de_dados` é o nome do banco de dados ao qual você deseja se conectar.

Exemplo utilizado no projeto

```
#Update the database schema based on the entities create-drop / update
spring.jpa.hibernate.ddl-auto=create-drop
#create database if not exists mysql true spring boot
spring.datasource.url=jdbc:mysql://localhost:3306/SPRING_JPA?createDatabaseIfNotExist=true
#DB User
spring.datasource.username=root
#DB password
spring.datasource.password=laboratorio

```

Além disso, certifique-se de que você tenha a dependência correta para o driver JDBC MySQL no seu arquivo `pom.xml` (se estiver usando Maven) ou `build.gradle` (se estiver usando Gradle), para que o Spring Boot possa se conectar ao banco de dados MySQL. Por exemplo, para Maven:

```xml
<dependency>
    <groupId>mysql</groupId>
    <artifactId>mysql-connector-java</artifactId>
    <version>8.0.28</version> <!-- versão pode variar -->
</dependency>
```

Com essa configuração, o Spring Boot usará a URL do banco de dados fornecida para se conectar ao seu banco de dados MySQL quando a aplicação for inicializada.

## Prática 1

Desenvolver a estrutura de sistema de gerenciamento empresarial completo utilizando Spring Boot com JPA. Neste desafio, você terá a oportunidade de aplicar seus conhecimentos em uma situação realista, criando um sistema capaz de gerenciar funcionários, projetos, departamentos e supervisores para uma empresa.

### Contexto da Empresa:

Imagine que você está colaborando com uma empresa de médio porte que busca otimizar seus processos internos através da tecnologia. Eles desejam uma solução moderna e eficiente para gerenciar seus recursos humanos e projetos de forma integrada.

Utilizando o Spring Boot com JPA, sua tarefa é projetar e implementar um sistema robusto que atenda às necessidades da empresa. Você deve utilizar a estrutura de dados fornecida pela empresa e representada nas imagens abaixo.

<div align="center">
    
![MER Conceitual](https://github.com/Herysson/Projeto-de-Banco-de-Dados/blob/main/EMPRESA%20(MER%20-%20Conceitual).png)

![Modelo Físico](https://github.com/Herysson/Projeto-de-Banco-de-Dados/blob/main/EMPRESA%20(Modelo%20F%C3%ADsico).png)

</div>

### Resultado

<div align="center">
    
![image](https://github.com/user-attachments/assets/1c46672e-48d8-406e-a432-1aa1162c2619)


</div>



## Practice 2

Introduction:
Our goal is to develop a robust product selling system tailored for bars, burger joints, and restaurants. This system will enable customers to conveniently browse, select, and purchase food and beverages. Leveraging Java Spring Boot for the backend and React for the frontend, we aim to create a seamless and user-friendly experience for both customers and business owners.

In the product selling system designed for bars, burger joints, and restaurants, several key entities play crucial roles in facilitating its functionality. Here are the main entities:

Product:
Represents the items available for purchase, such as food items (e.g., burgers, pizzas, salads) and beverages (e.g., soft drinks, alcoholic drinks).
Contains attributes like name, description, price, category, availability status, and possibly images.

Customer:
Represents individuals who interact with the system to browse, select, and purchase products.
Contains information such as name, contact details, delivery address, payment preferences, and order history.
May have an associated authentication credential for secure access to their account.

Order:
Represents a single transaction initiated by a customer to purchase one or more products.
Contains details such as the list of products ordered, quantities, total amount, delivery/pickup instructions, and status (e.g., pending, in progress, completed).
May include timestamps for order placement and fulfillment.

User (Business Owner/Admin):
Represents individuals responsible for managing the system, including adding/removing products, monitoring orders, and analyzing sales data.
Contains information like username, password, role (admin or staff), and possibly contact details.

Shopping Cart:
Represents a temporary storage mechanism where customers can add products before proceeding to checkout.
Contains information about the selected products, quantities, and subtotal amount.
Associated with a specific customer session or account to maintain persistence across browsing sessions.

Payment:
Represents the financial transaction associated with an order.
Contains details such as payment method (credit card, debit card, cash), transaction amount, payment status, and transaction ID.
May include integration with external payment gateways for secure processing.
    
### Backend Development with Java Spring Boot:
Utilizing Java Spring Boot framework for building a scalable and robust backend infrastructure.
Integrating with databases such as MySQL or PostgreSQL to store and retrieve data efficiently.

### **Referências:**

Spring [Spring Data JPA](https://docs.spring.io/spring-data/jpa/reference/jpa.html)

Oracle [Oracle JPA - Documentation](https://docs.oracle.com/javaee/6/tutorial/doc/bnbpz.html)

Jakarta [Jakarta Persistence](https://en.wikipedia.org/wiki/Jakarta_Persistence)

Aqeel Abbas [Hibernate/JPA commonly used Annotations](https://medium.com/@aqeelabbas3972/hibernate-jpa-commonly-used-annotations-3771dc0e0e)

Baeldung [Introduction to Spring Data JPA](https://www.baeldung.com/the-persistence-layer-with-spring-data-jpa)

Zehra Gökçe Aynacı [Spring JPA Annotations](https://medium.com/@zehragokce/spring-jpa-annotations-863574d13121)



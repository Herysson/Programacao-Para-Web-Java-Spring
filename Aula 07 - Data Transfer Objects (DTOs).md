# Data Transfer Objects (DTOs) 

Uma classe DTO (Data Transfer Object) é um padrão de design utilizado para transferir dados entre subsistemas de um software. O conceito principal por trás dos DTOs é encapsular os dados em objetos simples, reduzindo o número de chamadas de método (especialmente em interfaces de rede) e centralizando a transferência de dados em uma estrutura compacta e otimizada.

![1 _8sx2kgavp5H_3K-M7qeEA](https://github.com/Herysson/Programacao-Para-Web-Java-Spring/assets/7634437/7c4e643a-d24b-449c-92dc-405460474b27)

## Características Principais de um DTO:

1. **Simplicidade**: DTOs geralmente contêm apenas dados e nenhum comportamento (métodos além de getters e setters).
2. **Encapsulamento**: Eles servem para agrupar múltiplos elementos de dados em uma única estrutura, facilitando o transporte desses dados como uma unidade.
3. **Desacoplamento**: Permitem que os dados sejam transmitidos sem expor detalhes das classes de negócio.
4. **Customização para a vista**: Podem ser moldados para atender exatamente os requisitos de dados de interfaces específicas ou APIs, diferindo assim dos modelos de domínio que podem conter mais dados do que necessário para certas operações.
**CustomerDTO.java**

```java
package com.example.MenuStream.dto;

public class CustomerDTO {
    private Long id;
    private String name;
    private String email;
    private String deliveryAddress;  // Assume que queremos isso na API

    // Getters e Setters
}
```

DTOs são usados para aumentar a eficiência da comunicação, reduzindo o número de chamadas necessárias entre processos, além de simplificar as estruturas de dados transmitidas.

## O que é uma classe Record?

Em Java, **Record** é um tipo especial de classe introduzido a partir do Java 14, destinado a simplificar a modelagem de dados imutáveis. Records são uma forma concisa de criar classes que são apenas portadoras de dados — similar aos DTOs, mas com características específicas que os diferenciam.

### Características Principais de um Record:

1. **Imutabilidade**: Uma vez criado, os dados de um record não podem ser alterados.
2. **Sintaxe Concisa**: A declaração de um record é mais concisa comparada à de uma classe tradicional. O compilador automaticamente gera getters, métodos `equals()`, `hashCode()`, e `toString()`.
3. **Semântica de Dados**: Records são destinados a representar dados puros e simples, sem a necessidade de encapsular comportamento complexo.

Exemplo de uma declaração de record em Java:
```java
public record CustomerRecord(String name, String email, String address) {}
```
Este record define uma classe imutável com três campos: `name`, `email`, e `address`. Java cria automaticamente os métodos getters (que têm o mesmo nome dos campos), além dos métodos `equals()`, `hashCode()`, e `toString()`.

### Conceito dessas Classes

Tanto DTOs quanto records são utilizados para lidar com dados de maneiras que favorecem a simplicidade e a eficiência na transferência de dados. Enquanto DTOs são usados para desacoplar a camada de apresentação das regras de negócio e simplificar o transporte de dados entre camadas ou sistemas, records são usados para fornecer uma maneira compacta e imutável de representar uma entidade de dados com garantias adicionais fornecidas pela linguagem Java.

Ambas as abordagens servem para diferentes propósitos em diferentes contextos, mas ambas buscam melhorar a clareza, manutenção e eficiência do código ao lidar com estruturas de dados em uma aplicação.

## Exemplo utilizando ModelMapper

O uso do ModelMapper é uma alternativa para automatizar o processo de transferência de dados entre objetos, o que é muito útil quando você tem muitos campos ou deseja um código mais limpo e fácil de manter. Como sua classe `Customer` já usa a anotação `@Data` do Lombok, ela automaticamente inclui os getters e setters necessários para cada campo, o que facilita a integração com o ModelMapper.

### Passo a Passo para Utilizar o ModelMapper

1. **Adicionar a Dependência do ModelMapper:**
   Primeiro, você precisa adicionar a dependência do ModelMapper ao seu projeto. Se você está usando Maven, adicione o seguinte ao seu arquivo `pom.xml`:

   ```xml
   <dependency>
       <groupId>org.modelmapper</groupId>
       <artifactId>modelmapper</artifactId>
       <version>2.4.4</version>
   </dependency>
   ```

2. **Usar o ModelMapper para Mapear os Dados:**
   Agora você pode usar o ModelMapper para mapear dados do `CustomerDTO` para o `Customer`. Você pode fazer isso diretamente no seu método `createCustomer`:

**CustomerController.java**
   ```java
   @PostMapping
   public ResponseEntity<Customer> createCustomer(@RequestBody CustomerDTO customerDTO) {
       ModelMapper modelMapper = new ModelMapper();
       Customer customer = modelMapper.map(customerDTO, Customer.class);
       return ResponseEntity.ok(customerService.saveCustomer(customer));
   }
   ```

### Vantagens do ModelMapper

- **Automatização:** Reduz a necessidade de escrever código boilerplate para mapear objetos manualmente.
- **Flexibilidade:** Facilmente configurável para mapeamentos mais complexos.
- **Redução de Erros:** Minimiza o risco de erros humanos em mapeamentos manuais.

Usar o ModelMapper pode realmente simplificar seu código quando você tem muitos campos para transferir ou quando as transformações entre os tipos de dados são não-triviais. Ele também ajuda a manter seu código limpo e fácil de entender.


**CustomerController.java**

```java

    @PostMapping
    public ResponseEntity<Customer> createCustomer(@RequestBody CustomerDTO customerDTO) {
        ModelMapper modelMapper = new ModelMapper();
        Customer customer = modelMapper.map(customerDTO, Customer.class);
        return ResponseEntity.ok(customerService.saveCustomer(customer));
    }

// Similar para outros métodos
```

### Anotações e Declaração do Método

```java
@PostMapping
public ResponseEntity<CustomerDTO> createCustomer(@RequestBody CustomerDTO customerDTO) {
    ...
}
```

- **@PostMapping**: Esta anotação é uma especialização da anotação `@RequestMapping`. Ela indica que este método deve ser invocado quando uma requisição HTTP POST for recebida no caminho especificado na anotação `@RequestMapping` na classe controladora. Como não há um caminho especificado na anotação `@PostMapping`, ele usará o caminho base definido na classe controladora (`/customers`).

- **ResponseEntity<CustomerDTO>**: O tipo de retorno `ResponseEntity<CustomerDTO>` é usado para fornecer uma resposta HTTP completa, incluindo o status, cabeçalhos e o corpo da resposta. Neste caso, o corpo da resposta será um objeto `CustomerDTO`.

- **createCustomer(@RequestBody CustomerDTO customerDTO)**: O método `createCustomer` é projetado para criar um novo cliente. Ele recebe um parâmetro `customerDTO` que é um objeto `CustomerDTO`, o qual contém os dados necessários para criar um novo cliente.

  - **@RequestBody**: A anotação `@RequestBody` informa ao Spring que o parâmetro `customerDTO` deve ser vinculado ao corpo da requisição HTTP. O Spring automaticamente converte o JSON do corpo da requisição para o objeto Java `CustomerDTO` usando Jackson ou outra biblioteca de serialização configurada.

### Corpo do Método

```java
ModelMapper modelMapper = new ModelMapper();
Customer customer = modelMapper.map(customerDTO, Customer.class);
return ResponseEntity.ok(customerService.saveCustomer(customer));
```

- **Model Mapping**: A linha `Customer customer = modelMapper.map(customerDTO, Customer.class);` utiliza uma instância de `ModelMapper` para converter o `CustomerDTO` (objeto de transferência de dados) em uma entidade `Customer`. Esta entidade `Customer` é a que será persistida no banco de dados.

- **Resposta HTTP**: Finalmente, `return ResponseEntity.ok(savedDto);` constrói uma resposta HTTP com o status 200 OK, contendo o `CustomerDTO` que reflete o cliente recém-criado. Este objeto `CustomerDTO` inclui todos os dados relevantes do cliente, incluindo qualquer identificador único atribuído durante o processo de salvamento.

Este método é um exemplo de como manipular dados de entrada e saída em APIs RESTful utilizando DTOs para desacoplar a representação dos dados das entidades de domínio. Além disso, ele demonstra boas práticas de programação, incluindo a separação de preocupações e o uso de injeção de dependência para a manipulação de lógicas de negócios fora dos controladores.

## Exemplo

Abaixo, fiz algumas melhorias e adicionei a utilização de uma classe DTO para separar a camada de apresentação da camada de domínio na sua aplicação Spring Boot. Vamos criar um `CustomerDTO` para usar na comunicação da API, e adaptar a classe `CustomerController` e `CustomerService` para trabalhar com esse novo DTO:

### CustomerDTO.java
Primeiro, criaremos um novo DTO para o `Customer`:

```java
public class CustomerDTO {
    private Long id;
    private String name;
    private String email;
    private String deliveryAddress;

    // Getters e setters
    // Você pode adicionar construtores se necessário
}
```

### CustomerController.java
Agora, vamos adaptar o `CustomerController` para usar o `CustomerDTO`:

```java
@RestController
@RequestMapping("/customers")
public class CustomerController {

    @Autowired
    private CustomerService customerService;

    @Autowired
    private ModelMapper modelMapper;

    @PostMapping
    public ResponseEntity<CustomerDTO> createCustomer(@RequestBody CustomerDTO customerDTO) {
        Customer customer = modelMapper.map(customerDTO, Customer.class);
        Customer savedCustomer = customerService.saveCustomer(customer);
        CustomerDTO savedDto = modelMapper.map(savedCustomer, CustomerDTO.class);
        return ResponseEntity.ok(savedDto);
    }

    @GetMapping("/{id}")
    public ResponseEntity<CustomerDTO> getCustomerById(@PathVariable Long id) {
        Customer customer = customerService.getCustomerById(id);
        CustomerDTO customerDTO = modelMapper.map(customer, CustomerDTO.class);
        return ResponseEntity.ok(customerDTO);
    }

    @GetMapping
    public ResponseEntity<List<CustomerDTO>> getAllCustomers() {
        List<Customer> customers = customerService.getAllCustomers();
        List<CustomerDTO> customerDTOs = customers.stream()
            .map(customer -> modelMapper.map(customer, CustomerDTO.class))
            .collect(Collectors.toList());
        return ResponseEntity.ok(customerDTOs);
    }

    @PutMapping("/{id}")
    public ResponseEntity<CustomerDTO> updateCustomer(@PathVariable Long id, @RequestBody CustomerDTO customerDTO) {
        Customer updatedCustomer = customerService.updateCustomer(id, modelMapper.map(customerDTO, Customer.class));
        CustomerDTO updatedDto = modelMapper.map(updatedCustomer, CustomerDTO.class);
        return ResponseEntity.ok(updatedDto);
    }

    @DeleteMapping("/{id}")
    public ResponseEntity<Void> deleteCustomer(@PathVariable Long id) {
        customerService.deleteCustomer(id);
        return ResponseEntity.ok().build();
    }
}
```

### CustomerService.java
Agora, adaptamos `CustomerService` para trabalhar diretamente com a entidade `Customer`, sem grandes mudanças, já que a transformação DTO <-> Entidade está acontecendo no controlador:

```java
@Service
public class CustomerService {

    @Autowired
    private CustomerRepository customerRepository;

    public Customer saveCustomer(Customer customer) {
        return customerRepository.save(customer);
    }

    public Customer getCustomerById(Long id) {
        return customerRepository.findById(id).orElseThrow(() -> new RuntimeException("Customer not found"));
    }

    public List<Customer> getAllCustomers() {
        return customerRepository.findAll();
    }

    public Customer updateCustomer(Long id, Customer customerDetails) {
        Customer customer = getCustomerById(id);
        customer.setName(customerDetails.getName());
        customer.setEmail(customerDetails.getEmail());
        customer.setDeliveryAddress(customerDetails.getDeliveryAddress());
        return customerRepository.save(customer);
    }

    public void deleteCustomer(Long id) {
        customerRepository.deleteById(id);
    }
}
```



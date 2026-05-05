# Unidade: Consulta por Derivação de Nome de Método

Considere a entidade `User` com:

* id
* name
* email
* age
* active

## Exercícios

1. Implemente métodos no repositório para atender os seguintes requisitos:

   * Buscar usuários pelo nome exato
   * Buscar usuários por email
   * Buscar usuários ativos (true)

2. Crie métodos para consultas parciais:

   * Buscar usuários cujo nome contenha uma string
   * Buscar usuários cujo nome comece com um prefixo
   * Buscar usuários cujo nome termine com um sufixo

3. Implemente consultas combinadas:

   * Buscar usuários por nome e email
   * Buscar usuários por nome ou email
   * Buscar usuários ativos com idade maior que um valor

4. Trabalhe com intervalos:

   * Buscar usuários com idade entre dois valores
   * Buscar usuários com idade maior ou igual a X
   * Buscar usuários com idade menor que X

5. Ordenação:

   * Buscar usuários por email ordenando por nome ascendente
   * Buscar usuários ativos ordenando por idade decrescente

6. Negação e listas:

   * Buscar usuários cujo email seja diferente de um valor
   * Buscar usuários com idade dentro de uma lista de idades (IN)
   * Buscar usuários com idade fora de uma lista (NOT IN)

7. Case insensitive:

   * Buscar usuários por nome ignorando maiúsculas/minúsculas

8. Contagem e existência:

   * Criar um método que conte usuários ativos
   * Criar um método que verifique se existe usuário com determinado email

9. Exercício de análise:

   * Dado o método `findByNameContainingAndAgeGreaterThanAndActiveTrue`, explique qual consulta será gerada

10. Exercício de refatoração:

* Dado um método muito longo com vários critérios, proponha uma alternativa usando @Query

---

# Unidade: Consulta por Anotação (@Query)

Considere `User` com relacionamento `phones`.

## Exercícios

1. Crie uma consulta JPQL com @Query que:

   * Retorne todos os usuários
   * Retorne usuários por nome (parâmetro nomeado)

2. Crie consultas com filtros:

   * Buscar usuários com idade maior que um valor
   * Buscar usuários ativos com determinado domínio de email (ex: “@gmail.com”)

3. Trabalhe com LIKE corretamente:

   * Buscar usuários cujo nome termine com determinado texto
   * Buscar usuários cujo nome contenha determinado texto

4. JOIN FETCH:

   * Crie uma consulta que carregue usuários junto com seus telefones
   * Explique o problema que essa abordagem resolve

5. Consultas com múltiplos critérios:

   * Buscar usuários ativos com idade entre dois valores e nome contendo uma string

6. Projeção:

   * Crie uma consulta que retorne apenas nome e email (Object[] ou DTO)

7. Consulta nativa:

   * Reescreva uma consulta JPQL como SQL nativo
   * Buscar usuário por email usando nativeQuery

8. Comparação:

   * Para uma mesma consulta, implemente:

     * método derivado
     * JPQL com @Query
     * SQL nativo
   * Compare legibilidade e flexibilidade

9. Erro proposital:

   * Dada uma consulta com LIKE mal construída (sem %), corrija
   * Explique o impacto no resultado

10. Desempenho:

* Explique quando usar @Query ao invés de derivação de método
* Cite um cenário onde JOIN FETCH é obrigatório

---

# Unidade: Consulta Nomeada (@NamedQuery)

## Exercícios

1. Crie uma @NamedQuery na entidade `User` para:

   * Buscar usuário por email

2. Utilize essa NamedQuery no repositório:

   * Criar método correspondente
   * Testar execução

3. Crie uma NamedQuery com múltiplos critérios:

   * Buscar usuários ativos com idade maior que um valor

4. Parâmetros nomeados:

   * Crie uma NamedQuery usando dois parâmetros (nome e idade)
   * Execute passando ambos

5. Comparação com derivação:

   * Compare a NamedQuery de busca por email com o método `findByEmail`
   * Quando faz sentido usar cada um?

6. Validação em tempo de inicialização:

   * Crie uma NamedQuery com erro proposital
   * Observe o comportamento da aplicação ao iniciar
   * Explique a vantagem disso

7. Organização:

   * Proponha um padrão para nomear NamedQueries no projeto

8. Refatoração:

   * Pegue uma consulta complexa com @Query e transforme em NamedQuery

9. XML NamedQuery:

   * Crie uma NamedQuery no `orm.xml`
   * Configure no `persistence.xml`
   * Execute no repositório

10. Análise crítica:

* Liste vantagens e desvantagens de:

  * Derivação de método
  * @Query
  * @NamedQuery

---


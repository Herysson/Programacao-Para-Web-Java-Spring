# **HTML**  


## **Seção 1:Introdução ao HTML**  

### **O que é HTML?**  
HTML (*HyperText Markup Language*) é a linguagem padrão para criar páginas da web. Ele define a estrutura e o conteúdo de uma página usando **elementos** (tags) que informam ao navegador como exibir textos, imagens, links e outros componentes.  

### **Como o HTML Funciona?**  
- O HTML consiste em uma série de **tags** (etiquetas) que envolvem o conteúdo.  
- O navegador lê o HTML e renderiza a página conforme as instruções das tags.  
- Páginas HTML são salvas com a extensão **.html**.  

Exemplo básico:  
```html
<!DOCTYPE html>
<html>
<head>
    <title>Título da Página</title>
</head>
<body>
    <h1>Meu Primeiro Cabeçalho</h1>
    <p>Meu primeiro parágrafo.</p>
</body>
</html>
```
 

### **Estrutura Básica de um Documento HTML**  
Todo documento HTML possui uma estrutura fundamental:  

1. **`<!DOCTYPE html>`**  
   - Declara o tipo de documento (HTML5).  

2. **`<html>`**  
   - Elemento raiz que engloba todo o conteúdo da página.  

3. **`<head>`**  
   - Contém metadados, como título da página (`<title>`), links para CSS e scripts.  

4. **`<body>`**  
   - Contém o conteúdo visível da página (textos, imagens, links, etc.).  
 

### **Tags HTML Básicas**  
Algumas das principais tags incluem:  

| Tag                      | Descrição                            | Exemplo                                 |
|--------------------------|----------------------------------------|------------------------------------------|
| `<h1>` - `<h6>`          | Cabeçalhos (títulos)                  | `<h1>Título Principal</h1>`              |
| `<p>`                    | Parágrafo                             | `<p>Texto aqui.</p>`                     |
| `<br>`                   | Quebra de linha                       | `<p>Bairro Jardim<br>São Paulo/SP</p>`   |
| `<a>`                    | Link                                  | `<a href="url">Link</a>`                 |
| `<img>`                  | Imagem                                | `<img src="imagem.jpg">`                 |
| `<ul>`, `<ol>`, `<li>`   | Listas (não ordenadas/ordenadas)      | `<ul><li>Item 1</li></ul>`               |
| `<div>`                  | Divisão/container genérico            | `<div>Conteúdo</div>`                    |

### **Atributos HTML**  
Atributos fornecem informações adicionais sobre elementos. Exemplos comuns:  

- **`href`** (em `<a>`) – Define o destino de um link.  
  ```html
  <a href="https://www.google.com">Visite o Google</a>
  ```
- **`src`** (em `<img>`) – Especifica o caminho da imagem.  
  ```html
  <img src="foto.jpg" alt="Descrição da imagem">
  ```
- **`alt`** – Texto alternativo para acessibilidade.  


### **Estrutura Básica de um Documento HTML**  
Todo arquivo HTML válido deve seguir este esqueleto:  
```html
<!DOCTYPE html>
<html lang="pt-BR">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Título da Página</title>
</head>
<body>
    <!-- Conteúdo visível vai aqui -->
</body>
</html>
```

#### **Explicação das Tags Essenciais:**
| Tag/Atributo               | Função                                                                 |
|----------------------------|------------------------------------------------------------------------|
| `<!DOCTYPE html>`          | Define o documento como HTML5.                                         |
| `<html lang="pt-BR">`      | Raiz do documento + idioma (português do Brasil).                      |
| `<meta charset="UTF-8">`   | Permite acentos, ç, emojis e caracteres especiais.                     |
| `<meta name="viewport"...` | Adapta a página para telas de celulares e tablets.                     |
| `<title>`                  | Define o título da aba/janela do navegador.                            |

 

### **Como os Navegadores Funcionam?**  
Os navegadores (*browsers* como Chrome, Firefox, Edge) **não exibem as tags HTML**, mas as usam para renderizar o conteúdo corretamente.  >

![image](https://github.com/user-attachments/assets/fdd5fe09-61e0-4318-956d-3af37771825a)
 

### **Estrutura da pagina HTML**  

Abaixo uma visualização da estrutura de uma pagina HTML.

![image](https://github.com/user-attachments/assets/ecc8f0b3-ca65-4a52-9459-6ad1162622b1)
  

### Atividade: 

Criar um mini currículo pessoal em HTML contendo:
- Foto
- Nome, profissão
- Pequena bio
- Lista de habilidades
- Link para redes sociais

## **Seção 2: Elementos HTML e Atributos**

### **O que é um Elemento HTML?**

Um **elemento HTML** é a unidade fundamental de um documento HTML. Ele é composto por uma **tag de abertura**, **conteúdo** e, na maioria dos casos, uma **tag de fechamento**:

```html
<p>Este é um parágrafo.</p>
```

Neste exemplo:

* `<p>` é a **tag de abertura**.
* `Este é um parágrafo.` é o **conteúdo**.
* `</p>` é a **tag de fechamento**.

Alguns elementos são **autofechados**, ou seja, não possuem conteúdo interno:

```html
<img src="foto.jpg" alt="Foto de perfil">
<br>
```
 

### **O que são Atributos HTML?**

Atributos HTML fornecem **informações adicionais** sobre os elementos. Eles são sempre especificados **dentro da tag de abertura** e seguem o formato:

```html
<tag atributo="valor">Conteúdo</tag>
```

### **Regras Gerais dos Atributos**

* Sempre aparecem na tag de abertura.
* São compostos por um **nome** e um **valor**.
* Os valores devem estar entre **aspas duplas** `" "`.
 

### **Principais Atributos HTML e Exemplos**

#### `href` (em `<a>`)

Especifica o destino de um link.

```html
<a href="https://www.google.com">Visite o Google</a>
```

#### `src` (em `<img>`)

O atributo `src` especifica o **caminho para o arquivo de imagem** que será exibido na página.

```html
<img src="foto.jpg" alt="Foto de perfil">
```

##### **Formas de especificar o valor de `src`:**

Existem duas formas principais de informar o caminho da imagem:
 

**1. URL Absoluta**

* Aponta para uma **imagem externa**, hospedada em outro site.
* Inclui o protocolo (https) e o nome do domínio.

```html
<img src="https://upload.wikimedia.org/wikipedia/commons/thumb/2/2f/Google_2015_logo.svg/1200px-Google_2015_logo.svg.png" alt="Imagem externa">
```

> ⚠️ **Atenção:**
>
> * Imagens externas podem estar protegidas por direitos autorais. Usá-las sem permissão pode violar leis de copyright.
> * Você **não tem controle** sobre imagens externas – elas podem ser removidas ou alteradas a qualquer momento, quebrando sua página.
 

**2. URL Relativa**

* Aponta para uma **imagem armazenada no próprio site** (no seu servidor).
* É o método mais recomendado.

**Exemplo 1: Caminho relativo ao arquivo atual (sem barra inicial)**

```html
<img src="img/foto.jpg" alt="Foto local">
```

**Exemplo 2: Caminho relativo à raiz do domínio (com barra inicial)**

```html
<img src="/imagens/foto.jpg" alt="Foto da pasta imagens">
```

> 💡 **Dica:**
> Prefira **URLs relativas**. Elas são mais seguras e **não quebram** caso o domínio do site seja alterado ou movido para outro servidor.
 

#### `width` e `height` (em `<img>`)

Definem a largura e altura de imagens (em pixels ou porcentagem).

```html
<img src="foto.jpg" width="300" height="200" alt="Paisagem">
```

#### `alt` (em `<img>`)

Texto alternativo, exibido quando a imagem não carrega. Também é importante para **acessibilidade**.

```html
<img src="grafico.png" alt="Gráfico de barras mostrando crescimento">
```

#### `style` (em qualquer elemento)

Permite adicionar **estilo CSS** direto na tag HTML.

```html
<p style="color:blue; font-size:18px;">Texto azul e maior</p>
```

#### `lang` (em `<html>`)

Declara o idioma principal da página. Essencial para SEO e acessibilidade.

```html
<html lang="pt-BR">
```

#### `title` (em qualquer elemento)

Mostra uma **dica flutuante** (tooltip) quando o mouse passa sobre o elemento.

```html
<p title="Este é um parágrafo explicativo.">Passe o mouse aqui</p>
```
 

### **Resumo: Atributos Comuns e Sua Utilização**

| Atributo       | Tag Comum | Finalidade                                          |
|----------------|------------|------------------------------------------------------|
| `href`         | `<a>`      | URL de destino de um link                           |
| `src`          | `<img>`    | Caminho para o arquivo de imagem                    |
| `alt`          | `<img>`    | Texto alternativo em caso de erro ou acessibilidade |
| `width/height` | `<img>`    | Dimensões da imagem                                 |
| `style`        | Todos      | Aplicar CSS inline                                  |
| `lang`         | `<html>`   | Define o idioma do documento                        |
| `title`        | Todos      | Exibe uma dica sobre o conteúdo                     |


### **Exemplo Integrado**

```html
<!DOCTYPE html>
<html lang="pt-BR">
<head>
  <meta charset="UTF-8">
  <title>Exemplo com Atributos</title>
</head>
<body>

  <h1 title="Título Principal">Bem-vindo!</h1>
  
  <p style="color:orange;" title="Texto de introdução">Este parágrafo está em verde.</p>

  <img src="logo.png" alt="Logotipo da empresa" width="150" height="150">

  <a href="https://www.exemplo.com" title="Clique para visitar">Acesse nosso site</a>

</body>
</html>
```

![image](https://github.com/user-attachments/assets/3e69415f-3f91-4c5e-bd69-e8e7c5473a0c)

### **Atividade Prática – Mini Currículo com Atributos**

Agora que você aprendeu sobre **elementos HTML** e seus **atributos mais comuns**, **refaça a atividade** criando uma página HTML com as seguintes informações:

#### **Requisitos do mini currículo:**

* Uma **foto pessoal ou ilustrativa** usando `<img>` com os atributos:

  * `src` (caminho da imagem),
  * `alt` (texto alternativo),
  * `width` (largura),
  * `title` (dica ao passar o mouse).
* **Nome completo** e **profissão** com uso de títulos (`<h1>`, `<h2>`).
* Uma **breve biografia** utilizando parágrafo (`<p>`), com atributo `title`.
* Uma **lista de habilidades** utilizando `<ul>` e `<li>`.
* Um ou mais **links para suas redes sociais** com `<a>` contendo `href` e `title`.

###  **Dicas Técnicas:**

* Utilize **URL relativa** para a imagem (por exemplo: `src="minhafoto.jpg"`).
* Adicione `lang="pt-BR"` no elemento `<html>` e `meta charset="UTF-8"` no `<head>`.
* O uso de `style` inline é opcional, mas pode ser usado para personalização simples.
 
## **Seção 3: Estilos (Styles) e Formatação (Formatting)**

### Estilos com HTML

O HTML permite modificar a aparência dos elementos usando o **atributo `style`**. Esse atributo aplica estilos diretamente a um elemento HTML utilizando propriedades da linguagem CSS.

#### Sintaxe do atributo `style`

```html
<tagname style="propriedade:valor;">
```

* A **propriedade** é uma propriedade do CSS (ex: `color`, `font-size`, `background-color`).
* O **valor** é o valor desejado para essa propriedade (ex: `blue`, `16px`, `center`).

Você aprenderá mais sobre CSS em seções futuras deste curso.

#### Exemplo: alterando a cor de fundo da página

```html
<body style="background-color:powderblue;">

  <h1>Este é um título</h1>
  <p>Este é um parágrafo.</p>

</body>
```

#### Exemplo: aplicando diferentes cores de fundo a elementos

```html
<body>

  <h1 style="background-color:powderblue;">Este é um título</h1>
  <p style="background-color:tomato;">Este é um parágrafo.</p>

</body>
```

### Principais propriedades de estilo

| Propriedade        | Efeito sobre o elemento                    | Exemplo de uso                     |
|--------------------|---------------------------------------------|------------------------------------|
| `color`            | Define a cor do texto                      | `style="color:red;"`               |
| `background-color` | Define a cor de fundo                      | `style="background-color:yellow;"` |
| `font-size`        | Define o tamanho da fonte                  | `style="font-size:20px;"`          |
| `font-family`      | Define o tipo de fonte                     | `style="font-family:Arial;"`       |
| `text-align`       | Alinha o texto (esquerda, centro, direita) | `style="text-align:center;"`       |


### Formatação de Texto no HTML

Além de aplicar estilos com o atributo `style`, o HTML possui **tags específicas para formatação de texto**, que alteram sua aparência ou enfatizam partes importantes do conteúdo.

#### Tags de formatação mais utilizadas

| Tag        | Descrição                                   | Exemplo                             |
|------------|---------------------------------------------|-------------------------------------|
| `<b>`      | Exibe o texto em **negrito**                | `<b>Texto em negrito</b>`           |
| `<strong>` | Aplica negrito com ênfase semântica         | `<strong>Texto importante</strong>` |
| `<i>`      | Exibe o texto em *itálico*                  | `<i>Texto em itálico</i>`           |
| `<em>`     | Aplica ênfase semântica com itálico         | `<em>Com ênfase</em>`               |
| `<mark>`   | Destaca o texto com um fundo amarelo padrão | `<mark>Texto destacado</mark>`      |
| `<small>`  | Reduz o tamanho da fonte                    | `<small>Texto pequeno</small>`      |
| `<del>`    | Riscado, indica remoção                     | `<del>Texto removido</del>`         |
| `<ins>`    | Sublinhado, indica inserção                 | `<ins>Texto inserido</ins>`         |
| `<sub>`    | Subscrito (abaixo da linha)                 | `H<sub>2</sub>O`                     |
| `<sup>`    | Sobrescrito (acima da linha)                | `2<sup>3</sup>`                     |


### Exemplo Integrado de Estilo e Formatação

```html
<p style="color:darkgreen; font-size:18px;">
  <strong>Bem-vindo</strong> ao <em>nosso site</em>. Este texto está <mark>formatado</mark> e com estilo aplicado.
</p>

<p>
  Fórmula da água: H<sub>2</sub>O<br>
  Potência de dois: 2<sup>3</sup> = 8
</p>
```

### Atividade

Reabra o exercício do mini currículo e:

1. Aplique pelo menos **três estilos diferentes** utilizando o atributo `style` (ex: cor, tamanho, alinhamento).
2. Utilize **três ou mais tags de formatação** de texto, como `<strong>`, `<em>`, `<mark>`, `<sub>` ou `<sup>`.
3. Mantenha a estrutura HTML válida e organizada.
 

## **Seção 4: Cores em HTML**

### Introdução

No HTML, cores podem ser aplicadas a qualquer elemento utilizando o atributo `style` com propriedades CSS como `color` (para texto) e `background-color` (para fundo).

### Formas de Definir Cores

Existem **quatro principais formas** de definir cores no HTML (via CSS):

1. **Nomes de cores (color names)**
2. **Códigos Hexadecimais (Hex)**
3. **Modelo RGB (Red, Green, Blue)**
4. **Modelo HSL (Hue, Saturation, Lightness)**
 

### 1. Usando Nomes de Cores

Você pode usar **nomes de cores pré-definidos**, como `red`, `blue`, `green`, `black`, `gray`, etc.

```html
<p style="color:blue;">Texto azul com nome de cor</p>
```

> Existem mais de 140 nomes de cores definidos oficialmente.
 

### 2. Usando Códigos Hexadecimais

Códigos hexadecimais começam com `#` seguido de seis caracteres.
Exemplo: `#RRGGBB`, onde:

* `RR` = quantidade de vermelho
* `GG` = quantidade de verde
* `BB` = quantidade de azul

```html
<p style="color:#ff0000;">Texto em vermelho (hexadecimal)</p>
```

* `#000000` → preto
* `#ffffff` → branco
* `#00ff00` → verde
* `#0000ff` → azul
 

### 3. Usando o Modelo RGB

O RGB define a cor com três valores numéricos de 0 a 255.

```html
<p style="color:rgb(255, 165, 0);">Texto laranja (RGB)</p>
```

* `rgb(255, 0, 0)` → vermelho
* `rgb(0, 255, 0)` → verde
* `rgb(0, 0, 255)` → azul
 

### 4. Usando o Modelo HSL

HSL significa Hue (matiz), Saturation (saturação) e Lightness (luminosidade).

```html
<p style="color:hsl(120, 100%, 25%);">Texto verde escuro (HSL)</p>
```

* Matiz (Hue): cor básica em graus (0°=vermelho, 120°=verde, 240°=azul)
* Saturação: intensidade da cor (0% a 100%)
* Luminosidade: brilho da cor (0% escuro, 100% claro)
 

### Comparando os Formatos

| Formato | Exemplo                    | Observações                            |
|---------|----------------------------|----------------------------------------|
| Nome    | `color: red`               | Fácil de lembrar, limitado a 140 cores |
| Hex     | `color: #ff0000`           | Muito usado em design gráfico          |
| RGB     | `color: rgb(255, 0, 0)`    | Boa legibilidade para ajustes finos    |
| HSL     | `color: hsl(0, 100%, 50%)` | Ideal para manipulação de paletas      |

 

### Tabela Visual de Cores

| Cor         | Nome        | Hexadecimal | RGB                | HSL                   |
|-------------|-------------|-------------|--------------------|------------------------|
| Vermelho    | `red`       | `#ff0000`   | `rgb(255,0,0)`     | `hsl(0, 100%, 50%)`    |
| Verde       | `green`     | `#008000`   | `rgb(0,128,0)`     | `hsl(120, 100%, 25%)`  |
| Azul        | `blue`      | `#0000ff`   | `rgb(0,0,255)`     | `hsl(240, 100%, 50%)`  |
| Dourado     | `gold`      | `#ffd700`   | `rgb(255,215,0)`   | `hsl(51, 100%, 50%)`   |
| Cinza Claro | `lightgray` | `#d3d3d3`   | `rgb(211,211,211)` | `hsl(0, 0%, 83%)`      |


![image](https://github.com/user-attachments/assets/5e3309f3-2fef-4bac-817f-c391704b884e)
 

### Exemplo Integrado

```html
<h3 style="color:red;">Nome de cor</h3>
<h3 style="color:#00ff00;">Hexadecimal</h3>
<h3 style="color:rgb(0,0,255);">RGB</h3>
<h3 style="color:hsl(60, 100%, 50%);">HSL</h3>
```
 

### Atividade

1. Crie uma página HTML com 4 parágrafos, cada um com uma cor diferente utilizando:

   * Um nome de cor
   * Um código hexadecimal
   * Um valor RGB
   * Um valor HSL

2. Aplique cores também no `background-color` de pelo menos um desses elementos.


## **Seção 5: Links e Imagens no HTML**

### Links no HTML

Links são criados com a tag `<a>`, permitindo a navegação entre páginas, arquivos, endereços externos ou e-mails.

#### Sintaxe básica:

```html
<a href="URL">Texto do link</a>
```

* `href`: define o endereço de destino do link.
* O texto entre as tags será clicável.

#### Exemplo de link externo:

```html
<a href="https://www.google.com">Visite o Google</a>
```

#### Exemplo de link interno (outra página do seu projeto):

```html
<a href="sobre.html">Sobre nós</a>
```

#### Abrindo link em nova aba:

Use o atributo `target="_blank"`:

```html
<a href="https://www.google.com" target="_blank">Abrir em nova aba</a>
```

#### Link para um e-mail:

Use o prefixo `mailto:` no `href` para abrir o programa de e-mail do usuário:

```html
<a href="mailto:aluno@exemplo.com">Enviar email</a>
```

 

### Usando Imagens

Imagens são adicionadas com a tag `<img>`, que é um elemento vazio.

#### Sintaxe básica:

```html
<img src="caminho.jpg" alt="Descrição da imagem">
```

* `src`: caminho da imagem (relativo ou URL).
* `alt`: texto alternativo para acessibilidade.
* `width` e `height`: ajustam tamanho da imagem.
* `title` (opcional): exibe um texto ao passar o mouse.

#### Exemplo com imagem local:

```html
<img src="perfil.jpg" alt="Foto de perfil" width="200">
```

#### Exemplo com imagem externa:

```html
<img src="https://www.google.com/images/branding/googlelogo/1x/googlelogo_color_272x92dp.png" alt="Logo do Google">
```

 

### Usando Imagem como Link

Você pode usar uma **imagem clicável** ao colocar a tag `<img>` dentro de uma `<a>`:

```html
<a href="https://www.google.com">
  <img src="https://www.google.com/images/branding/googlelogo/1x/googlelogo_color_272x92dp.png" alt="Google" style="width:100px;height:auto;">
</a>
```

 

### Botão como Link (com JavaScript)

Para usar um botão como link, utilize JavaScript com o evento `onclick`:

```html
<button onclick="document.location='https://www.google.com'">Ir para o Google</button>
```

> Este botão funciona como link, redirecionando para a página indicada ao ser clicado.

 

### Combinando Links e Imagens

Exemplo prático com imagem clicável:

```html
<a href="https://www.google.com">
  <img src="google.png" alt="Google" width="100">
</a>
```

### Dicas

* Use `target="_blank"` para abrir links externos em nova aba.
* Sempre forneça `alt` em imagens.
* Links de e-mail devem usar `mailto:`.
* Para criar botões que funcionam como links, utilize JavaScript.


### Atividade – Complementando o Mini Currículo com Links e Imagens

Adicione ao seu mini currículo pessoal os seguintes elementos:

1. **Uma imagem de perfil** com os atributos `src`, `alt`, `width` e `title`.
2. **Uma imagem clicável** que leve ao seu perfil profissional (ex: LinkedIn).
3. **Dois links para redes sociais**, sendo um deles com `target="_blank"`.
4. **Um link de e-mail** usando `mailto:`.
5. **Um botão que funcione como link**, redirecionando para seu portfólio ou para o Google.


## **Seção 6: Introdução ao CSS no HTML**

### O que é CSS?

CSS (**Cascading Style Sheets**, ou Folhas de Estilo em Cascata) é uma linguagem usada para **controlar o estilo e o layout** de elementos HTML em uma página web.

Com o CSS, você pode alterar:

* Cores
* Fontes
* Tamanhos
* Alinhamentos
* Bordas
* Espaçamentos
* Layouts responsivos e muito mais

 

### Formas de Aplicar CSS ao HTML

O CSS pode ser aplicado de **três maneiras diferentes**:

### 1. **CSS Inline**

Estilo aplicado diretamente dentro de uma tag HTML, usando o atributo `style`.

```html
<p style="color:blue;">Texto azul com CSS inline</p>
```

 

### 2. **CSS Interno (Internal Style Sheet)**

Estilo definido dentro do próprio arquivo HTML, entre as tags `<style>` no `<head>`.

```html
<!DOCTYPE html>
<html>
<head>
  <style>
    body {
      background-color: lightgray;
    }

    h1 {
      color: navy;
      font-family: Arial, sans-serif;
    }

    p {
      color: darkgreen;
    }
  </style>
</head>
<body>

  <h1>Exemplo com CSS Interno</h1>
  <p>Este parágrafo está estilizado via folha de estilo interna.</p>

</body>
</html>
```

 

### 3. **CSS Externo (External Style Sheet)**

Estilo definido em um **arquivo `.css` separado**, que é referenciado no HTML através da tag `<link>`.

**Arquivo externo: `estilos.css`**

```css
body {
  background-color: beige;
}

h1 {
  color: teal;
  text-align: center;
}

p {
  font-size: 16px;
  color: #333;
}
```

**Arquivo HTML:**

```html
<!DOCTYPE html>
<html>
<head>
  <link rel="stylesheet" href="estilos.css">
</head>
<body>

  <h1>Usando CSS Externo</h1>
  <p>Texto estilizado por um arquivo .css externo.</p>

</body>
</html>
```

 

### Vantagens do CSS Externo

* Permite **reutilizar estilos** em várias páginas.
* Melhora a **organização e manutenção** do código.
* Separa o conteúdo (HTML) da aparência (CSS).

 

### Prioridade (Cascata) no CSS

Se você usar os três tipos de CSS ao mesmo tempo, a prioridade será:

1. CSS Inline (mais forte)
2. CSS Interno (sobrescreve o externo, se for depois)
3. CSS Externo (menos prioridade)

 

### Propriedades CSS Comuns (Complemento)

#### Cores, Fontes e Tamanhos

Essas são propriedades muito utilizadas e você aprenderá mais sobre elas nas próximas seções:

* `color`: define a **cor do texto**
* `font-family`: define a **fonte** usada
* `font-size`: define o **tamanho do texto**

**Exemplo:**

```html
<!DOCTYPE html>
<html>
<head>
  <style>
    h1 {
      color: blue;
      font-family: Verdana;
      font-size: 300%;
    }
    p {
      color: red;
      font-family: Courier;
      font-size: 160%;
    }
  </style>
</head>
<body>

  <h1>Este é um título</h1>
  <p>Este é um parágrafo.</p>

</body>
</html>
```

 

#### Border (Borda)

A propriedade `border` define uma borda ao redor de quase qualquer elemento HTML.

```css
p {
  border: 2px solid powderblue;
}
```

 

#### Padding (Preenchimento Interno)

A propriedade `padding` define o espaço **entre o conteúdo e a borda** do elemento.

```css
p {
  border: 2px solid powderblue;
  padding: 30px;
}
```

 

#### Margin (Margem Externa)

A propriedade `margin` define o espaço **externo**, fora da borda do elemento.

```css
p {
  border: 2px solid powderblue;
  margin: 50px;
}
```

 

### Atividade – Estilizando o Mini Currículo com CSS

Atualize seu mini currículo HTML, adicionando os seguintes estilos:

1. Aplique **CSS interno** para:

   * Alterar a cor de fundo da página.
   * Estilizar o nome e profissão com `color`, `font-family` e `font-size`.
   * Adicionar `border`, `padding` e `margin` ao parágrafo da biografia.

2. Crie um **arquivo externo `curriculo.css`** e:

   * Estilize os links sociais (cor, espaçamento, estilo de texto).
   * Estilize os botões com cor de fundo, borda arredondada e cursor.

3. Use **CSS inline** em pelo menos um elemento para destacar um trecho do conteúdo (ex: `style="color:orange;"` em uma palavra na bio).


## **Seção 7: Tabelas no HTML**

As **tabelas** são usadas no HTML para exibir dados organizados em **linhas e colunas**. Elas são construídas com várias tags específicas.


### Estrutura Básica de uma Tabela

```html
<table>
  <tr>
    <td>Celula 1</td>
    <td>Celula 2</td>
  </tr>
</table>
```

| Tag       | Função                         |
|-----------|---------------------------------|
| `<table>` | Define a tabela                |
| `<tr>`    | Define uma linha (table row)   |
| `<td>`    | Define uma célula (table data) |
| `<th>`    | Define um cabeçalho de coluna  |


 

### Bordas em Tabelas (`border`)

Sem borda, as células ficam “invisíveis”. Para adicionar borda simples:

```html
<table border="1">
  <tr>
    <th>Nome</th>
    <th>Idade</th>
  </tr>
  <tr>
    <td>Ana</td>
    <td>22</td>
  </tr>
</table>
```

> Com CSS, é preferível usar:

```css
table, th, td {
  border: 1px solid black;
  border-collapse: collapse;
}
```

 

### Tamanhos da Tabela

Você pode definir a largura da tabela, colunas ou células com `width` e a altura com `height`.

```html
<table style="width:100%">
  <tr>
    <td style="height:50px;">Linha com altura</td>
  </tr>
</table>
```

 

### Cabeçalhos de Tabela

Use `<th>` para destacar as células de cabeçalho. Por padrão, elas ficam em **negrito e centralizadas**.

```html
<tr>
  <th>Produto</th>
  <th>Preço</th>
</tr>
```

 

### Padding e Spacing

**Padding**: Espaço interno da célula
**Spacing**: Espaço entre as células

```css
th, td {
  padding: 15px;
}

table {
  border-spacing: 10px;
}
```

> Para remover o espaço entre células:

```css
table {
  border-collapse: collapse;
}
```

 

### Colspan e Rowspan

* `colspan`: faz uma célula ocupar **mais de uma coluna**
* `rowspan`: faz uma célula ocupar **mais de uma linha**

```html
<!-- COLSPAN -->
<tr>
  <td colspan="2">Célula unida em duas colunas</td>
</tr>

<!-- ROWSPAN -->
<tr>
  <td rowspan="2">Célula em duas linhas</td>
  <td>Linha 1</td>
</tr>
<tr>
  <td>Linha 2</td>
</tr>
```

 

### Estilizando Tabelas com CSS

```css
table {
  font-family: Arial, sans-serif;
  border-collapse: collapse;
  width: 100%;
}

th {
  background-color: #f2f2f2;
  text-align: left;
}

td, th {
  border: 1px solid #ddd;
  padding: 8px;
}

tr:hover {
  background-color: #f5f5f5;
}
```

 

### Exemplo Completo

```html
<table style="width:100%; border-collapse: collapse;" border="1">
  <tr>
    <th>Nome</th>
    <th>Curso</th>
    <th>Nota</th>
  </tr>
  <tr>
    <td>Ana</td>
    <td>Engenharia</td>
    <td>8.5</td>
  </tr>
  <tr>
    <td colspan="2">Média Final</td>
    <td>8.5</td>
  </tr>
</table>
```

 

### Atividade – Tabela de Habilidades no Currículo

Expanda o seu **mini currículo** e adicione uma **tabela de habilidades** com os seguintes requisitos:

1. A tabela deve ter **cabeçalhos (`<th>`)** para: "Habilidade", "Nível", "Experiência (anos)".
2. Use **`border` com CSS**, e defina **padding** nas células.
3. Aplique **colspan ou rowspan** em pelo menos um exemplo.
4. Estilize com CSS para definir:

   * Fonte
   * Cores de cabeçalho
   * Destaque na linha ao passar o mouse (`hover`)
     
 

## **Seção 8: Trabalhando com `<div>` no HTML**

### O elemento `<div>`

O elemento `<div>` é um **contêiner em bloco** usado para agrupar elementos HTML. Ele não possui estilo visual por padrão, mas é essencial para organização e estilização com CSS.

 
### `<div>` como um contêiner

É comum agrupar títulos, parágrafos ou outras seções em um único bloco com `<div>`:

```html
<div>
  <h2>Seção</h2>
  <p>Texto descritivo.</p>
</div>
```

 

### Centralizando um `<div>`

Para centralizar uma `<div>` horizontalmente:

```html
<div style="width: 300px; margin: auto;">
  <p>Conteúdo centralizado.</p>
</div>
```

 

## **Exemplo Base (para todas as subseções)**

```html
<!DOCTYPE html>
<html>
<head>
    <link rel="stylesheet" href="estilo.css">
</head>
<body>

<div class="mycontainer">
    <div style="background-color: #fff8b3;">
        <h2>London</h2>
        <p>London is the capital city of England.</p>
        <p>London has over 9 million inhabitants.</p>
    </div>

    <div style="background-color: #ffccd5;">
        <h2>Oslo</h2>
        <p>Oslo is the capital city of Norway.</p>
        <p>Oslo has over 700,000 inhabitants.</p>
    </div>

    <div style="background-color: #e2f0e2;">
        <h2>Rome</h2>
        <p>Rome is the capital city of Italy.</p>
        <p>Rome has over 4 million inhabitants.</p>
    </div>
</div>

</body>
</html>
```

## **Subseções com Layouts Diferentes**

### Float

A propriedade `float` do CSS **não foi originalmente criada** para alinhar elementos lado a lado, mas por muito tempo foi usada para isso.

Ela posiciona elementos **horizontalmente**, permitindo que fiquem lado a lado.

**Arquivo `estilo.css`:**

```css
.mycontainer {
  width: 100%;
  overflow: auto;
}

.mycontainer div {
  width: 33%;
  float: left;
}
```

 

### Inline-block

Ao alterar o valor de `display` para `inline-block`, os `<div>`s são exibidos **lado a lado**, sem quebras de linha antes e depois.

**Arquivo `estilo.css`:**

```css
.mycontainer div {
  width: 30%;
  display: inline-block;
}
```

 

### Flex

O **Flexbox** foi criado para facilitar o desenvolvimento de layouts responsivos e flexíveis, sem a necessidade de usar `float`.

Para isso, o contêiner deve usar `display: flex`.

**Arquivo `estilo.css`:**

```css
.mycontainer {
  display: flex;
}

.mycontainer > div {
  width: 33%;
}
```

 

### Grid

O **CSS Grid** permite criar layouts bidimensionais com controle sobre linhas e colunas.

**Arquivo `estilo.css`:**

```css
.mycontainer {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  gap: 20px;
}

.mycontainer > div {
  background-color: #f2f2f2;
}
```

 

## **Atividade**

Crie um exemplo com `<div>`s representando três cidades (London, Oslo, Rome), e:

1. Implemente o HTML base acima.
2. Crie diferentes versões do `estilo.css` com:

   * `float`
   * `inline-block`
   * `flex`
   * `grid`
3. Visualize os efeitos de cada técnica.
4. Compare o comportamento das abordagens e escolha a mais adequada para o seu mini currículo.



## **Seção 9: Atributos `class` e `id` no HTML**

O HTML permite aplicar estilos e identificar elementos específicos utilizando os atributos `class` e `id`. Ambos são fundamentais para trabalhar com CSS e JavaScript.

 

### O Atributo `class`

O atributo `class` define **um nome de classe que pode ser reutilizado** em múltiplos elementos. Ele é muito utilizado para aplicar estilos em grupo via CSS.

#### Sintaxe:

```html
<tag class="nome-da-classe">Conteúdo</tag>
```

 

#### Exemplo: Aplicando estilo a uma classe

**HTML:**

```html
<p class="destaque">Este parágrafo está em destaque.</p>
```

**CSS:**

```css
.destaque {
  background-color: yellow;
  font-weight: bold;
}
```

 

### Múltiplas Classes

Um elemento pode ter **mais de uma classe**, separadas por espaços:

```html
<p class="destaque importante">Texto com duas classes</p>
```

Você pode estilizar cada classe individualmente ou em conjunto:

```css
.importante {
  color: red;
}
```

 

### Diferentes Elementos com a Mesma Classe

Você pode aplicar a **mesma classe a diferentes tipos de elementos**:

```html
<h1 class="azul">Título Azul</h1>
<p class="azul">Parágrafo Azul</p>
```

```css
.azul {
  color: blue;
}
```

 

### O Atributo `id`

O atributo `id` define um **identificador único** para um elemento. Ele deve ser **usado apenas uma vez por página**.

#### Sintaxe:

```html
<tag id="nome-unico">Conteúdo</tag>
```

 

#### Exemplo: Estilizando um ID

```html
<p id="meuTexto">Texto com ID</p>
```

```css
#meuTexto {
  color: green;
  font-style: italic;
}
```

 

### Diferença entre `class` e `id`

| Característica | `class`                  | `id`                            |
|----------------|---------------------------|----------------------------------|
| Uso            | Para múltiplos elementos | Para um único elemento          |
| CSS            | `.nomeDaClasse`          | `#nomeDoId`                     |
| Reutilizável   | Sim                      | Não (deve ser único por página) |


 

### Criando Marcadores com `id` e Links Internos

IDs também podem ser usados como **"âncoras"** para links dentro da mesma página.

```html
<a href="#contato">Ir para Contato</a>

...

<h2 id="contato">Seção de Contato</h2>
<p>Email: contato@exemplo.com</p>
```

 

### Atividade – Usando `class` e `id` no Mini Currículo

Atualize seu mini currículo e:

1. Aplique **classes** para estilizar grupos de elementos:

   * Use a mesma classe para estilizar todos os títulos secundários.
   * Crie uma classe `destaque` e aplique a um trecho da bio.

2. Aplique **IDs**:

   * Atribua um `id="topo"` no início da página.
   * Crie um link com `<a href="#topo">Voltar ao topo</a>` no final.

3. Estilize essas classes e IDs com um arquivo CSS.


## **Seção 10: Formulários em HTML**

### Introdução

Formulários HTML são usados para **coletar dados do usuário**, como nome, e-mail, senha, preferências e muito mais. Esses dados podem ser enviados para um servidor ou processados por scripts.


### O Elemento `<form>`

O elemento `<form>` serve como **contêiner principal** de todos os campos de entrada (inputs), botões e controles do formulário.

#### Sintaxe básica:

```html
<form action="/processa" method="post">
  <!-- Campos aqui -->
</form>
```

| Atributo | Finalidade                                                                        |
| -------- | --------------------------------------------------------------------------------- |
| `action` | Define o **destino** para onde os dados serão enviados                            |
| `method` | Define o **método de envio**: `get` (via URL) ou `post` (via corpo da requisição) |


### Atributos do `<form>`

| Atributo       | Descrição                                                          |
| -------------- | ------------------------------------------------------------------ |
| `action`       | URL para onde os dados serão enviados                              |
| `method`       | `get` ou `post` (preferência por `post` quando há dados sensíveis) |
| `target`       | Ex: `_blank`, `_self`, `_parent`, `_top`                           |
| `autocomplete` | `on` ou `off` para sugerir preenchimento automático                |


### O Elemento `<input>`

O `<input>` é um dos elementos mais versáteis do HTML. Ele pode representar **caixas de texto, senhas, botões, seletores de data, rádio, checkbox e muito mais**, dependendo do seu atributo `type`.

```html
<input type="text">
```


### Tipos de Input (`type`)

| Tipo       | Descrição                          |
| ---------- | ---------------------------------- |
| `text`     | Campo de texto padrão              |
| `password` | Campo para senhas (oculta o texto) |
| `email`    | Validação automática para e-mails  |
| `number`   | Aceita apenas números              |
| `date`     | Campo para datas (com seletor)     |
| `radio`    | Botões de opção                    |
| `checkbox` | Caixa de seleção                   |
| `submit`   | Botão para envio do formulário     |
| `reset`    | Botão para limpar os campos        |
| `hidden`   | Campo invisível (ex: tokens)       |

### Atributos Comuns dos Inputs

| Atributo      | Descrição                                               |
| ------------- | ------------------------------------------------------- |
| `placeholder` | Texto de dica dentro do campo                           |
| `value`       | Valor padrão do campo                                   |
| `required`    | Campo obrigatório                                       |
| `maxlength`   | Número máximo de caracteres permitidos                  |
| `min`/`max`   | Valores mínimo e máximo (números, datas)                |
| `step`        | Incremento permitido (útil com `number`, `range`, etc.) |
| `readonly`    | Campo visível mas não editável                          |
| `disabled`    | Campo desativado (não pode ser preenchido nem enviado)  |
| `autofocus`   | O foco é dado a esse campo ao carregar a página         |


### Campos de Texto

```html
<form>
  <label for="nome">Nome:</label><br>
  <input type="text" id="nome" name="nome"><br>
</form>
```

* O atributo `name` é importante para identificar o campo no envio.
* O atributo `id` é usado em conjunto com `<label>`.


### O Elemento `<label>`

Melhora a acessibilidade e a usabilidade do formulário.

```html
<label for="email">E-mail:</label>
<input type="email" id="email" name="email">
```

> O valor de `for` em `<label>` deve ser igual ao `id` do `<input>` correspondente.


### Botões de Rádio (`radio`)

Permitem que o usuário selecione apenas **uma opção entre várias**.

```html
<form>
  <p>Sexo:</p>
  <input type="radio" id="masc" name="sexo" value="M">
  <label for="masc">Masculino</label><br>

  <input type="radio" id="fem" name="sexo" value="F">
  <label for="fem">Feminino</label>
</form>
```

> Todos os botões de uma mesma pergunta devem ter o **mesmo `name`**.


### Caixas de Seleção (`checkbox`)

Permitem que o usuário selecione **uma ou mais opções**.

```html
<form>
  <p>Interesses:</p>
  <input type="checkbox" id="html" name="interesse" value="html">
  <label for="html">HTML</label><br>

  <input type="checkbox" id="css" name="interesse" value="css">
  <label for="css">CSS</label>
</form>
```


### Botão de Envio (`submit`)

Permite enviar os dados do formulário:

```html
<input type="submit" value="Enviar">
```

### O Elemento `<select>` / `<option>`

Uma **lista suspensa** (dropdown) permite que o usuário selecione uma opção entre várias disponíveis.

#### Exemplo básico:

```html
<label for="curso">Curso:</label><br>
<select id="curso" name="curso">
  <option value="html">HTML</option>
  <option value="css">CSS</option>
  <option value="js">JavaScript</option>
</select>
```

* O atributo `value` representa o valor enviado ao formulário.
* Você pode usar `selected` para marcar a opção padrão.

```html
<option value="html" selected>HTML</option>
```

### Outros Elementos Comuns em Formulários

| Elemento                  | Finalidade                              |
| ------------------------- | --------------------------------------- |
| `<textarea>`              | Campo de texto multilinha               |
| `<fieldset>` / `<legend>` | Agrupamento e legenda de seções         |
| `<button>`                | Botão personalizado (com ou sem `type`) |



### Exemplo Completo
```html
<form action="/enviar.php" method="post">
  <label for="nome">Nome:</label><br>
  <input type="text" id="nome" name="nome" placeholder="Seu nome" required><br><br>

  <label for="email">E-mail:</label><br>
  <input type="email" id="email" name="email" placeholder="seu@email.com" required><br><br>

  <label for="curso">Curso de Interesse:</label><br>
  <select id="curso" name="curso">
    <option value="html">HTML</option>
    <option value="css">CSS</option>
    <option value="js">JavaScript</option>
  </select><br><br>

  <p>Gênero:</p>
  <input type="radio" id="masc" name="genero" value="masculino">
  <label for="masc">Masculino</label>
  <input type="radio" id="fem" name="genero" value="feminino">
  <label for="fem">Feminino</label><br><br>

  <p>Interesses:</p>
  <input type="checkbox" id="html" name="interesses" value="HTML">
  <label for="html">HTML</label>
  <input type="checkbox" id="css" name="interesses" value="CSS">
  <label for="css">CSS</label><br><br>

  <label for="mensagem">Mensagem:</label><br>
  <textarea id="mensagem" name="mensagem" rows="4" cols="40"></textarea><br><br>

  <input type="submit" value="Enviar">
</form>
```


### Atividade – Criando seu Formulário de Contato

1. Crie um formulário com:

   * Nome
   * E-mail
   * Curso de Interesse (usando `<select>`)
   * Gênero (radio)
   * Interesses (checkbox)
   * Comentário (textarea)
   * Botão de envio

2. Utilize os atributos aprendidos: `placeholder`, `required`, `value`, `selected`, `autofocus`, etc.
3. Estilize o formulário com CSS (se desejar, usando classes).


## **Seção 11: Referências**

* FLATSCHART, Fábio. *HTML 5: embarque imediato*. 1. ed. Rio de Janeiro: Brasport, 2011. E-book. Disponível em: [https://plataforma.bvirtual.com.br](https://plataforma.bvirtual.com.br).
* MAZZA, Lucas. *HTML5 e CSS3: domine a web do futuro*. São Paulo, SP: Casa do Código, 2014. E-book. Disponível em: [https://plataforma.bvirtual.com.br](https://plataforma.bvirtual.com.br). 

* W3SCHOOLS. *HTML Tutorial*. Disponível em: [https://www.w3schools.com/html](https://www.w3schools.com/html). 

* FREEMAN, Elisabeth; ROBSON, Eric. *Use a Cabeça! HTML e CSS*. 2. ed. Rio de Janeiro: Alta Books, 2012. (Head First HTML and CSS). 





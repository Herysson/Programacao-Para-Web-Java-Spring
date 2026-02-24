  # CSS Cascading Style Sheets

## Introdução ao CSS

CSS é a sigla para **Cascading Style Sheets** (Folhas de Estilo em Cascata).

CSS descreve como os **elementos HTML** devem ser exibidos na tela, em papel ou em outros meios.

CSS **economiza muito trabalho**. Ele pode controlar o layout de várias páginas da web ao mesmo tempo.

Elementos HTML podem ser exibidos de forma diferente, dependendo do **dispositivo** ou **tamanho da tela**.
Com o CSS, é possível adaptar a exibição de uma página para **diferentes tipos de dispositivos**, como telas grandes, pequenas ou impressoras.

### Estilo 1
![image](https://github.com/user-attachments/assets/5f71e2af-dbde-46a7-adb8-a744887a9ab2)
### Estilo 2
![image](https://github.com/user-attachments/assets/3eccf5f5-6f3d-418b-96a1-303b6ebe5929)

## Como Usar CSS

Existem três maneiras principais de aplicar CSS a documentos HTML. Cada uma tem suas características, e a escolha adequada depende da organização e do tamanho do projeto.

### 1. CSS Externo

O CSS externo é definido em um arquivo separado com a extensão `.css`. Esse arquivo é então referenciado no HTML com a tag `<link>` dentro do elemento `<head>`.

```html
<head>
  <link rel="stylesheet" href="estilo.css">
</head>
```

Arquivo `estilo.css`:

```css
body {
  background-color: lightblue;
}
```

**Vantagens:**

* Permite reutilização de estilos em várias páginas.
* Mantém o HTML limpo e organizado.
* Facilita a manutenção e a colaboração em equipe.

É a forma **mais recomendada** para projetos reais e páginas com múltiplas seções.

 

### 2. CSS Interno

O CSS interno é definido dentro do próprio documento HTML, utilizando a tag `<style>` no cabeçalho (`<head>`).

```html
<head>
  <style>
    body {
      font-family: Arial, sans-serif;
    }
  </style>
</head>
```

**Vantagens:**

* Útil para páginas únicas ou testes rápidos.
* Código CSS e HTML ficam no mesmo arquivo.

**Desvantagens:**

* Pode dificultar a manutenção se o código CSS crescer.

 

### 3. CSS Inline

O CSS inline é inserido diretamente no elemento HTML, usando o atributo `style`.

```html
<p style="color:red;">Este parágrafo está em vermelho</p>
```

**Vantagens:**

* Aplicação rápida e direta.

**Desvantagens:**

* Não reutilizável.
* Dificulta a leitura e manutenção do código.
* Deve ser **evitado em projetos maiores**.

 

### Ordem de Prioridade (Cascade Order)

Quando diferentes formas de CSS são aplicadas ao mesmo elemento, a **ordem de cascata** determina qual estilo será aplicado.

A prioridade é a seguinte (da menor para a maior):

1. CSS Externo
2. CSS Interno
3. CSS Inline

Ou seja, o CSS inline **sobrepõe** o CSS interno e externo. O CSS interno **sobrepõe** o externo.

Além da forma de inserção, a **especificidade do seletor** (ID > Classe > Elemento) também influencia. Por exemplo, um seletor `#id` tem mais prioridade que `.classe`.

Exemplo de prioridade:

```html
<p id="exemplo" class="texto" style="color: red;">Texto</p>
```

* `color: red` no `style` será aplicado mesmo que exista `#exemplo { color: blue; }` no CSS.

Essa lógica é importante para entender por que certos estilos “não funcionam” — geralmente estão sendo sobrescritos por outro com maior prioridade.


## Sintaxe do CSS

A sintaxe básica do CSS é formada por um **seletor** e um **bloco de declaração**.

```css
seletor {
  propriedade: valor;
}
```

### Exemplo:


```html
<!DOCTYPE html>
<html lang="pt-BR">
<head>
  <meta charset="UTF-8">
  <title>Exemplo de Sintaxe CSS</title>
</head>
<body>

  <h1 id="titulo">Título Principal</h1>
  <h2>Subtítulo</h2>
  <p>Este é um parágrafo com estilo padrão.</p>
  <p class="destaque">Este parágrafo possui a classe "destaque".</p>

</body>
</html>
```

Nesse exemplo:

* `p` é o seletor (aplica-se a todos os parágrafos `<p>`).
* `color` e `text-align` são propriedades.
* `red` e `center` são os valores atribuídos a essas propriedades.
* As declarações são separadas por ponto e vírgula `;`.

## Selectors (Seletores)

Seletores são usados para **apontar qual ou quais elementos HTML devem ser estilizados** com CSS. Abaixo estão os tipos mais comuns de seletores.

### Seletor de Elemento (Type Selector)

Aplica estilo a todas as ocorrências de um elemento HTML.

```css
h1 {
  color: blue;
}
```

Aplica a todos os títulos `<h1>`.

### Seletor de Classe (Class Selector)

Aplica estilo a elementos com um atributo `class` específico. Usa o `.` antes do nome.

```css
.intro {
  font-size: 20px;
}
```

```html
<p class="intro">Este parágrafo será estilizado.</p>
```

### Seletor de ID (ID Selector)

Aplica estilo a um único elemento com `id`. Usa `#` antes do nome.

```css
#menu {
  background-color: lightgray;
}
```

```html
<div id="menu">Menu aqui</div>
```

### Seletor Universal

Aplica estilo a todos os elementos.

```css
* {
  margin: 0;
  padding: 0;
}
```

### Seletor de Agrupamento (Grouping Selector)

Aplica o mesmo estilo a vários seletores separados por vírgula.

```css
h1, h2, p {
  font-family: Arial;
}
```

### Seletor de Descendente

Aplica estilo a elementos que estão **dentro de outros elementos**.

```css
div p {
  color: green;
}
```

Seleciona todos os `<p>` que estão dentro de um `<div>`.

### Exercício Prático

**Objetivo:** Aplicar seletores CSS para estilizar diferentes seções do currículo.

**Instruções:**

1. Abra o arquivo HTML do seu currículo.
2. Adicione um arquivo CSS externo ou uma tag `<style>` no `<head>` do seu HTML.
3. Utilize os seguintes seletores para aplicar estilos:

   * **Seletor de Elemento:** Estilize todos os títulos `<h2>` com uma cor de sua escolha.
   * **Seletor de ID:** Aplique um fundo diferente à seção com `id="experiencia"`.
   * **Seletor de Classe:** Altere a fonte dos parágrafos com `class="descricao"`.
   * **Seletor de Descendente:** Mude a cor do texto dos `<li>` que estão dentro de uma `<ul>` com `class="habilidades"`.
 
## Comentários em CSS

Comentários são usados para explicar partes do código ou desativar regras temporariamente. Eles são ignorados pelo navegador e não afetam a exibição da página.

### Sintaxe

```css
/* Isso é um comentário */
```

### Usos comuns:

1. **Explicação de regras**

   ```css
   /* Define cor de fundo da página */
   body {
     background-color: white;
   }
   ```

2. **Desativar trechos de código**

   ```css
   /*
   p {
     font-size: 18px;
   }
   */
   ```

Utilize comentários para documentar seu código, especialmente em projetos maiores ou em equipe.

### Exercício Prático

**Objetivo:** Consolidar os conceitos de forma de uso do CSS, ordem de prioridade e uso de comentários no código.

**Instruções:**

1. Crie um arquivo chamado `estilo.css` na pasta do seu currículo.
2. Vincule esse arquivo ao seu HTML com a tag `<link>` no `<head>`.
3. No CSS externo, aplique pelo menos três estilos:

   * Um para o `body` (cor de fundo ou fonte).
   * Um para um elemento com classe (ex: `.secao`).
   * Um para um elemento com ID (ex: `#contato`).
4. Escreva comentários explicando para que serve cada regra.
5. Crie um exemplo comentando uma regra para testá-la desativada.

## Elementos Básicos do CSS: `background`

O plano de fundo de um elemento pode ser estilizado com **cores sólidas**, **imagens**, **gradientes** e **propriedades combinadas**. Essas técnicas ajudam a destacar seções, organizar visualmente a página e melhorar a experiência do usuário.

```html
<body>

  <div class="exemplo exemplo1">
    <p>Exemplo 1: background-color (lightblue)</p>
  </div>

  <div class="exemplo exemplo2">
    <p>Exemplo 2: background-color com hexadecimal (#f0f0f0)</p>
  </div>

  <div class="exemplo exemplo3">
    <p>Exemplo 3: background-color com rgba (vermelho transparente)</p>
  </div>

  <div class="exemplo exemplo4">
    <p>Exemplo 4: background-image com repetição</p>
  </div>

  <div class="exemplo exemplo5">
    <p>Exemplo 5: background-image centralizada, sem repetição</p>
  </div>

  <div class="exemplo exemplo6">
    <p>Exemplo 6: background com gradiente em ângulo (135deg)</p>
  </div>

  <div class="exemplo exemplo7">
    <p>Exemplo 7: gradiente horizontal (to right)</p>
  </div>

  <div class="exemplo exemplo8">
    <p>Exemplo 8: gradiente vertical (to bottom)</p>
  </div>

</body>
```


### 1. `background-color`

Define uma **cor sólida de fundo**.

```css
body {
  background-color: lightblue;
}

.secao {
  background-color: #f0f0f0;
}

.destaque {
  background-color: rgba(255, 0, 0, 0.3); /* vermelho com transparência */
}
```

Você pode usar cores em:

* nome (`red`, `blue`, `lightgray`)
* hexadecimal (`#f5f5f5`)
* RGB/RGBA (`rgb(255,255,255)`, `rgba(255,0,0,0.5)`)
* HSL/HSLA (`hsl(0, 100%, 50%)`)

 

### 2. `background-image`

Define uma **imagem como plano de fundo**.

```css
body {
  background-image: url("textura.png");
}
```

Para evitar repetições inesperadas, configure:

```css
body {
  background-repeat: no-repeat;
  background-position: center;
  background-size: cover;
}
```

 

### 3. `background-repeat`

Controla **se a imagem de fundo será repetida**.

```css
background-repeat: repeat;      /* padrão */
background-repeat: repeat-x;    /* só na horizontal */
background-repeat: repeat-y;    /* só na vertical */
background-repeat: no-repeat;   /* não repete */
```

 

### 4. `background-position` e `background-size`

Controlam **onde a imagem será exibida** e **seu tamanho**.

```css
background-position: top right;
background-size: cover;       /* preenche a área toda mantendo proporção */
background-size: contain;     /* ajusta a imagem dentro do espaço */
```

 

### 5. `linear-gradient` (fundo com gradiente de cores)

O `linear-gradient()` permite criar transições suaves entre duas ou mais cores. Pode ser usado como valor de `background-image`.

```css
body {
  background: linear-gradient(135deg, #ffffff, #e0f0ff, #cce0f5, #b3d1f0);
  min-height: 100vh;
}
```

Neste exemplo:

* `135deg` define o ângulo do gradiente.
* A sequência de cores será misturada suavemente.
* min-height: 100vh; → garante que o body tenha no mínimo a altura total da tela, mesmo sem conteúdo.

Outros exemplos:

```css
header {
  background: linear-gradient(to right, #ffcc00, #ff9900);
}

.destaque {
  background: linear-gradient(to bottom, #ffffff, #eeeeee);
}
```

 

## Exercício Prático

**Objetivo:** Explorar diferentes técnicas de fundo (cores, imagens, gradientes) no currículo.

**Instruções:**

1. No seu arquivo `curriculo.css`, aplique ao menos **3 variações de background**:

   * Um com **cor sólida** usando `rgba` ou `hsl`.
   * Um com **imagem de fundo**, utilizando `background-repeat`, `background-position` e `background-size`.
   * Um com **gradiente** utilizando `linear-gradient`.

2. Experimente aplicar essas variações em diferentes seções da página:

   * `body`
   * `.secao` (classe de uma seção do currículo)
   * `#formacao` ou `#experiencia` (IDs de seções específicas)

3. Comente ao lado de cada regra explicando o que ela faz.
 

## Elementos Básicos do CSS: `border`

A propriedade `border` é usada para aplicar **contornos visuais** em volta de elementos HTML. Ela é muito útil para destacar seções, caixas de conteúdo, menus e divisores.

### Tipos de bordas

Você pode definir diferentes estilos de borda usando `border-style`. Os valores permitidos são:

```css
border-style: dotted;   /* pontilhada */
border-style: dashed;   /* tracejada */
border-style: solid;    /* sólida */
border-style: double;   /* dupla */
border-style: groove;   /* efeito 3D entalhado */
border-style: ridge;    /* efeito 3D em relevo */
border-style: inset;    /* parece afundado */
border-style: outset;   /* parece elevado */
border-style: none;     /* sem borda */
border-style: hidden;   /* borda oculta (usado em tabelas) */
```

### Exemplo:

```css
div {
  border-style: solid;
}
```

 

### Largura da borda (`border-width`)

Controla **a espessura da borda**:

```css
border-width: 1px;
border-width: 2px 4px; /* cima/baixo | esquerda/direita */
```

Você pode especificar larguras diferentes para cada lado com:

```css
border-top-width: 4px;
border-bottom-width: 2px;
```

 

### Cor da borda (`border-color`)

Define a cor da borda:

```css
border-color: red;
border-top-color: blue;
```

 

### Lados da borda

Você pode aplicar bordas em lados específicos:

```css
border-top: 2px solid red;
border-bottom: 1px dashed blue;
border-left: 5px solid green;
border-right: none;
```

 

### Shorthand `border`

Você pode combinar estilo, cor e largura de forma simplificada:

```css
border: 2px solid black;
```

 

### Bordas arredondadas (`border-radius`)

Permite **arredondar os cantos** de um elemento:

```css
border-radius: 10px;
```

Exemplo completo:

```css
.caixa {
  border: 1px solid gray;
  border-radius: 8px;
  padding: 10px;
}
```

 

### Exemplos práticos

```html
<div style="border: 1px solid black; padding: 10px;">
  Eu tenho bordas em todos os lados.
</div>

<div style="border-bottom: 2px solid red; margin-top: 20px;">
  Eu tenho uma borda inferior vermelha.
</div>

<div style="border: 1px solid #ccc; border-radius: 10px; padding: 10px; margin-top: 20px;">
  Eu tenho bordas arredondadas.
</div>

<div style="border-left: 5px solid blue; background-color: #e0fafa; padding: 10px; margin-top: 20px;">
  Eu tenho uma borda esquerda azul.
</div>
```

 

## Exercício Prático

**Objetivo:** Aplicar diferentes tipos e estilos de bordas no projeto de currículo.

**Instruções:**

1. No seu arquivo `curriculo.css`, escolha pelo menos **3 seções** do currículo para aplicar estilos de borda diferentes.

2. Em cada uma, utilize uma combinação de:

   * `border-style`
   * `border-color`
   * `border-width`
   * `border-radius` (quando quiser cantos arredondados)

3. Teste também aplicar bordas **em apenas um lado** (topo, esquerda, etc).

4. Adicione comentários no CSS explicando suas escolhas.


## Espaçamento e Tamanho de Elementos: `margin`, `padding`, `width`, `height`

No CSS, o **tamanho e espaçamento dos elementos** são controlados principalmente por estas quatro propriedades:

* `margin`: espaço **externo** ao redor do elemento (fora da borda).
* `padding`: espaço **interno** entre o conteúdo e a borda do elemento.
* `width`: **largura** do elemento.
* `height`: **altura** do elemento.


### `margin`

Define o espaço **ao redor** do elemento (do lado de fora da borda).

```css
div {
  margin: 20px;
}
```

#### Variações:

```css
margin-top: 10px;
margin-right: 15px;
margin-bottom: 20px;
margin-left: 5px;
```

#### Shorthand:

```css
margin: 10px 15px 20px 5px;
/* ordem: top right bottom left */
```

Se dois valores forem usados:

```css
margin: 10px 20px;
/* top/bottom = 10px, left/right = 20px */
```

 

### `padding`

Define o espaço **interno** entre o conteúdo e a borda do elemento.

```css
div {
  padding: 10px;
}
```

#### Variações:

```css
padding-top: 8px;
padding-right: 12px;
padding-bottom: 10px;
padding-left: 5px;
```

#### Shorthand:

```css
padding: 8px 12px 10px 5px;
/* ordem: top right bottom left */
```

 

### `width` e `height`

Definem a **largura** e a **altura** de um elemento. Podem ser usadas com unidades fixas ou relativas.

```css
div {
  width: 300px;
  height: 150px;
}
```

Também é possível usar valores relativos como `%`:

```css
div {
  width: 80%;
}
```

 

### Exemplo completo

 ```html
 <div class="exemplo ex-margin">
    <div class="titulo">Exemplo: margin</div>
    <div class="conteudo">
        Esta `div` possui <code>margin: 40px</code>.
        Ela se afasta de outros elementos ao seu redor.
    </div>
</div>

<div class="exemplo ex-padding">
    <div class="titulo">Exemplo: padding</div>
    <div class="conteudo">
        Esta `div` possui <code>padding: 30px</code>.
        O conteúdo tem mais espaço interno entre ele e a borda.
    </div>
</div>

<div class="exemplo ex-width">
    <div class="titulo">Exemplo: width</div>
    <div class="conteudo">
        Esta `div` possui <code>width: 300px</code>.
        A largura do elemento foi definida manualmente.
    </div>
</div>

<div class="exemplo ex-height">
    <div class="titulo">Exemplo: height</div>
    <div class="conteudo">
        Esta `div` possui <code>height: 100px</code>.
        A altura do elemento foi definida manualmente.
    </div>
</div>
``` 

```css
   body {
            font-family: Arial, sans-serif;
            padding: 30px;
            background-color: #f4f4f4;
        }

        .exemplo {
            border: 2px solid #999;
            margin-bottom: 30px;
            background-color: #fff;
        }

        .titulo {
            background-color: #eee;
            padding: 10px;
            font-weight: bold;
        }

        .conteudo {
            padding: 10px;
        }

        .ex-margin {
            background-color: #fdd;
            margin: 40px;
        }

        .ex-padding {
            background-color: #dfd;
            padding: 30px;
        }

        .ex-width {
            background-color: #d0e0f0;
            width: 300px;
        }

        .ex-height {
            background-color: #f0d0f0;
            height: 100px;
        }
```

## Diferença visual entre margin e padding

| Propriedade | Descrição                  | Resultado                                              |
| ----------- | -------------------------- | ------------------------------------------------------ |
| `padding`   | Espaço **dentro** da borda | Aumenta o espaço entre o conteúdo e a borda            |
| `margin`    | Espaço **fora** da borda   | Aumenta a distância entre o elemento e outros ao redor |

 

## Exercício Prático

**Objetivo:** Aplicar espaçamentos e tamanhos personalizados às seções do currículo usando `margin`, `padding`, `width` e `height`.

**Instruções:**

1. No seu arquivo `curriculo.css`, escolha pelo menos **três seções** e defina:

   * Um `padding` interno que deixe o conteúdo confortável.
   * Um `margin` para separar visualmente essa seção das demais.
   * Uma `width` fixa ou relativa (como `80%`).
   * Uma `height` (opcional, mas interessante testar).

2. Use diferentes combinações de shorthand e propriedades específicas (`top`, `left`, etc).

3. Adicione **comentários explicando** por que cada espaçamento foi usado.

## Controle de Posição 

A propriedade `position` define **como um elemento HTML é posicionado no documento**. Ela funciona em conjunto com as propriedades `top`, `right`, `bottom` e `left`.

### 1. `static` (padrão)

* É o valor padrão.
* Os elementos são posicionados de forma "normal", seguindo o fluxo do HTML.
* Não aceita `top`, `left`, etc.

```css
div {
  position: static;
}
```

### 2. `relative`

* Posiciona o elemento **relativamente à sua posição original**.
* Ele continua ocupando o mesmo espaço no fluxo do documento.

```css
div {
  position: relative;
  top: 20px;   /* move 20px para baixo */
  left: 10px;  /* move 10px para a direita */
}
```

### 3. `absolute`

* Remove o elemento do fluxo normal da página.
* Ele é posicionado **em relação ao elemento pai mais próximo com `position: relative`** (ou ao `<html>` se não houver pai posicionado).

```css
div {
  position: absolute;
  top: 0;
  right: 0;
}
```

### 4. `fixed`

* O elemento é fixado em um lugar da tela, **mesmo durante o scroll da página**.
* Muito usado em menus fixos e botões “voltar ao topo”.

```css
#topo {
  position: fixed;
  top: 10px;
  right: 10px;
}
```

### 5. `sticky`

* Combina características de `relative` e `fixed`.
* O elemento se comporta como `relative` até atingir um limite (ex: topo da página), e então passa a agir como `fixed`.

```css
h2 {
  position: sticky;
  top: 0;
  background-color: white;
}
```

```html
<body>

<h2 class="sticky-header">Cabeçalho Sticky: Fixa ao topo quando rolar</h2>

<div class="exemplo static">
    <strong>Position: static (padrão)</strong><br>
    Este elemento segue o fluxo normal do HTML.
</div>

<div class="exemplo relative">
    <strong>Position: relative</strong><br>
    Este bloco foi deslocado <code>top: 20px</code> e <code>left: 15px</code>, mas continua ocupando seu espaço original.
</div>

<div class="container">
    <strong>Contêiner com position: relative</strong>
    <div class="absolute">
        Position: absolute<br>
        Este bloco é posicionado em relação ao contêiner pai.
    </div>
</div>

<div class="conteudo">
    Role para ver o botão fixo no canto inferior direito...
</div>

<div class="fixed">
    Position: fixed<br>
    Este bloco fica fixo na tela, mesmo ao rolar.
</div>

</body>
```

```css
body {
            font-family: Arial, sans-serif;
            padding: 60px 20px;
        }

        .exemplo {
            margin-bottom: 40px;
            padding: 20px;
            border: 2px solid #ccc;
            background-color: #f9f9f9;
            position: static;
        }

        /* STATIC */
        .static {
            position: static;
        }

        /* RELATIVE */
        .relative {
            position: relative;
            top: 20px;
            left: 15px;
            background-color: #e3f2fd;
        }

        /* ABSOLUTE dentro de container com position: relative */
        .container {
            position: relative;
            height: 150px;
            background-color: #f0f0f0;
            border: 1px dashed #999;
            margin-bottom: 50px;
        }

        .absolute {
            position: absolute;
            top: 10px;
            right: 10px;
            background-color: #ffebee;
            padding: 10px;
            border: 1px solid red;
        }

        /* FIXED */
        .fixed {
            position: fixed;
            bottom: 10px;
            right: 10px;
            background-color: #c8e6c9;
            padding: 10px;
            border: 1px solid green;
        }

        /* STICKY */
        .sticky-header {
            position: sticky;
            top: 0;
            background-color: #fff59d;
            padding: 10px;
            border-bottom: 2px solid #fbc02d;
        }

        /* Conteúdo para scroll */
        .conteudo {
            height: 800px;
        }
```
 
## Controle de Alinhamento

A seguir, vamos abordar as propriedades que controlam o alinhamento de texto e blocos.

### `text-align`

Alinha o **conteúdo de texto** (e elementos inline) **dentro de um elemento**.

```css
p {
  text-align: center;   /* left | right | justify */
}
```

### `text-align-last`

Alinha a **última linha** de um parágrafo.

```css
p {
  text-align: justify;
  text-align-last: right;
}
```

### `vertical-align`

Alinha elementos **inline** verticalmente dentro de sua linha.

```css
img {
  vertical-align: middle; /* top | bottom | text-top | text-bottom */
}
```

### `line-height`

Define o **espaçamento vertical entre as linhas de texto**.

```css
p {
  line-height: 1.5;
}
```

### `direction`

Define a direção do texto: da esquerda para a direita (`ltr`) ou da direita para a esquerda (`rtl`).

```css
p {
  direction: rtl;
}
```

### `unicode-bidi`

Controla como o navegador deve lidar com direções mistas (esquerda-direita / direita-esquerda).

```css
p {
  direction: rtl;
  unicode-bidi: bidi-override;
}

```
### Centralizando Elementos com Flexbox

Além do `text-align` e `vertical-align`, uma forma poderosa e moderna de **centralizar elementos horizontal e verticalmente** é utilizando **Flexbox**, com as propriedades `display: flex`, `justify-content` e `align-items`.

### Exemplo: centralização perfeita no centro do contêiner

```css
.align-center-container {
    display: flex;
    justify-content: center; /* Centraliza horizontalmente */
    align-items: center;     /* Centraliza verticalmente */
    height: 100px;           /* Altura do contêiner */
    border: 1px solid #aaa;  /* Visualização */
}
```

HTML correspondente:

```html
<div class="align-center-container">
  <p>Eu estou centralizado!</p>
</div>
```

**Explicação**:

* `display: flex` ativa o layout flexível no contêiner.
* `justify-content: center` centraliza o conteúdo **na horizontal**.
* `align-items: center` centraliza o conteúdo **na vertical**.
* O contêiner precisa de uma **altura definida** para que a centralização vertical funcione corretamente.
  
```html
<body>

<div class="exemplo text-center">
    <div class="titulo">text-align: center</div>
    <p>Este parágrafo está centralizado horizontalmente.</p>
</div>

<div class="exemplo text-right">
    <div class="titulo">text-align: right</div>
    <p>Este parágrafo está alinhado à direita.</p>
</div>

<div class="exemplo text-justify">
    <div class="titulo">text-align: justify</div>
    <p>
        Este parágrafo está justificado. O texto se ajusta às margens laterais,
        criando um visual uniforme em ambas as bordas do bloco de texto.
    </p>
</div>

<div class="exemplo text-last">
    <div class="titulo">text-align-last: right</div>
    <p>
        Este parágrafo tem alinhamento justificado, mas sua última linha está alinhada à direita.
    </p>
</div>

<div class="exemplo">
    <div class="titulo">vertical-align: middle</div>
    <p class="linha">
        <img src="https://img.icons8.com/color/512/google-logo.png" width="30" class="inline-img">
        Imagem alinhada ao centro vertical da linha de texto.
    </p>
</div>

<div class="exemplo linha-alta">
    <div class="titulo">line-height: 2.5</div>
    <p>Este parágrafo tem espaçamento maior entre as linhas, facilitando a leitura.</p>
    <p>O valor <code>line-height</code> foi definido como <strong>2.5</strong>.</p>
</div>

<div class="exemplo rtl">
    <div class="titulo">direction: rtl</div>
    <p>Este texto está sendo exibido da direita para a esquerda.</p>
</div>

<div class="exemplo bidi">
    <div class="titulo">unicode-bidi: bidi-override</div>
    <p>Este texto está forçando a inversão da ordem com `bidi-override`.</p>
</div>

<div class="exemplo flexbox-container">
    <p>Centralizado com Flexbox</p>
</div>

</body>
```

```css
body {
            font-family: Arial, sans-serif;
            padding: 20px;
        }

        .exemplo {
            border: 1px solid #ccc;
            margin-bottom: 30px;
            padding: 15px;
            background-color: #f9f9f9;
        }

        .titulo {
            font-weight: bold;
            margin-bottom: 10px;
        }

        /* Text-align */
        .text-left {
            text-align: left;
        }

        .text-center {
            text-align: center;
        }

        .text-right {
            text-align: right;
        }

        .text-justify {
            text-align: justify;
        }

        /* Text-align-last */
        .text-last {
            text-align: justify;
            text-align-last: right;
        }

        /* Vertical-align */
        .linha {
            border: 1px dashed #999;
            height: 40px;
        }

        .inline-img {
            vertical-align: middle;
        }

        /* Line-height */
        .linha-alta {
            line-height: 2.5;
        }

        /* Direction e Unicode-bidi */
        .rtl {
            direction: rtl;
        }

        .bidi {
            direction: rtl;
            unicode-bidi: bidi-override;
        }

        /* Flexbox */
        .flexbox-container {
            display: flex;
            justify-content: center;
            align-items: center;
            height: 120px;
            border: 2px dashed #999;
            background-color: #eef;
        }
```

```html
<body>
<div style="text-align: center;">
    Texto centralizado
</div>

<div style="width: 100%; text-align: center;  background-color: #494949; padding: 10px;">
    <div style="width: 200px; margin: 0 auto; background-color: #999999">Elemento centralizado</div>
</div>

<!--
justify-content: center → centraliza horizontalmente
align-items: center → centraliza verticalmente
-->
<div style="display: flex; justify-content: center; align-items: center; height: 200px; background-color: #999999; margin: 10px">
    <div>Centralizado ao centro</div>
</div>

<!-- Centralizar com Grid Layout  -->
<div style="display: grid; place-items: center; height: 200px; background-color: #6a6a6a; margin: 10px">
    <div>Centralizado com Grid</div>
</div>

<!-- Centralizar com posição absoluta (antigo, mas ainda usado em alguns casos)  -->
<div style="position: relative; height: 200px; background-color: #a5a5a5; margin: 10px">
    <div style="position: absolute; top: 50%; left: 50%; transform: translate(-50%, -50%);">
        Centralizado
    </div>
</div>

<!--
: flex → ativa o Flexbox
flex-wrap: wrap → permite que os elementos quebrem para a próxima linha quando não houver mais espaço horizontal.
 -->
<div style="display: flex; flex-wrap: wrap;">
    <div style="width: 200px; height: 100px; background: lightblue; margin: 5px;">Item 1</div>
    <div style="width: 200px; height: 100px; background: lightcoral; margin: 5px;">Item 2</div>
    <div style="width: 200px; height: 100px; background: lightgreen; margin: 5px;">Item 3</div>
    <div style="width: 200px; height: 100px; background: #bd90ee; margin: 5px;">Item 4</div>
    <div style="width: 200px; height: 100px; background: #ee90c5; margin: 5px;">Item 5</div>
    <div style="width: 200px; height: 100px; background: #eede90; margin: 5px;">Item 6</div>
    <div style="width: 200px; height: 100px; background: #fbfae9; margin: 5px;">Item 7</div>
    <div style="width: 200px; height: 100px; background: #2e2e2e; margin: 5px;">Item 8</div>
</div>

<!--
grid-template-columns: repeat(auto-fit, minmax(...)) → define colunas responsivas
Os elementos se ajustam e quebram de linha automaticamente conforme o espaço disponível.
-->
<div style="display: grid; grid-template-columns: repeat(auto-fit, minmax(200px, 1fr)); gap: 10px;">
    <div style="background: lightblue; height: 100px;">Item 1</div>
    <div style="background: lightcoral; height: 100px;">Item 2</div>
    <div style="background: lightgreen; height: 100px;">Item 3</div>
</div>

</body>
```

## Exercício Prático

**Objetivo:** Aplicar posicionamento e alinhamento em seções do currículo.

### Parte A: Position

1. Escolha **dois elementos** do seu currículo:

   * Um que será reposicionado com `position: relative`.
   * Outro que pode ser fixado com `position: fixed` (ex: botão "voltar ao topo").

2. Adicione um bloco com `position: absolute` dentro de um contêiner com `position: relative`.

3. Teste um cabeçalho de seção com `position: sticky`.

### Parte B: Align

1. Aplique `text-align: center` nos títulos.
2. Ajuste o `line-height` dos parágrafos para melhorar a leitura.
3. Experimente `vertical-align` em uma imagem com texto ao lado.


## Estilizando Tabelas com CSS

As tabelas HTML podem ser estilizadas com CSS para ficarem mais legíveis, modernas e responsivas. A seguir, veremos como personalizar tabelas utilizando as propriedades de `border`, tamanho, alinhamento, estilo visual e responsividade.


### 1. Bordas de Tabelas (`border`)

Por padrão, as tabelas exibem bordas separadas para cada célula. Podemos unificá-las com `border-collapse`.

```css
table {
  border-collapse: collapse;
  width: 100%;
}

th, td {
  border: 1px solid black;
  padding: 8px;
}
```

### 2. Tamanho de Colunas e Altura de Linhas (`width` e `height`)

Você pode controlar a **largura das colunas** e a **altura das linhas**:

```css
th, td {
  width: 150px;
  height: 40px;
}
```

Use `width: 100%` na tabela para que ela se expanda completamente no contêiner pai.



### 3. Alinhamento (`text-align` e `vertical-align`)

O alinhamento do conteúdo das células pode ser ajustado horizontal e verticalmente.

```css
th {
  text-align: center;
  vertical-align: middle;
}

td {
  text-align: left;
  vertical-align: top;
}
```


### 4. Estilo Visual (Cores Alternadas, Hover)

Use pseudo-classes para criar efeitos visuais agradáveis:

```css
tr:nth-child(even) {
  background-color: #f2f2f2;
}

tr:hover {
  background-color: #e0f7fa;
}

th {
  background-color: #4caf50;
  color: white;
}
```

Esses estilos melhoram a leitura e a experiência do usuário.

### 5. Tabela Responsiva

Tabelas largas podem estourar o layout em telas pequenas. Use `overflow-x: auto` para adicionar rolagem horizontal.

```css
.table-container {
  overflow-x: auto;
}

table {
  width: 100%;
  border-collapse: collapse;
}
```

HTML correspondente:

```html
<body>

<div class="table-container">
    <table>
        <caption>Lista de Funcionários</caption>
        <thead>
        <tr>
            <th>Nome</th>
            <th>Cargo</th>
            <th>Departamento</th>
        </tr>
        </thead>
        <tbody>
        <tr>
            <td>João</td>
            <td>Desenvolvedor</td>
            <td>TI</td>
        </tr>
        <tr>
            <td>Ana</td>
            <td>Designer</td>
            <td>Criação</td>
        </tr>
        <tr>
            <td>Marcos</td>
            <td>Analista</td>
            <td>Financeiro</td>
        </tr>
        <tr>
            <td>Sofia</td>
            <td>Coordenadora</td>
            <td>RH</td>
        </tr>
        </tbody>
    </table>
</div>

</body>
```


### Exemplo completo de CSS para Tabela

```css
 .table-container {
            overflow-x: auto;
            margin-top: 20px;
        }

        table {
            border-collapse: collapse;
            width: 100%;
            min-width: 400px;
            font-family: Arial, sans-serif;
        }

        th, td {
            border: 1px solid #ddd;
            padding: 12px;
            height: 25px;
        }

        th {
            text-align: center;
            vertical-align: middle;
            background-color: #4caf50;
            color: white;
        }

        td {
            text-align: left;
            vertical-align: top;
        }

        tr:nth-child(even) {
            background-color: #f9f9f9;
        }

        tr:hover {
            background-color: #e0f7fa;
        }

        caption {
            caption-side: top;
            text-align: left;
            padding: 10px;
            font-weight: bold;
        }
```

## Exercício Prático

**Objetivo:** Criar uma tabela estilizada com CSS que organize alguma informação relevante no currículo (ex: histórico profissional, habilidades técnicas, cronograma de projetos).

**Instruções:**

1. Crie uma tabela em seu HTML com pelo menos **3 colunas e 3 linhas**.
2. Envolva a tabela em uma `div` com classe `table-container` para torná-la responsiva.
3. Aplique as seguintes propriedades:

   * `border` com `border-collapse`
   * cores alternadas nas linhas com `:nth-child(even)`
   * alinhamento do texto
   * `hover` na linha
   * largura 100% e rolagem horizontal
4. Utilize `th` para os cabeçalhos.


## Estilizando Formulários com CSS

Formulários são componentes essenciais da web. Com CSS, é possível torná-los mais elegantes, acessíveis e integrados ao design da página.

A seguir, trabalharemos com um exemplo HTML de formulário que será incrementado passo a passo com técnicas de estilização.


### Exemplo Base de Formulário

```html
<form>
  <label for="nome">Nome:</label>
  <input type="text" id="nome" name="nome">

  <label for="email">Email:</label>
  <input type="email" id="email" name="email">

  <label for="mensagem">Mensagem:</label>
  <textarea id="mensagem" name="mensagem"></textarea>

  <label for="setor">Setor:</label>
  <select id="setor" name="setor">
    <option>TI</option>
    <option>RH</option>
    <option>Financeiro</option>
  </select>

  <input type="submit" value="Enviar">
</form>
```


### Styling Input Fields

```css
input[type=text],
input[type=email],
textarea,
select {
  width: 100%;
  padding: 10px;
  margin-top: 6px;
  margin-bottom: 16px;
  box-sizing: border-box;
}
```


### Padded Inputs

Adicionando preenchimento interno (`padding`) para melhor usabilidade.

```css
input[type=text] {
  padding: 12px;
}
```


### Bordered Inputs

```css
input[type=text],
input[type=email],
textarea {
  border: 2px solid #ccc;
  border-radius: 4px;
}
```

### Colored Inputs

```css
input[type=text] {
  background-color: #f8f8f8;
}
```

### Focused Inputs

```css
input[type=text]:focus,
textarea:focus {
  border: 2px solid #4CAF50;
  background-color: #e8f5e9;
  outline: none;
}
```


### Input com ícone

```html
<div class="input-icon">
  <i class="fa fa-user"></i>
  <input type="text" placeholder="Nome de usuário">
</div>
```

```css
.input-icon {
  position: relative;
}

.input-icon i {
  position: absolute;
  left: 10px;
  top: 12px;
  color: gray;
}

.input-icon input {
  padding-left: 30px;
}
```


### Animated Search Input

```html
<input type="text" id="pesquisa" placeholder="Pesquisar...">
```

```css
#pesquisa {
  width: 100px;
  transition: width 0.4s ease-in-out;
}

#pesquisa:focus {
  width: 250px;
}
```


### Styling Textareas

```css
textarea {
  height: 100px;
  resize: vertical; /* ou none, both, horizontal */
}
```

### Styling Select Menus

```css
select {
  background-color: #fff;
  border: 1px solid #ccc;
  padding: 10px;
  border-radius: 4px;
}
```

### Styling Input Buttons

```css
input[type=submit] {
  background-color: #4CAF50;
  color: white;
  padding: 12px 20px;
  border: none;
  border-radius: 4px;
  cursor: pointer;
}

input[type=submit]:hover {
  background-color: #45a049;
}
```


## Exemplo Final Combinado

![image](https://github.com/user-attachments/assets/598644d2-47a7-4719-9e0c-7dd43bf0df02)


```html
<form>
  <label for="nome">Nome:</label>
  <input type="text" id="nome" name="nome" placeholder="Digite seu nome">

  <label for="email">Email:</label>
  <input type="email" id="email" name="email" placeholder="Digite seu email">

  <label for="mensagem">Mensagem:</label>
  <textarea id="mensagem" name="mensagem" placeholder="Digite sua mensagem"></textarea>

  <label for="setor">Setor:</label>
  <select id="setor" name="setor">
    <option>TI</option>
    <option>RH</option>
    <option>Financeiro</option>
  </select>

  <input type="submit" value="Enviar">
</form>
```

```css
form {
  max-width: 500px;
  margin: auto;
  background-color: #f2f2f2;
  padding: 20px;
  border-radius: 8px;
}

input[type=text],
input[type=email],
textarea,
select {
  width: 100%;
  padding: 12px;
  margin-top: 6px;
  margin-bottom: 16px;
  border: 1px solid #ccc;
  border-radius: 4px;
  box-sizing: border-box;
}

input[type=text]:focus,
input[type=email]:focus,
textarea:focus {
  border: 2px solid #4CAF50;
  background-color: #e8f5e9;
  outline: none;
}

input[type=submit] {
  background-color: #4CAF50;
  color: white;
  padding: 12px;
  border: none;
  border-radius: 4px;
  cursor: pointer;
}

input[type=submit]:hover {
  background-color: #45a049;
}
```



## Exercício Prático

**Objetivo:** Criar um formulário de contato ou cadastro no seu currículo, aplicando diferentes técnicas de estilização.

**Instruções:**

1. Crie uma seção `<form>` no seu currículo com os campos:

   * Nome
   * Email
   * Área de atuação (Select)
   * Comentários (Textarea)
   * Botão de envio

2. Aplique:

   * `padding` e `border-radius` nos inputs
   * `hover` e `focus` para campos e botões
   * Um input com ícone (opcional)
   * Campo de busca com `transition` (opcional)

3. Comente seu CSS explicando cada estilo aplicado.

## Alternando Estilos com JavaScript

Em muitos sites modernos, é comum oferecer ao usuário a possibilidade de escolher entre **modo claro (light)** e **modo escuro (dark)**.
Com um pouco de JavaScript, é possível trocar o **arquivo de CSS** dinamicamente para alterar o tema da página.

### Exemplo básico

No `<head>` do seu HTML, você deve ter um link apontando para o arquivo de estilos:

```html
<link id="theme" rel="stylesheet" href="estilo-light.css">
```

A seguir, crie um script com a função que troca o estilo:

```html
<script>
  function changeStyle(sheet) {
    document.getElementById('theme').href = sheet;
  }
</script>
```

Depois, crie os botões que o usuário pode clicar para alternar os temas:

```html
<button onclick="changeStyle('estilo-light.css')">Modo Claro</button>
<button onclick="changeStyle('estilo-dark.css')">Modo Escuro</button>
```

### Estrutura completa no HTML

```html
<!DOCTYPE html>
<html lang="pt-BR">
<head>
  <meta charset="UTF-8">
  <title>Currículo</title>
  <link id="theme" rel="stylesheet" href="estilo-light.css">
</head>
<body>

  <h1>Meu Currículo</h1>
  <p>Informações pessoais, formação, experiências...</p>

  <button onclick="changeStyle('estilo-light.css')">🌞 Modo Claro</button>
  <button onclick="changeStyle('estilo-dark.css')">🌙 Modo Escuro</button>

  <script>
    function changeStyle(sheet) {
      document.getElementById('theme').href = sheet;
    }
  </script>
</body>
</html>
```

---

## Atividade Final

**Objetivo:** Criar duas versões estilizadas do seu currículo — uma clara e uma escura — e permitir a troca entre elas com JavaScript.

### Instruções:

1. Crie dois arquivos CSS:

   * `estilo-light.css` com fundo claro, texto escuro e visual tradicional.
   * `estilo-dark.css` com fundo escuro, texto claro e estilo contrastante.

2. No HTML do seu currículo:

   * Adicione o elemento `<link id="theme">` com o `href` inicial apontando para `estilo-light.css`.
   * Crie dois botões para alternar entre os estilos.

3. Adicione o script com a função `changeStyle()` como mostrado acima.

4. Personalize cada tema:

   * Light: use cores como `#ffffff`, `#f5f5f5`, `#222222`.
   * Dark: use cores como `#121212`, `#333333`, `#e0e0e0`.

**Extra (opcional):** adicione um `:hover` nos botões ou troque ícones para melhorar a experiência.
---

## Referências

ZEMEL, Tárcio. *CSS eficiente: técnicas e ferramentas que fazem a diferença nos seus estilos*. São Paulo, SP: Casa do Código, 2015. E-book. Disponível em: [https://plataforma.bvirtual.com.br](https://plataforma.bvirtual.com.br). 

FRASSON, Rosicléia. *Turbine seu CSS: folhas de estilo inteligentes com Sass*. São Paulo, SP: Casa do Código, 2016. E-book. Disponível em: [https://plataforma.bvirtual.com.br](https://plataforma.bvirtual.com.br). 

W3Schools. *CSS Tutorial*. Disponível em: [https://www.w3schools.com/css/](https://www.w3schools.com/css/). Acesso em: 15 maio 2025.


# Design Pattern para estilo

Ao trabalhar com estilos em CSS, não há padrões de design no mesmo sentido que existem para programação. No entanto, há boas práticas e metodologias que ajudam a organizar e estruturar seus estilos de forma mais eficiente e sustentável. Alguns desses padrões e metodologias são:

1. **BEM (Block, Element, Modifier):**
   - O BEM é uma metodologia que visa tornar o código CSS mais modular e reutilizável, dividindo-o em blocos, elementos e modificadores.
   - Exemplo:

    ```css
    .block {
      /* Estilos do bloco */
    }

    .block__element {
      /* Estilos do elemento dentro do bloco */
    }

    .block--modifier {
      /* Estilos modificados para o bloco */
    }
    ```

2. **SMACSS (Scalable and Modular Architecture for CSS):**
   - O SMACSS é uma metodologia que divide os estilos em categorias específicas, promovendo a escalabilidade e manutenção do código.
   - Categorias incluem base, layout, módulo, estado e tema.
   - Exemplo:

    ```css
    /* Base Styles */
    body {
      font-size: 16px;
    }

    /* Layout Styles */
    .container {
      width: 100%;
      max-width: 1200px;
      margin: 0 auto;
    }

    /* Module Styles */
    .button {
      /* Estilos do botão */
    }

    /* State Styles */
    .is-active {
      /* Estilos para o estado ativo */
    }
    ```

3. **OOCSS (Object-Oriented CSS):**
   - O OOCSS incentiva a separação da estrutura e do design visual, promovendo a reutilização de estilos em diferentes partes do site.
   - Exemplo:

    ```css
    /* Estrutura */
    .box {
      padding: 10px;
      margin: 10px;
    }

    /* Design Visual */
    .box--blue {
      background-color: blue;
      color: white;
    }
    ```

4. **ITCSS (Inverted Triangle CSS):**
   - O ITCSS organiza os estilos em uma pirâmide invertida, com estilos mais genéricos e de baixo nível na base, e estilos mais específicos e de alto nível no topo.
   - Exemplo:

    ```css
    /* Configurações globais e resets */
    html {
      font-size: 16px;
    }

    /* Estilos base */
    body {
      font-family: 'Arial', sans-serif;
    }

    /* Componentes e módulos */
    .button {
      /* Estilos do botão */
    }

    /* Estilos de layout e templates */
    .container {
      /* Estilos do layout */
    }

    /* Estilos de temas e variações específicas do projeto */
    .theme-dark {
      /* Estilos para o tema escuro */
    }
    ```

Essas metodologias não são mutuamente exclusivas, e você pode combiná-las ou adaptá-las conforme necessário para atender às necessidades específicas do seu projeto. O importante é manter a consistência, modularidade e reusabilidade em seus estilos.

## Estrutura de Cascading Style Sheets

Montar uma boa estrutura de Cascading Style Sheets (CSS) é fundamental para garantir a manutenibilidade e a escalabilidade do seu código. Abaixo estão algumas diretrizes e boas práticas que podem ajudar a criar uma estrutura organizada e eficiente para o seu CSS:

### 1. **Organização Geral:**

- **Divisão Modular:**
  - Separe o CSS em módulos ou componentes, cada um responsável por uma parte específica da interface.

- **Arquivos Separados:**
  - Mantenha arquivos CSS separados para diferentes partes do seu projeto (ex: base, layout, componentes, páginas).

```plaintext
styles/
|-- base/
|   |-- reset.css
|   |-- typography.css
|-- layout/
|   |-- grid.css
|   |-- header.css
|   |-- footer.css
|-- components/
|   |-- button.css
|   |-- card.css
|-- pages/
|   |-- home.css
|   |-- about.css
|-- main.css
```

### 2. **Metodologias e Padrões:**

- **BEM, SMACSS, ou OOCSS:**
  - Considere a adoção de uma metodologia de nomenclatura como BEM, SMACSS ou OOCSS para padronizar a nomenclatura e a estrutura.

- **Nomeação Semântica:**
  - Use nomes semânticos para classes, evitando estilos baseados em apresentação.

### 3. **Resets e Normalizações:**

- **Reset CSS ou Normalize:**
  - Inclua um arquivo de reset ou normalização para garantir uma base consistente entre diferentes navegadores.

### 4. **Responsividade:**

- **Media Queries:**
  - Utilize media queries para estilos responsivos e adaptação a diferentes dispositivos.

```css
/* Exemplo de media query */
@media screen and (max-width: 768px) {
  /* Estilos para telas menores */
}
```

### 5. **Variáveis e Configurações:**

- **Variáveis CSS:**
  - Use variáveis CSS para armazenar valores reutilizáveis, como cores e tamanhos.

```css
:root {
  --primary-color: #3498db;
  --font-size: 16px;
}

body {
  color: var(--primary-color);
  font-size: var(--font-size);
}
```

### 6. **Arquitetura de Diretórios:**

- **Organização de Arquivos:**
  - Estruture seus diretórios de forma lógica, agrupando arquivos semelhantes.

- **Arquivos Importados:**
  - Importe arquivos CSS necessários em um arquivo principal (entry point) para manter a ordem correta.

### 7. **Comentários:**

- **Comentários Descritivos:**
  - Adicione comentários descritivos para explicar blocos de código complexos ou para documentar o propósito de um componente.

```css
/* Estilos para a barra de navegação */
.navbar {
  /* ... */
}
```

### 8. **Nomenclatura Consistente:**

- **Consistência de Nomes:**
  - Mantenha uma nomenclatura consistente para facilitar a leitura e a manutenção do código.

### 9. **Desempenho:**

- **Concatenação e Minificação:**
  - Ao implantar, considere concatenar e minificar arquivos CSS para otimizar o desempenho.

### 10. **Ferramentas e Pré-processadores:**

- **Sass ou Less:**
  - Considere o uso de pré-processadores como Sass ou Less para adicionar funcionalidades como variáveis, mixins e aninhamento.

### 11. **Versionamento:**

- **Controle de Versão:**
  - Considere o uso de controle de versão para rastrear alterações em seus arquivos CSS.

### Exemplo de `main.css` (Entry Point):

```css
/* Importação dos estilos globais */
@import 'base/reset.css';
@import 'base/typography.css';

/* Importação dos estilos de layout */
@import 'layout/grid.css';
@import 'layout/header.css';
@import 'layout/footer.css';

/* Importação dos estilos dos componentes */
@import 'components/button.css';
@import 'components/card.css';

/* Importação dos estilos das páginas */
@import 'pages/home.css';
@import 'pages/about.css';
```

Lembre-se de que essas diretrizes podem ser adaptadas conforme a necessidade do seu projeto. O objetivo principal é manter uma estrutura organizada, modular e fácil de manter.

## Usando o Sass 

Ao usar Sass (Syntactically Awesome Stylesheets) para criar uma estrutura de Cascading Style Sheets (CSS), você pode aproveitar recursos como variáveis, aninhamento, mixins e importações para tornar seu código mais modular e fácil de manter. Abaixo está um exemplo de como você poderia estruturar seus arquivos Sass:

### Estrutura de Diretórios:

```plaintext
styles/
|-- base/
|   |-- _reset.scss
|   |-- _typography.scss
|-- layout/
|   |-- _grid.scss
|   |-- _header.scss
|   |-- _footer.scss
|-- components/
|   |-- _button.scss
|   |-- _card.scss
|-- pages/
|   |-- _home.scss
|   |-- _about.scss
|-- main.scss
```

### `main.scss` (Entry Point):

```scss
/* Importação dos estilos globais */
@import 'base/reset';
@import 'base/typography';

/* Importação dos estilos de layout */
@import 'layout/grid';
@import 'layout/header';
@import 'layout/footer';

/* Importação dos estilos dos componentes */
@import 'components/button';
@import 'components/card';

/* Importação dos estilos das páginas */
@import 'pages/home';
@import 'pages/about';
```

### Exemplo de Uso de Variáveis:

```scss
/* _variables.scss */
$primary-color: #3498db;
$font-size: 16px;

/* _button.scss */
.button {
  background-color: $primary-color;
  font-size: $font-size;
  /* ... outros estilos ... */
}
```

### Exemplo de Aninhamento e Mixins:

```scss
/* _card.scss */
.card {
  padding: 10px;

  h2 {
    font-size: 1.5em;
  }

  @include box-shadow(0 0 10px rgba(0, 0, 0, 0.1));
}

/* Mixin para sombra */
@mixin box-shadow($shadow) {
  -webkit-box-shadow: $shadow;
  -moz-box-shadow: $shadow;
  box-shadow: $shadow;
}
```

### Vantagens do Sass:

1. **Variáveis:** Use variáveis para armazenar valores reutilizáveis.

2. **Aninhamento:** Aninhe seletores para refletir a estrutura HTML.

3. **Mixins:** Crie mixins para reutilizar padrões de estilos.

4. **Importações:** Importe arquivos Sass para manter uma estrutura modular.

5. **Partials e Importações Condicionais:** Use partials (arquivos começando com `_`) para dividir seu código em partes menores e importe apenas o que for necessário.

Ao compilar o arquivo `main.scss` com Sass, ele gerará um único arquivo CSS, aproveitando as importações e mantendo a organização da estrutura. Certifique-se de instalar o Sass e configurar um script de compilação em seu projeto para começar a trabalhar com essas práticas.

## Configurar variáveis globais de estilo 

Webpack, por si só, não lida diretamente com variáveis globais de estilo sem import. No entanto, você pode alcançar esse comportamento usando ferramentas como loaders e plugins no ecossistema do Webpack, juntamente com pré-processadores CSS como Sass.

Aqui estão os passos básicos para configurar variáveis globais de estilo sem a necessidade de importar em cada arquivo no Webpack usando Sass:

### 1. Instalar Dependências:

Certifique-se de ter os pacotes necessários instalados:

```bash
npm install sass sass-loader style-loader css-loader --save-dev
```

### 2. Configurar o Webpack:

Configure o seu arquivo `webpack.config.js` para incluir os loaders necessários:

```javascript
const path = require('path');

module.exports = {
  entry: './src/index.js', // Seu ponto de entrada principal
  output: {
    filename: 'bundle.js',
    path: path.resolve(__dirname, 'dist'),
  },
  module: {
    rules: [
      {
        test: /\.scss$/,
        use: [
          'style-loader', // Adiciona estilos ao DOM via tag <style>
          'css-loader',   // Converte CSS em módulos CommonJS
          'sass-loader'   // Compila Sass para CSS
        ],
      },
    ],
  },
};
```

### 3. Criar Variáveis Globais com Sass:

Crie um arquivo `_variables.scss` com suas variáveis globais:

```scss
// _variables.scss

$primary-color: #3498db;
$font-size: 16px;
```

### 4. Usar Variáveis no Estilo:

Agora, em seus estilos Sass, você pode usar essas variáveis diretamente sem importar:

```scss
// styles.scss

body {
  color: $primary-color;
  font-size: $font-size;
}

.button {
  background-color: $primary-color;
  /* outros estilos */
}
```

### 5. Importar Arquivos Sass no Seu Ponto de Entrada:

Certifique-se de importar seus arquivos Sass no ponto de entrada do seu aplicativo (geralmente um arquivo JavaScript):

```javascript
// index.js

import './styles.scss'; // Importa os estilos Sass
```

### 6. Compilar e Executar:

Execute o webpack para compilar e gerar seu bundle:

```bash
npx webpack
```

O resultado final será um único arquivo JavaScript (bundle) que inclui tanto seu código JavaScript quanto os estilos Sass. Isso elimina a necessidade de importar variáveis globalmente em cada arquivo Sass.

## Mixins em Sass para criar media queries com breakpoints

Ao utilizar mixins em Sass para criar media queries com breakpoints, você pode criar um sistema flexível e fácil de manter. Aqui está um exemplo básico:

```scss
// Defina seus breakpoints
$breakpoints: (
  small: 576px,
  medium: 768px,
  large: 992px,
  xlarge: 1200px
);

// Mixin para media queries
@mixin breakpoint($point) {
  $breakpoint: map-get($breakpoints, $point);
  @media only screen and (min-width: $breakpoint) {
    @content;
  }
}

// Exemplos de uso
.element {
  width: 100%;

  @include breakpoint(medium) {
    width: 50%;
  }

  @include breakpoint(large) {
    width: 33.33%;
  }

  @include breakpoint(xlarge) {
    width: 25%;
  }
}
```

Neste exemplo:

1. Definimos um mapa chamado `$breakpoints` que associa nomes de breakpoints a valores em pixels.
2. Criamos um mixin chamado `breakpoint` que aceita um ponto (nome do breakpoint) e aplica as regras dentro da media query correspondente.
3. Em seguida, usamos o mixin nos estilos do nosso elemento, especificando as regras específicas para cada breakpoint.

Isso torna fácil ajustar e manter os breakpoints em um único lugar (no mapa) e simplifica a aplicação de estilos condicionais com mixins.

Se você preferir usar nomes mais descritivos, renomear os `$breakpoints` para refletir tipos de dispositivos, como "mobile", "tablet", "notebook", etc., é uma escolha sensata. Aqui está o exemplo atualizado:

```scss
// Defina seus tipos de media
$mediaTypes: (
  mobile: 576px,
  tablet: 768px,
  notebook: 992px,
  desktop: 1200px
);

// Mixin para media queries
@mixin media-type($type) {
  $media: map-get($mediaTypes, $type);
  @media only screen and (min-width: $media) {
    @content;
  }
}

// Exemplos de uso
.element {
  width: 100%;

  @include media-type(tablet) {
    width: 50%;
  }

  @include media-type(notebook) {
    width: 33.33%;
  }

  @include media-type(desktop) {
    width: 25%;
  }
}
```

Agora, os nomes dos tipos de media estão mais alinhados com os dispositivos que representam, tornando o código mais semântico e fácil de entender. Essa é uma boa prática para manter a clareza e a consistência no seu código Sass.

### Referências adicionais

[How to Write Media Queries with SASS Mixins](https://dev.to/rembertdesigns/how-to-write-media-queries-with-sass-mixins-32e)\
[A Complete Guide to CSS Media Queries
](https://css-tricks.com/a-complete-guide-to-css-media-queries/)

## Style Guide

Configurar um guia de estilo (style guide) usando Sass envolve definir diretrizes para a tipografia, paleta de cores e outros estilos visuais que serão consistentemente aplicados em um projeto. Vou fornecer um exemplo básico para começar. Certifique-se de ajustar conforme as necessidades específicas do seu projeto.

1. **Estrutura de Pastas:**
   - Comece organizando seu projeto. Aqui está uma estrutura simples:
     ```
     styles/
     ├── base/
     │   ├── _typography.scss
     │   ├── _colors.scss
     ├── components/
     │   ├── _buttons.scss
     │   ├── _forms.scss
     ├── main.scss
     ```

2. **Definindo Tipografia (_typography.scss):**
   ```scss
   // _typography.scss
   $base-font-size: 16px;

   body {
     font-family: 'Arial', sans-serif;
     font-size: $base-font-size;
     line-height: 1.5;
   }

   h1, h2, h3, h4, h5, h6 {
     font-family: 'Helvetica', sans-serif;
     // Defina outros estilos de cabeçalho conforme necessário
   }
   ```

3. **Definindo Paleta de Cores (_colors.scss):**
   ```scss
   // _colors.scss
   $primary-color: #3498db;
   $secondary-color: #2ecc71;
   $accent-color: #e74c3c;

   // Pode incluir mais cores conforme necessário
   ```

4. **Componentes (buttons, forms, etc.):**
   ```scss
   // _buttons.scss
   .button {
     padding: 10px 20px;
     font-size: $base-font-size;
     background-color: $primary-color;
     color: #fff;
     border: none;
     cursor: pointer;

     &:hover {
       background-color: darken($primary-color, 10%);
     }
   }
   ```

   ```scss
   // _forms.scss
   input, textarea {
     padding: 10px;
     margin: 5px 0;
     border: 1px solid $primary-color;
   }
   ```

5. **Main Stylesheet (main.scss):**
   ```scss
   // main.scss
   @import 'base/typography';
   @import 'base/colors';
   @import 'components/buttons';
   @import 'components/forms';
   ```

6. **Compilando com Sass:**
   Certifique-se de compilar seu arquivo Sass em um arquivo CSS usando um compilador Sass. Você pode usar ferramentas como `node-sass`, `sass`, ou integrar com frameworks como Angular ou React que incluem suporte ao Sass.

   Exemplo com `node-sass`:
   ```bash
   node-sass styles/main.scss -o dist/css
   ```

7. **Integrando no HTML:**
   Inclua o arquivo CSS gerado no HTML:
   ```html
   <!DOCTYPE html>
   <html lang="en">
   <head>
     <meta charset="UTF-8">
     <meta name="viewport" content="width=device-width, initial-scale=1.0">
     <link rel="stylesheet" href="dist/css/main.css">
     <title>Seu Projeto</title>
   </head>
   <body>
     <!-- Seu conteúdo HTML aqui -->
   </body>
   </html>
   ```

Este é um exemplo básico para começar. Você pode expandir e personalizar de acordo com as necessidades específicas do seu projeto. Certifique-se de ajustar as variáveis, estilos e estrutura conforme necessário.

### Usando mixins

Vamos refatorar o exemplo anterior para incluir mixins no lugar das variáveis para a tipografia e paleta de cores. Os mixins oferecem mais flexibilidade ao aplicar estilos reutilizáveis em diferentes contextos.

1. **Estrutura de Pastas:**
   ```
   styles/
   ├── mixins/
   │   ├── _typography.scss
   │   ├── _colors.scss
   ├── components/
   │   ├── _buttons.scss
   │   ├── _forms.scss
   ├── main.scss
   ```

2. **Definindo Mixins para Tipografia e Cores:**

   ```scss
   // _typography.scss
   @mixin typography {
     $base-font-size: 16px;

     body {
       font-family: 'Arial', sans-serif;
       font-size: $base-font-size;
       line-height: 1.5;
     }

     h1, h2, h3, h4, h5, h6 {
       font-family: 'Helvetica', sans-serif;
       // Defina outros estilos de cabeçalho conforme necessário
     }
   }
   ```

   ```scss
   // _colors.scss
   @mixin colors {
     $primary-color: #3498db;
     $secondary-color: #2ecc71;
     $accent-color: #e74c3c;

     // Pode incluir mais cores conforme necessário
   }
   ```

3. **Componentes (buttons, forms, etc.):**
   
   ```scss
   // _buttons.scss
   @import '../mixins/colors';

   @mixin button-styles {
     padding: 10px 20px;
     font-size: $base-font-size;
     background-color: $primary-color;
     color: #fff;
     border: none;
     cursor: pointer;

     &:hover {
       background-color: darken($primary-color, 10%);
     }
   }

   .button {
     @include button-styles;
   }
   ```

   ```scss
   // _forms.scss
   @mixin form-styles {
     input, textarea {
       padding: 10px;
       margin: 5px 0;
       border: 1px solid $primary-color;
     }
   }

   @include form-styles;
   ```

4. **Main Stylesheet (main.scss):**

   ```scss
   // main.scss
   @import 'mixins/typography';
   @import 'mixins/colors';
   @import 'components/buttons';
   @import 'components/forms';
   ```

5. **Compilando com Sass:**

   Compile seu arquivo Sass em um arquivo CSS como anteriormente.

6. **Integrando no HTML:**

   Inclua o arquivo CSS gerado no HTML.

Este exemplo usa mixins para tornar os estilos mais modulares e reutilizáveis. Você pode criar mixins adicionais conforme necessário e aplicá-los nos componentes desejados. Ajuste conforme as necessidades específicas do seu projeto.

## Paleta de cores

Usar `sass:map` para criar uma paleta de cores em Sass pode tornar o código mais organizado e fácil de gerenciar. Aqui está um exemplo básico:

1. **Definindo a Paleta de Cores:**

   ```scss
   // _colors.scss
   $color-palette: (
     primary: #3498db,
     secondary: #2ecc71,
     accent: #e74c3c,
     // Adicione mais cores conforme necessário
   );
   ```

2. **Criando uma Função para Obter Cores:**

   ```scss
   // _colors.scss
   @function get-color($color) {
     @return map-get($color-palette, $color);
   }
   ```

3. **Usando a Paleta de Cores em Componentes:**

   ```scss
   // _buttons.scss
   @import 'colors';

   .button {
     background-color: get-color(primary);
     // Outros estilos de botão
   }
   ```

   ```scss
   // _forms.scss
   @import 'colors';

   input {
     border: 1px solid get-color(primary);
     // Outros estilos de formulário
   }
   ```

4. **Compilando com Sass:**

   Certifique-se de compilar todos os arquivos Sass em um único arquivo CSS.

Dessa forma, você tem uma paleta de cores centralizada que pode ser facilmente ajustada ou expandida. A função `get-color` ajuda a obter uma cor específica da paleta em diferentes partes do seu código. Isso facilita a manutenção e a consistência nas escolhas de cores em todo o projeto.


### Usando function get-color

Você pode adaptar a função `get-color` para retornar um objeto de cores se você precisar de mais informações além da cor principal. Aqui está um exemplo de como você poderia fazer isso:

1. **Modificando a Função `get-color`:**

   ```scss
   // _colors.scss
   $color-palette: (
     primary: #3498db,
     secondary: #2ecc71,
     accent: #e74c3c,
     // Adicione mais cores conforme necessário
   );

   @function get-color($color) {
     $color-value: map-get($color-palette, $color);

     @return (
       name: $color,
       value: $color-value
     );
   }
   ```

2. **Usando a Função com Objetos de Cores:**

   ```scss
   // _buttons.scss
   @import 'colors';

   .button {
     $primary-color: get-color(primary);

     background-color: $primary-color;
     border: 2px solid $primary-color;
     // Outros estilos de botão
   }
   ```

Agora, quando você usa `get-color(primary)`, ele retorna um objeto com a propriedade `value` contendo o valor da cor principal e a propriedade `name` contendo o nome da cor. Você pode ajustar essa estrutura conforme necessário para atender aos requisitos específicos do seu projeto.

### Usando de forma global a função get-color

Se você deseja tornar a função `get-color` global sem importar manualmente em cada arquivo SCSS, você pode considerar o uso de variáveis globais do Sass e o webpack para configurar o carregamento dessas variáveis globais.

Aqui está um exemplo de como você pode fazer isso:

1. **Criar um arquivo `_colors.scss`:**

   ```scss
   // _colors.scss
   $color-palette: (
     primary: #3498db,
     secondary: #2ecc71,
     accent: #e74c3c,
     // Adicione mais cores conforme necessário
   );

   @function get-color($color) {
     $color-value: map-get($color-palette, $color);

     @return (
       name: $color,
       value: $color-value
     );
   }

   // Exportando variáveis globais
   :export {
     get-color: get-color;
   }
   ```

2. **Configurar o Webpack para carregar variáveis globais:**

   Adicione a seguinte configuração ao seu arquivo `webpack.config.js` para carregar as variáveis globais no início de seus estilos:

   ```javascript
   // webpack.config.js
   const path = require('path');

   module.exports = {
     // ... outras configurações

     module: {
       rules: [
         {
           test: /\.scss$/,
           use: [
             'style-loader',
             'css-loader',
             'sass-loader',
             {
               loader: 'sass-resources-loader',
               options: {
                 resources: [
                   path.resolve(__dirname, 'caminho/para/_colors.scss'),
                   // Adicione outros caminhos conforme necessário
                 ],
               },
             },
           ],
         },
       ],
     },
   };
   ```

   Certifique-se de ajustar o caminho para `_colors.scss` conforme necessário.

Dessa forma, você terá a função `get-color` disponível globalmente em todos os seus estilos sem precisar importá-la manualmente em cada arquivo SCSS.

## Grids

Dê preferencia ao uso de grid para o layout geral da página e flexbox para componentes internos.

### Abordagem Híbrida:

Propõe uma estratégia de combinar as vantagens do grid e do flexbox em um projeto.
Sugere usar grid para o layout geral da página, definindo a estrutura de linhas e colunas.
Recomenda utilizar flexbox para posicionar e organizar os componentes internos dentro dessas áreas do grid.

### Grid para o Layout Principal:

Enfatiza o uso de grid para criar um layout principal, dividindo a página em seções e áreas.
Destaca a capacidade do grid de lidar com layouts bidimensionais de forma eficiente.
flexbox para Componentes Internos:

Sugere que flexbox seja aplicado aos componentes internos dentro das áreas do grid.
Aponta para a flexibilidade do flexbox em organizar elementos em uma única dimensão, como linhas ou colunas.

### Vantagens de grid:

Aborda as vantagens do grid na criação de layouts complexos e alinhamento bidimensional.
Destaca a capacidade de criar estruturas de layout de forma mais rápida e eficiente.
Vantagens de flexbox:

Salienta que flexbox é especialmente eficaz para organizar itens em uma direção, sendo ideal para componentes internos.
Exemplos Práticos:

Oferece exemplos práticos de como implementar essa abordagem híbrida em projetos reais.
Demonstração de código e explicações sobre como usar grid e flexbox em conjunto.
Conclusão:

Conclui destacando que a escolha entre grid e flexbox pode depender das necessidades específicas de cada parte do layout.

A abordagem proposta no artigo visa aproveitar o melhor de ambos os mundos, utilizando as características específicas de grid e flexbox para diferentes partes do projeto. Isso permite uma maior flexibilidade e eficiência no desenvolvimento de layouts complexos.

O uso de `display: grid` e `display: flex` em vez de bibliotecas prontas de grids e colunas oferece algumas vantagens, embora a escolha dependa dos requisitos específicos do projeto. Aqui estão algumas vantagens:

### Vantagens de `display: grid`:

1. **Flexibilidade na Estruturação:**
   - Permite criar layouts complexos e personalizados.
   - Facilita a criação de layouts bidimensionais com linhas e colunas.

2. **Alinhamento de Conteúdo:**
   - Oferece controle granular sobre o alinhamento de itens em ambas as direções (horizontal e vertical).

3. **Responsividade:**
   - Suporta facilmente designs responsivos com media queries.
   - Redimensionamento de colunas e linhas pode ser ajustado automaticamente em layouts responsivos.

4. **Espaçamento e Margens:**
   - Permite controlar espaçamento entre células e colunas com propriedades como `grid-gap` e `grid-template-columns`.

### Vantagens de `display: flex`:

1. **Alinhamento de Itens:**
   - Permite fácil alinhamento de itens em uma única direção (horizontal ou vertical).
   - Ótimo para estruturas lineares como barras de navegação ou listas.

2. **Flexibilidade e Crescimento:**
   - Itens dentro de um contêiner flexível podem crescer ou encolher para se ajustar ao espaço disponível.
   - Ideal para layouts dinâmicos.

3. **Orquestração Rápida:**
   - É mais fácil de entender e implementar para layouts simples.
   - Útil quando a complexidade de um sistema de grid completo não é necessária.

### Desvantagens de Bibliotecas Prontas:

1. **Peso Adicional:**
   - Bibliotecas podem adicionar um peso considerável ao seu projeto, especialmente se você usar apenas uma pequena parte delas.

2. **Menos Controle:**
   - Em algumas situações, você pode ter menos controle sobre o design e comportamento dos elementos.

3. **Personalização Limitada:**
   - A personalização pode ser limitada, pois você está restrito às opções oferecidas pela biblioteca.

### Considerações Gerais:

- **Complexidade do Projeto:**
  - Projetos mais complexos podem se beneficiar do poder e controle total oferecidos por `display: grid`.
  - Projetos mais simples podem encontrar `display: flex` mais eficiente e fácil de usar.

- **Compatibilidade do Navegador:**
  - `display: flex` é amplamente suportado, mas `display: grid` pode ter alguns problemas de compatibilidade com versões mais antigas de navegadores.

- **Necessidades Específicas:**
  - A escolha entre `display: grid` e `display: flex` dependerá das necessidades específicas do seu layout e design.

Em resumo, a escolha entre `display: grid`, `display: flex`, ou uma biblioteca de grids depende do contexto e requisitos específicos do projeto. Ambas as abordagens têm seu lugar e podem ser usadas de forma complementar em um mesmo projeto.

### Referências adicionais

[Grid para layout, flexbox para componentes](https://dev.to/codecasts/grid-para-layout-flexbox-para-componentes-gb3)\
[A Complete Guide to Flexbox](https://css-tricks.com/snippets/css/a-guide-to-flexbox/)\
[A Complete Guide to CSS Grid](https://css-tricks.com/snippets/css/complete-guide-grid/)

### Usando um custom grid

Se você quiser criar um arquivo Sass com estilos usando o display grid, inspirado no Bootstrap, pode seguir alguns passos básicos. Primeiro, certifique-se de ter o Sass instalado no seu projeto. Você pode instalar o Sass utilizando um gerenciador de pacotes, como o npm. Se ainda não o fez, você pode executar:

```bash
npm install sass
```

Aqui está um exemplo básico de como você poderia criar um arquivo Sass usando o display grid:

```scss
// _grid.scss

// Container
.container {
  width: 100%;
  max-width: 1140px;
  margin-right: auto;
  margin-left: auto;
  padding-right: 15px;
  padding-left: 15px;
}

// Row
.row {
  display: grid;
  grid-template-columns: repeat(12, 1fr);
  gap: 15px;
}

// Column
.col {
  position: relative;
  width: 100%;
  min-height: 1px;
  padding-right: 15px;
  padding-left: 15px;

  // Responsive columns
  @for $i from 1 through 12 {
    &.col-#{$i} {
      grid-column: span $i;
    }
  }
}
```

Depois de criar este arquivo `_grid.scss`, você pode importá-lo no seu arquivo principal Sass:

```scss
// styles.scss

@import 'grid';

// Seus estilos adicionais abaixo
```

Agora, você pode usar as classes `.container`, `.row`, e `.col` em seu HTML de maneira semelhante ao Bootstrap. Este é apenas um exemplo básico, e você pode ajustar e expandir conforme necessário para atender às suas necessidades específicas. Certifique-se de compilar seus arquivos Sass em um arquivo CSS usando um compilador Sass, como `sass` ou `node-sass`.
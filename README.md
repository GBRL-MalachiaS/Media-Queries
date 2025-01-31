
### **Media Types and Media Queries em HTML/CSS**

**O que são Media Types?**

Media Types são tipos de mídia que definem em quais dispositivos ou meios de apresentação determinadas folhas de estilo devem ser aplicadas. Eles permitem que você especifique estilos específicos para tipos de mídia como telas, impressoras, leitores de tela, entre outros.

**Principais Media Types e seus atributos:**

1. **all**
   - **Descrição**: Aplica-se a todos os dispositivos.
   - **Uso**: Quando você deseja que os estilos sejam universais.
   - **Exemplo de uso em CSS**:
     ```css
     @media all {
       body {
         font-family: Arial, sans-serif;
       }
     }
     ```

2. **screen**
   - **Descrição**: Destinado a telas de computador, tablets, smartphones e outros dispositivos de tela.
   - **Uso**: Para definir estilos específicos para visualização em telas.
   - **Exemplo**:
     ```css
     @media screen {
       /* Estilos para telas */
     }
     ```

3. **print**
   - **Descrição**: Projetado para impressão em papel.
   - **Uso**: Para ajustar o layout e estilos ao imprimir a página.
   - **Exemplo**:
     ```css
     @media print {
       /* Estilos para impressão */
     }
     ```

4. **speech**
   - **Descrição**: Para leitores de tela que convertem texto em fala.
   - **Uso**: Otimizar o conteúdo para síntese de voz.
   - **Exemplo**:
     ```css
     @media speech {
       /* Estilos para leitores de tela */
     }
     ```

5. **Atributos Obsoletos**:
   - **braille**, **embossed**, **handheld**, **projection**, **tty**, **tv**.
   - **Observação**: Essas mídias foram depreciadas e não são mais recomendadas, pois a maioria dos dispositivos modernos não as suporta ou seu uso é irrisório.

**Como utilizar Media Types no CSS e HTML:**

- **No HTML**:
  ```html
  <link rel="stylesheet" href="estilo.css" media="screen">
  ```
  - Aqui, o arquivo `estilo.css` será aplicado apenas em dispositivos de tela.

- **No CSS**:
  ```css
  @media print {
    /* Estilos aplicados durante a impressão */
    body {
      font-size: 12pt;
    }
  }
  ```

---

### **Media Queries**

**O que são Media Queries?**

Media Queries são uma funcionalidade do CSS3 que permite aplicar estilos condicionais com base em características do dispositivo ou ambiente, como largura da tela, orientação, resolução, entre outros. Elas são essenciais para criar designs responsivos que se adaptam a diferentes tamanhos e tipos de tela.

**Principais atributos (Media Features) e seus operadores:**

1. **Media Features (Características de Mídia):**

   - **`width` e `height`**:
     - Representam a largura e altura da área de exibição (viewport).
     - **Exemplo**:
       ```css
       @media (min-width: 768px) {
         /* Estilos para dispositivos com largura mínima de 768px */
       }
       ```

   - **`device-width` e `device-height`**:
     - Refere-se à largura e altura da tela física do dispositivo.

   - **`orientation`**:
     - Indica a orientação do dispositivo.
     - Valores: `portrait` (retrato) ou `landscape` (paisagem).
     - **Exemplo**:
       ```css
       @media (orientation: landscape) {
         /* Estilos para modo paisagem */
       }
       ```

   - **`resolution`**:
     - Define a resolução da tela.
     - Pode ser especificado em dpi (dots per inch) ou dppx (dots per pixel).
     - **Exemplo**:
       ```css
       @media (min-resolution: 2dppx) {
         /* Estilos para telas de alta densidade de pixels */
       }
       ```

   - **`aspect-ratio`**:
     - Relação entre a largura e a altura do viewport.
     - **Exemplo**:
       ```css
       @media (aspect-ratio: 16/9) {
         /* Estilos para telas com proporção 16:9 */
       }
       ```

   - **`prefers-color-scheme`**:
     - Detecta a preferência do usuário para esquemas de cores (claro ou escuro).
     - Valores: `light`, `dark`.
     - **Exemplo**:
       ```css
       @media (prefers-color-scheme: dark) {
         /* Estilos para modo escuro */
       }
       ```

   - **`pointer`**:
     - Indica a precisão do dispositivo apontador.
     - Valores: `none`, `coarse` (grosseiro), `fine` (preciso).
     - **Exemplo**:
       ```css
       @media (pointer: coarse) {
         /* Estilos para dispositivos touch */
       }
       ```

   - **`hover`**:
     - Indica se o dispositivo permite estado de hover.
     - Valores: `none`, `hover`.
     - **Exemplo**:
       ```css
       @media (hover: hover) {
         /* Estilos para dispositivos que suportam hover */
       }
       ```

2. **Operadores em Media Queries:**

   - **`and`**:
     - Combina múltiplas condições que devem ser verdadeiras.
     - **Exemplo**:
       ```css
       @media (min-width: 600px) and (orientation: landscape) {
         /* Estilos aplicados se ambas as condições forem satisfeitas */
       }
       ```

   - **`or`** (representado pela vírgula `,`):
     - Uma ou outra condição deve ser verdadeira.
     - **Exemplo**:
       ```css
       @media (max-width: 599px), (orientation: portrait) {
         /* Estilos aplicados se qualquer uma das condições for satisfeita */
       }
       ```

   - **`not`**:
     - Inverte a condição.
     - **Exemplo**:
       ```css
       @media not screen and (color) {
         /* Estilos aplicados a dispositivos que não são telas coloridas */
       }
       ```

   - **`only`**:
     - Aplica estilos somente se o tipo de mídia for reconhecido.
     - **Exemplo**:
       ```css
       @media only screen and (min-width: 800px) {
         /* Estilos aplicados apenas se a mídia for tela e a largura mínima for 800px */
       }
       ```

**Como utilizar Media Queries no CSS:**

- **Sintaxe básica**:
  ```css
  @media [tipo de mídia] [operador] (condição) {
    /* Regras CSS */
  }
  ```
  - O **tipo de mídia** é opcional e pode ser omitido.

**Exemplos práticos:**

1. **Design Responsivo para Dispositivos Móveis**:
   ```css
   /* Estilos gerais */
   body {
     font-size: 16px;
   }

   /* Estilos específicos para dispositivos com largura máxima de 600px */
   @media (max-width: 600px) {
     body {
       font-size: 14px;
     }
   }
   ```

2. **Adaptando Layout para Modo Escuro**:
   ```css
   /* Estilos padrão para modo claro */
   body {
     background-color: #ffffff;
     color: #000000;
   }

   /* Estilos para usuários que preferem modo escuro */
   @media (prefers-color-scheme: dark) {
     body {
       background-color: #000000;
       color: #ffffff;
     }
   }
   ```

3. **Ajustando para Dispositivos Touch**:
   ```css
   /* Aumentar áreas clicáveis em dispositivos touch */
   @media (pointer: coarse) {
     button {
       padding: 1em;
     }
   }
   ```

**Operadores e suas aplicações:**

- **Combinação de múltiplas condições**:
  ```css
  @media (min-width: 768px) and (max-width: 1024px) and (orientation: landscape) {
    /* Estilos para tablets em modo paisagem */
  }
  ```

- **Aplicação em múltiplas condições alternativas**:
  ```css
  @media (max-width: 500px), (hover: none) {
    /* Estilos aplicados se a largura for até 500px OU se o dispositivo não suportar hover */
  }
  ```

---

### **Resumo e Dicas de Utilização**

- **Media Types** são usados para direcionar estilos para tipos específicos de mídia (tela, impressão, etc.).
- **Media Queries** permitem ajustar estilos com base em características específicas do dispositivo ou ambiente.
- **Operadores lógicos** como `and`, `not` e `,` (or) enriquecem as Media Queries, permitindo condições complexas.
- **Práticas Modernas**:
  - Evite usar Media Types obsoletos.
  - Foque em Media Queries para criar layouts responsivos e acessíveis.
  - Teste seu site em diferentes dispositivos e tamanhos de tela para garantir uma experiência consistente.

---

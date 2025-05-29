# Módulo 20 - Construa emails com HTML

## Menu 
[Aula 1 - Crie o primeiro e-mail](#aula-1--crie-o-primeiro-e-mail)  
[Aula 2 - Teste o e-mail](#aula-2--teste-o-e-mail)  
[Aula 3 - Crie um e-mail de recuperação de senha](#aula-3--crie-um-e-mail-de-recuperação-de-senha)  
[Aula 4 - Crie um e-mail de confirmação de pedido](#aula-4--crie-um-e-mail-de-confirmação-de-pedido)  
[Aula 5 - Crie um e-mail de promoções](#aula-5--crie-um-e-mail-de-promoções)  

## **Aula 1 – Crie o primeiro e-mail**

### **Objetivos da aula**

* Compreender a estrutura básica de um e-mail HTML;
* Criar um e-mail a partir de uma interface do Figma;
* Conhecer as boas práticas na construção de e-mails responsivos e compatíveis;
* Entender as limitações e particularidades dos clientes de e-mail;
* Aprender a usar tabelas e CSS inline como base para o layout.

---

### **Introdução ao projeto**

O projeto da aula consiste na construção de um e-mail transacional para uma **loja virtual fictícia**. Os quatro modelos de e-mails planejados são:

1. Notificação de recebimento de pedido;
2. Recuperação de senha;
3. Promoções da loja;
4. Confirmação de transferência (estilo aviso de banco).

Começamos a aula construindo o **e-mail de notificação de Pix recebido**, com layout baseado em um design feito no **Figma**.

---

### **Por que usamos tabelas para e-mails?**

Nos e-mails, **não é seguro usar Flexbox, Grid ou até mesmo estilos modernos de CSS externo**. Isso acontece porque muitos clientes de e-mail (como o Outlook, Gmail, Yahoo Mail...) **não interpretam corretamente** essas tecnologias.

Por isso, usamos **HTML "retrô"**, com a boa e velha `<table>`, para **garantir compatibilidade máxima**.

---

### **Estrutura geral do código**

Vamos destrinchar o código em partes para explicar cada trecho de maneira didática.

#### 1. `<center>` e `<table width="600">`

```html
<center>
  <table width="600" cellpadding="0" cellspacing="0">
```

* **`<center>`**: Tag antiga usada para centralizar conteúdo. Funciona bem em e-mails.
* **`<table width="600">`**: Cria a estrutura principal com 600px de largura.
* **`cellpadding="0"` e `cellspacing="0"`**: Removem espaços internos e externos automáticos nas células.

#### 2. `<thead>` – Cabeçalho da tabela

```html
<thead>
  <tr>
    <th style="padding: 32px 0;">
      <img src="src/img/ebac_banking.png" alt="EBAC Banking">
    </th>
  </tr>
</thead>
```

* **`<thead>`**: Define a parte do cabeçalho da tabela.
* **`<tr>`**: Linha da tabela.
* **`<th>`**: Célula de cabeçalho (em e-mails, pode ser substituída por `<td>` para evitar problemas de estilo).

#### 3. `<tbody>` – Corpo da tabela

```html
<tbody>
  ...
</tbody>
```

Contém todas as informações principais do e-mail.

#### Exemplo de linha de mensagem principal:

```html
<tr>
  <td style="background-color: #10AC84;">
    <p style="text-align: center; color: #fff; font-family: sans-serif; font-size: 24px; font-weight: bold;">
      Você recebeu uma transferência!
    </p>
  </td>
</tr>
```

#### Saudação personalizada:

```html
<tr>
  <td style="padding-left: 40px; padding-top: 32px; padding-bottom: 32px;">
    <p style="font-size: 20px; font-family: sans-serif; margin: 0;">
      Olá <b>Matheus Aguiar</b><br>
      Você recebeu um pix do <b>Saitama</b>
    </p>
  </td>
</tr>
```

#### Valor recebido (tabela aninhada):

```html
<tr>
  <td style="background-color: #F8F2F2; padding: 16px 40px;">
    <table width="460" cellpadding="0" cellspacing="0">
      <tbody>
        <tr>
          <td align="left">
            <p style="font-size: 14px; margin: 0;">Valor recebido</p>
          </td>
          <td align="right">
            <b>R$3.000,00</b>
          </td>
        </tr>
      </tbody>
    </table>
  </td>
</tr>
```

Essa tabela é colocada dentro de um `<td>` para alinhar dois textos: a descrição e o valor, em lados opostos.

#### Mensagem secundária:

```html
<tr>
  <td align="right">
    <p style="font-size: 12px; font-family: sans-serif; margin-top: 8px;">
      Pix recebido em 27/05/2025 às 20:07 <br>
      Para mais detalhes acesse o app
    </p>
  </td>
</tr>
```

#### Rodapé com redes sociais:

```html
<tr>
  <td style="padding-top: 128px;">
    <center>
      <a href="https://www.facebook.com/?locale=pt_BR" style="text-decoration: none;">
        <img src="src/img/facebook (1) 1.png" alt="">
      </a>
      <a href="https://www.instagram.com/" style="margin: 0 16px; text-decoration: none;">
        <img src="src/img/instagram 1.png" alt="">
      </a>
      <a href="https://x.com/">
        <img src="src/img/twitter 1.png" alt="">
      </a>
    </center>
  </td>
</tr>
```

---

### **Resumo da Aula 1**

* A estrutura de e-mails HTML deve ser feita com tabelas para garantir compatibilidade com todos os clientes de e-mail;
* Evitamos CSS externo e usamos CSS inline diretamente nas tags;
* A estrutura se baseia em três partes: `<thead>`, `<tbody>`, e opcionalmente `<tfoot>`;
* Elementos como `<center>`, `cellspacing="0"`, `cellpadding="0"`, e largura fixa ajudam a manter a consistência visual;
* Para alinhamentos, usamos propriedades como `align="right"` e `text-align` diretamente nas tags;
* A construção precisa ser testada em diferentes clientes de e-mail, pois a renderização pode variar entre Gmail, Outlook, etc.;
* O uso de imagens (como logos e ícones de redes sociais) é comum para garantir controle visual quando fontes e estilos falham.


### Aula 2 – Teste o e-mail

**Objetivos da aula:**

* Compreender o processo de teste de e-mails;
* Compreender a importância do teste para garantir que os e-mails sejam exibidos corretamente.

---

Durante essa aula, o professor apresentou uma plataforma chamada **[PutsMail.com](https://putsmail.com/)**. Essa ferramenta permite que testemos e visualizemos os e-mails HTML que construímos, colando o código diretamente no site para enviá-lo como uma prévia para nosso próprio e-mail.

Logo no início, enfrentamos um pequeno desafio: as **imagens utilizadas no e-mail** não aparecem corretamente ao colar o HTML no PutsMail, porque elas estão salvas **localmente** no computador, e **não estão hospedadas online**.

Para resolver isso, o professor propõe o seguinte fluxo:

1. **Criar um repositório no GitHub** (ele chamou de "servidor de estáticos");
2. Adicionar apenas os **arquivos de imagem** nesse repositório;
3. Fazer o **deploy desse repositório na Vercel**;
4. A Vercel inicialmente retorna uma tela em branco, pois o repositório não tem um `index.html`, mas é possível visualizar qualquer imagem acessando diretamente a URL com o nome da imagem no final (por exemplo, `https://servidor-static.vercel.app/facebook.png`);
5. Depois disso, basta **substituir os caminhos locais** das imagens no código HTML pelas URLs públicas da Vercel.

Essas URLs online garantem que, ao colar o código no PutsMail, as imagens sejam carregadas corretamente no e-mail enviado.

O professor também comentou que a **versão paga** do PutsMail oferece um preview mais completo e facilitado dos e-mails, mas a **versão gratuita já é suficiente** para testar a estrutura básica, visual e links.

Excelente, Matheus! Com base no **código HTML final** que você compartilhou, aqui está o **resumo completo da Aula 3 – Crie um e-mail de recuperação de senha**, estruturado em **formato Markdown**, seguindo o modelo das aulas anteriores:

---

## **Aula 3 – Crie um e-mail de recuperação de senha**

### **Objetivos da aula**

* Entender o uso de atributos em elementos HTML;
* Aplicar estilos e formatação em elementos HTML;
* Compreender as melhores práticas para construção de e-mails.

---

### **Estrutura geral do e-mail**

O e-mail foi construído utilizando uma estrutura tradicional baseada em tabelas, respeitando as limitações de compatibilidade dos clientes de e-mail. A organização ficou da seguinte forma:

1. Tag `<center>` para centralizar todo o conteúdo;
2. Tabela com `width="600"`, `cellspacing="0"` e `cellpadding="0"`;
3. Cabeçalho (`<thead>`) com título e logo;
4. Corpo principal (`<tbody>`) com mensagem e botão;
5. Rodapé (`<tfoot>`) com link e logo da empresa.

---

### **Cabeçalho – Recuperação de senha + Logo**

```html
<thead>
  <tr bgcolor="#1C54A8">
    <th style="padding-top: 24px; padding-bottom: 24px;">
      <p style="margin: 0; color: #fff; font-size: 20px; font-family: sans-serif; font-weight: normal;">
        Recuperação de senha
      </p>
    </th>
    <th style="padding-top: 28px; padding-bottom: 24px;">
      <img src="https://servidor-estaticos.vercel.app/EBAC_SHOES.png" alt="EBAC Shoes">
    </th>
  </tr>
</thead>
```

* Utilização de `bgcolor` diretamente na tag `<tr>`;
* Fontes com `sans-serif`, `font-size: 20px`, `color: white`;
* Uso de `<th>` para duas colunas alinhadas com paddings distintos;
* Logo exibida com `<img>`.

---

### **Corpo da mensagem**

```html
<td colspan="2" style="padding: 24px 40px 80px;">
  <h2 style="font-size: 16px; font-family: sans-serif;">
    <b><i>Olá, tudo bem?</i></b>
  </h2>
  <p style="margin-top: 0; padding-bottom: 24px; font-family: sans-serif; font-size: 14px;">
    Recebemos sua solicitação de recuperação de senha, para criar uma nova senha clique no botão abaixo:
  </p>
```

* Cabeçalho textual com `<h2>` + `<b>` + `<i>` para manter compatibilidade com e-mails;
* Padding utilizado em vez de margin para garantir espaçamento consistente;
* Mensagem explicativa com `font-size: 14px`.

---

### **Botão de ação: "Cadastrar nova senha"**

```html
<a href="" style="text-decoration: none; background-color: #1C54A8; color: #fff; padding: 16px 8px; border-radius: 6px; font-family: sans-serif;">
  <b><i>Cadastrar nova senha</i></b>
</a>
```

* Estilizado com `padding`, `border-radius`, `background-color` e `color`;
* Remoção do `text-decoration`;
* Texto com negrito + itálico;
* Compatível com a maioria dos clientes de e-mail.

---

### **Mensagem de validade e aviso**

```html
<p style="padding-top: 16px;">
  <i>
    <span style="color: #616161;">O link é válido por 24h</span><br><br>
    <b>Importante:</b> caso não tenha feito a solicitação, desconsidere o e-mail.
  </i>
</p>
```

* Uso de `<i>` e `<span>` para formatação de aviso;
* Destaque em negrito para o alerta;
* Cor suave para aviso de expiração (`#616161`).

---

### **Rodapé com logo e link**

```html
<tfoot>
  <tr>
    <td align="center" colspan="2" bgcolor="#1C54A8" style="padding: 16px 8px;">
      <a href="https://ebacshoes.com.br/">
        <img src="https://servidor-estaticos.vercel.app/ebac_shoes_site.png" alt="EBAC Shoes">
      </a>
    </td>
  </tr>
</tfoot>
```

* Uso de `align="center"` em vez de `<center>`;
* Cor de fundo consistente com o topo;
* Logo com link para o site oficial;
* `colspan="2"` para alinhar com a estrutura do cabeçalho.

---

### **Observações importantes**

* **`padding` funciona melhor do que `margin`** em e-mails HTML;
* O uso de **`colspan="2"`** é essencial para manter o alinhamento entre cabeçalho e corpo;
* Imagens devem estar hospedadas online (utilizou-se a Vercel como repositório);
* Muita estilização inline é necessária para garantir renderização uniforme em diferentes serviços de e-mail.

Claro! Aqui está o texto unificado da **Aula 4 – Crie um e-mail de confirmação de pedido**, seguindo exatamente a estrutura e estilo da referência que você forneceu:

---

## **Aula 4 – Crie um e-mail de confirmação de pedido**

### **Objetivos da aula**

* Dominar a estrutura e formatação dos e-mails HTML;
* Aplicar técnicas avançadas de formatação;
* Entender as melhores práticas de design de e-mail;
* Inserir seções de descrição de produto no e-mail;
* Corrigir problemas de alinhamento e compatibilidade visual.

---

### **Introdução ao projeto**

Dando continuidade ao projeto da loja virtual fictícia, nesta aula desenvolvemos o **e-mail de confirmação de pedido**. Ele é uma evolução direta do e-mail de recuperação de senha criado na aula anterior, mantendo a mesma estrutura de header, corpo e rodapé, mas introduzindo uma **seção com os detalhes do pedido**, como:

* Imagem do produto;
* Nome do produto;
* Tamanho, cor e quantidade;
* Preço e forma de pagamento;
* Frete e número do pedido.

Além disso, o botão principal da mensagem passou de **“Cadastrar nova senha”** para **“Acompanhar o pedido”**.

---

### **Dificuldades enfrentadas durante o processo**

Durante a adaptação do layout no HTML, uma tentativa de trocar as tags `<p>` por `<i>` para representar o itálico causou **problemas de espaçamento e alinhamento** entre os elementos. Os textos começaram a se sobrepor, o botão subiu e ignorou o conteúdo ao redor.

A solução foi **retornar ao uso das tags `<p>`** com estilo `font-style: italic` e, quando necessário, envolver o conteúdo com `<i>` **dentro do `<p>`**, garantindo a semântica e mantendo a formatação consistente.

---

### **Estrutura geral do e-mail**

#### 1. Cabeçalho (`<thead>`)

```html
<thead>
  <tr bgcolor="#1C54A8">
    <th align="left" style="padding: 24px 0 24px 40px;">
      <p style="margin: 0; color: #fff; font-size: 20px; font-family: sans-serif;">
        Recebemos o seu pedido
      </p>
    </th>
    <th style="padding: 28px 0 24px;">
      <img src="https://servidor-estaticos.vercel.app/EBAC_SHOES.png" alt="EBAC Shoes">
    </th>
  </tr>
</thead>
```

* A primeira célula usa `align="left"` e `padding-left: 40px` para alinhar o texto ao início;
* A segunda célula exibe o logo da EBAC Shoes.

#### 2. Mensagem principal (`<tbody>`)

```html
<tr>
  <td colspan="2" style="padding: 24px 40px 56px;">
    <h2 style="font-size: 16px; font-family: sans-serif;">
      <b><i>Olá, tudo bem ?</i></b>
    </h2>
    <p style="font-size: 14px; font-family: sans-serif;">
      <i>Recebemos o seu pedido e agora estamos aguardando a confirmação do pagamento pela operadora.</i>
    </p>
    <p style="font-size: 14px; font-family: sans-serif; padding-bottom: 16px;">
      <i>Você pode acompanhar os detalhes do pedido clicando no botão abaixo:</i>
    </p>
    <a href=""
      style="text-decoration: none; background-color: #1C54A8; color: #fff; padding: 16px 8px; border-radius: 6px; font-family: sans-serif;">
      <b><i>Acompanhar o pedido</i></b>
    </a>
  </td>
</tr>
```

* Aqui temos o título da mensagem e o botão de ação com formatação apropriada.

#### 3. Título da seção de detalhes

```html
<tr>
  <td colspan="2" style="font-family: sans-serif; font-size: 16px; padding-left: 40px;">
    <b><i>Detalhes do pedido</i></b>
  </td>
</tr>
```

* O título “Detalhes do pedido” é destacado com `<b><i>...</i></b>` e padding à esquerda.

#### 4. Seção de produto com imagem e descrição

```html
<tr>
  <td colspan="2" style="padding-left: 40px; padding-top: 16px; padding-bottom: 80px;">
    <div style="display: inline-block;">
      <img src="https://servidor-estaticos.vercel.app/produto.png" alt="">
    </div>
    <div style="display: inline-block; margin-left: 16px;">
      <p style="font-size: 14px; font-family: sans-serif; margin: 0;">
        <b>Tênis Nike</b><br>
        <b>Tamanho:</b> 40<br>
        <b>Cor:</b> Preta<br>
        <b>Quantidade:</b> 1<br>
        <b>Preço:</b> R$350,00 em 5x R$70,00<br>
        <b>Frete:</b> grátis<br>
        <b>Número do pedido:</b> 9876523453
      </p>
    </div>
  </td>
</tr>
```

* A imagem do produto fica ao lado da descrição;
* Para alinhar corretamente, usamos `display: inline-block` nas duas `<div>`;
* O espaçamento entre as divs é feito com `margin-left: 16px`.

---

### **Rodapé (`<tfoot>`)**

```html
<tfoot>
  <tr>
    <td align="center" colspan="2" bgcolor="#1C54A8" style="padding: 16px 8px;">
      <a href="https://ebacshoes.com.br/">
        <img src="https://servidor-estaticos.vercel.app/ebac_shoes_site.png" alt="EBAC Shoes">
      </a>
    </td>
  </tr>
</tfoot>
```

* Mantém o estilo do cabeçalho, com fundo azul e o logo da loja.

---

### **Resumo da Aula 4**

* A estrutura de e-mails foi reutilizada e expandida com sucesso;
* Incluímos uma seção de detalhes do pedido com imagem e dados em texto;
* Identificamos e corrigimos problemas causados por alterações de tags como `<i>` no lugar de `<p>`;
* Para alinhar imagem e descrição, usamos `display: inline-block`;
* Usamos `colspan="2"` nas linhas principais para manter alinhamento com o cabeçalho;
* Ajustamos `padding` e `margin` para evitar colagens ou desalinhamentos visuais;
* Aprendemos que até mesmo o exemplo do professor apresentou desalinhamento leve, o que reforça a necessidade de sempre testar o layout em múltiplos clientes de e-mail.

Claro! Abaixo está o **texto final da Aula 5** estruturado conforme o modelo das aulas anteriores:

---

## **Aula 5 – Crie um e-mail de promoções**

### **Objetivos da aula**

* Criar um e-mail promocional personalizado e compatível com clientes de e-mail;
* Trabalhar layout com tabelas e `<div>`s para mostrar múltiplos produtos;
* Utilizar técnicas seguras para estilização e destaque de cupons;
* Compreender limitações de tecnologias modernas como `display: grid` e `flex` em e-mails;
* Aplicar boas práticas de acessibilidade e semântica HTML em campanhas.

---

### **Introdução ao projeto**

Nesta aula, construímos um e-mail promocional da fictícia **EBAC Shoes**, contendo:

* Cabeçalho com o título “Promoções da semana” e a logo da marca;
* Mensagem introdutória e cupom com destaque visual;
* Seção de produtos em promoção, organizados lado a lado;
* Rodapé com o link para o site oficial da loja.

O layout seguiu uma estrutura reaproveitável das aulas anteriores, adaptando o conteúdo central para atender às necessidades específicas de uma campanha promocional.

---

### **Estrutura e componentes principais do e-mail**

#### 1. **Cabeçalho com título e logo**

Utilizamos a tag `<thead>` para criar o cabeçalho com duas colunas:

```html
<tr bgcolor="#1C54A8">
  <th align="left" style="padding-left: 40px;">
    Promoções da semana
  </th>
  <th>
    <img src=".../EBAC_SHOES.png" alt="EBAC Shoes">
  </th>
</tr>
```

* A cor azul escura define o fundo do cabeçalho.
* O texto está alinhado à esquerda, enquanto o logo fica à direita.
* Toda a linha é envolta pela tag `<thead>` para garantir clareza estrutural.

---

#### 2. **Mensagem promocional com cupom de desconto**

Dentro do `<tbody>`, temos uma mensagem introdutória seguida por um destaque com o cupom promocional:

```html
<h2>
  <b><i>Temos promoções exclusivas para você</i></b>
</h2>

<p>
  Separamos algumas promoções exclusivas... <b>ganhar 10% OFF e frete grátis!</b>
</p>

<span style="...">
  <b>EBAC_S_10</b>
</span>

<span style="...">Válido até 10/06/2025</span>
```

* O cupom foi estilizado com `border`, `padding`, `border-radius` e `font-size` para criar um efeito de botão visual.
* Em vez de usar uma imagem, o professor optou por estilizar diretamente a `tag <span>`, aumentando a compatibilidade.
* A validade do cupom aparece logo abaixo com tamanho reduzido e cor cinza.

---

#### 3. **Listagem de produtos promocionais**

Por limitações de CSS moderno em e-mails, **não foi usado `display: grid`**. Em vez disso, optou-se por `inline-block` com `max-width`, criando uma grade visual de produtos.

Cada produto segue a estrutura:

```html
<div style="display: inline-block; max-width: 127px; width: 100%; padding-bottom: 24px;">
  <a href="..." style="text-decoration: none; color: #000;">
    <img src="...produto.png">
    <div>
      <h3>Tênis Nike</h3>
      <span style="text-decoration: line-through;">R$ 350,00</span>
      <p>R$ 200,00<br>4x de R$ 50,00</p>
    </div>
  </a>
</div>
```

* O `a` envolve imagem e descrição para tornar o card inteiro clicável.
* `text-decoration: none` e `color: #000` evitam o comportamento padrão de links.
* Os preços usam `<span>` com `line-through` para mostrar o valor antigo e `<p>` para destacar o novo.
* O `padding-bottom: 24px` garante espaçamento vertical uniforme entre os cards.

---

#### 4. **Rodapé com chamada para o site**

Ao final, o rodapé contém um link com imagem levando ao site da EBAC Shoes:

```html
<tfoot>
  <tr bgcolor="#1C54A8">
    <td align="center" colspan="2">
      <a href="https://ebacshoes.com.br/">
        <img src=".../ebac_shoes_site.png" alt="EBAC Shoes">
      </a>
    </td>
  </tr>
</tfoot>
```

---

### **Resumo da Aula 5**

* Estruturamos um e-mail promocional compatível com clientes como Gmail e Outlook;
* O cupom foi estilizado manualmente com `span`, `padding`, `border`, `color` e `font-size`;
* Produtos foram organizados com `inline-block` e `max-width`, mantendo o layout fluido;
* Usamos `<table>`, `<div>`, `<span>` e `inline CSS` por segurança e compatibilidade;
* Evitamos `display: grid` ou `flexbox`, pois podem não funcionar corretamente;
* A validação do layout foi feita com testes reais por e-mail, garantindo exibição correta;
* O módulo exigiu atenção a detalhes e domínio de boas práticas em HTML retrô para e-mail marketing.

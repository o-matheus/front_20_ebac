# Módulo 20 - Construa emails com HTML

## Menu 
[Aula 1 - Crie o primeiro e-mail](#aula-1--crie-o-primeiro-e-mail)  
[Aula 2 - Teste o e-mail](#aula-2--teste-o-e-mail)  
[Aula 3 - Crie um e-mail de recuperação de senha](#aula-3--crie-um-e-mail-de-recuperação-de-senha)  
[Aula 4 -](#aula-)  
[Aula 5 -](#aula-)  

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

Perfeito, Matheus! Aqui está a anotação da **Aula 2 – Teste o e-mail**, revisada com clareza e ortografia ajustadas, mantendo sua linguagem e raciocínio:

---

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

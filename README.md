# Módulo 20 - Construa emails com HTML

## Menu 
[Aula 1 - Crie o primeiro e-mail](#aula-1--crie-o-primeiro-e-mail)  
[Aula 2 - Teste o e-mail](#aula-2--teste-o-e-mail)  
[Aula 3 -](#aula-)  
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

# **Automação de Testes com Cypress**

## **Introdução**
A automação de testes é uma parte crucial do desenvolvimento de software moderno. Com o Cypress, uma poderosa ferramenta de teste de front-end, você pode automatizar testes de interface de usuário (UI) de forma eficiente e confiável. Neste artigo, vou detalhar como você pode usar o Cypress para criar testes automatizados, seguindo um projeto prático que você pode adicionar ao seu portfólio no GitHub.

## **1. Configuração do Ambiente**
Antes de começar a escrever testes, você precisa configurar o Cypress em seu ambiente de desenvolvimento.

### **1.1. Instalação**
Instale o Cypress via npm com o seguinte comando:
```bash
npm install cypress --save-dev
```

### **1.2. Abertura do Cypress**
Após a instalação, abra o Cypress com:
```bash
npx cypress open
```

## **2. Estrutura de Testes**
O Cypress organiza os testes em arquivos de especificação dentro da pasta `cypress/integration`.

### **2.1. Criando um Teste**
Crie um novo arquivo de teste, por exemplo, `login_spec.js`, e comece a escrever seu primeiro teste.

### **2.2. Exemplo de Teste de Login**
```javascript
describe('Teste de Login', () => {
    it('Deve logar com sucesso', () => {
        cy.visit('https://example.com/login')
        cy.get('input[name=username]').type('usuario')
        cy.get('input[name=password]').type('senha')
        cy.get('form').submit()
        cy.url().should('include', '/dashboard')
    })
})
```

## **3. Seletores e Ações**
O Cypress fornece uma API para interagir com elementos da página, como clicar em botões ou digitar em campos de texto.

### **3.1. Selecionando Elementos**
Use `cy.get()` ou `cy.find()` para selecionar elementos DOM.

### **3.2. Executando Ações**
Após selecionar um elemento, você pode executar ações como `click()`, `type()`, `check()`, entre outras.

## **4. Assertions**
As asserções são verificações que confirmam se o comportamento esperado ocorreu.

### **4.1. Exemplo de Assertion**
```javascript
cy.get('.alert').should('contain', 'Login realizado com sucesso')
```

## **5. Testes Avançados**
À medida que você se familiariza com o básico, pode começar a explorar recursos mais avançados do Cypress.

### **5.1. Testes de API**
Você pode testar APIs diretamente com comandos como `cy.request()`.

### **5.2. Custom Commands**
Crie comandos personalizados para reutilizar lógicas de teste com `Cypress.Commands.add()`.

## **6. CI/CD Integration**
Integre seus testes Cypress com sistemas de integração contínua/entrega contínua (CI/CD) para automatizar a execução de testes.

### **6.1. Exemplo de Integração com GitHub Actions**
```yaml
name: Cypress Tests

on: [push]

jobs:
  cypress-run:
    runs-on: ubuntu-latest
    steps:
    - name: Checkout
      uses: actions/checkout@v2
    - name: Cypress run
      uses: cypress-io/github-action@v2
      with:
        start: npm start
        wait-on: 'http://localhost:3000'
```

## **Conclusão**
Com o Cypress, você pode criar testes robustos e confiáveis para suas aplicações web. Ao adicionar esses testes ao seu repositório no GitHub, você não apenas demonstra suas habilidades técnicas, mas também contribui para a qualidade e confiabilidade do software que desenvolve.

Espero que este artigo tenha sido útil e que você se sinta confiante para implementar testes automatizados com Cypress.

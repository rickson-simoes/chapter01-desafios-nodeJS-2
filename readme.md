<h1>Aplicação para estudar e adaptar melhores middlewares para a aplicação.</h1>

[![Package][nodemon-image]][nodemon-url] 
[![Technology][node-image]][node-url] 


[nodemon-url]: https://www.npmjs.com/package/nodemon
[nodemon-image]: https://img.shields.io/badge/Nodemon-green?style=for-the-badge&logo=Nodemon&logoColor=black

[node-url]: https://nodejs.org/
[node-image]: https://img.shields.io/badge/NodeJS-green?style=for-the-badge&logo=Node-dot-js&logoColor=black

---
## Instruções para uso:

1º - yarn install

2º - yarn dev

3º - yarn test (Para verificar se todas as tarefas foram executadas.)

---

### Essa será uma aplicação para criar um usuário e gerenciar as tarefas, manipulando os objetos. (em inglês *todos*). Será permitida a criação de um usuário com `name` e `username` , bem como fazer o CRUD de *todos*:

- Criar um novo *todo*;
- Listar todos os *todos*;
- Alterar o `title` e `deadline` de um *todo* existente;
- Marcar um *todo* como feito;
- Excluir um *todo*;

### Middlewares melhorados/criados:

#### `checksExistsUserAccount`
Esse middleware é responsável por receber o username do usuário pelo header e validar se existe ou não um usuário com o username passado. Caso exista, o usuário deve ser repassado para o request e a função next deve ser chamada.

---

#### `checksCreateTodosUserAvailability`
Esse middleware deve receber o **usuário** já dentro do request e chamar a função next apenas se esse usuário ainda estiver no **plano grátis e ainda não possuir 10 *todos* cadastrados** ou se ele **já estiver com o plano Pro ativado**. 

---

#### `checksTodoExists`
Esse middleware deve receber o **username** de dentro do header e o **id** de um *todo* de dentro de `request.params`. Você deve validar o usuário, validar que o `id` seja um uuid e também validar que esse `id` pertence a um *todo* do usuário informado.

Com todas as validações passando, o *todo* encontrado deve ser passado para o `request` assim como o usuário encontrado também e a função next deve ser chamada.

---

#### `findUserById`
Esse middleware possui um funcionamento semelhante ao middleware `checksExistsUserAccount` mas a busca pelo usuário deve ser feita através do **id** de um usuário passado por parâmetro na rota. Caso o usuário tenha sido encontrado, o mesmo deve ser repassado para dentro do `request.user` e a função next deve ser chamada.
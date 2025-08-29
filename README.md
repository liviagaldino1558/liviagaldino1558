Olá! 👋 Sou Livia Galdino 


 <a href="https://www.linkedin.com/in/livia-galdino-07523023a">LinkedIn</a>

# 📋 Lista de Tarefas (To-Do List)

Aplicação web simples em **HTML, CSS e JavaScript** que permite ao usuário visualizar uma lista de tarefas, marcar como concluídas e removê-las.  
O foco é treinar conceitos de **JavaScript para front-end**, como manipulação do DOM e lógica de programação.

---

## 🚀 Funcionalidades

- Marcar tarefas como concluídas clicando sobre elas;  
- Remover tarefas da lista;  
- Lista inicial de tarefas predefinidas;  
- Interface simples e intuitiva.  

---

## 🛠️ Tecnologias utilizadas

- **HTML5**  
- **CSS3**  
- **JavaScript (ES6+)**

---

## 📚 O que aprendi

- **Manipulação do DOM:** criar, atualizar e remover elementos dinamicamente;  
- **Eventos:** usar `onclick` para interação com a lista;  
- **Arrays e objetos:** armazenar tarefas como objetos em um array;  
- **Renderização Condicional:** alterar a aparência das tarefas concluídas (`text-decoration: line-through`);  
- **Estilização básica:** aplicar CSS para deixar a lista visualmente agradável.

▶️  executar o projeto

<!DOCTYPE html>
<html lang="pt-BR">
<head>
  <meta charset="UTF-8">
  <title>Lista de Tarefas</title>
  <style>
    ul {
      list-style: none;
      padding: 0;
    }
    li {
      display: flex;
      justify-content: space-between;
      align-items: center;
      margin-bottom: 10px;
      background: #f1f1f1;
      padding: 10px;
      border-radius: 5px;
    }
    li span {
      cursor: pointer;
    }
    li button {
      background: red;
      color: white;
      border: none;
      padding: 5px 10px;
      border-radius: 3px;
      cursor: pointer;
    }
    .concluida {
      text-decoration: line-through;
    }
    .assinatura {
      margin-top: 20px;
      font-weight: bold;
      font-size: 1.1em;
    }
  </style>
</head>
<body>

  <ul id="listaTarefas"></ul>

  <div class="assinatura">Livia Galdino</div>

  <script>
    const tarefas = [
      { id: 1, texto: 'Aprender HTML', concluida: false },
      { id: 2, texto: 'Aprender CSS', concluida: false },
      { id: 3, texto: 'Aprender JavaScript', concluida: false },
      { id: 4, texto: 'Aprender Inglês', concluida: false },
      { id: 5, texto: 'Aprender Francês', concluida: false }
    ];

    function renderizarTarefas() {
      const lista = document.getElementById('listaTarefas');
      lista.innerHTML = '';

      tarefas.forEach(tarefa => {
        const li = document.createElement('li');

        const span = document.createElement('span');
        span.textContent = tarefa.texto;
        if (tarefa.concluida) span.classList.add('concluida');
        span.onclick = () => {
          tarefa.concluida = !tarefa.concluida;
          renderizarTarefas();
        };

        const button = document.createElement('button');
        button.textContent = 'X';
        button.onclick = () => {
          const index = tarefas.findIndex(t => t.id === tarefa.id);
          tarefas.splice(index, 1);
          renderizarTarefas();
        };

        li.appendChild(span);
        li.appendChild(button);
        lista.appendChild(li);
      });
    }

    renderizarTarefas();
  </script>

</body>
</html>

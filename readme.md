## Comando de banco de dados

### Criar Database
* Database: espaço onde pode-se criar tabelas (campos onde vão ficar armazenados as informações do sistemas)
```
create database NOME_DATABASE
```

### Para executar qualquer comando no Workbanch:
```
Ctrl + Enter
```

### Selecionar database:
```
use NOME_DATABASE
```
<hr>

### Exemplo: Projeto site Ecommerce

* Tabela de usuários
* Tabela de produtos
* Tabela de carrinho de compras

### Criar tabela de usuários
```
create table usuarios(
    id int not null auto_autoincrement,
    nome varchar(120) not null,
    email varchar(120) not null,
    senha varchar(120) not null,
    primary key(id)
);
```

* id: identificador de registro
* not null: diz que o campo não pode ser nulo, precisa ser preenchido
* auto_autoincrement: soma +1 no último registro de id, ou seja, não terá id repetida
* varchar(120): campo de texto com 120 caracteres
* vírgula em todas as linhas menos na última (se não vai dar erro) 

### Criar tabela de produtos

´´´
create table produtos(
    id int not null auto_autoincrement,
    modelo varchar(120),
    nome_produto varchar(120) not null,
    valor float not null,
    primary key(id)
);
´´´

* float: possibilita ponto e vírgula nos números

### Criar tabela de carrinho:

```
crate table carrinho(
    id int not null auto_autoincrement,
    id_usuario int not null,
    id_produto int not null,
    primary key(id),
    foreign key(id_usuario) references usuario(id),
    foreign key(id_produto) references produto(id)
);
```

* foreign key: chave estrangeira que recebe referência de outra tabela
* references: atributo para definir a tabela e o campo estrangeiro

### Inserir usuários:
```
insert into usuario(nome, email, senha) values('tata','tata','tata')
```

### Inserir produtos:
```
insert into produto(modelo, nome, valor) values('nike','camiseta','129,90')
```

### Inserir carrinho:
```
insert into carrinho(id_usuario, id_produto) value(43, 234);
```

### Listar todas as informações de usuários:
```
select * from usuarios;
```

### Listar somente os nomes dos usuários:
```
select nome from usuarios;
```

### Listar nome e email dos usuarios:
```
select name, email from usuarios;
```

### listar usuarios pelo id:
```
select * from usuarios where id = 23;
```

### Verificar produtos no carrinho pelo id do usuario:
```
select p.name
from produtos p, carrinho c
where c.id_usuario = 23 AND p.id = c.id_produto;
```
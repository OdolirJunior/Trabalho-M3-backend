## Trabalho M3 (BACK-END)

### Banco de dados: 

Para utilizar o sistema com as mesmas configurações de banco de dados (MySQL) deve ser executado os seguintes comandos: <br/> 

1° ```CREATE DATABASE PUBLIC; ```<br/><br/>
2° ```CREATE TABLE public.users (	
      id INT NOT NULL AUTO_INCREMENT, 
      username VARCHAR(255) NOT NULL,
      senha VARCHAR(255) NOT null,
      PRIMARY KEY (id) )  ENGINE = InnoDB DEFAULT CHARACTER SET = utf8;```<br/><br/>
3° ```CREATE TABLE public.group_todos ( 
      id INT NOT NULL AUTO_INCREMENT, 
      title VARCHAR(255) NOT NULL,
      username VARCHAR(255),
      PRIMARY KEY (id) ) ENGINE = InnoDB DEFAULT CHARACTER SET = utf8;```<br/><br/>

4° ```CREATE TABLE public.todos (
	id INT NOT NULL AUTO_INCREMENT,
	title VARCHAR(45) NOT NULL, 
	content VARCHAR(45) NULL, 
	status TINYINT NOT NULL, 
	group_id int, 
	created_at DATETIME NULL, 
	updated_at DATETIME NULL, 
	FOREIGN KEY (group_id) REFERENCES group_todos(id)
	ON DELETE CASCADE,
	PRIMARY KEY (id)
) ENGINE = InnoDB DEFAULT CHARACTER SET = utf8;```<br/><br/>

5° ```CREATE TABLE public.todos_items (
 	id INT NOT NULL AUTO_INCREMENT,
	title VARCHAR(45) NOT NULL,
	content VARCHAR(45) NULL, 
	todo_id int, 
	FOREIGN KEY (todo_id) REFERENCES todos(id)
	ON DELETE CASCADE,
	primary key (id)
) ENGINE = InnoDB DEFAULT CHARACTER SET = utf8;```<br/><br/>

6° ```INSERT INTO `public`.`users` (`username`, `senha`) VALUES ('admin', 'admin');```<br/><br/>
       
No banco, o usuário é "root" e senha é vazia.

### Iniciar a aplicação:
Após criar o banco de dados, 
para iniciar a aplicação basta rodar o comando `mvn spring-boot:run` para 
linux ou `mvnw spring-boot:run` para windows.

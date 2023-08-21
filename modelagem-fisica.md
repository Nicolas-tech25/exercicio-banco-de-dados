## Criação do banco *tecinternet_escola_seunome**


```SQL
CREATE TABLE cursos(
    id INT NOT NULL PRIMARY KEY AUTO_INCREMENT,
    titulo VARCHAR(30) NOT NULL
    carga_horaria TINYINT NOT NULL,
    professor_id TINYINT  NULL
);
```

```SQL
CREATE TABLE professores(
    id TINYINT NOT NULL PRIMARY KEY AUTO_INCREMENT,
    nome VARCHAR(50) NOT NULL,
   	area_atuacao ENUM('design', 'desenvolvimento', 'infra') NOT NULL, 
    carga_horaria TINYINT NOT NULL,
    curso_id TINYINT NOT NULL
);
```

```SQL
CREATE TABLE alunos(
    id TINYINT NOT NULL PRIMARY KEY AUTO_INCREMENT,
    nome VARCHAR(50) NOT NULL,
    data_nascimento DATE NOT NULL,
    primeira_nota DECIMAL(4,2),
    segunda_nota DECIMAL(4,2),
    curso_id TINYINT NOT NULL,
    CONSTRAINT fk_cursos FOREIGN KEY (curso_id)  REFERENCES cursos(id)
);
```
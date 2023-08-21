 http://localhost/phpmyadmin/index.php?route=/sql&pos=0&db=tecinternet_escola_seunome&table=alunos 
### ETAPA 1

![modelagem-logica](images/modelagem-logica-etapa-1.png)

## Criação do banco *tecinternet_escola_seunome**

### ETAPA 2

## Tabela cursos, professores e alunos
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

## Chaves estrangeiras

# Índices para tabela `alunos`

ALTER TABLE `alunos`
  ADD PRIMARY KEY (`id`),
  ADD KEY `fk_cursos_alunos` (`curso_id`);


# Índices para tabela `cursos`

ALTER TABLE `cursos`
  ADD PRIMARY KEY (`id`),
  ADD KEY `fk_cursos_professores` (`professor_id`);


# Índices para tabela `professores`

ALTER TABLE `professores`
  ADD PRIMARY KEY (`id`);



##  Adicionando Cursos

```SQL
INSERT INTO `cursos` (`id`, `titulo`, `carga_horaria`, `professor_id`) VALUES
(1, 'Front-End', 40, 5),
(2, 'Back-End', 80, 4),
(3, 'UX/UI Design', 30, 3),
(4, 'Figma', 10, 2),
(5, 'Redes de Computadores', 100, 1);
```

![modelagem-logica](images/cursos.PNG)

## Adicionando os Professores

```SQL
INSERT INTO `professores` (`id`, `nome`, `area_atuacao`, `curso_id`) VALUES
(1, 'Jason', 'infra', 5),
(2, 'Mestre Splinter', 'design', 4),
(3, 'Shifu', 'design', 3),
(4, 'Sócrates', 'desenvolvimento', 2),
(5, 'Tomas', 'desenvolvimento', 1);
```

![modelagem-logica](images/professores.PNG)

## Adicionando Alunos

```SQL
INSERT INTO `alunos` (`id`, `nome`, `data_nascimento`, `primeira_nota`, `segunda_nota`, `curso_id`) VALUES
(4, 'Maria Silva', '0000-00-00', 8.00, 9.00, 1),
(5, 'Ana Santos', '0000-00-00', 7.00, 6.00, 2),
(6, 'Sofia Rodrigues', '0000-00-00', 9.00, 10.00, 3),
(7, 'Laura Costa', '0000-00-00', 6.00, 7.00, 4),
(8, 'Beatriz Oliveira', '0000-00-00', 9.00, 8.00, 5),
(9, 'João Santos', '0000-00-00', 5.00, 9.00, 5),
(10, 'Pedro Almeida', '0000-00-00', 8.00, 9.00, 4),
(11, 'Miguel Pereira', '0000-00-00', 5.00, 6.00, 3),
(12, 'Lucas Fernandes', '0000-00-00', 7.00, 6.00, 2),
(13, 'Guilherme Ribeiro', '0000-00-00', 6.00, 5.00, 1);
```

![modelagem-logica](images/alunos.PNG)

### ETAPA 3

## Consulta de alunos que nasceram antes de 2009

```SQL
SELECT alunos.nome as aluno, data_nascimento.alunos as aluno
FROM  alunos INNER JOIN data_nascimento.alunos
ON alunos.aluno_id = alunos.id;
```
# aula_2-SQL

CREATE TABLE alunos (
  id SERIAL PRIMARY KEY,
  nome TEXT NOT NULL,
  turma TEXT NOT NULL,
  curso TEXT NOT NULL
);

CREATE TABLE cursos (
  id SERIAL PRIMARY KEY,
  nome TEXT NOT NULL,
  duracao_anos INT
);

CREATE TABLE matriculas (
  id SERIAL PRIMARY KEY,
  aluno_id INT REFERENCES alunos(id) ON DELETE CASCADE,
  curso_id INT REFERENCES cursos(id) ON DELETE CASCADE,
  data_matricula DATE DEFAULT CURRENT_DATE
);

INSERT INTO alunos (nome, turma, curso)
VALUES ('Thulio', 'T15', 'Ciências da computação'),
       ('Henrique', 'T15', 'Engenharia de software'),
       ('Isabela', 'T15', 'Egenharia da computação'),
       ('Reimar', 'T15', 'Engenharia da computação'),
       ('João', 'T15', 'Ciências da computação'),
       ('Hugo', 'T15', 'Adm Tech'),
       ('Paulo', 'T15', 'Sistema de informação'),
       ('Rafofo', 'T15', 'Engenharia da computação'),
       ('Schimt', 'T15', 'Engenharia de software'),
       ('Antonio', 'T15', 'Engenharia de software');

       INSERT INTO cursos (nome, duracao_anos)
VALUES ('Engenharia da computação', 4),
       ('Adm Tech', 4),
       ('Sistema de informação', 4),
       ('Egenharia de software', 4),
       ('Ciências da computação', 4);


       INSERT INTO matriculas (aluno_id, curso_id)
VALUES (1, 5),
       (2, 4),
       (3, 1),
       (4, 1),
       (5, 5),
       (6, 2),
       (7, 3),
       (8, 1),
       (9, 4),
       (10, 4);


       SELECT * FROM alunos;
       SELECT * FROM cursos;
       
       SELECT a.nome AS aluno, c.nome AS curso, m.data_matricula
FROM matriculas m
JOIN alunos a ON m.aluno_id = a.id
JOIN cursos c ON m.curso_id = c.id;

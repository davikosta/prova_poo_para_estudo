# Texto OCR da prova de POO

## PrintExercicio_page-0001

Curso: Tecnólogo em Análise e Desenvolvimento de Sistemas

Disciplina: Programação Orientadas a Objetos Turma: 2026.1 POO
Professor: Leandro Costa Souza Data: 08/09/2026
Aluno:

Prova

Orientações para a avaliação (Duração: 1h 40min)

1. Confira e assine sua avaliação;
2. Na avaliação deverá ser utilizada caneta apenas nas cores
azul ou preta;

4. Respostas deverão ser escritas no local designado para cada
questão;
5. A interpretação das questões faz parte da avaliação;

3. Questões respondidas à lápis não darão direito a recorreção;

6.

. Em questões objetivas deve ser preenchido todo o espaço

para a marcação;

. Não é permitido qualquer tipo de consulta;

. Não é permitida a troca de materiais entre colegas;

. Não é permitido o uso de equipamentos eletrônicos;
. Não é permitido destacar folhas da avaliação;

. Não é permitido conversa entre os avaliados.

12. Não é permitido utilizar folhas extras.

Clínica Veterinária “Pata Amiga”

Contexto e Cenário da Atividade

A clínica “Pata Amiga” quer um sistema desktop Java + JavaFX em três camadas, dados em memória, login COMUM/
ADMIN e auditoria (quem criou/alterou e quando). Entidades: Usuario (login único 4-20, senha >6, perfil), Tutor (nome,
CPF 11 único), Animal (nome, espécie, idadeMeses >0, tutor obrigatório), Veterinario (nome, CRMV único, especiali-
dade, situação), Consulta (animal, veterinario, dataHora futura, motivo, status). Regras: R1 sem sobreposição de 30 min
por veterinário; R2 máx. 2 AGENDADAS por animal/dia;

* RI significa: o mesmo veterinário não pode ter duas consultas cujo intervalo se sobreponha considerando uma janela de

30 minutos.

* Exemplo: se a Dra. Paula tem consulta às 10:00, não se pode agendar outra para ela entre 09:31 e 10:29 — só a partir
das 10:30. Cada consulta ocupa um bloco de 30 min na agenda daquele veterinário. Se houver sobreposição, o serviço
lança ConsultaInvalidaException e a operação é abortada.

* R2 significa: o mesmo animal pode ter no máximo 2 consultas com status AGENDADA no mesmo dia.

* Exemplo: o Rex já tem 2 consultas agendadas para 01/10 — uma terceira nesse dia é bloqueada com LimiteConsulta-

sException. Consultas REALIZADAS ou CANCELADAS não contam para o limite.

Telas do sistema

* Login MyName |, v Nome

Password set

Figura 1: Tela de Login

» Especie
q Tutor [Ana - 11122233344 |V]

Figura 3: Tela de Cadastro de Animais

* Login newlogin

* Password Pete 4 Nome “Ana Souza ,

* Perfil c [7] * cpr 1122233344

O Telefone 1999990000 ,

Figura 4: Tela de Cadastro de Tutores

Figura 2: Tela de Cadastro de Usuario

Página 1 de 10

---

## PrintExercicio_page-0002

Prova - 08/09/2026

2 Nome Dra Paula + Animal [Rex Ana
* CRMV BA-1234 * Veterinario [Dra Paula |v]

& Especialidade[Clinica geral [| O Data Hora (01/11/2026 10:00 ,

Figura 5: Tela de Cadastro de Veterinarios Figura 6: Tela de Agenda da Consulta
o Entidade [Consulta |V]
E Periodo 01/09/2026 , 30/09/2026

Q Filtrar

Figura 7: Tela de Auditoria

Questões

1) [ [1,5] Classe abstrata mãe - Escreva o código da classe abstrata AbstractModel com generics no id
(AbstractModel<ID>): atributos id, createdAt, createdBy, updatedAt, updatedBy, construtores, getters/setters
e um método abstrato ou concreto de validação básica. Use LocalDate Time para datas.

2026.1 POO Página 2 de 10 Programação Orientadas a Objetos

---

## PrintExercicio_page-0003

Prova - 08/09/2026

2) [. [1,5] Camada de modelo completa - Desenhe o diagrama UML e escreva o código das 5 classes Usuario, Tutor,
Animal, Veterinario, Consulta herdando de AbstractModel<ID>, com atributos próprios, enums necessários
(Perfil, Especie, StatusConsulta, Especialidade), construtor que chama super, getters/setters e relacionamen-
tos. Não omita tipos.

2026.1 POO Página 3 de 10 Programação Orientadas a Objetos

---

## PrintExercicio_page-0004

Prova - 08/09/2026

2026.1 POO Página 4 de 10 Programação Orientadas a Objetos

---

## PrintExercicio_page-0005

Prova - 08/09/2026

3) [1,5] Interfaces DAO e Service - Escreva as interfaces genéricas Generi cDAO<T> e GenericService<T> com
as 5 operações CRUD (salvar, buscarPorld, listarTodos, atualizar, remover), usando generics com limite T extends
AbstractModel<ID>. Explique em 2 linhas por que o limite é necessário.

2026.1 POO Página 5 de 10 Programação Orientadas a Objetos

---

## PrintExercicio_page-0006

Prova - 08/09/2026

4) [2,0] DAO genérico em memória - Escreva a classe Generi cDAOImpl<T extends AbstractModel<ID>>
implements GenericDAO<T> usando HashMap<ID, T>. Implemente os 5 métodos definidos na interface. A busca por id
deve retornar o objeto ou uma exceção.

2026.1 POO Página 6 de 10 Programação Orientadas a Objetos

---

## PrintExercicio_page-0007

Prova - 08/09/2026

5) [ . [2,0] Serviço genérico + regras
a) [  |1,0] Escreva GenericServiceImpl<T> que recebe GenericDAO<T> no construtor, implementa os 5 métodos
delegando ao DAO e preenche createdat/createdBy ao salvar e updatedat /updatedBy ao atualizar (receba

usuarioLogado como parâmetro).

2026.1 POO Página 7 de 10 Programação Orientadas a Objetos

---

## PrintExercicio_page-0008

Prova - 08/09/2026

5) [ . [2,0] Serviço genérico + regras
b) [ |1,0] Escreva Consultaservice extends GenericServiceImpl<Consulta> com os métodos
validarConflitoAgenda( consulta) e validarLimiteDiario(consulta) aplicando RlI e R2 e lançando
ConsultaInvalidaException/ LimiteConsultasException.

2026.1 POO Página 8 de 10 Programação Orientadas a Objetos

---

## PrintExercicio_page-0009

Prova - 08/09/2026

6) [. [1,5] Controller exemplo - Escreva o ConsultaController para a tela da Figura 6 e que dependa SOMENTE
da interface GenericService<Consulta> (ou ConsultaService) respeitando a definição de comunicação entre as
camandas. Contenha o método salvar( consulta, usuarioLogado) que monta a chamada ao serviço dentro de try/
catch das exceções da Questão 5)a) e exibe Alert de sucesso/erro. Mostre que a instância consulta inteira é passada ao
serviço, não atributos soltos.

2026.1 POO Página 9 de 10 Programação Orientadas a Objetos

---

## PrintExercicio_page-0010

Prova - 08/09/2026

Apresentacao Boundary Negocio Control Persistencia Entity
Modelo

' ConsultaController ConsultaService
Usuario
1

| preenche dados da consulta

new consulta

Consulta

salvar(consulta, usuarioLogado) 1

1
1
1
1
1
1
1
1
1
1

validarConflitoAgenda(consulta)

1
| validarLimiteDiario(consulta)

! validarDataFuturaEVeterinarioAtivo(consulta) |

lt j Iregras atendidas]

consulta sal

»

mensagem del sucesso

[regra violada]
h

ConsultaInvalidaException ou LimiteConsultasException.

alerta de erro)

<

Figura 8: Exemplificação de comunicação entre as camadas

2026.1 POO Página 10 de 10 Programação Orientadas a Objetos

---


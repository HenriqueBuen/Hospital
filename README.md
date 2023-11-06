# Hospital


Um pequeno hospital local busca desenvolver um novo sistema que atenda melhor às suas necessidades. Atualmente, parte da operação ainda se apoia em planilhas e arquivos antigos, mas espera-se que esses dados sejam transferidos para o novo sistema assim que ele estiver funcional. Neste momento, é necessário analisar com cuidado as necessidades desse cliente e sugerir uma estrutura de banco de dados adequada por meio de um Diagrama Entidade-Relacionamento.



Mãos a Obra
Analise a seguinte descrição e extraia dela os requisitos para o banco de dados:

O hospital necessita de um sistema para sua área clínica que ajude a controlar consultas realizadas. Os médicos podem ser generalistas, especialistas ou residentes e têm seus dados pessoais cadastrados em planilhas digitais. Cada médico pode ter uma ou mais especialidades, que podem ser pediatria, clínica geral, gastroenterologia e dermatologia. Alguns registros antigos ainda estão em formulário de papel, mas será necessário incluir esses dados no novo sistema.

Os pacientes também precisam de cadastro, contendo dados pessoais (nome, data de nascimento, endereço, telefone e e-mail), documentos (CPF e RG) e convênio. Para cada convênio, são registrados nome, CNPJ e tempo de carência.

As consultas também têm sido registradas em planilhas, com data e hora de realização, médico responsável, paciente, valor da consulta ou nome do convênio, com o número da carteira. Também é necessário indicar na consulta qual a especialidade buscada pelo paciente.

Deseja-se ainda informatizar a receita do médico, de maneira que, no encerramento da consulta, ele possa registrar os medicamentos receitados, a quantidade e as instruções de uso. A partir disso, espera-se que o sistema imprima um relatório da receita ao paciente ou permita sua visualização via internet.




![Untitled Diagram drawio](https://github.com/HenriqueBuen/Hospital/assets/142261748/31629b08-75f2-488c-9a24-5cfd9b50eda7)





Projeto de Sistema de Gerenciamento de Clínicas Médicas

Este é um projeto de um sistema de gerenciamento de clínicas médicas que utiliza um banco de dados MySQL para armazenar informações sobre pacientes, convênios, especialidades médicas, médicos, consultas e receitas médicas.
Estrutura de Dados
Banco de Dados MySQL

    Central de Atendimento
        Tabela: central_atendimento
            Campos:
                id (Chave Primária)
                nome
    Cadastro do Paciente
        Tabela: pacientes
            Campos:
                id (Chave Primária)
                nome
                data_nascimento
                rg
                endereço
                telefone
                email
                cpf
    Convênio
        Tabela: convenios
            Campos:
                id (Chave Primária)
                nome
                tempo_carencia
                cnpj
    Especialidades
        Tabela: especialidades
            Campos:
                id (Chave Primária)
                nome
    Médicos
        Tabela: medicos
            Campos:
                id (Chave Primária)
                nome
                especialidade_id (Chave Estrangeira para a tabela especialidades)
    Consultas
        Tabela: consultas
            Campos:
                id (Chave Primária)
                data
                hora
                valor_particular
                convenio_id (Chave Estrangeira para a tabela convenios)
                paciente_id (Chave Estrangeira para a tabela pacientes)
                medico_id (Chave Estrangeira para a tabela medicos)
    Receita Médica
        Tabela: receitas_medicas
            Campos:
                id (Chave Primária)
                consulta_id (Chave Estrangeira para a tabela consultas)
                medicamento
                quantidade
                instrucoes_uso
                relatorio_consulta



      
               
# Sistema de Gerenciamento Hospitalar

Este repositório contém um esquema de banco de dados e um script SQL para um Sistema de Gerenciamento Hospitalar. O sistema é projetado para gerenciar pacientes, médicos, consultas e agora inclui o módulo de gerenciamento de internações.
Contexto

Um pequeno hospital local busca desenvolver um novo sistema que atenda melhor às suas necessidades operacionais. Atualmente, algumas operações ainda dependem de planilhas e arquivos antigos. É essencial analisar cuidadosamente os requisitos do cliente e sugerir uma estrutura de banco de dados apropriada por meio de um Diagrama Entidade-Relacionamento (DER).
Tarefa

Nesta atividade, expandimos o sistema de gerenciamento hospitalar para incluir o gerenciamento de internações. Aqui está um resumo dos requisitos:

    Para cada internação, precisamos registrar a data de admissão, data prevista de alta, data efetiva de alta e uma descrição textual dos procedimentos planejados.
    Cada admissão de paciente deve estar associada a um quarto, incluindo número do quarto e tipo de quarto (apartamento, quarto duplo ou enfermaria).
    Cada tipo de quarto deve ter uma descrição e uma taxa diária.
    O sistema também deve rastrear os profissionais de enfermagem responsáveis por cada paciente internado. Cada enfermeiro deve ter um nome, CPF e número de registro no conselho de enfermagem (CRE).
    As internações estão naturalmente associadas aos pacientes, que podem ser internados várias vezes no hospital.
    Cada internação deve ter um único médico responsável.

Passos Realizados

    Começamos analisando os requisitos para o módulo de gerenciamento de internações.
    Estendemos o Diagrama Entidade-Relacionamento (DER) existente para incorporar as novas entidades e seus relacionamentos com as entidades existentes.
    Projetamos o DER para incluir entidades como "Internações", "Quartos", "Tipos de Quartos" e "Profissionais de Enfermagem", estabelecendo os relacionamentos necessários entre essas entidades e as entidades anteriormente definidas, como "Pacientes" e "Médicos".
    Criamos um script SQL para gerar as tabelas do banco de dados e seus relacionamentos.
    Aplicamos chaves primárias e estrangeiras para garantir a integridade dos dados.
    Documentamos o script SQL para fácil referência.


![Untitled Diagram drawio(1)](https://github.com/HenriqueBuen/Hospital/assets/142261748/ddc07eb0-e75f-4777-8a5f-d7a81d98a230)




### Tabela: central_atendimento
#### Descrição: Registra informações da central de atendimento do hospital.
```
CREATE TABLE central_atendimento (
    id INT PRIMARY KEY,  -- Chave Primária
    nome VARCHAR(255)    -- Nome da central de atendimento
);
```
### Tabela: pacientes
#### Descrição: Armazena informações sobre os pacientes.
```
CREATE TABLE pacientes (
    id INT PRIMARY KEY,  -- Chave Primária
    nome VARCHAR(255),   -- Nome do paciente
    data_nascimento DATE, -- Data de nascimento do paciente
    rg VARCHAR(20),       -- Número de RG do paciente
    endereco VARCHAR(255), -- Endereço do paciente
    telefone VARCHAR(20),  -- Número de telefone do paciente
    email VARCHAR(255),    -- Endereço de e-mail do paciente
    cpf VARCHAR(20)        -- Número de CPF do paciente
);
```
### Tabela: convenios
#### Descrição: Armazena informações sobre os convênios médicos.
```
CREATE TABLE convenios (
    id INT PRIMARY KEY,  -- Chave Primária
    nome VARCHAR(255),   -- Nome do convênio médico
    tempo_carencia INT,   -- Tempo de carência em meses
    cnpj VARCHAR(20)      -- Número de CNPJ do convênio
);
```
### Tabela: especialidades
#### Descrição: Registra informações sobre as especialidades médicas.
```
CREATE TABLE especialidades (
    id INT PRIMARY KEY,  -- Chave Primária
    nome VARCHAR(255)    -- Nome da especialidade médica
);
```
### Tabela: medicos
#### Descrição: Armazena informações sobre os médicos, incluindo sua especialidade.
```
CREATE TABLE medicos (
    id INT PRIMARY KEY,  -- Chave Primária
    nome VARCHAR(255),   -- Nome do médico
    especialidade_id INT, -- Chave Estrangeira para a tabela especialidades
    FOREIGN KEY (especialidade_id) REFERENCES especialidades(id)
);
```
### Tabela: consultas
#### Descrição: Registra informações sobre as consultas médicas, incluindo médico, paciente e convênio.
```
CREATE TABLE consultas (
    id INT PRIMARY KEY,       -- Chave Primária
    data DATE,               -- Data da consulta
    hora TIME,               -- Hora da consulta
    valor_particular DECIMAL(10, 2),  -- Valor da consulta particular
    convenio_id INT,         -- Chave Estrangeira para a tabela convenios
    paciente_id INT,         -- Chave Estrangeira para a tabela pacientes
    medico_id INT,           -- Chave Estrangeira para a tabela medicos
    FOREIGN KEY (convenio_id) REFERENCES convenios(id),
    FOREIGN KEY (paciente_id) REFERENCES pacientes(id),
    FOREIGN KEY (medico_id) REFERENCES medicos(id)
);
```

### Tabela: receitas_medicas
#### Descrição: Registra informações sobre as receitas médicas emitidas após as consultas.
```
CREATE TABLE receitas_medicas (
    id INT PRIMARY KEY,            -- Chave Primária
    consulta_id INT,               -- Chave Estrangeira para a tabela consultas
    medicamento VARCHAR(255),     -- Nome do medicamento
    quantidade INT,               -- Quantidade de medicamento
    instrucoes_uso TEXT,          -- Instruções de uso do medicamento
    relatorio_consulta TEXT       -- Relatório da consulta
);
```
### Tabela: internacoes
#### Descrição: Armazena informações sobre as internações de pacientes.
```
CREATE TABLE internacoes (
    id INT PRIMARY KEY,             -- Chave Primária
    data_entrada DATE,             -- Data de entrada na internação
    data_prevista_alta DATE,        -- Data prevista para a alta
    data_efetiva_alta DATE,         -- Data efetiva da alta
    procedimentos TEXT,             -- Descrição dos procedimentos planejados
    paciente_id INT,                -- Chave Estrangeira para a tabela pacientes
    medico_responsavel_id INT,      -- Chave Estrangeira para a tabela medicos
    enfermeiro_id INT,              -- Chave Estrangeira para a tabela profissionais_enfermagem
    FOREIGN KEY (paciente_id) REFERENCES pacientes(id),
    FOREIGN KEY (medico_responsavel_id) REFERENCES medicos(id),
    FOREIGN KEY (enfermeiro_id) REFERENCES profissionais_enfermagem(id)
);
```
### Tabela: quartos
#### Descrição: Registra informações sobre os quartos utilizados nas internações.
```
CREATE TABLE quartos (
    id INT PRIMARY KEY,          -- Chave Primária
    numero INT,                 -- Número do quarto
    tipo_quarto_id INT,         -- Chave Estrangeira para a tabela tipos_quartos
    internacao_id INT,          -- Chave Estrangeira para a tabela internacoes
    FOREIGN KEY (tipo_quarto_id) REFERENCES tipos_quartos(id),
    FOREIGN KEY (internacao_id) REFERENCES internacoes(id)
);
```
### Tabela: tipos_quartos
#### Descrição: Armazena informações sobre os tipos de quartos disponíveis no hospital.
```
CREATE TABLE tipos_quartos (
    id INT PRIMARY KEY,         -- Chave Primária
    descricao VARCHAR(255),     -- Descrição do tipo de quarto
    valor_diario DECIMAL(10, 2) -- Valor diário do quarto
);
```
### Tabela: profissionais_enfermagem
#### Descrição: Registra informações sobre os profissionais de enfermagem.
```
CREATE TABLE profissionais_enfermagem (
    id INT PRIMARY KEY,                    -- Chave Primária
    nome VARCHAR(255),                    -- Nome do profissional de enfermagem
    cpf VARCHAR(20),                      -- Número de CPF do profissional de enfermagem
    registro_conselho_enfermagem VARCHAR(20) -- Número de registro no conselho de enfermagem (CRE)
);
```


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




# Cassio_Bernardo
Projeto engenharia software marcelandia
---
# 1. Descrição do Sistema
Sistema para Clínica veterinária

Autor: Cassio Bernardo

Amigo Pet
1.Uma clínica veterinária atende apenas os animais: gatos e cachorros. 
2.Os clientes devem fazer um cadastro de si e dos animais. 
3.Os clientes devem informar as condições nas quais os animais chegam. 
4.Os clientes devem informar o tipo de ração que o animal come. 
5.O cliente deve informar hábitos do animal. 
6.Para cada animal é possível que mais de um veterinário o atenda. 
7.Os animais podem chegar e serem atendidos de acordo com uma agenda do dia. 
8.Cada animal atendido receberá uma ficha e um prontuário. 
9.Outros donos podem querer marcar horários de atendimento futuro. 
10.O atendimento gera uma receita para o animal. 
11.Quando um cliente chega na clínica veterinária ele é atendido por um atendente. 
12.O atendente deve verificar se existe agenda disponível com um veterinário. 
13.O atendente deve colocar o cliente e seu animal na fila de espera, se for o caso. 
14.O atendente deve levar o cliente e o animal até o veterinário. 
14.O veterinário deve realizar uma entrevista com o dono do animal. 
15.O resultado da entrevista deve ir para um formulário. 
16.O veterinário deverá examinar o animal e anotar em prontuário(ficha) suas observações. 
17.Dependendo da situação do animal este receberá uma receita.
18.A clinica funcionara das 8:00 as 19:00 h.
19.A clinica tem plantões depois das 19:00h
20.A clinica havera programas de fidelidade para clientes.
21.Temos uma loja para Petz.
22.Programa de pontos para Clientes.
23.Atendimento a domicilio.
24.A clinica tem um hotel para cães.
25.A clinica atende por agendamentos.
26.A clinica faz a vacinação periodicas dos animais.
![]()
---
# 2. Diagrama do banco de dados


```mermaid

erDiagram
    CLIENTE {
        int id
        string nome
        string telefone
        string endereco
        string email
        int pontos_fidelidade
    }

    ANIMAL {
        int id
        string nome
        string especie
        string raca
        int idade
        string condicao_chegada
        string tipo_racao
        string habitos
        int cliente_id FK
    }

    VETERINARIO {
        int id
        string nome
        string especialidade
        string horario_disponivel
    }

    ATENDENTE {
        int id
        string nome
        string turno
    }

    PRONTUARIO {
        int id
        string observacoes
        string receita
        int animal_id FK
    }

    AGENDA {
        int id
        date data
        time horario
        int animal_id FK
        int veterinario_id FK
        int atendente_id FK
    }

    FICHA {
        int id
        string detalhes_entrevista
        int animal_id FK
    }

    LOJA_PET {
        int id
        string nome
        string descricao
        float preco
    }

    HOTEL {
        int id
        string nome
        string tipo_acomodacao
        float preco
        int animal_id FK
    }

    VACINACAO {
        int id
        date data
        string tipo_vacina
        int animal_id FK
    }

    CLIENTE ||--o{ ANIMAL: possui
    ANIMAL ||--o{ PRONTUARIO: possui
    ANIMAL ||--o{ AGENDA: possui
    VETERINARIO ||--o{ AGENDA: atende
    ATENDENTE ||--o{ AGENDA: agenda
    ANIMAL ||--o{ FICHA: tem
    PRONTUARIO ||--|| RECEITA: emite
    CLIENTE ||--o{ LOJA_PET: compra
    ANIMAL ||--o{ HOTEL: hospeda
    ANIMAL ||--o{ VACINACAO: recebe

```


---
# 3. Diagrama de casos de uso

![https://github.com/cassiobernardo1989/Cassio_Bernardo/blob/main/Diagrama%20sem%20nome.drawio.png](https://github.com/cassiobernardo1989/Cassio_Bernardo/blob/main/Diagrama%20sem%20nome.drawio.png)
---
# 4. Principais telas do sistema


---
# 5. Arquitetura do sistema


```mermaid
graph TD
    %% Define os nós
    ClienteWeb[Cliente Web]
    ServidorWeb[Servidor Web]
    AplicacaoPHP[Aplicação PHP]
    ServidorBD[Servidor de Banco de Dados]

    %% Define as conexões entre os nós
    ClienteWeb -->|Solicita Dados| ServidorWeb
    ServidorWeb -->|Passa Requisições| AplicacaoPHP
    AplicacaoPHP -->|Consulta/Atualiza Dados| ServidorBD
    AplicacaoPHP -->|Responde a Requisições| ServidorWeb
    ServidorWeb -->|Retorna Resposta| ClienteWeb

```


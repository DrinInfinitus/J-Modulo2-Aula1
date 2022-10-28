# J-Modulo2-Aula1



create table usuario (
ID_USU int NOT NULL,
nome_usu varchar2 (50) NOT NULL,
cpf varchar2 (14) NOT NULL,
dat_nasc varchar2 (10) NOT NULL,
CONSTRAINT ID_USU_PK PRIMARY KEY (ID_USU)ENABLE
);

create table Banco (
ID_BANC int NOT NULL,
nome_banco varchar2 (10) NOT NULL,
agencia varchar2 (10) NOT NULL,
CNPJ varchar2 (20) NOT NULL,
CONSTRAINT ID_BANC_PK PRIMARY KEY (ID_BANC) ENABLE
);

create table conta (
ID_CONTA int NOT NULL,
saldo varchar2(50) NOT NULL,
num_conta varchar2(10) NOT NULL,
tipo_conta varchar2(20) NOT NULL,
ID_USU int NOT NULL,
ID_BANC int NOT NULL,
CONSTRAINT ID_CONTA_PK PRIMARY KEY (ID_CONTA) ENABLE
);

INSERT INTO USUARIO (ID_USU, nome_usu, cpf, dat_nasc) VALUES (6, 'RFB', '8795874', '17/06/1991');

UPDATE USUARIO SET nome_usu='RaifB' WHERE ID_USU=1;
UPDATE USUARIO SET dat_nasc='16/09/1950' WHERE ID_USU=4;
UPDATE USUARIO SET cpf='7895648', dat_nasc='02/11/1900' WHERE ID_USU=2;
 
UPDATE Banco SET NOME_BANCO='Nubank', agencia='Nubank302', cnpj='8799' WHERE ID_Banc=1;
UPDATE Banco SET NOME_BANCO='Inter', agencia='Inter17', cnpj='9999' WHERE ID_Banc=2;
UPDATE Banco SET NOME_BANCO='LA', agencia='LadroesAno', cnpj='13922' WHERE ID_Banc=3;

UPDATE CONTA SET SALDO='3000', num_conta='97856', tipo_conta='Poupança' WHERE ID_Conta=1;

DELETE FROM USUARIO;
DELETE FROM BANCO;
DELETE FROM CONTA;

CREATE SEQUENCE SEQUENCE_USUARIO INCREMENT BY 1 START WITH 1;

create or replace trigger TRIGGER_USUARIO
    before insert on USUARIO
    for each row
    begin
    select SEQUENCE_USUARIO.nextval into :new.ID_USU from dual;
    end;
    
CREATE SEQUENCE SEQUENCE_BANCO INCREMENT BY 1 START WITH 1;

create or replace trigger TRIGGER_BANCO
    before insert on BANCO
    for each row
    begin
    select SEQUENCE_BANCO.nextval into :new.ID_BANC from dual;
    end;

CREATE SEQUENCE SEQUENCE_CONTA INCREMENT BY 1 START WITH 1;

create or replace trigger TRIGGER_CONTA
    before insert on CONTA
    for each row
    begin
    select SEQUENCE_CONTA.nextval into :new.ID_CONTA from dual;
    end;

INSERT INTO USUARIO (NOME_USU, CPF, DAT_NASC) VALUES ('RB','13922','13/09/2022');

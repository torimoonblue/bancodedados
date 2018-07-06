CREATE DATABASE proata
DEFAULT CHARACTER  SET utf8
default collate utf8_general_ci;


use proata;

show tables;

drop table if exists proata.professor;

create table if not exists 

proata.professor(

id_prof int not null auto_increment,
nome varchar(200) not null,
    formacao varchar(200) not null,
    titualacao varchar(200),
primary key (id_prof)

);


create table if not exists
proata.projeto(
id_proj int not null auto_increment,
    noe varchar(200) not null,
    professor int not null,
    primary key (id_proj),
    foreign key (professor) 
references proata.professor(id_prof)
        
);

drop table if exists proata.ata;
create table if not exists
proata.ata(
id_ata int not null auto_increment,
        assunto varchar(200) not null,
        data_realizacao date,
        professor int not null,
        primary key (id_ata),
        foreign key(professor)
references proata.professor(id_prof)
        
    
    
    );




drop table if exists proata.projetoata;
create table if not exists 
proata.projetoata(
ata int not null,
    projeto int not null,
primary key (ata,projeto),
    foreign key (ata)
references proata.ata(id_ata),
foreign key (projeto)
references proata.projeto(id_proj)
        

);

drop table if exists proata.aluno;
create table if not exists
proata.aluno(
id_aluno int not null,
    nome varchar(200) not null,
    cpf int not null,
    curso varchar(200) not null,
    primary key(id_aluno)

);

drop table if exists proata.encaminhamento;
create table if not exists
proata.encaminhamento(
id_enc int not null,
    assunto varchar(200) not null,
    aluno int not null,
    tarefa varchar(200) not null,
    primary key (id_enc),
    foreign key(aluno)
references proata.aluno(id_aluno)

);

drop table if exists ataencaminhamento;
create table if not exists
proata.ataencaminhamento(
ata int not null,
    enc int not null,
    primary key(ata,enc),
    foreign key(ata)
references proata.ata(id_ata),
foreign key(enc)
references proata.encaminhamento(id_enc)
);


drop table if exists proata.ataaluno;
create table if not exists
proata.ataaluno(
ata int not null,
    aluno int not null,
    primary key(ata,aluno),
    foreign key (ata)
references proata.ata(id_ata),
foreign key (aluno)
references proata.aluno(id_aluno)


);

# curso-de-sql
curso de sql com  professor bruno cfb curso


## chave estrangeira

alter table clientes add constraint fk_tipo_cliente foreign key
(i_tipo_cliente)references tipocliente (i_tipo_tipocliente);


Como funciona foreign key mysql?
A chave estrangeira, ou foreign key, é um conceito ligeiramente diferente.
...
Diferentemente da chave primária, a chave estrangeira:
Pode ser nula (NOT NULL);
É um campo em uma tabela que faz referência a um campo que é chave primária em outra tabela;
É possível ter mais de uma (ou nenhuma) em uma tabela.

sintaxe 
 
 alter table clientes add constraint fk_tipo_cliente foreign key
(i_tipo_cliente)references tipocliente (i_tipo_tipocliente);




















# insert dml

## insert

para  inserir uma coluna em uma tabela use 
# alter table cliente add column i_tipo_cliente int not null

para inserir um dado em uma coluna use

## insert into "nome da tabela" values ("aqui insira os valores que serão adicionados na mesma ordem da coluna");


veja os exemplos abaixo

/*
insert into tipocliente values (01,"pessoa fisica");
insert into tipocliente values  (02,"pessoa juridica");
insert into tipocliente values (03,"cliente especial");
*/

/*
insert into cliente values (01,"mariscleia","11111111111","2000-12-20",01);
insert into cliente values (02,"jurinalva","11111111113","2000-11-20",03);
*/




caso seja adicionado um dado em uma coluna especifica basta especificar a coluna antes do parametro "values"


#como ver essee dados que foram inseridos ?

para isso usaremos DQL (data query language)

## select

select * from ("nome da tabela);

usar o (" * ") significa pegar todas as colunas dentro da tabela
para especificar a coluna basta apenas substituir o * pelo numero da coluna


![alt](dtl.png)



# fazendo inserção multipla

para fazer uma inserção multipla voce precisa usar inser em conjunto com o select 

insert into cliente2 (i_cliente_cliente,s_nome_cliente,s_cpf_cliente,d_nasc_cliente,i_tipo_cliente)
select 
i_cliente_cliente,
s_nome_cliente,
s_cpf_cliente,
d_nasc_cliente,
i_tipo_cliente

from cliente2

![alt](ss.png)



# update 
é usado para modifcar registros de uma coluna

update cliente set s_nome_cliente="lauricio" where i_cliente_cliente=1;

![cliente](ssa.png)


# delete 
para deletar use a sintaxe 

delete from cliente where i_cliente_cliente > 0

para deletar um registro especifico basta usar as condições



# select 

voce pode selecionar quais registros ver e para isso use a sintaxe

select upper(s_nome_cliente),s_cpf_cliente from cliente 

como voce pode ver acima voce pode passar mais de um registro como parametro apos o select ;


# alias 

é uma forma de dar apelidos aos registros afim de facilitar as buscas e o uso nas funções

para usar o alias use a sintaxe

select s_nome_cliente as nome_dos_clientes from cliente 

voce tambem pode na mesma sintaxe atribuir um nome a tabela
para isto basta adicionar logo apos o nome da tabel o nome apelido(alias)
e lembre-se de voltar ao nome da coluna e atribuir o nome alias e ponto como no exemplo abaixo


select tbc.s_nome_cliente as nome_dos_clientes from cliente tbc

# distinct

serve para remover registros duplicados de uma coluna
para isso use a sintaxe 

select distinct i_cliente_cliente from cliente 


# subselect 

trata-se da possibilidade de adicionar operações como um parametro de um insert 
veja a sintaxe a baixo ;

operação:

select max(c.i_cliente_cliente)+1 as i_cliente_cliente from cliente c

esta opéração acia será passada como um parametro de uma inserção veja a seguir

insert into cliente values (select max(
    c.i_cliente_cliente)+1 as i_cliente_cliente from cliente c,
    "lauricio de souza","09871232135","2010-03-01",4);
 )
<<<<<<< HEAD


 ##     INNER JOIN 

 trata se a da possibilidade de adicionar em uma consulta a junção de uma coluna que estaja em outra tabela;


![alt](4222.png);

tambem podemos fazer varios inner jois na mesma consulta 
![alt](3q2q.png);


# group by

trata se da possibilidade de agrupar registros que se repetem 
e atraves da função count mostrar a quantidade

![alt](groupby.png);

atenção isso é importante;


adicionando inner join

select 
count(i_cliente_cliente) as qtd,
s_desc_tipocliente
from cliente
inner join tipocliente on i_tipo_tipocliente = i_tipo_cliente
group by i_tipo_cliente


reversão do join 

select 
tc.s_desc_tipocliente,
count(c.i_cliente_cliente) as qtd
from
tipocliente as tc
inner join cliente c on tc.i_tipo_tipocliente  = c.i_tipo_cliente
group by tc.i_tipo_tipocliente




# group by 

![alt](aaaaa.png);

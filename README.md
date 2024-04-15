# WebfoodDB

Para a criação do banco de dados, utilizamos uma imagem Docker.
Segue abaixo os passos necessários para configurar e executar corretamente.

1. Baixe a versão do Postgres no docker (é necessário ter o docker instalado localmente);

   docker pull postgres

2. Depois de baixada a imagem, execute o comando para configurar e executar o banco de dados:

   docker run -d --name dbWebFood -p 5432:5432 -e POSTGRES_PASSWORD=123@web postgres

3. Execute o comando para verificar se a instancia foi criada e está funcional:

  docker ps

  ![image](https://github.com/tiladeira/WebfoodDB/assets/6598511/1f7de8ef-e703-428e-8c08-d409d1007fdb)

4. Utilizando o gerenciador de banco de dados de sua escolha, faça a conexão de teste:

   ![image](https://github.com/tiladeira/WebfoodDB/assets/6598511/00ddfacb-c7f1-4463-a1e7-e83a2081b7c8)

Executando os comandos de criação da tabela produtos

CREATE TABLE products(
   ID SERIAL PRIMARY KEY,
   PRODUCT_NAME TEXT NOT null,
   DESCRIPTION TEXT null,
   QUANTITY INT NOT null,
   STATUS INT NOT NULL
);

Comandos do CRUD para auxiliar a consulta:

SELECT id, product_name, description, quantity, status
FROM public.products;

SELECT id, product_name, description, quantity, status FROM public.products WHERE id = 1;

INSERT INTO public.products
(id, product_name, description, quantity, status)
VALUES(nextval('products_id_seq'::regclass), 'Suco de Laranja Primo', 'Primo Laranjas Doces LTDA', 12, 1);

UPDATE public.products SET product_name='Pão Italiano', description='Pão Artesanal LTDA', quantity=44, status=0 WHERE id=1;

DELETE FROM public.products WHERE id=2


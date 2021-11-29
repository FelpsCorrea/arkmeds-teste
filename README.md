# Teste técnico Arkmeds

Clone esse repositório (atenção a flag de submódulos)

    git clone --recurse-submodules https://github.com/FelpsCorrea/arkmeds-teste.git
    
### API setup

Acesse o diretório da API

    cd arkmeds-teste-api

Necessitaremos de um banco de dados para armazenar as informações, para criar é necessário ter configurado o Postgree em sua máquina, e então execute o comando:

    createdb -U postgres arkmeds-db

Para instalar as dependências é recomendado criar um ambiente virtual, para que as bibliotecas não influenciem nos seus demais programas. Para isso crie o ambiente virtual:

    python -m virtualenv venv

Com o ambiente virtual baixado, abra o arquivo Activate.ps1 (localizado em venv/Scripts) e adicione as seguintes linhas conforme suas configurações:

    $env:ARKMEDS_DEV_TOKEN = "token de autenticação da api de desenvolvimento da arkmeds"
    $env:DB_NAME_VARIABLE = "arkmeds-db"
    $env:DB_USER_VARIABLE = "nome do usuário do postgree"
    $env:DB_PASSWORD_VARIABLE = "senha do postgree"
    
Agora com as variáveis de ambientes configuradas para iniciarem junto com o ambiente virtual, inicie o ambiente virtual:

    venv/Scripts/activate
    
Agora que o ambiente virtual foi iniciado, finalmente baixaremos as dependências do projeto, para isso execute os seguintes comandos:

    cd arkmedsproject
    pip install requirements.txt
    
Com as dependências já baixadas, hora de gerar as tabelas em nosso banco, para isso execute o seguinte comando:

    python manage.py migrate
    
Agora que já temos toda nossa API configurada, hora de iniciar ela! Para isso execute o seguinte comando:

    python manage.py runserver
    
Agora que nosso backend está funcionando e possui as tabelas, necessitamos popular elas através da API da Arkmeds, para isso, com o servidor ligado faça uma requisição do tipo POST em uma ferramenta como o Postman, utilizando a url "http://127.0.0.1:8000/popular-banco". Isso pode demorar um pouco, pois são muitas requisições, então depende do tempo de resposta da API externa. Esse quesito poderia ser melhorado utilizando conceitos de paralelismo, mas por falta de tempo não foi possível aplicar.
    
### FRONTEND

Com nosso back configurado, vamos para o front! Primeiramente acesse o diretório do nosso frontend:

    cd arkmedsfrontend
    
Agora instale as dependências do projeto:

    npm install
    
Por fim, inicie o frontend, ele será iniciado na porta 3000 do localhost.

    npm start
    
Pronto, já tem o ambiente do back e do front configurado :)

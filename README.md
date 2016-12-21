# aulaDjango

PYTHON + DJANGO

checar versao python
	python --version
criar ambiente virtual
	py -m venv
entrar no ambiente
	[nome do ambiente]\Scripts\activate.bat
instalar django
	pip install django
iniciar projeto 
	django-admin startproject [nome do projeto] .
testar inicialização
	python manage.py runserver
inicializar aplicação
	python manage.py startapp [nome da aplicacao]

adicionar [nome do projeto].[nome da app] em INSTALLED_APPS em settings.py
adicionar from [nome do projeto].[nome da app] import views as [nome da view]
adicionar url(r'^$', [nome da view].home) em urls.py
criar função home em core > views.py
criar pasta "templates" em core
criar arquivo "index.html" em templates
criar pasta "static" em core
Opcional:	adicionar tag "{% load static %}" na primeira linha do index.html


HEROKU

baixar, criar conta e logar
instalar decouple
	pip install python-decouple
adicionar from decouple import config em settings.py
adicionar SECRET_KEY = config('SECRET_KEY') em settings.py após SECRET_KEY...
adicionar DEBUG = config('DEBUG', default = false, cast = bool) em settings.py após DEBUG...
criar ".env" na pasta do projeto
mover as linhas antigas de secret_key e debug para o arquivo .env
instalar dj-database-url
	pip install dj-database-url
adicionar from dj_database_url import parse as dburl em settings.py
modificar valor 'default' em DATABASES =... em settings.py para config('DATABASE_URL', default = default_dburl, cast = dburl)
adicionar STATIC_ROOT = os.path.join(BASE_DIR, 'staticfiles') apos STATIC_URL... em settings.py
instalar dj-static
	pip install dj-static
adicionar from dj_static import Cling em wsgi.py
modificar application = get_wsgi_application() para application = Cling(get_wsgi_application()) em wsgi.py
criar arquivo requirements.txt na raiz do projeto
adicionar resultado do comando pip freeze no arquivo
adicionar gunicorn==19.4.1 e psycopg2==2.6.1 no arquivo requirements.txt
criar arquivo Procfile na pasta raiz
adicionar web: gunicorn [nome do projeto].wsgi --log-file - no arquivo Profile
criar arquivo runtime.txt na pasta raiz
adicionar versão do python ao arquivo runtime.txt (python --version no cmd)
inicializar git
	git init
criar .gitignore
adicionar arquivos a serem ignorados pelo git
	.env
	.ambiente
	*.sqlite3
	*.pyc
	__pycache__
commita os arquivos
	git add .
	git commit -m "[mensagem aqui]"
configurar variaveis de ambiente
	heroku plugins:install heroku-config
	heroku config:push
	(ao dar erro em alguma das variaveis, troca a ordem delas e faz o heroku config:push dnovo)
pusha os arquivos para o heroku
	git push heroku master

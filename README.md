# aulaDjango

PYTHON + DJANGO

<p>checar versao python</p>
	python --version
<p>criar ambiente virtual</p>
	py -m venv [nome do ambiente]
<p>entrar no ambiente </p>
	[nome do ambiente]\Scripts\activate.bat
<p>instalar django</p>
	pip install django
<p>iniciar projeto</p>
	django-admin startproject [nome do projeto] .
<p>testar inicialização</p>
	python manage.py runserver
<p>inicializar aplicação</p>
	python manage.py startapp [nome da aplicacao]

<p>adicionar [nome do projeto].[nome da app] em INSTALLED_APPS em settings.py<p>
<p>adicionar from [nome do projeto].[nome da app] import views as [nome da view]</p>
<p>adicionar url(r'^$', [nome da view].home) em urls.py</p>
<p>criar função home em core > views.py</p>
<p>criar pasta "templates" em core</p>
<p>criar arquivo "index.html" em templates</p>
<p>criar pasta "static" em core</p>
<p>Opcional:	adicionar tag "{% load static %}" na primeira linha do index.html</p>


HEROKU

<p>baixar, criar conta e logar</p>
<p>instalar decouple</p>
	pip install python-decouple
<p>adicionar from decouple import config em settings.py</p>
<p>adicionar SECRET_KEY = config('SECRET_KEY') em settings.py após SECRET_KEY...</p>
<p>adicionar DEBUG = config('DEBUG', default = false, cast = bool) em settings.py após DEBUG...</p>
<p>criar ".env" na pasta do projeto</p>
<p>mover as linhas antigas de secret_key e debug para o arquivo .env</p>
<p>instalar dj-database-url</p>
	pip install dj-database-url
<p>adicionar from dj_database_url import parse as dburl em settings.py</p>
<p>modificar valor 'default' em DATABASES =... em settings.py para config('DATABASE_URL', default = default_dburl, cast = dburl)</p>
<p>adicionar STATIC_ROOT = os.path.join(BASE_DIR, 'staticfiles') apos STATIC_URL... em settings.py</p>
<p>instalar dj-static</p>
	pip install dj-static
<p>adicionar from dj_static import Cling em wsgi.py</p>
<p>modificar application = get_wsgi_application() para application = Cling(get_wsgi_application()) em wsgi.py</p>
<p>criar arquivo requirements.txt na raiz do projeto</p>
<p>adicionar resultado do comando pip freeze no arquivo</p>
<p>adicionar gunicorn==19.4.1 e psycopg2==2.6.1 no arquivo requirements.txt</p>
<p>criar arquivo Procfile na pasta raiz</p>
<p>adicionar web: gunicorn [nome do projeto].wsgi --log-file - no arquivo Profile</p>
<p>criar arquivo runtime.txt na pasta raiz</p>
<p>adicionar versão do python ao arquivo runtime.txt (python --version no cmd)</p>
<p>inicializar git</p>
	git init
<p>criar .gitignore</p>
<p>adicionar arquivos a serem ignorados pelo git</p>
	.env
	.ambiente
	*.sqlite3
	*.pyc
	__pycache__
<p>commita os arquivos</p>
	git add .
	git commit -m "[mensagem aqui]"
<p>configurar variaveis de ambiente</p>
	heroku plugins:install heroku-config
	heroku config:push
	(ao dar erro em alguma das variaveis, troca a ordem delas e faz o heroku config:push dnovo)
<p>pusha os arquivos para o heroku</p>
	git push heroku master

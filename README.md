# Gallery Space

Aplicação web em Django para gerenciar e exibir uma galeria de imagens. Projeto de portfólio com foco em organização de mídia, CRUD de fotos e interface limpa para navegação.

> Stack: Django 5.1 • Python 3.10 • SQLite (dev) • Gunicorn (prod)

## ✨ Destaques

- **CRUD de imagens**: cadastro, edição, visualização e exclusão
- **Uploads** salvos em `media/` (configurado via `MEDIA_ROOT`)
- **Templates prontos** em `templates/`
- **Admin do Django** habilitado
- **Arquivos estáticos** configurados (`setup/static/` → coletados em `static/`)

## 🔗 Links úteis

- Código do app: `gallery/`
- Templates principais: `templates/galeria/`
- Assets: `setup/static/`
- Configurações: `setup/settings.py`
- (Opcional) Deploy: host permitido `galleryspace-production-abc8.up.railway.app` (ajuste conforme seu deploy)

## 🚀 Executando localmente

Pré-requisitos:

- Python 3.10.6 (veja `runtime.txt`)
- pip e venv habilitados

Passos:

```bash
# 1) Clone e entre no projeto
git clone <URL_DO_SEU_REPO> gallery_space
cd gallery_space

# 2) Ambiente virtual
python3 -m venv .venv
source .venv/bin/activate   # Windows: .venv\Scripts\activate

# 3) Dependências
pip install -r requirements.txt

# 4) Migrações do banco
python manage.py migrate

# 5) (Opcional) Superusuário para /admin
python manage.py createsuperuser

# 6) Rodar servidor de desenvolvimento
python manage.py runserver
```

Acesse:

- App: `http://127.0.0.1:8000`
- Admin: `http://127.0.0.1:8000/admin`

Uploads ficarão em `media/`.

## ⚙️ Configuração rápida

Arquivo: `setup/settings.py`

- `DEBUG`: está `False` no repo — ative em dev se quiser
- `ALLOWED_HOSTS`: inclui `*` e host de produção
- Banco local: SQLite (`db.sqlite3`)
- Estáticos:
  - `STATICFILES_DIRS = [setup/static]`
  - `STATIC_ROOT = static/`

Dica para produção: use variáveis de ambiente (`SECRET_KEY`, `DEBUG`, `ALLOWED_HOSTS`). O projeto já inclui `django-environ`.

## 📁 Estrutura (parcial)

```
setup/
  ├─ settings.py        # Configurações Django
  ├─ urls.py            # Rotas raiz
  ├─ static/            # Assets de desenvolvimento
  └─ ...
gallery/
  ├─ models.py          # Modelos
  ├─ views.py           # Views
  ├─ urls.py            # Rotas do app
  └─ templates/         # (templates em /templates/galeria)
media/                  # Uploads em dev
static/                 # Coletados (collectstatic)
```

## 🧪 Comandos úteis

```bash
# Migrações
python manage.py makemigrations
python manage.py migrate

# Coleta de estáticos (produção)
python manage.py collectstatic --noinput
```

## ☁️ Deploy

Arquivos para PaaS: `Procfile` e `runtime.txt` (Railway/Heroku).

- Runtime: Python 3.10.6
- WSGI: `setup.wsgi`
- Comando de release sugerido:
  ```bash
  python manage.py migrate && python manage.py collectstatic --noinput
  ```

Em produção, defina `SECRET_KEY`, `DEBUG=False` e `ALLOWED_HOSTS`.

## 👤 Autor

Matheus Antunes — aberto a oportunidades.

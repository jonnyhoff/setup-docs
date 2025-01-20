# Django Rest Framework

## Install

```bash
mkdir -p backend/apps
cd backend
```

```bash
poetry add python-decouple djangorestframework drf-spectacular django-cors-headers daphne whitenoise
```

Packages:

- python-decouple: for environment variables
- djangorestframework: for REST API
- drf-spectacular: for API documentation
- django-cors-headers: for CORS
- daphne: for ASGI
- whitenoise: for static files

## Create project

```bash
cd backend
poetry run django-admin startproject core
```

## Apps

When creating apps, create them in the `apps` directory.

```bash
poetry run django-admin startapp apps/api
```

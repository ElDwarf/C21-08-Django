# Ejersicio 01

Basando el repositorio del ejercicio anterior o en el del ejemplo ((Repo)[https://github.com/ElDwarf/django-examples]), implementar los siguientes cambios.


## Paso 1. Crear un branch en el repositorio.

## Paso 2. Agrega Login

Para poder agrgar el login primero tiene agregar las urls, el template y la config

`urls.py`
```python
path('accounts/', include('django.contrib.auth.urls')),
```

`teamplates/registration/login.html`
```html
{% extends "base.html" %}

{% block content %}

<form method="post" action="{% url 'login' %}">
{% csrf_token %}
<div>
  <td>{{ form.username.label_tag }}</td>
  <td>{{ form.username }}</td>
</div>
<div>
  <td>{{ form.password.label_tag }}</td>
  <td>{{ form.password }}</td>
</div>
<div>
  <input type="submit" value="login" />
  <input type="hidden" name="next" value="{{ next }}" />
</div>
</form>

{% if form.errors %}
<p>Usuario o password erroneo</p>
{% endif %}

{% endblock %}
```

Por ultimo agremamos las settings

`settings.py`
```python
LOGIN_REDIRECT_URL = '/alumnos'
LOGOUT_REDIRECT_URL = '/alumnos'
```

## Paso 4. Agrega seguridad para restringir el aseso a la lista de alumnos y al detalle solo permitiendo acceso a los usuarios logueados.

NOTA: Acordate de los decoradores.-

## Paso extra. agrega al model de alumnos un status que tenga solo una serie de opciones validas.

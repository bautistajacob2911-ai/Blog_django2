[Uploading README.md…]()
# Mi Blog - Django

Proyecto de blog desarrollado con Django como parte del Módulo 7. Incluye plantillas con herencia, rutas organizadas por app y estilos con archivos estáticos.

## Funcionalidades

- Página de **Inicio** con título y mensaje de bienvenida.
- Página **Acerca de** con reseña del autor y propósito del sitio.
- Menú de navegación compartido mediante `base.html`.
- Estilos CSS cargados desde la carpeta `static`.

## Tecnologías

- Python
- Django 6.1
- HTML5 y CSS3

## Estructura principal

```
blog_project2/
├── manage.py
├── blog_project2/        # Configuración del proyecto
│   ├── settings.py
│   └── urls.py
└── posts/                # App principal
    ├── views.py
    ├── urls.py
    ├── templates/posts/  # base.html, inicio.html, acerca.html
    └── static/posts/css/ # estilos.css
```

## Instalación y uso

1. Clonar el repositorio:
   ```bash
   git clone <URL-DEL-REPOSITORIO>
   cd blog_django2
   ```

2. Crear y activar el entorno virtual (Windows):
   ```bash
   python -m venv venv
   venv\Scripts\activate
   ```

3. Instalar Django:
   ```bash
   pip install django
   ```

4. Aplicar migraciones:
   ```bash
   python manage.py migrate
   ```

5. Iniciar el servidor:
   ```bash
   python manage.py runserver
   ```

6. Abrir en el navegador:
   - Inicio: http://127.0.0.1:8000/
   - Acerca de: http://127.0.0.1:8000/acerca/

Aclaración!!!!
cree otro repositorio para esta entrega porque la 7 seguía en correción y no podía modificarlo antes de la correción.

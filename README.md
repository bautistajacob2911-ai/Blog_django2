# Mi Blog - Django

Proyecto de blog desarrollado con Django como parte del Módulo 7. Incluye plantillas con herencia, rutas organizadas por app, estilos con archivos estáticos y publicaciones cargadas desde la base de datos mediante el panel de administración.

## Funcionalidades

- Página de **Inicio** con portada de bienvenida y las últimas 3 publicaciones.
- Página de **Publicaciones** con el listado dinámico de los posts publicados, del más reciente al más antiguo.
- Página **Acerca de** con la reseña del autor y el propósito del sitio.
- Menú de navegación compartido mediante `base.html`, con la página actual resaltada.
- **Panel de administración** para crear, editar, filtrar y buscar publicaciones.
- Estilos CSS cargados desde la carpeta `static`.

## Cambios recientes

### Modelo `Post` y base de datos
- Nuevo modelo `Post` en `posts/models.py` con los campos `titulo`, `contenido`, `autor`, `fecha_creacion` (`auto_now_add=True`) y `estado`.
- El campo `estado` usa `choices`: **Borrador**, **Publicado** y **Archivado**.
- El método `__str__` devuelve el título del post.
- Migración inicial `0001_initial` generada y aplicada.

### Panel de administración
- Modelo `Post` registrado con una clase `PostAdmin`.
- Columnas visibles: título, autor, estado y fecha de creación.
- Filtros por estado y fecha, búsqueda por título, contenido y autor, y edición rápida del estado desde el listado.

### Vistas y plantillas
- La view `lista_posts` consulta los posts con el ORM:
  `Post.objects.filter(estado="publicado").order_by("-fecha_creacion")`.
- La view `inicio` envía al template las últimas 3 publicaciones.
- Las plantillas recorren los posts con `{% for post in posts %}` y muestran título, autor, fecha y contenido.
- Mensaje de aviso cuando todavía no hay publicaciones (`{% empty %}`).

### Rediseño visual
- Nueva portada azul con título centrado y botón de acción.
- Publicaciones presentadas como **tarjetas** con una franja de color y la fecha destacada.
- Paleta de colores: azul oscuro, azul, verde agua y coral, definida con variables CSS en `:root` para cambiarla fácilmente.
- Tipografías de Google Fonts: Playfair Display (títulos) y Nunito Sans (texto), con fuentes de respaldo.
- Diseño responsive, enlace para saltar al contenido y foco visible para navegación con teclado.

## Tecnologías

- Python
- Django 6.1
- SQLite
- HTML5 y CSS3

## Estructura principal

```
blog_django2/
├── manage.py
├── README.md
├── requirements.txt
├── blog_project2/            # Configuración del proyecto
│   ├── settings.py
│   └── urls.py
└── posts/                    # App principal
    ├── admin.py
    ├── apps.py
    ├── models.py
    ├── urls.py
    ├── views.py
    ├── migrations/
    │   └── 0001_initial.py
    ├── templates/posts/      # base.html, inicio.html, lista_posts.html, acerca.html
    └── static/posts/css/     # estilos.css
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

3. Instalar las dependencias:
   ```bash
   pip install -r requirements.txt
   ```

4. Aplicar migraciones:
   ```bash
   python manage.py migrate
   ```

5. Crear un superusuario para entrar al panel de administración:
   ```bash
   python manage.py createsuperuser
   ```

6. Iniciar el servidor:
   ```bash
   python manage.py runserver
   ```

7. Abrir en el navegador:
   - Inicio: http://127.0.0.1:8000/
   - Publicaciones: http://127.0.0.1:8000/posts/
   - Acerca de: http://127.0.0.1:8000/acerca/
   - Panel de administración: http://127.0.0.1:8000/admin/

## Cargar contenido

1. Ingresar a http://127.0.0.1:8000/admin/ con el superusuario.
2. Entrar en **Posts** y crear al menos 3 publicaciones.
3. Dejar el estado en **Publicado** para que aparezcan en el sitio. Los posts en **Borrador** o **Archivado** no se muestran.

## Commit del checkpoint

```bash
git add .
git commit -m "Checkpoint: Modelos y Admin configurados"
git push
```

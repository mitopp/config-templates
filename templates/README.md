# Twig Templates

## Blocks

### Head

The `head` block contains `meta` tags and other global blocks like `title`, `stylesheets` and `javascripts`. The block can be overwritten or extended. An example for extend:

~~~html
<!-- eg. page/homepage/index.html.twig -->
{% extends 'base.html.twig' %}

{% block head %}
    <!-- render the default head -->
    {{ parent() }}

    <!-- append a link to favicon -->
    <link rel="shortcut icon" type="image/svg+xml" href="favicon.ico">
{% endblock %}
~~~

#### Title

The page title can defined by: (Default: empty)

~~~html
<!-- eg. page/homepage/index.html.twig -->
{% extends 'base.html.twig' %}

{% block title 'Foobar' %}

<!-- Translate -->
{% block title 'Welcome'|trans %}

<!-- Translate and convert to uppercase -->
{% block title %}
    {{ 'homepage.title'|trans|upper }}
{% endblock %}
...
~~~

#### Stylesheets

The block contains the stylesheet links. (Default: empty)

~~~html
<!-- eg. page/homepage/index.html.twig -->
{% extends 'base.html.twig' %}

<!-- Static scripts -->
{% block stylesheets %}
    <!-- Optional: Extend the block -->
    <!-- {{ parent() }} -->
    <link rel="stylesheet" href="path/to/style.css">
{% endblock %}
~~~

#### Javascripts

The block contains the javascript links. (Default: empty)

~~~html
<!-- eg. page/homepage/index.html.twig -->
{% extends 'base.html.twig' %}

<!-- Static scripts -->
{% block javascripts %}
    <!-- Optional: Extend the block -->
    <!-- {{ parent() }} -->
    <script src="path/to/script.js"></script>
{% endblock %}

<!-- Asset mapper -->
{% block javascripts %}
    {% block importmap %}{{ importmap('app') }}{% endblock %}
{% endblock %}
~~~

### Page Classes

Page classes can be used to add CSS Class(es) direct to the `body` element. (Default: empty)

~~~html
<!-- eg. page/homepage/index.html.twig -->
{% extends 'base.html.twig' %}

{% block page_classes 'home' %}
{% block page_classes 'home page' %}

<!-- rendered to -->
<body class="home"></body>
<body class="home page"></body>
~~~

### Page Id

Similar to `page_classes` the `page_id` can be used direct to the `body` element. (Default: empty)

~~~html
<!-- eg. page/homepage/index.html.twig -->
{% extends 'base.html.twig' %}

{% block page_id 'home' %}

<!-- rendered to -->
<body id="home"></body>
~~~

### Body

The `body` block contains other blocks like `header`, `main`, `footer` etc. The block can be overwritten to reset the entire page markup.

#### Header

The `header` block is a child of the `body` block. It contains the markup for page header (include) and can be overwritten. (Use: `container_class`)

#### Main

In the `main` block contains the `content` block for extended templates.

##### Content

The `content` block is available after extend the layout template. (Default: empty)

#### Footer

The `footer` block is a child of the `body` block. It contains the markup for page footer (include) and can be overwritten. (Use: `container_class`)

## Variables

### Container Class

The `container_class` variable controls the layout. In this example: `boxed` (default) or `fluid` (100% width). It can be overwritten by a layout template file.

## Rendered example

The example ist rendered as:

~~~html
<!-- page/homepage/index.html.twig -->

<!doctype html>
<html lang="en">
    <head>
        <meta charset="utf-8">
        <meta name="viewport" content="width=device-width, initial-scale=1.0">
        <meta http-equiv="X-UA-Compatible" content="ie=edge">
        <title>Welcome</title>
    </head>

    <body class="" id="home">
        <header>
            <nav>
                <div class="boxed">
                    header
                </div>
            </nav>
        </header>

        <main class="boxed" id="content">
            <h1>Homepage</h1>
        </main>

        <footer>
            <div class="boxed">
                footer
            </div>
        </footer>
    </body>
</html>
~~~

## Read more 

- [Template Inheritance and Layouts on symfony.com](https://symfony.com/doc/current/templates.html#template-inheritance-and-layouts)
- [Template Inheritance on twig.symfony.com](https://twig.symfony.com/doc/3.x/templates.html#template-inheritance)

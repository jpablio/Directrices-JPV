# Directrices JPV

Esta página presenta las directrices de codificación para los proyectos desarrollados por JPV. Estas
directrices tienen por objeto mejorar la calidad del código: que tengan 
Mejor sostenibilidad, mejor estabilidad y menos regresiones.

Este documento esta basado en la direcctrices de [OCA](https://github.com/OCA/maintainer-tools/blob/master/CONTRIBUTING.md)
Que a su vez estos se basan libremente en las  [Directrices de Odoo](https://www.odoo.com/documentation/8.0/reference/guidelines.html)
Y [Viejas Directricces de Odoo](https://doc.odoo.com/contribute/15_guidelines/coding_guidelines_framework.html)
con adaptaciones para mejorar sus directrices y hacerlas más adecuadas para las necesidades propias de JPV. tambien tomamos encuenta las  Diferecias que tiene OCA con las Directrices Odoo
[Diferencias Con Las Directrices Odoo](#Diferencias-Con-Las-Directrices-Odoo)


##### Tabla de contenido

  * [Directrices JPV](#Directrices-JPV)
    * [Módulos](#módulos)
      * [Los números de versión](#Los-números-de-versión)
      * [Directorios](#directorios)
      * [La Nomenclatura De Archivos](#la-nomenclatura-de-archivos)
      * [Ganchos De Instalación](#ganchos-de-instalación)
    * [Archivos XML](#archivos XML)
      * [Formato](#Formato)
      * [Archivos](#Archivos)
      * [Nombrando xml_id](#nombrando-xml_id)
        * [Seguridad, Vistas y Acciónes](#Seguridad-Vistas-y-Acciónes)
        * [XML Heredado](#XML-heredado)
      * [Las Dependencias Externas](#Las-dependencias-externas)
        * [`__openerp__.py`](#__openerp__py)
        * [ImportError](#importerror)
        * [README](#user-content-readme)
    * [Python](#python)
      * [Opciones PEP8](#opciones-PEP8)
      * [Las Importaciones](#Las-importaciones)
      * [Modismos](#Modismos)
      * [Símbolos](#símbolos)
        * [Las clases de Odoo y Python](#Las-clases-de-Odoo-y-Python)
        * [Los Nombres de Variables](#Los-nombres-de-variables)
      * [SQL](#sql)
        * [Sin Inyección de SQL](#Sin-inyección-de-SQL)
        * [Nunca Confirmar La Transacción](#nunca-confirmar-la-transacción)
      * [No Pasar Por Alto El ORM](#No-pasar-por-alto-el-ORM)
      * [Modelos](#modelos)
      * [Campos](#Campos)
      * [Excepciones](#Excepciones)
    * [Javascript](#javascript)
    * [CSS](#css)
    * [Pruebas](#pruebas)
    * [Git](#git)
      * [Mensajes Del Commit](#mensajes-del-commit)
      * [Revisión](#revisión)
        * [Por favor, respetar algunas reglas básicas:](#Por-favor-respetar-algunas-reglas-básicas:)
        * [Es importante que sus commit contengan:](#Es-importante-que-sus-commit-contengan:)
        * [Tiene sentido ser exigentes en los siguientes casos:](#Tiene-sentido-ser-exigentes-en-los-siguientes-casos)
    * [Github](#github)
      * [Equipos](#equipos)
      * [Repositorios](#repositorios)
      * [Issues](#issues)
    * [Diferencias Con Las Directrices Odoo](#Diferencias-Con-Las-Directrices-Odoo)
  * [Traspasar Modulos a Odoo](#Traspasar-modulos-a-Odoo)

## Módulos

* El uso de la forma singular en el nombre del módulo, excepto cuando el nombre compuesto del módulo o objeto Odoo ya este en plural (es decir `mrp_operaciones_...`)
* Si el propósito de su módulo es la de servir como base para otros módulos, debe preceder su nombre con base_. Es decir base_location_nuts.
* Al crear un módulo de localización,Usa el prefijo en su nombre con `l10n_CC_`, donde
   `CC` es su código de país. Es decir. `l10n_ve_pos`.
* Al extender un módulo Odoo, Usa el prefijo del tuyo `Mail` con el nombre de ese módulo`forward`. Es decir.
   `Mail_forward`.
* Al combinar un módulo Odoo con otro de JPV, el nombre de Odoo va antes.
   Es decir, si usted quiere combinar de Odoo el `crm` con el modulo JPV `partner_rif`, el
   Nombre debe ser `crm_partner_rif`
* Utilice la [plantilla de descripción] (https://github.com/ACJPV/maintainer-tools/tree/master/template/module) pero elimine las secciones sin contenido significativo.
* En el archivo de manifiesto `__openerp__.py`/`__manifest__.py`:
  * Evitar los espacios vacíos
  * Asegúrese de que tiene las `licencias` y `imagenes`.
  * Asegúrese de que se adjunte el texto `, Asociacion Cooperativa Juventud productiva Venezolana (JPV)`
     Y tambien en el texto el `author`.
* No utilice el logotipo de su empresa ni su marca corporativa. Utilizando el sitio web, el autor y la lista de contribuidores es Suficiente para que la gente sepa acerca de su empleador/empresa y se contacte con usted.

### Los Números De Versión

El número de versión en el manifiesto del módulo debe ser el de la Versión
De Odoo (por ejemplo `10.0`) seguido por el módulo`x.y.z` números de versiónes.
Por ejemplo: `10.0.1.0.0` seria el primer lanzamiento de un módulo de odoo 10.0.

Los números de versión `x.y.z` siguen la semántica `breaking.feature.fix`:

  * `x` se incrementa cuando el modelo de datos o las vistas tenían
     Cambios. Es posible que sea necesaria la migración de datos.
  * `y` se incrementa cuando se agregan nuevas características que no afectan el modelo de datos. Es probablemente que
     sea necesaria la actualización de un módulo.
  * `z` se incrementa cuando se realizaron correcciones de errores. Por lo general, con un reinicio del servidor
     Los arreglos estaran disponibles.

Si se aplica, se espera que los cambios que afectan el modelo de datos incluyan instrucciones
O scripts para realizar la migración en las instalaciones actuales.


### Directorios

Un módulo está organizado en unos pocos directorios:

* `controllers/`: Contiene controladores (rutas http)
* `data/`: data xml
* `demo/`: demo xml
* `models/`: Definiciones de modelos
* `report/`: Modelos de informes (BI/análisis), plantillas de informes de impresión Webkit/RML
* `static/`: Contiene los recursos web, separados en  `css/`, `js/`, `img/`,
  `lib/`, ...
* `views/`: Contiene las vistas y plantillas,tambien contiene las plantillas de impresión de informes de QWeb
* `wizards/`: wizard model and views
* `examples/`: Archivos externos


### La Nomenclatura De Archivos

Para las declaraciones `models`,` views` y `data`, dividir archivos con el modelo
Involucrado, ya sean creados o heredados. Estos archivos deben ser nombrados despues del
modelo. Por ejemplo, los datos de demostración para res.partner deben ir en un archivo llamado
`demo/res_partner.xml` y la vista debe ir en un archivo llamado
`views/res_partner.xml`. Se puede hacer una excepción cuando el modelo es un
Modelo que se pretende utilizar sólo como un modelo de un solo
modelo. En este caso, puede incluir la definición del modelo en su interior.
Ejemplo `sale.order.line` modelo puede estar junto con` sale.order` en
El archivo `models/sale_order.py`.

Para el modelo denominado `<main_model>` se pueden crear los siguientes archivos:

* `models/<main_model>.py`
* `data/<main_model>.xml`
* `demo/<main_model>.xml`
* `templates/<main_model>.xml`
* `views/<main_model>.xml`

Para `controller`, si sólo hay un archivo, debe llamarse` main.py`.
Si hay varias clases o funciones del controlador, puede dividirlas en
Varios archivos.

Para `static files`, el patrón de nombre es` <nombre_módulo> .ext` (es decir,
`static/js/im_chat.js`,`static/css/im_chat.css`, `static/xml/im_chat.xml`,
...). No enlazar datos (imagenes, bibliotecas) fuera de Odoo: no utilice una url para
Imagenes, la debe copiar en la base de código en su lugar.

### Ganchos De Instalación

Cuando tengamos **`pre_init_hook`**, **`post_init_hook`** y **`uninstall_hook`** 
Se deben colocar en **`hooks.py`** situado en la raíz del módulo y en la
Estructura de directorios y en el archivo de manifiesto se debe mantener igual que el
siguiente ejmeplo

```python
{
    ...
    'pre_init_hook': 'pre_init_hook',
    'post_init_hook': 'post_init_hook',
    'uninstall_hook': 'uninstall_hook',
    ...
}
```

Recuerde agregar en el **`__init__.py`** Las importaciones siguientes son 
necesarias. Por ejemplo:
```python
...
from .hooks import pre_init_hook
from .hooks import post_init_hook
from .hooks import uninstall_hook
...
```

El árbol completo debe tener este aspecto:

```
addons/<my_module_name>/
|-- __init__.py
|-- __openerp__.py
|-- hooks.py
|-- controllers/
|   |-- __init__.py
|   `-- main.py
|-- data/
|   `-- <main_model>.xml
|-- demo/
|   `-- <inherited_model>.xml
|-- models/
|   |-- __init__.py
|   |-- <main_model>.py
|   `-- <inherited_model>.py
|-- report/
|   |-- __init__.py
|   |-- report.xml
|   |-- <bi_reporting_model>.py
|   |-- report_<rml_report_name>.rml
|   |-- report_<rml_report_name>.py
|   |-- <webkit_report_name>.mako
|-- security/
|   |-- ir.model.access.csv
|   `-- <main_model>_security.xml
|-- static/
|   |-- img/
|   |   |-- my_little_kitten.png
|   |   `-- troll.jpg
|   |-- lib/
|   |   `-- external_lib/
|   `-- src/
|       |-- js/
|       |   `-- <my_module_name>.js
|       |-- css/
|       |   `-- <my_module_name>.css
|       |-- less/
|       |   `-- <my_module_name>.less
|       `-- xml/
|           `-- <my_module_name>.xml
|-- tests/
|   |-- __init__.py
|   |-- <test_file>.py
|   |-- <test_file>.yml
|-- views/
|   |-- <main_model>.xml
|   `-- <inherited_main_model>_views.xml
|   |-- report_<qweb_report>.xml
|-- templates/
|   |-- <main_model>.xml
|   `-- <inherited_main_model>.xml
`-- wizards/
    |-- __init__.py
    |-- <wizard_model>.py
    `-- <wizard_model>.xml
|-- examples/
|   |-- my_example.csv
```

En los nombres de archivo sólo deben utilizarse `[a-z0-9_]`

Utilice los permisos de archivo correctos: carpetas 755 y archivos 644.

### Archivos XML

### Formato

Al declarar un registro en XML:

* Colocar el atributo `id` antes de `model`
* Para las declaraciones de campo, el atributo `name` es el primero. Luego coloque el `value`
   Ya sea en la etiqueta `field`, tambien en el atributo` eval`, y finalmente en otros
   Atributos (widget, opciones, ...) ordenados por importancia.
* Trate de agrupar los registros por modelo. En caso de dependencia entre
   Acción/menú/vistas, esta convención puede no ser aplicable.
* Utilice la convención de nomenclatura definida en el siguiente punto.
* La etiqueta `<data>` sólo se utiliza para establecer datos no actualizables con `noupdate = 1`
* No prefijar el xmlid por el nombre del módulo actual
  (`<record id="view_id"...`, no `<record id="current_module.view_id"...`)


```xml
<record id="view_id" model="ir.ui.view">
    <field name="name">view.name</field>
    <field name="model">object_name</field>
    <field name="priority" eval="16"/>
    <field name="arch" type="xml">
        <tree>
            <field name="my_field_1"/>
            <field name="my_field_2" string="My Label" widget="statusbar" statusbar_visible="draft,sent,progress,done" statusbar_colors='{"invoice_except":"red","waiting_date":"blue"}' />
        </tree>
    </field>
</record>
```

### Archivos

* Para los registros del modelo `ir.filters` use el campo explícito`user_id`.

```xml
<record id="filter_id" model="ir.filters">
    <field name="name">Filter name</field>
    <field name="model_id">filter.model</field>
    <field name="user_id" eval="False"/>
</record>
```

Para mas informacion [Use este Link](https://github.com/odoo/odoo/pull/8218)

### Nombrando xml_id

#### Seguridad, Vistas y Acciónes

Utilice el siguiente patrón:

* Para un menú: `<model_name>_menu`
* Para una vista: `<model_name>_view_<view_type>`, Donde `view_type` es kanban,
  form, tree, search, ...
* Para una acción: la acción principal debe respetar a `<model_name> _action`. los otros son
   Sufijos como `_ <detail>`, donde `detail` es una cadena con `-` y en minúsculas
   Explicando la acción (no debe ser larga). Esto se utiliza sólo si
   Se declaran múltiples acciones para el modelo.
* Para un grupo: `<model_name>_group_<group_name>` dónde `group_name` es el
   Nombre del grupo, generalmente 'user', 'manager', ...
* Para una regla: `<model_name>_rule_<concerned_group>` dónde `concerned_group` es
  El nombre abreviado del grupo en cuestión ('user' para el
  'model_name_group_user', 'public' para public user, 'company' para
  multi-company rules, ...).

```xml
<!-- views and menus -->
<record id="model_name_menu" model="ir.ui.menu">
    ...
</record>

<record id="model_name_view_form" model="ir.ui.view">
    ...
</record>

<record id="model_name_view_kanban" model="ir.ui.view">
    ...
</record>

<!-- actions -->
<record id="model_name_action" model="ir.actions.act_window">
    ...
</record>

<record id="model_name_action_child_list" model="ir.actions.act_window">
    ...
</record>

<!-- security -->
<record id="model_name_group_user" model="res.groups">
    ...
</record>

<record id="model_name_rule_public" model="ir.rule">
    ...
</record>

<record id="model_name_rule_company" model="ir.rule">
    ...
</record>
```

#### XML Heredado

Un módulo puede extender una vista sólo una vez.

Las reglas de nomenclatura deben seguirse incluso cuando se hereda una vista, el nombre del
Módulo evita conflictos de xid. En el caso de que una vista heredada tenga un nombre
Que no sigue las pautas establecidas arriba, es preferible nombrar la vista
Heredada después de la original primero el nombre de la que sigue las directrices. Esto
Facilita la búsqueda de la vista original y de la herencia si todos tienen el
mismo nombre.


```xml
<record id="original_id" model="ir.ui.view">
<field name="inherit_id" ref="original_module.original_id"/>
    ...
</record>
```


Uso de `<... position="replace">` No es recomendable porque
Podría mostrar el siguente error `Element ... cannot be located in parent view`
Desde otras vistas heredadas con este campo.

Si necesita usar esta opción, debe tener un comentario explícito
Explicar por qué es absolutamente necesario y también utilizar un
Alto valor en su `prioridad '(se recomienda más de 100) para evitar el error.


```xml
<record id="view_id" model="ir.ui.view">
    <field name="name">view.name</field>
    <field name="model">object_name</field>
    <field name="priority">110</field> <!--Priority greater than 100-->
    <field name="arch" type="xml">
        <!-- It is necessary because...-->
        <xpath expr="//field[@name='my_field_1']" position="replace"/>
    </field>
</record>
```

También, podemos ocultar un elemento de la vista usando `invisible="1"`.


### Dependencias Externas

#### `__openerp__.py`
Si su módulo utiliza dependencias adicionales de python o binarios, debe agregar
La sección `external_dependencies` a `__openerp __.py`.

```python
{
    'name': 'Example Module',
    ...
    'external_dependencies': {
        'bin': [
            'external_dependency_binary_1',
            'external_dependency_binary_2',
            ...
            'external_dependency_binary_N',
        ],
        'python': [
            'external_dependency_python_1',
            'external_dependency_python_2',
            ...
            'external_dependency_python_N',
        ],
    },
    ...
    'installable': True,
}
```

Una entrada en `bin` necesita estar en `PATH`, compruebe corriendo
`Which external_dependency_binary_N`.

Una entrada en `python` necesita estar en `PYTHONPATH`, compruebe corriendo
`Python -c" import external_dependency_python_N "`.

#### ImportError
En los archivos python donde se utilizan dependencias externas,
Necesita agregar `try-except` con un registro de depuración.

```python
try:
    import external_dependency_python_N
    import external_dependency_python_M
    EXTERNAL_DEPENDENCY_BINARY_N_PATH = tools.find_in_path('external_dependency_binary_N')
    EXTERNAL_DEPENDENCY_BINARY_M_PATH = tools.find_in_path('external_dependency_binary_M')
except (ImportError, IOError) as err:
    _logger.debug(err)
```
Esta regla no se aplica a los archivos de prueba ya que estos archivos se cargan sólo cuando
Y en tal caso su módulo y sus dependencias externas están instaladas.

#### README
Si su módulo utiliza dependencias adicionales de python o binarios, explique
Cómo instalarlos en el archivo `README.rst` en la sección` Instalación`.


## Python

### Opciones PEP8

El uso de linter flake8 puede ayudar a ver sintaxis y advertencias semánticas o errores.
El código fuente del proyecto debe cumplir con los estándares PEP8 y PyFlakes
Salvo algunas excepciones:

* En el  `__init__.py` solo
    *  F401: `module` Importados pero no utilizados

### Las Importaciones

Las importaciones se ordenan

1. Importaciones de bibliotecas estándar
2. Importaciones de terceros conocidas (una por línea ordenada y dividida en python stdlib)
3. Las importaciones de Odoo («openerp»)
4. Importaciones de módulos Odoo (rara vez, y sólo si es necesario)
5. Importaciones locales en la forma relativa
6. Importaciones de terceros desconocidas (una por línea ordenada y dividida en python stdlib)

Dentro de estos 6 grupos, las líneas importadas se ordenan alfabéticamente.

```python
# 1: imports of python lib
import base64
import logging
import re
import time

# 2: import of known third party lib
import lxml

# 3:  imports of openerp
import openerp
from openerp import api, fields, models  # alphabetically ordered
from openerp.tools.safe_eval import safe_eval
from openerp.tools.translate import _

# 4:  imports from odoo modules
from openerp.addons.website.models.website import slug
from openerp.addons.web.controllers.main import login_redirect

# 5: local imports
from . import utils

# 6: Import of unknown third party lib
_logger = logging.getLogger(__name__)
try:
  import external_dependency_python_N
except ImportError:
  _logger.debug('Cannot `import external_dependency_python_N`.')
```

 * Nota:
   * Puede utilizar [isort] (https://pypi.python.org/pypi/isort/) para
      Ordenar las importaciones.
   * Instala con `pip install isort` y usala con `isort myfile.py`.

### Modismos

* Cada archivo python debería tener como primera línea
  ``# coding: utf-8`` or ``# -*- coding: utf-8 -*-``. 
* Preferir `%` sobre `.format()`, preferir `%(varname)` En lugar de posición.
  Esto es mejor para la traducción y claridad.
* Siempre favorecer **Readability** sobre **conciseness** o usar las caracteristicas propias del 
   Lenguaje o los modismos.
* Utilizar la comprensión de la lista, la comprensión del dict y la manipulación básica usando
   `Map`,`filter`, `sum`, ... Ellos hacen que el código sea más pythonico, más fácil de leer
    Y son generalmente más eficientes.
* Lo mismo se aplica a los métodos del conjunto de registros: use `filtered`, `mapped`, `sorted`,
  ...
* Excepciones: Uso `from openerp.exceptions import Warning as UserError` (v8)
  O `from openerp.exceptions import UserError` (v9)
  O encontrar una excepción más apropiada en `openerp.exceptions.py`
* Documentar su código
    * Docstring en los métodos se debe explicar el propósito de una función,
       No un resumen del código.
    * Comentarios simples para partes de código que hacen cosas que no son
       inmediatamente obvias.
    * Demasiados comentarios son generalmente una señal de que el código es ilegible y
       Necesita ser refactorizado.
* Utilizar nombres de variables/clases/métodos significativos
* Si una función es demasiado larga o demasiado indentada debido a bucles, esto es un signo
   Que necesita ser refactorizado en funciones más pequeñas.
* Si una llamada de función, diccionario, lista o tupla se divide en dos líneas,
   Cortar en el símbolo de apertura. Esto agrega un sangrado de cuatro espacios en la siguiente
   Línea en lugar de iniciar la siguiente línea en el símbolo de apertura..
  Ejemplo:
  ```python
  partner_id = fields.Many2one(
      "res.partner",
      "Partner",
      "Required",
  )
  ```
* Al hacer una lista separada por comas, dict, tuple, ... con un elemento por
   , Agrega una coma al último elemento. Esto hace que el siguiente elemento
   Añadido, sólo cambia una línea en el conjunto de cambios, en lugar de cambiar el último
   Elemento para agregar simplemente una coma.
* Si un argumento a una llamada de función no es inmediatamente obvio,
   es preferible llamarlo por el parámetro.
* Utilice nombres de variables en inglés y escriba comentarios en inglés. Cuando se necesiten
   Ser mostrados en otros idiomas se traducirán mediante la traducción del 
   sistema.
* Evite el uso del decorador ``api.v7`` en el nuevo código, a menos que ya exista una API de 
   Fragmentación en los métodos de los padres.

### Símbolos

#### Las clases de Odoo y Python

Utilice UpperCamelCase para el código en api v8, desestime la notación minúscula para los antiguos
Api

```python
class AccountInvoice(models.Model):
    ...

class account_invoice(orm.Model):
    ...
```

#### Los Nombres de Variables
* Utilice la notación `_` para las variables comunes (snake_case).
* Dado que el nuevo API funciona con registros o conjuntos de registros en lugar de listas de id, no Fijar
   Sufijos a los nombres de variables con `_id` o `_ids` si no contienen un ids o una
   Lista de ids

```python
    ...
    res_partner = self.env['res.partner']
    partners = res_partner.browse(ids)
    partner_id = partners[0].id
```

* Utilice la notación en mayúscula con `_` para variables globales o constantes.
```python
...
CONSTANT_VAR1 = 'Value'
...
class...
...
```

### SQL

#### Sin Inyección de SQL
Se debe tener cuidado de no introducir vulnerabilidades de inyecciones de SQL al utilizar consultas SQL manuales. La vulnerabilidad está Presente cuando la entrada del usuario está incorrectamente filtrada o mal citada, lo que permite a un atacante introducir cláusulas Indeseables en una consulta SQL (como eludir filtros o ejecutar comandos **UPDATE** o **DELETE**).

La mejor manera de estar seguro es nunca, NUNCA usar la concatenación de cadenas de Python (+) o la interpolación de parámetros de cadena (%) para pasar variables a una cadena de consulta SQL.

La segunda razón, que es casi tan importante como la primera, es el trabajo de la capa de abstracción de base de datos (psycopg2) decidir cómo formatear los parámetros de consulta, NO SU TRABAJO! Por ejemplo, psycopg2 sabe que cuando pasa una lista de valores que necesita para dar formato a ellos como una lista separada por comas, entre paréntesis!

```python
# the following is very bad:
#   - it's a SQL injection vulnerability
#   - it's unreadable
#   - it's not your job to format the list of ids
cr.execute('select distinct child_id from account_account_consol_rel ' +
           'where parent_id in ('+','.join(map(str, ids))+')')

# better
cr.execute('SELECT DISTINCT child_id '\
           'FROM account_account_consol_rel '\
           'WHERE parent_id IN %s',
           (tuple(ids),))
```

Esto es muy importante, así que tenga cuidado también cuando este refactorizando, y lo más importante no copie estos patrones!.

Aquí está un [ejemplo memorable] (http://www.bobby-tables.com) para ayudarle a recordar de qué se trata el problema (pero no copiar el código allí).

Antes de continuar, por favor asegúrese de leer la documentación en línea de pyscopg2 para aprender a usarlo correctamente:

  - [El problema con los parámetros de consulta](http://initd.org/psycopg/docs/usage.html#the-problem-with-the-query-parameters)
  - [Cómo pasar los parámetros con psycopg2](http://initd.org/psycopg/docs/usage.html#passing-parameters-to-sql-queries)
  - [Tipos de parámetros avanzados](http://initd.org/psycopg/docs/usage.html#adaptation-of-python-values-to-sql-types)

#### Nunca Confirmar La Transacción

El framework OpenERP/OpenObject se encarga de proporcionar el contexto transaccional para todas las llamadas RPC. El principio es que un nuevo cursor de base de datos se abre al principio de cada llamada RPC y se confirma cuando la llamada ha vuelto, justo antes de transmitir la respuesta al cliente RPC, aproximadamente así:

```python
def execute(self, db_name, uid, obj, method, *args, **kw):
    db, pool = pooler.get_db_and_pool(db_name)
    # create transaction cursor
    cr = db.cursor()
    try:
        res = pool.execute_cr(cr, uid, obj, method, *args, **kw)
        cr.commit() # all good, we commit
    except Exception:
        cr.rollback() # error, rollback everything atomically
        raise
    finally:
        cr.close() # always close cursor opened manually
    return res
```

Si se produce algún error durante la ejecución de la llamada RPC, la transacción se deshace de forma atómica, preservando el estado del sistema.

Del mismo modo, el sistema también proporciona una transacción dedicada durante la ejecución de conjuntos de pruebas, por lo que se puede revertir o no dependiendo de las opciones de inicio del servidor.

La consecuencia es que si usted llama manualmente `cr.commit ()` en cualquier lugar del codigo hay una posibilidad muy alta de romper el sistema de varias maneras, ya que causará compromisos parciales y, por tanto, rollbacks parciales e impuros, causando entre otros:

 - Datos comerciales inconsistentes, generalmente pérdida de datos;
 - Desincronización del flujo de trabajo, documentos pegados permanentemente;
 - Pruebas que no se pueden revertir de forma limpia, y comenzará a contaminar la base de datos, y desencadenar error (esto es cierto incluso si no ocurre ningún error durante la transacción);

A no ser que:

 - ¡Has creado tu propio cursor de base de datos explícitamente! ¡Y las situaciones donde usted necesita hacer eso son excepcionales!
    Y por cierto si creaste tu propio cursor, entonces necesitas manejar casos de error y rollback adecuados, así como cerrar correctamente el cursor cuando hayas terminado con él.

   Y al contrario de la creencia popular, ni siquiera necesita llamar a `cr.commit ()` en las siguientes situaciones:

   - En el método `_auto_init ()` de un objeto `models.Model`: debe tener cuidado con el método de inicialización addons, o por la transacción ORM al crear modelos personalizados.
   - En  reportes:El `commit ()` es manejado por el framework también, por lo que puede actualizar la base de datos incluso desde dentro de un informe.
   - Dentro de los métodos `models.TransientModel`: estos métodos se llaman exactamente como los` models.Model` regulares, dentro de una transacción y con la correspondiente `cr.commit ()` / `rollback ()` al final;
   - Etc. (vea la regla general arriba si usted tiene alguna duda!)

 - Todas las llamadas `cr.commit ()` fuera del marco del servidor de ahora en adelante deben tener un comentario explícito explicando por qué son absolutamente necesarias, por qué son realmente correctas y por qué no rompen las transacciones. ¡De lo contrario pueden y serán quitados!.

 - Puede evitar el `cr.commit` utilizando el método` cr.savepoint`.

  ```python
    try:
        with cr.savepoint():
            # Create a savepoint and rollback this section if any exception is raised.
            method1()
            method2()
    # Catch here any exceptions if you need to.
    except (except_class1, except_class2):
        # Add here the logic if anything fails. NOTE: Don't need rollback sentence.
        pass

  ```

 - Puede aislar una transacción para un `cr.commit` válido usando` Environment`:

  ```python
    with openerp.api.Environment.manage():
        with openerp.registry(self.env.cr.dbname).cursor() as new_cr:
            # Create a new environment with new cursor database
            new_env = api.Environment(new_cr, self.env.uid, self.env.context)
            # with_env replace original env for this method
            self.with_env(new_env).write({'name': 'hello'})  # isolated transaction to commit
            new_env.cr.commit()  # Don't show a invalid-commit in this case
        # You don't need close your cr because is closed when finish "with"
    # You don't need clear caches because is cleared when finish "with"
  ```


### No Pasar Por Alto El ORM

Usted NUNCA debe utilizar el cursor de la base de datos directamente cuando el ORM puede hacer lo mismo! Al hacerlo, está pasando por alto todas las funciones de ORM, posiblemente las transacciones, los derechos de acceso y así sucesivamente.

Y es probable que también esté haciendo que el código sea más difícil de leer y probablemente menos seguro (vea también la siguiente guía):

```python
# Muy muy mal
cr.execute('select id from auction_lots where auction_id in (' +
           ','.join(map(str, ids)) + ') and state=%s and obj_price>0',
           ('draft',))
auction_lots_ids = [x[0] for x in cr.fetchall()]

# Sin inyección, pero aún mal
cr.execute('select id from auction_lots where auction_id in %s '
           'and state=%s and obj_price>0',
           (tuple(ids), 'draft',))
auction_lots_ids = [x[0] for x in cr.fetchall()]

# Mejor
auction_lots_ids = self.search(cr, uid, [
    ('auction_id', 'in', ids),
    ('state', '=', 'draft'),
    ('obj_price', '>', 0),
])
```

### Modelos
* Nombres de los modelos
    * Utilice el nombre en minúsculas para los modelos. Ejemplo: `sale.order`
    * Usar el nombre en una forma singular `sale.order` en lugar de `sale.orders`
* Convenciones de los métodos
    * Campo de cálculo: el patrón de método de cálculo es `_compute_<field_name>`
    * Método inverso: el patrón del método inverso es `_inverse_<field_name>`
    * Método de búsqueda: el patrón del método de búsqueda es `_search_<field_name>`
    * Método predeterminado: el patrón de método predeterminado es `_default_<field_name>`
    * Método Onchange: el patrón del método onchange es `_onchange_<field_name>`
    * Método de restricción: el patrón de método de restricción es
      `_check_<constraint_name>`
    * Método de acción: un método de acción de objeto usa el prefijo `action_`.
      Su decorador es `@api.multi`, Pero si utiliza sólo un registro, agregue
      `self.ensure_one()` Al principio del método.
    * `@api.one` Método: Para v8 se recomienda utilizar `@api.multi` y evitar el uso
      `@api.one`, Para compatibilidad con v9 donde está obsoleto `@api.one`.
* En un atributo de modelo debe
     1. Atributos privados (`_name`,`_description`, `_inherit`, ...)
     2. Método por defecto  `_default_get`
     3. Declaraciones de campos
     4. Calcular y buscar métodos en el mismo orden que la declaración de campo
     5. Restringe los métodos (`@api.constrains`) y los métodos onchange
        (`@api.onchange`)
     6. Métodos CRUD (anulación de ORM)
     7. Métodos de acción
     8. Y finalmente, otros métodos del modelo de negocio.

```python
class Event(models.Model):
    # Private attributes
    _name = 'event.event'
    _description = 'Event'

    # Default methods
    def _default_name(self):
            ...

    # Fields declaration
    name = fields.Char(string='Name', default=_default_name)
    seats_reserved = fields.Integer(
        oldname='register_current',
        string='Reserved Seats',
        store=True,
        readonly=True,
        compute='_compute_seats',
    )
    seats_available = fields.Integer(
        oldname='register_avail',
        string='Available Seats',
        store=True,
        readonly=True,
        compute='_compute_seats',
    )
    price = fields.Integer(string='Price')

    # Calcular y buscar campos, en el mismo orden que se declararon los campos.
    @api.multi
    @api.depends('seats_max', 'registration_ids.state')
    def _compute_seats(self):
        ...

    # Limitaciones y cambios
    @api.constrains('seats_max', 'seats_available')
    def _check_seats_limit(self):
        ...

    @api.onchange('date_begin')
    def _onchange_date_begin(self):
        ...

    # Methodos CRUD
    def create(self):
        ...

    # Métodos de acción
    @api.multi
    def action_validate(self):
        self.ensure_one()
        ...

    # Métodos del modelo de negocio
    def mail_user_confirm(self):
        ...
```


### Campos
* `One2Many` y `Many2Many` Siempre deben tener campos `_ids` Como sufijo
  (Ejemplo: sale_order_line_ids)
* `Many2One` Los campos deben tener `_id` Como sufijo
  (Ejemplo: partner_id, user_id, ...)
* Si el nombre técnico del campo (el nombre de la variable) es el mismo para el
   String de la etiqueta, no ponga el parámetro `string` para los nuevos campos API, porque
   Se toma automáticamente. Si el nombre de su variable contiene "_" en el nombre,
   Se convierten en espacios al crear la cadena automática y cada palabra
   Se capitaliza.
  (Ejemplo: old api `'name': fields.char('Name', ...)`
            new api `'name': fields.Char(...)`)
* Las funciones por defecto deben declararse con una llamada lambda en uno mismo. La razón
   Para que esto sea así es que una función por defecto pueda ser heredada. Asignación de una función
   Puntero directamente al parámetro `default` no permite la herencia.

  ```python
  a_field(..., default=lambda self: self._default_get())
  ```

### excepciones

El passbloque en excepto que no es una buena práctica!

Al incluir el passasumimos que nuestro algoritmo puede seguir funcionando después de que ocurrió la excepción

Si realmente necesita usar el passconsiderar la tala de esta excepción

```
try:
        sentences
    except:
        _logger.debug('Why the exception is safe....', exc_info=1))
```    

## Javascript

* `use strict;` Se recomienda para todos los archivos javascript.
* Utilizar un linter (jshint, ...).
* Nunca agregue bibliotecas JavaScript minificadas.
* Utilice UpperCamelCase para declaraciones de las clases.

## CSS

* Prefijo en todas sus clases como `o_ <nombre_módulo>` donde `nombre_módulo` es el
   Nombre técnico del módulo (`sale`,`im_chat`, ...) o la ruta principal
   Reservado por el módulo (para el módulo del Web site principalmente,
   Es decir, `o_forum` para el módulo website_forum). La única excepción para esta regla es
   El webclient: simplemente usa el prefijo `o_`.
* Evitar el uso de ids.
* Usar clases nativas de arranque.
* Usar subtítulos en minúsculas para nombrar clases

## Pruebas

Como regla general, una corrección de errores debe venir con un unittest que fallaría
Sin la corrección misma. Esto es para asegurar que la regresión no ocurra en
el futuro. También es una buena manera de demostrar que el arreglo funciona en todos los casos.

Los nuevos módulos o adiciones idealmente deberían probar todas las funciones definidas. los
La utilidad de overoles comentará sobre las solicitudes de extracción que indican si la cobertura a
Aumentado o disminuido. Si ha disminuido, esto suele ser una señal de que una prueba
debería ser añadida. La interfaz web también puede mostrar qué líneas necesitan
Casos de prueba..

## Git

### Mensajes Del Commit

Anteponga al Commit 

* [IMP] para mejoras
* [FIX] para la corrección de errores
* [REF] para refactorización
* [ADD] para agregar nuevos recursos
* [REM] para retirar de los recursos
* [MOV] para mover archivos (no cambie el contenido del archivo movido, o Git va a perder la pista, y se perderá la historia!), O simplemente moviendo el código de un archivo a otro.
* [Merge] para la fusión se compromete (sólo para adelante / atrás-puerto)
* [CLA] para la firma de la Licencia Individual Sénior Openerp

Escribe un breve resumen de confirmación sin prefijarlo. No debe ser superior a
50 caracteres: `Este es un Commit de confirmación`

A continuación, en el propio mensaje, especifique la parte del código afectada por su
Cambios (nombre del módulo, lib, objeto transversal, ...) y una descripción del
Cambios. Esta parte debe ser de varias líneas pero no más de 80 caracteres en total.

* Los Commit deben estar en inglés
* Las propuestas de combinación `Merge` deben seguir las mismas reglas que el título de la propuesta en la primera línea del commit de combinación y la descripción corresponde a la descripción de commit.
* Siempre ponga mensajes de confirmación significativos: los mensajes de confirmación deben ser
   (El tiempo suficiente) incluyendo el nombre del módulo que
   Ha sido cambiado y la razón detrás de ese cambio. No utilice
   Palabras simples como "bugfix" o "mejoras"
* Evite commits que afectan simultáneamente a muchos módulos. Intentar
   Se dividen en diferentes commits donde los módulos impactados son diferentes.
   Esto es útil si necesitamos revertir cambios en un módulo por separado.
* Haga sólo una commit por un conjunto de cambios lógicos. No agregue commit como
   "Fix pep8", "Revisión de código" o "Add unittest" si se corrigen los commit que se estan 
    Proponiéndo.
* Utilice el imperativo actual (Corrige el formato, elimina el campo no utilizado) evita añadir
   'S' a los verbos: arregla, elimina

```
website: remove unused alert div

Fix look of input-group-btn
Bootstrap's CSS depends on the input-group-btn element being the first/last
child of its parent.
This was not the case because of the invisible and useless alert.
```
```
web: add module system to the web client
This commit introduces a new module system for the javascript code.
Instead of using global ...
```

### Revisión

La revisión por pares es la única manera de garantizar la buena calidad del código y tambien para
Poder confiar en los otros desarrolladores. La revisión por pares de este proyecto será
Gestionado mediante solicitudes de extracción. Servirá los siguientes propósitos principales:

* Tener un segundo aspecto en un fragmento de código para evitar problemas no deseados / erroress.
* Evitar las fallas técnicas o de diseño del modelo de negocios.
* Permitir la coordinación y convergencia de los desarrolladores informando a la
   Comunidad de lo que se ha hecho.
* Permitir que los responsabilidades de ver a todos los desarrolladores y mantener a los interesados informados de lo que se ha hecho.
* Evitar incompatibilidades de addon cuando sea posible.
* La justificación para la revisión por pares tiene su equivalente en la ley de Linus, a menudo
   "Dando suficientes ojos, todos bugs estan a simple vista"

Significado: "Si hay suficientes revisores, todos los problemas son fáciles de resolver". Eric
S. Raymond ha escrito influyentemente sobre la revisión por pares en el desarrollo de software:
 http://en.wikipedia.org/wiki/Software_peer_review.

#### Por favor, respetar algunas reglas básicas:

* Dos revisores deben aprobar una propuesta de merge para poder aceptar el merge
* Se deben esperar como minimo 5 días calendario para poder realizar el merge
* Un PR se puede combinar en menos de 5 días calendario si y sólo si se aprueba
  Por 3 evaluadores. en caso que sea un modulo de JPV Si tiene prisa, envíe un correo a
  info@juventudproductiva.com.ve, en caso que sea un modulo de OCA Si tiene prisa, envíe un correo a
  Contributors@odoo-community.org o preguntar por IRC (FreeNode
  Oca, canal openobject).
* En caso que sea un modulo de OCA al menos uno de los exámenes anteriores debe ser de un miembro del PSC o tener
  Acceso de escritura en el repositorio (aquí uno de los
  [OCA Core Maintainers] (https://odoo-community.org/project/core-maintainers-55)
  Puede hacer el trabajo. Puede notificarlos en Github utilizando '@OCA/core-maintainers')
* ¿Es el módulo lo suficientemente genérico como para ser parte de addons de la comunidad?
* ¿El módulo está duplicando funciones con otros complementos de la comunidad?
* ¿La documentación le permite entender lo que hace y cómo usarlo?
* ¿El problema que intenta resolver esta dirigido de buena forma, utilizando 
  ¿conceptos?
* ¿Existen algunos casos de uso?
* ¿Hay alguna configuración en el código? ¡No debería!
* ¿Hay datos de demostración?

Otras lecturas relacionadas:
* https://insidecoding.wordpress.com/2013/01/07/code-review-guidelines/

#### Es importante que sus commit contengan:

* Comience por agradecer al colaborador/desarrollador por su trabajo. No importa la
   Cuestión del PR, alguien ha hecho el trabajo para usted, así que sea agradecido por eso.
* Sea cordial y educado. Nada es obvio en un PR.
* La descripción de los cambios debe ser lo suficientemente clara para que usted pueda entender
   Su finalidad y, si procede, contener una demostración para
   Permitir a la gente ejecutar y probar el código
* Elija la etiqueta de revisión (comment, approve, rejected, needs information,...)
   Y no se olvide de añadir un tipo de revisión para que la gente sepa:
  * Revisión de código: significa que revisan el código.
  * Prueba: significa que lo probó funcionalmente hablando.

Mientras realiza la fusión, respete al autor utilizando la opción `--author`
Al hacer un commit. El autor lo encontrara utilizando el comando git log. Utilice el comando commit
Mensaje proporcionado por el contribuyente, si lo hubiere.

#### Tiene sentido ser exigentes en los siguientes casos:

* El origen/motivo del patch/dev no está bien documentado.
* Ninguna descripción adaptada/convincente escrita en el archivo `__openerp __. Py` para
   El módulo
* Las pruebas o el escenario no estan del todos maduras y/o no se adaptan.
* Tener pruebas es muy lentado.
* Problemas con licencia, copyright, autoría.
* Respeto de Odoo/convenciones de la comunidad.
* Diseño de código y mejores prácticas.

La larga descripción trata de explicar el **por qué** no el **qué**, el **qué**
Se puede ver en el diff.

Las solicitudes de extracción pueden cerrarse si:

* No hay actividad durante 6 meses.

## Github

### Equipos
      
* El nombre del equipo no debe contener odoo o openerp.
* El nombre del equipo para la localización es "JPV Maintainers" para proyectos de JPV.

### Repositorios

#### Nombre

* El nombre del proyecto no debe contener odoo o openerp.
* El nombre del proyecto para la localización es "l10n-Venezuela" para Venezuela.
* El nombre del proyecto para los conectores es "connector-magento" para el conector Magento.

#### Configuración de rama
Paquetes de Python que requieren ser instalados, se deben definir en el archivo requirements.txt de travis.yml.
Requirements.txt evita repetir paquetes en todos los archivos travis.yml de repositorios en caso de utilizar el archivo oca_dependencies.txt

### Issues

* Los issues se utilizan para los planos y los errores.

## Diferencias Con Las Directrices Odoo

No todas las directrices de Odoo se ajustan a las necesidades de los módulos OCA. En muchos casos, las normas
Para ser más estrictos. En otros casos, las convenciones se mejoran para
Mantenibilidad en un ecosistema de muchos módulos más pequeños.

Las diferencias incluyen:

* [Estructura del módulo](#módulos)
     * Uso de un archivo por modelo.
     * Separación de datos y carpetas xml de demostración de datos.
     * No cambia xml_ids mientras hereda.
     * Añadir guía para usar dependencias externas.
     * Definir un archivo separado para los ganchos de instalación.
* [XML](#archivos xml)
     * Evite utilizar el módulo actual en xml_id.
     * Utilizar el campo explícito `user_id` para los registros del modelo `ir.filters`.
* [Python](# python)
     * Utilizar los estándares de Python.
     * Cumplimiento de las PEP8.
     * Utilice ``#codificación:utf-8`` o ``#-*-codificación:utf-8-*-`` en la primera línea.
     * Uso de importación relativa para archivos locales.
     * Más modismos de python.
     * Una forma de tratar largas líneas separadas por comas.
     * Consejos sobre la documentación.
     * No utilice CamelCase para las variables del modelo.
     * Usar mayúsculas en subrayado para variables globales o constantes.
* [SQL](#sql)
     * Añadir sección para No Inyección de SQL.
     * Añadir sección para no omitir el ORM.
     * Añadir sección para nunca confirmar la transacción.
* [Campo](#campo)
     * Una sugerencia para los valores predeterminados de la función.
     * Utilizar la cadena de etiquetas predeterminada si es posible.
     * Añadir el patrón de método inverso.
* [Se ha añadido una sección de pruebas](#pruebas)
* [Git](#git)
     * Sin prefijo de confirmación
     * Estándares de mensajes de confirmación git commit predeterminados
     * Aplastando los cambios en las solicitudes de tracción cuando sea necesario
     * Uso del presente imperativo
* [Sección Github](#github)
* [Sección de Revisión](#revisión)

# Traspasar Modulos a Odoo

Sugerir un backport de un módulo entre un repositorio OCA es posible, pero usted
Debe respetar unas pocas reglas:

  * Es necesario mantener la licencia del módulo codificada por Odoo SA
  * Es necesario agregar la OCA como autor (y Odoo SA, por supuesto)
  * Es necesario que el módulo "OCA compatible": PEP8, OCA convención y así
    Por lo que no va a romper nuestro CI como runbot, Travis y así.
  * Debe agregar un descargo de responsabilidad en el archivo Léame con el texto siguiente:
```
** Este módulo es un backport de Odoo SA y como tal, no está incluido en el OCA CLA. Eso significa que no tenemos una copia de los derechos de autor como todos los demás módulos OCA. **
¡Bienvenido!
```

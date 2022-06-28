---
layout: workshop      # NO CAMBIAR ESTO 
venue: "COMPLETAR"        # nombre breve del espacio donde se lleva adelante el taller, sin dirección (por ejemplo, "Universidad de Buenos Aires")
address: "COMPLETAR"      # dirección completa del espacio donde se realizará el taller (por ejemplo, "Aula 3, Av. Córdoba 1234, Buenos Aires, Argentina")
country: "COMPLETAR"      # código ISO del país, dos letras en minúscula como por ejemplo "fr" (ver https://en.wikipedia.org/wiki/ISO_3166-1)
language: "COMPLETAR"     # código ISO del idioma, dos letras en minúscula como por ejemplo "fr" (ver https://en.wikipedia.org/wiki/ISO_639-1)
latitude: "COMPLETAR"       # latitud del espacio en formato decimal (por ejemplo, "41.7901128" - usar http://www.latlong.net/)
longitude: "COMPLETAR"    # longitud del espacio en formato decimal (por ejemplo, "-87.6007318" - usar http://www.latlong.net/)
humandate: "COMPLETAR"    # fechas del taller en formato legible (por ejemplo, "Feb 17-18, 2020")
humantime: "COMPLETAR"    # hora del taller en formato legible (por ejemplo, "9:00 am - 4:30 pm")
startdate: COMPLETAR      # fecha de inicio del taller en formato YYYY-MM-DD (por ejemplo, 2015-01-01)
enddate: COMPLETAR        # fecha de finalización del taller en formato YYYY-MM-DD, por ejemplo 2015-01-02
instructor: ["COMPLETAR"] # lista de nombres de las instructoras separados por comas y entre corchetes, como ["Hedy Lamarr", "Ada Lovelace", "Madame Curie"]
helper: ["COMPLETAR"]     # lista de nombres de las **helpers** separados por comas y entre corchetes, como ["Carrie Fisher", "Frances Allen", "Margaret Hamilton"]
email: ["fixme@example.org"]    # lista de direcciones de correo electrónico de contacto con la **host** ó **lead instructor**, separadas por comas y entre corchetes, como ["ada.lovelace@ejemplo.org", "carrie.fisher@ejemplo.org", "hedy.lamarr@example.org"]
collaborative_notes:             # optional: URL de las notas colaborativas del taller, por ejemplo un Etherpad o documento de Google Docs 
eventbrite:           # optional: clave alfanumérica de registro en Eventbrite, por ejemplo "1234567890AB" (si se está utilizando Eventbrite)
---

{% comment %} Ver en los comentarios que siguen las instrucciones sobre cómo editar secciones específicas de esta plantilla de taller {% endcomment %}

{% comment %}
  ENCABEZADO

  Edita los valores en el bloque de arriba para tu taller.
  Si el valor no es 'true', 'false', 'null', o un número, por favor usa
  comillas dobles alrededor del valor, salvo que se especifique de otro modo.
  Por último ejecuta 'make workshop-check' *antes* de comitear para asegurarte que los cambios estan bien.
{% endcomment %}

{% comment %}
  EVENTBRITE

  Este bloque incluye el widget para registro en Eventbrite, en caso de que 'eventbrite' haya sido especificado en el encabezado. Puedes borrarlo si no estás usando Eventbrite, o dejarlo, ya que no se mostrará si el campo 'eventbrite' en el encabezado no fue especificado. 
{% endcomment %}
{% if page.eventbrite %}
<iframe
  src="https://www.eventbrite.com/tickets-external?eid={{page.eventbrite}}&ref=etckt"
  frameborder="0"
  width="100%"
  height="248px"
  scrolling="auto">
</iframe>
{% endif %}



<h4>Esta es la plantilla de taller. Elimina estas líneas y utiliza la plantilla para personalizar tu propio sitio web. Si estás desarrollando un taller auto-gestionado o aún no hiciste una solicitud de pedido de taller, por favor completa este <a href="{{site.amy_site}}/submit">formulario</a> para notificarnos y que nuestra administradora pueda contactarte si necesitamos información adicional.</h4>



<h2 id="general">Información General</h2>

{% comment %}
  INTRODUCCIÓN 

Para editar el párrafo introductorio general deberás modificar el archivo <code>intro.html</code>. Este archivo lo puedes encontrar navegando a la carpeta <code>_includes</code> y luego selecciona la carpeta para el tipo de taller que estás organizando (swc, dc o lc).
  
{% endcomment %}
{% if site.carpentry == "swc" %}
  {% include sc/intro.html %}
{% elsif site.carpentry == "dc" %}
  {% include dc/intro.html %}
{% elsif site.carpentry == "lc" %}
  {% include lc/intro.html %}
{% endif %}

{% comment %}
  PÚBLICO

  Explica quién es tu público. (En particular, cuenta a los lectores si el taller está abierto sólo a personas de una institución o grupo en particular).
  {% endcomment %}
  {% if site.carpentry == "swc" %}
  {% include sc/who.html %}
{% elsif site.carpentry == "dc" %}
  {% include dc/who.html %}
{% elsif site.carpentry == "lc" %}
  {% include lc/who.html %}
{% endif %}

{% comment %}
  UBICACIÓN

  Este bloque muestra la dirección y enlaces a mapas con instrucciones de cómo llegar al lugar del evento si la latitud y longitud fueron definidas en el encabezado. Puedes utilizar http://itouchmap.com/latlong.html para encontrar las coordenadas (lat/long) de una dirección. 
{% endcomment %}
{% assign begin_address = page.address | slice: 0, 4 | downcase  %}
{% if page.address == "online" %}
{% assign online = "true_private" %}
{% elsif begin_address contains "http" %}
{% assign online = "true_public" %}
{% else %}
{% assign online = "false" %}
{% endif %}
{% if page.latitude and page.longitude and online == "false" %}
<p id="where">
  <strong>Dónde:</strong>
  {{page.address}}.
  Obtener direcciones con:
  <a href="//www.openstreetmap.org/?mlat={{page.latlng | replace:',','&mlon='}}&zoom=16">OpenStreetMap</a>
  o
  <a href="//maps.google.com/maps?q={{page.latlng}}">Google Maps</a>.
</p>
{% elsif online == "true_public" %}
<p id="where">
  <strong>Dónde:</strong>
  en línea en <a href="{{page.address}}">{{page.address}}</a>.
  Si necesitas una clave de acceso u otra información para acceder este taller,
  esta información será compartida contigo antes del inicio del taller.
</p>
{% elsif online == "true_private" %}
<p id="where">
  <strong>Dónde:</strong> Este taller será en línea.
  Información sobre cómo conectarse al taller será compartida antes del inicio del evento.
</p>
{% endif %}

{% comment %}
  FECHA

  Este bloque muestra la fecha y enlaces a Google Calendar.
{% endcomment %}
{% if page.humandate %}
<p id="when">
  <strong>Cuándo:</strong>
  {{page.humandate}}.
  {% include workshop_calendar.html %}
</p>
{% endif %}

{% comment %}
  REQUERIMIENTOS ESPECIALES
  
  Modifica este bloque si hay algún requerimiento especial.
{% endcomment %}
<p id="requirements">
  <strong>Requerimientos:</strong> Las asistentes deben traer una computadora portátil con sistema operativo Mac, Linux o Windows (no tablets, Chromebooks, etc.), que tenga permisos de administrador habilitados. Deberán también tener los paquetes de software requeridos instalados, mira la lista <a href="#setup">aquí</a>. 
	
Es un requisito de este taller que todas las personas registradas respeten el <a href="{{site.swc_site}}/conduct.html">Código de Conducta</a> de 
  {% if site.carpentry == "swc" %}
  Software Carpentry
  {% elsif site.carpentry == "dc" %}
  Data Carpentry
  {% elsif site.carpentry == "lc" %}
  Library Carpentry
  {% endif %}. 
</p>

{% comment %}
  ACCESIBILIDAD

  Modifica este bloque si existen barreras de accesibilidad o instrucciones especiales.
{% endcomment %}
<p id="accessibility">
  <strong>Accesibilidad:</strong> Estamos comprometidas a hacer que este taller sea accesible para todas las personas registradas. Las organizadoras comprobaron que: 
</p>
<ul>
  <li>El salón es accesible para silla de ruedas o similar</li>
  <li>Baños accesibles están a disposición</li>
</ul>
<p>
  Los materiales se entregarán antes del taller, también se encuentra disponible material impreso si se pide a los organizadores con anticipación. Si podemos ayudar a facilitar el aprendizaje (por ejemplo, con intérpretes de lenguaje de señas, o instalaciones para lactancia), por favor contáctanos (utilizando los detalles de contacto listados debajo) e intentaremos proveerlos.
</p>

{% comment %}
  DIRECCIONES DE CORREO ELECTRÓNICO DE CONTACTO

  Muestra los correos electrónicos de contacto definidos en el archivo de configuración.
{% endcomment %}
<p id="contact">
  <strong>Contacto</strong>:
  Por favor escribe a
  {% if page.email %}
    {% for email in page.email %}
      {% if forloop.last and page.email.size > 1 %}
        o
      {% else %}
        {% unless forloop.first %}
        ,
        {% endunless %}
      {% endif %}
      <a href='mailto:{{email}}'>{{email}}</a>
    {% endfor %}
  {% else %}
    a ser anunciado
  {% endif %}
  para más información.
</p>

<hr/>

{% comment %}
  SCHEDULE



Muestra el cronograma del taller. Edita los ítems y horarios en la tabla para ajustarlos a tu planificación. Puede que quieras modificar 'Día 1' y 'Día 2' para mostrar fechas concretas o días de la semana.

{% endcomment %}
<h2 id="schedule">Cronograma</h2>

{% comment %} NO EDITAR LOS ENLACES A LAS ENCUESTAS {% endcomment %}
<p><em>Encuestas</em></p>
<p>Por favor, asegúrate de completar estas encuestas antes y después del taller.</p>
<p><a href="{{ site.pre_survey }}{{ site.github.project_title }}">Encuesta pre-taller</a></p>
<p><a href="{{ site.post_survey }}{{ site.github.project_title }}">Encuesta post-taller</a></p>

{% if site.carpentry == "swc" %}
  {% include sc/schedule.html %}
{% elsif site.carpentry == "dc" %}
  {% include dc/schedule.html %}
{% elsif site.carpentry == "lc" %}
  {% include lc/schedule.html %}
{% endif %}

{% comment %}
  Notas de colaboración

  Si quieres usar un Etherpad, ve a

      http://pad.software-carpentry.org/YYYY-MM-DD-site

  donde 'YYYY-MM-DD-site' es el identificador de su taller,
  e.g., '2015-06-10-esu'.
{% endcomment %}
{% if page.collaborative_notes %}
<p id="collaborative_notes">
 Utilizaremos este <a href="{{page.collaborative_notes}}"> documento colaborativo </a> para chatear, tomar notas y compartir URL y fragmentos de código.
</p>
{% endif %}

<hr/>

{% comment %}
  CURRICULA

  En inglés, syllabus. Muestra que tópicos van a ser cubiertos.

  1. Si tu taller es sobre R antes que Python, remueve el comentario
     alrededor de esa sección y pon un comentario alrededor de la sección Python.
  2. Algunos talleres van a remover SQL.
  3. Por favor asegúrate que la lista de tópicos esté sincronizada con lo que
     pretendes enseñar.
  4. Podría ser que necesites mover los campos div con class="col-md-6" alrededor
     dentro de los div con class="row" para balancear el diseño multi-columnar.

  Este es uno de los lugares donde la gente frecuentemente comete errores, así que
  por favor observa la previsualización del sitio antes de comitear, y asegúrate
  de ejecutar también 'tools/check'.
{% endcomment %}
<h2 id="syllabus">Currícula</h2>

{% if site.carpentry == "swc" %}
  {% include sc/syllabus.html %}
{% elsif site.carpentry == "dc" %}
  {% include dc/syllabus.html %}
{% elsif site.carpentry == "lc" %}
  {% include lc/syllabus.html %}
{% endif %}

<hr/>

{% comment %}
  CONFIGURACIÓN
 
  Borra las secciones irrelevantes de las instrucciones de configuración. Cada sección está dentro de un 'div' que no contiene clases para que el comienzo y el final sean más fáciles de encontrar.
  Este es otro lugar en donde las personas cometen errores de forma más frecuente, por favor previsualiza tu sitio antes de commitear y además asegurate de ejecutar 'tools/check'.
  
{% endcomment %}

<h2 id="setup">Configuración</h2>

<p>
  Para participar en un taller de
  {% if site.carpentry == "swc" %}
  Software Carpentry
  {% elsif site.carpentry == "dc" %}
  Data Carpentry
  {% elsif site.carpentry == "lc" %}
  Library Carpentry
  {% endif %},
  necesitarás acceso a los programas listados abajo.
  Además, necesitarás la versión más reciente de un navegador web como Google Chrome, Mozilla Firefox, o Safari.
</p>
<p>
  En caso de encontrar problemas durante la instalación de los programas requeridos en este taller, puedes acceder a una lista de problemas comunes que ocurren durante la instalación. Esta referencia puede ser útil para solucionar tus problemas de instalación: 
  <a href = "{{site.swc_github}}/workshop-template/wiki/Configuration-Problems-and-Solutions">Configuration Problems and Solutions wiki page</a>.
</p>

<div id="shell"> {% comment %} Start of 'shell' section. {% endcomment %}
  <h3>La terminal Bash</h3>

  <p>
    Bash es una de las terminales más frecuentemente utilizadas, que te permite realizar tareas simples de forma rápida.
  </p>

  <div class="row">
    <div class="col-md-4">
      <h4 id="shell-windows">Windows</h4>
      <a href="https://www.youtube.com/watch?v=339AEqk9c-8">Video Tutorial</a>
      <ol>
        <li>Descarga el <a href="https://git-for-windows.github.io/">instalador</a> de Git para Windows.</li> 
        <li>Ejecuta el instalador y sigue los siguientes pasos:
          <ol>
            {% comment %} Instalación de Git 2.8.2 {% endcomment %}
            {% comment %} Información {% endcomment %}
            <li>Click en "Siguiente".</li>
            {% comment %} Seleccionar Componentes{% endcomment %}
            <li>Click en "Siguiente".</li>
            {% comment %} Ajustar tu variable de entorno PATH {% endcomment %}
            <li>
              <strong>
                Dejar seleccionado "Utilizar Git desde la Línea de Comando de Windows" y click en "Siguiente".
              </strong>
                Si olvidaste hacer esto, los programas que necesitas para el taller no funcionarán correctamente. 
		Si esto sucede vuelve a ejecutar el instalador y selecciona la opción adecuada.
            </li>
            {% comment %} Eligiendo el ejecutable SSH {% endcomment %}
            <li>Click en "Siguiente".</li>
            {% comment %} Configurando los finales de línea {% endcomment %}
            <li>
              <strong>
                Deja seleccionado "Deshabilitar estilo Windows, confirmar estilo Unix para los finales de líneas" y click en "Siguiente".
              </strong>
            </li>
            {% comment %} Configurando el emulador de la terminal para ser utilizado con Git Bash {% endcomment %}
            <li>
              <strong>
                Dejar seleccionado "Utilizar ventana de consola de Windows por defecto" y click en "Siguiente".
              </strong>
            </li>
            {% comment %} Configurando ajustes de rendimiento experimental {% endcomment %}
            <li>Click en "Instalar".</li>
            {% comment %} Instalando {% endcomment %}
            {% comment %} Completando el Asistente de Instalación de Git{% endcomment %}
            <li>Click en "Finalizar".</li>
          </ol>
        </li>
        <li>
          Si tu variable de entorno "HOME" no está configurada (o si no sabes qué es esto):
          <ol>
            <li>Abre una terminal (Abrir Menú Inicio y escribir <code>cmd</code> y presionar [Enter])</li>
            <li>
              Escribe la siguiente línea en la ventana de la terminal exactamente como sigue:
              <p><code>setx HOME "%USERPROFILE%"</code></p>
            </li>
            <li>Presiona [Enter], deberías ver <code>SUCCESS: Specified value was saved.</code></li>
            <li>Sal de la terminal escribiendo <code>exit</code> y presionando [Enter]</li>
          </ol>
        </li>
      </ol>
      <p>Esto instalará tanto Git y Bash en el programa Git Bash.</p>
    </div>
    <div class="col-md-4">
      <h4 id="shell-macosx">macOS</h4>
      <p>
        La terminal por defecto en todas las versiones de macOS es Bash, así que no es necesario instalar nada. Puedes acceder a Bash desde la Terminal (se encuentra en
        <code>/Applications/Utilities</code>).
        Puedes ver el <a href="https://www.youtube.com/watch?v=9LQhwETCdwY">video tutorial</a> de instalación de Git a modo de ejemplo de cómo abrir la Terminal. 
	Puede que quieras mantener la Terminal en tu dock para este taller. 
      </p>
    </div>
    <div class="col-md-4">
      <h4 id="shell-linux">Linux</h4>
      <p>
        La consola por defecto es generalmente Bash, pero si tu máquina está configurada de forma distinta puedes ejecutarla abriendo una terminal y escribiendo <code>bash</code>. No hay necesidad de instalar nada.
      </p>
    </div>
  </div>
</div> {% comment %} End of 'shell' section. {% endcomment %}
<div id="git"> {% comment %} Start of 'Git' section. La compatibilidad de GitHub  
           esta en https://help.github.com/articles/supported-browsers/{% endcomment %}
  <h3>Git</h3>

  <p>
    Git es un sistema de versión de control que permite hacer un seguimiento de
    quién hizo qué cambios, dónde y cuándo. Git tiene la opción de actualizar fácilmente
    una versión pública o compartida de tu codigo a través de plataformas como <a href="https://github.com/">github.com</a>.
    Vas a necesitar un <a href="https://help.github.com/articles/supported-browsers/">navegador web soportado</a>
    por GitHub.
  </p>
  <p>
    También necesitarás una cuenta en <a href="https://github.com/">github.com</a>
    para alguna partes de la lección de Git. Las cuentas básicas en GitHub son gratuitas.
    Te incentivamos a crear una cuenta en GitHub si todavía no tienes una.
    Por favor considera que información personal te gustaría hacer pública.
    Puedes revisar este sitio web con <a href="https://help.github.com/articles/keeping-your-email-address-private/">instrucciones
    sobre cómo mantener tu dirección de email privada</a>.
  </p>

  <div class="row">
    <div class="col-md-4">
      <h4 id="git-windows">Windows</h4>
      <p>
        Git debería estar instalado en tu computadora como parte
        de tu instalación de Bash (mira la sección anterior sobre cómo instalar Bash).
      </p>
    </div>
    <div class="col-md-4">
      <h4 id="git-macosx">macOS</h4>
      <a href="https://www.youtube.com/watch?v=9LQhwETCdwY">Video Tutorial</a>
      <p>
        <strong>Para OS X versión 10.9 y superiores</strong>, instala Git para Mac
        ejecutando <a href="http://sourceforge.net/projects/git-osx-installer/files/">el instalador más reciente de "Mavericks" que puedes descargar
        aquí</a>.
        Después de instalar Git, no vas a ver nada en tu carpeta <code>/Applications</code> porque
        Git es un programa de línea de comando.
        <strong>Para versiones más antiguas de OS X (10.5-10.8)</strong>,
        usa <a href="http://sourceforge.net/projects/git-osx-installer/files/">el instalador disponible 
        más reciente para "Snow-leopard"</a>.
      </p>
    </div>
    <div class="col-md-4">
      <h4 id="git-linux">Linux</h4>
      <p>
        Si Git no está aún instalado en tu máquina puedes tratar de instalarlo a través
        de los repositorios de tu distribución. Para Debian/Ubuntu ejecuta
        <code>sudo apt-get install git</code> y para Fedora
        <code>sudo dnf install git</code>.
      </p>
    </div>
  </div>
</div> {% comment %} End of 'Git' section. {% endcomment %}

<div id="editor"> {% comment %} Start of 'editor' section. {% endcomment %}
  <h3>Editor de Texto</h3>

  <p>

    Cuando estés escribiendo código, es bueno tener un editor de texto que esté
    optimizado para escribir código, con características como predicción automática de código, uso de colores para resaltar palabras clave, etc. El editor de texto predeterminado en macOS y
    Linux es usualmente Vim, el cual no es famoso por ser
    intuitivo. Si accidentalmente te encuentras atascado en él, intenta
    presionando la tecla de escape (<kbd>ESC</kbd>), seguido de <kbd>:</kbd>+<kbd>Q</kbd>+<kbd>!</kbd> (dos puntos, la letra 'q' minúscula, y el
    signo de exclamación), luego presionando <kbd>Enter</kbd> para regresar al intérprete de comandos.
</p>

  <div class="row">
    <div class="col-md-4">
      <h4 id="editor-windows">Windows</h4>
      <a href="https://www.youtube.com/watch?v=339AEqk9c-8">Video Tutorial</a>
      <p>
	Nano es un editor básico y el predeterminado que usan los instructores en el taller.
	Nano se instalará automáticamente junto con la instalación de Git.
      </p>
      <p>
        Otros editores que puedes usar son
        <a href="http://notepad-plus-plus.org/">Notepad++</a> o
        <a href="http://www.sublimetext.com/">Sublime Text</a>.
        <strong>
	Ten en cuenta que debes
        agregar tu directorio de instalación a la ruta del sistema. </strong>
        Si tienes dificultades, pídele a tu instructor que te ayude a hacer esto.
	</p>
    </div>
    <div class="col-md-4">
      <h4 id="editor-macosx">macOS</h4>
      <p>
        Nano es un editor básico y el predeterminado que usan los instructores en el taller.
        Mira este <a href="https://www.youtube.com/watch?v=9LQhwETCdwY">video tutorial sobre la instalación de Git y Nano</a>.
        Recuerda que el editor de texto deberá estar instalado en tu computadora antes del inicio del taller.
	</p>
      <p>
	Otros editores que puedes usar son
        <a href="http://www.barebones.com/products/textwrangler/">Text Wrangler</a> o
        <a href="http://www.sublimetext.com/">Sublime Text</a>.
      </p>
    </div>
    <div class="col-md-4">
      <h4 id="editor-linux">Linux</h4>
      <p>
      Nano es un editor básico y el predeterminado que usan los instructores en el taller. 
      </p>
      <p>
	Otros editores que puedes usar son
        <a href="https://wiki.gnome.org/Apps/Gedit">Gedit</a>,
        <a href="http://kate-editor.org/">Kate</a> o
        <a href="http://www.sublimetext.com/">Sublime Text</a>.
        Recuerda que el editor de texto deberá estar instalado en tu computadora antes del inicio del taller.
      </p>
    </div>
  </div>
</div> {% comment %} End of 'editor' section. {% endcomment %}

<div id="python"> {% comment %} Comienzo de la sección de 'Python'. Eliminar el tercer párrafo si el taller enseñará Python usando algo diferente a **Jupyter notebook**.
           Detalles en https://jupyter-notebook.readthedocs.io/en/stable/notebook.html#browser-compatibility (en inglés){% endcomment %}
  <h3>Python</h3>

  <p>
    <a href="http://python.org">Python</a> es un lenguaje popular para
    investigación, y excelente para programación de propósito general.
    Instalar todos sus paquetes de investigación individualmente puede ser
    un poco difícil, así que recomendamos
    <a href="https://www.anaconda.com/distribution/">Anaconda</a>,
    un instalador "todo en uno".
  </p>

    <p>
      Independientemente de cómo elijas instalarlo,
      <strong>por favor asegúrate de instalar alguna de las versiones de Python 3</strong>
      (por ejemplo, 3.6).
    </p>

    <p>
      Enseñaremos Python usando <a href="https://jupyter.org/">Jupyter notebook</a>,
      un ambiente de programación que se ejecuta en un navegador web. Para que funcione necesitarás un
      navegador razonablemente actualizado.
      Las versiones actuales de los navegadores Chrome, Safari y Firefox están todas
      <a href="https://jupyter-notebook.readthedocs.io/en/stable/notebook.html#browser-compatibility">soportadas</a>
      (no están soportados algunos navegadores antiguos, incluyendo Internet Explorer versión 9 y
      anteriores).
    </p>

  <div class="row">
    <div class="col-md-4">
      <h4 id="python-windows">Windows</h4>
      <a href="https://www.youtube.com/watch?v=xxQ0mzZ8UvA">Video Tutorial</a>
      <ol>
        <li>Ingresa a <a href="https://www.anaconda.com/download/#windows">https://www.anaconda.com/download/#windows</a> con tu navegador web.</li>
        <li>Descarga el instalador de Python 3 para Windows</li>
        <li>Instala Python 3 usando todas las opciones por defecto, salvo la que dice <strong>Hacer Anaconda la instalación por defecto de Python</strong>, <em>asegúrate de tildarla</em></li>
      </ol>
    </div>
    <div class="col-md-4">
      <h4 id="python-macosx">macOS</h4>
      <a href="https://www.youtube.com/watch?v=TcSAln46u9U">Video Tutorial</a>
      <ol>
        <li>Ingresa a <a href="https://www.anaconda.com/download/#macos">https://www.anaconda.com/download/#macos</a> con tu navegador web.</li>
        <li>Descarga el instalador de Python 3 para OS X.</li>
        <li>Instala Python 3 usando todas las opciones por defecto.</li>
      </ol>
    </div>
    <div class="col-md-4">
      <h4 id="python-linux">Linux</h4>
      <ol>
        <li>Ingresa a <a href="https://www.anaconda.com/download/#linux">https://www.anaconda.com/download/#linux</a> con tu navegador web.</li>
        <li>Descarga el instalador de Python 3 para Linux.<br>
          (La instalación requiere el uso de la terminal. Si no te sientes cómoda
          haciendo la instalación por tu cuenta, detente aquí y pide ayuda en el taller).
        </li>
        <li>
          Abre una terminal.
        </li>
        <li>
          Escribe <pre>bash Anaconda3-</pre> presiona tab.
          El nombre del archivo que acabas de descargar debería aparecer.
          Si no lo hace, muévete a la carpeta donde descargaste el archivo,
          por ejemplo:
          <pre>cd Downloads</pre>
          Luego, intenta nuevamente.
        </li>
        <li>
          Presiona Enter. Deberás seguir las instrucciones en la línea de comandos.
          Para moverte por el texto, presiona la tecla de espacio. Escribe <code>yes</code> y
          presiona enter para aceptar la licencia. Presiona enter para aceptar la
          ruta por defecto de los archivos. Escribe <code>yes</code> y
          presiona enter para agregar Anaconda detrás de tu <code>PATH</code>
          (esto hace a la distribución de Anaconda el Python por defecto en nuestro sistema).
        </li>
        <li>
          Cierra la terminal.
        </li>
      </ol>
    </div>
  </div>
{% comment %}
  <p>
  Una vez que terminas de instalar los programas listados arriba,
  por favor ve a <a href="setup/index.html">esta página</a>,
  que tiene instrucciones sobre cómo testear que todo ha sido instalado correctamente.
  </p>
{% endcomment %}
</div> {% comment %} Fin de la sección 'Python'. {% endcomment %}

<div id="r"> {% comment %} Start of 'R' section. {% endcomment %}
  <h3>R</h3>

  <p>
    <a href="http://www.r-project.org">R</a> es un lenguaje de programación 
    especialmente poderoso para exploración y visualización de datos, así como para análisis estadísticos. Para trabajar con R, usamos el programa 
    <a href="http://www.rstudio.com/">RStudio</a>.
  </p>

  <div class="row">
    <div class="col-md-4">
      <h4 id="r-windows">Windows</h4>
      <a href="https://www.youtube.com/watch?v=q0PjTAylwoU">Video Tutorial en inglés </a>
      <p>

        Después de descargar 
        <a href="http://cran.r-project.org/bin/windows/base/release.htm">este archivo .exe </a>
        desde <a href="http://cran.r-project.org/index.html">CRAN</a>, ábrelo e instala R.
        Además, instala el entorno de desarrollo integrado (IDE por sus siglas en inglés, Integrated Development Environment): 
        <a href="http://www.rstudio.com/ide/download/desktop">RStudio</a>.
        Ten en cuenta que si tienes cuentas separadas de usuario y administrador en tu computador, deberás correr los instaladores como administrador (haz click con el botón derecho en el 
        archivo .exe y selecciona "Ejecutar como administrador" en lugar de hacer doble click).  
        De lo contrario pueden ocurrir problemas cuando instales paquetes de R.
      </p>
    </div>
    <div class="col-md-4">
      <h4 id="r-macosx">macOS</h4>
      <a href="https://www.youtube.com/watch?v=5-ly3kyxwEg">Video Tutorial en inglés</a>
      <p>
        Después de descargar 
        <a href="http://cran.r-project.org/bin/macosx/R-latest.pkg">este archivo .pkg </a>
        desde <a href="http://cran.r-project.org/index.html">CRAN</a>, ábrelo e instala R.
        Además, instala el entorno de desarrollo integrado (IDE por sus siglas en inglés, Integrated Development Environment): 
        <a href="http://www.rstudio.com/ide/download/desktop">RStudio</a>.
      </p>
    </div>
    <div class="col-md-4">
      <h4 id="r-linux">Linux</h4>
      <p>
        Puedes descargar los archivos binarios para tu distribución
        desde <a href="http://cran.r-project.org/index.html">CRAN</a>. También 
        puedes usar tu administrador de paquetes (por ejemplo: para Debian/Ubuntu
        corre <code>sudo apt-get install r-base</code> y para Fedora corre
        <code>sudo dnf install R</code>). Además, por favor instala el entorno de desarrollo integrado (IDE por sus siglas en inglés, Integrated Development Environment): 
        <a href="http://www.rstudio.com/ide/download/desktop">RStudio</a>.
      </p>
    </div>
  </div>
</div> {% comment %} End of 'R' section. {% endcomment %}


{% comment %}
 
 
<div id="sql"> {% comment %} Start of 'SQLite' section. {% endcomment %}
  <h3>SQLite</h3>
  
  <p>
    SQL es un lenguaje de programación especializado usado para acceder y manejar bases de datos.
    En nuestras lecciones usamos un administrador de bases de dato sencillo llamado 
    <a href="http://www.sqlite.org/">SQLite</a>.
  </p>

  <div class="row">
    <div class="col-md-4">
      <h4 id="sql-windows">Windows</h4>
      <p>
        El instalador para Windows de <a href="{{site.swc_installer}}">
          {% if site.carpentry == "swc" %}

          Software Carpentry
          {% elsif site.carpentry == "dc" %}
          Data Carpentry
          {% elsif site.carpentry == "lc" %}
          Library Carpentry
          {% endif %}
	</a>
        instala SQLite para Windows.
        Si utilizaste el instalador para configurar nano, no necesitas correrlo nuevamente.
      </p>
    </div>
    <div class="col-md-4">
      <h4 id="sql-macosx">macOS</h4>
      <p>
        SQLite viene pre-instalado en macOS.
      </p>
    </div>
    <div class="col-md-4">
      <h4 id="sql-linux">Linux</h4>
      <p>
        SQLite viene pre-instalado en Linux.
      </p>
    </div>
  </div>

  <p><strong>Si instalastes Anaconda, también tienes una copia de SQLite
    <a href="https://github.com/ContinuumIO/anaconda-issues/issues/307">que no soporta <code>readline</code></a>.
    Los instructores te ayudarán a resolver cualquier problema asociado con esta instalación.</strong></p>
</div> {% comment %} End of 'SQLite' section. {% endcomment %}

<div id="openrefine"> {% comment %} Start of 'OpenRefine' section. {% endcomment %}
  <h3>OpenRefine</h3>
  <p>
    Para esta lección necesitaremos <em>OpenRefine</em> y un
    navegador web. <em>Nota:</em> este es un programa Java que corre en tu máquina (no en la nube).
    El programa corre en tu navegador, pero no necesitas una conexión a internet para que funcione.
  </p>

  <div class="row">
    <div class="col-md-4">
      <h4 id="openrefine-windows">Windows</h4>
      <p>
        Verifica que tienes Firefox o Chrome instalados en tu computador y que son utilizados como navegadores por defecto en tu máquina.
        <strong>OpenRefine corre en tu navegador web.</strong>
        Este programa no funcionará correctamente en Internet Explorer.
      </p>
      <p>Descarga el software desde <a href="http://openrefine.org/">http://openrefine.org/</a></p>
      <p>Crea un nuevo directorio llamado OpenRefine.</p>
      <p>Unzip la carpeta descargada anteriormente dentro del directorio OpenRefine haciendo click derecho y seleccionando "Extraer...". </p>
      <p>Navega hacia el directorio OpenRefine que creaste en el paso anterior.</p>
      <p>Inicio el instalador OpenRefine haciendo click en <code>google-refine.exe</code> (esto abrirá una ventana de línea de comandos, la cual puedes ignorar - solo espera a que OpenRefine se abra en tu navegador).</p>
      <p>Si usas otro navegador diferente a Firefox o Chrome, o si OpenRefine no se abre automáticamente, copia y pega cualquiera de las dos direcciones web a continuación en tu navegador: <a href="http://127.0.0.1:3333/">http://127.0.0.1:3333/</a> o <a href="http://localhost:3333">http://localhost:3333</a> para usar el programa.</p>
    </div>
    <div class="col-md-4">
      <h4 id="openrefine-mac">Mac</h4>
      <p>Verifica que tienes Firefox o Chrome instalados en tu computador y que son utilizados como navegadores por defecto en tu máquina. <strong>OpenRefine corre en tu navegador web.</strong> Este programa no funcionará correctamente en Safari.</p>
      <p>Descarga el software desde <a href="http://openrefine.org/">http://openrefine.org/</a>.</p>
      <p>Crea un nuevo directorio llamado OpenRefine.</p>
      <p>Unzip la carpeta descargada anteriormente dentro del directorio OpenRefine haciendo doble click sobre la carpeta.</p>
      <p>Navega hacia el directorio OpenRefine que creaste en el paso anterior.</p>
      <p>Instala OpenRefine arrastrando el ícono dentro de la carpeta Applications.</p>
      <p>Usa <code>Ctrl-click/abrir... </code> para abrir el programa.</p>
      <p>Si usas otro navegador diferente a Firefox o Chrome, o si OpenRefine no se abre automáticamente, copia y pega cualquiera de las dos direcciones web a continuación en tu navegador: <a href="http://127.0.0.1:3333/">http://127.0.0.1:3333/</a> o <a href="http://localhost:3333">http://localhost:3333</a> para usar el programa.</p>
    </div>
    <div class="col-md-4">
      <h4 id="openrefine-linux">Linux</h4>
      <p>Verifica que tienes Firefox o Chrome instalados en tu computador y que son utilizados como navegadores por defecto en tu máquina. <strong>OpenRefine corre en tu navegador web.</strong></p>
      <p>Descarga el software desde <a href="http://openrefine.org/">http://openrefine.org/</a>.</p>
      <p>Crea un nuevo directorio llamado OpenRefine.</p>
      <p>Unzip la carpeta descargada anteriormente dentro del directorio OpenRefine.</p>
      <p>Navega hacia el directorio OpenRefine que creaste en el paso anterior.</p>
      <p>Abre OpenRefine con la siguiente línea <code>./refine</code> en la terminal meintras estás dentro del directorio OpenRefine.</p>
      <p>Si usas otro navegador diferente a Firefox o Chrome, o si OpenRefine no se abre automáticamente, copia y pega cualquiera de las dos direcciones web a continuación en tu navegador: <a href="http://127.0.0.1:3333/">http://127.0.0.1:3333/</a> o <a href="http://localhost:3333">http://localhost:3333</a> para usar el programa.</p>
    </div>
  </div>
</div> {% comment %} Fin de la sección 'OpenRefine'. {% endcomment %}


{% endcomment %}

{% comment %}
<div id="vm">
  <h3>Máquina Virtual</h3>

  <p>
      Algunos instructores prefieren que los alumnos utilicen una máquina virtual
      en lugar de instalar software en sus propias computadoras. Si tus
      instructores han elegido hacer esto, por favor: 
  </p>
  <ol>
    <li>
      Instala <a href="https://www.virtualbox.org/">VirtualBox</a>.
    </li>
    <li>
      Descarga nuestra <a href="{{site.swc_vm}}">imagen de máquina virtual</a>.
      <strong>Advertencia:</strong> este archivo pesa 1.7 GByte, así que por favor
      descárgalo <em>antes</em> de venir al taller.
    </li>
    <li>
      Carga la máquina virtual en VirtualBox seleccionando "Importar dispositivo" 
      y cargando el archivo <code>.ova</code>.
    </li>
  </ol>
</div>
{% endcomment %}

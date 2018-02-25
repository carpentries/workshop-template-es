---
layout: workshop      # NO CAMBIAR ESTO 
carpentry: "COMPLETAR"    # qué tipo de Carpentry (ya sea "lc", "dc" o "swc")
venue: "COMPLETAR"        # nombre breve del espacio donde se lleva adelante el taller, sin dirección (por ejemplo, "Universidad de Buenos Aires")
address: "COMPLETAR"      # dirección completa del espacio donde se realizará el taller (por ejemplo, "Aula 3, Av. Córdoba 1234, Buenos Aires, Argentina")
country: "COMPLETAR"      # código ISO del país, dos letras en minúscula como por ejemplo "fr" (ver https://en.wikipedia.org/wiki/ISO_3166-1)
language: "COMPLETAR"     # código ISO del idioma, dos letras en minúscula como por ejemplo "fr" (ver https://en.wikipedia.org/wiki/ISO_639-1)
latlng: "COMPLETAR"       # latitud y longitud del espacio en formato decimal (por ejemplo, "41.7901128,-87.6007318" - usar http://www.latlong.net/)
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



<h4>Esta es la plantilla de taller. Elimina éstas líneas y utilíza la plantilla para personalizar tu propio sitio web. Si estás desarrollando un taller auto-gestionado o aún no hiciste una solicitud de pedido de taller, por favor completa este <a href="{{site.amy_site}}/submit">formulario</a> para notificarnos y que nuestra administradora pueda contactarte si necesitamos información adicional.</h4>



<h2 id="general">General Information</h2>

{% comment %}
  INTRODUCCIÓN 

  Edita el párrafo introductorio general debajo si quieres modificar la presentación.
  
{% endcomment %}
{% if page.carpentry == "swc" %}
  {% include sc/intro.html %}
{% elsif page.carpentry == "dc" %}
  {% include dc/intro.html %}
{% elsif page.carpentry == "lc" %}
  {% include lc/intro.html %}
{% endif %}

{% comment %}
  PÚBLICO

  Explica quién es tu público. (En particular, cuenta a los lectores si el taller esta abierto sólo a personas de una institución o grupo en particular).
  {% endcomment %}
{% if page.carpentry == "swc" %}
  {% include sc/who.html %}
{% elsif page.carpentry == "dc" %}
  {% include dc/who.html %}
{% elsif page.carpentry == "lc" %}
  {% include lc/who.html %}
{% endif %}

{% comment %}
  UBICACIÓN

  Este bloque muestra la dirección y enlaces a mapas con instrucciones para llegar, si la latitud y longitud fueron definidas. Puedes utilizar http://itouchmap.com/latlong.html para encontrar la lat/long de una dirección. 
{% endcomment %}
{% if page.latlng %}
<p id="where">
  <strong>Dónde:</strong>
  {{page.address}}.
  Obtener direcciones con:
  <a href="//www.openstreetmap.org/?mlat={{page.latlng | replace:',','&mlon='}}&zoom=16">OpenStreetMap</a>
  o
  <a href="//maps.google.com/maps?q={{page.latlng}}">Google Maps</a>.
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
  <strong>Requerimientos:</strong> Las asistentes deben traer una computadora portátil con sistema operativo Mac, Linux o Windows (no tablet, Chromebook, etc.), que tenga permisos de administradora habilitados. Deben tener algunos paquetes de software específicos instalados (listados <a href="#setup">aquí</a>). 
	
También es requerido que respeten el 
  {% if page.carpentry == "swc" %}
  Software Carpentry's
  {% elsif page.carpentry == "dc" %}
  Data Carpentry's
  {% elsif page.carpentry == "lc" %}
  Library Carpentry's
  {% endif %}
  <a href="{{site.swc_site}}/conduct.html">Código de Conducta</a>. 
</p>


{% comment %}
  ACCESIBILIDAD

  Modifica este bloque si existen barreras de accesibilidad o instrucciones especiales.
{% endcomment %}
<p id="accessibility">
  <strong>Accesibilidad:</strong> Estamos comprometidas a hacer que este taller sea accesible para todas. Las organizadoras comprobaron que: 
</p>
<ul>
  <li>El salón es accesible para silla de ruedas o similar</li>
  <li>Baños accesibles a disposición</li>
</ul>
<p>
  Los materiales se entregaran antes del taller, también se encuentra disponible material impreso si se pide a los organizadores con anticipación. Si podemos ayudar a facilitar el aprendizaje (por ejemplo, con intérpretes de lenguaje de señas, o instalaciones para lactancia) por favor contáctanos (utilizando los detalles de contacto listados debajo) e intentaremos proveerlos.
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



 Muestra el cronograma del taller. Edita los ítems y horarios en la tabla para ajustarlos a tu planificación. Puede que quieras modificar 'Día 1' y 'Dia 2' para mostrar fechas concretas o días de la semana.

{% endcomment %}
<h2 id="schedule">Cronograma</h2>

{% comment %} NO EDITAR LOS ENLACES A LAS ENCUESTAS {% endcomment %}
<p><em>Encuestas</em></p>
{% if page.carpentry == "swc" %}
<p>Por favor, asegúrese de completar estas encuestas antes y después del taller.</p>
<p><a href="{{ site.swc_pre_survey }}{{ site.github.project_title }}">Encuesta pre-taller</a></p>
<p><a href="{{ site.swc_post_survey }}{{ site.github.project_title }}">Encuesta post-taller</a></p>

{% elsif page.carpentry == "dc" %}
  <p>Please be sure to complete these surveys before and after the workshop.</p>
<p><a href="{{ site.dc_pre_survey }}{{ site.github.project_title }}">Pre-workshop Survey</a></p>
<p><a href="{{ site.dc_post_survey }}{{ site.github.project_title }}">Post-workshop Survey</a></p>
{% elsif page.carpentry == "lc" %}
<p>Ask your instructor about pre- and post-workshop Survey details.</p>
{% endif %}


{% if page.carpentry == "swc" %}
  {% include sc/schedule.html %}
{% elsif page.carpentry == "dc" %}
  {% include dc/schedule.html %}
{% elsif page.carpentry == "lc" %}
  {% include lc/schedule.html %}
{% endif %}

{% comment %}
  Collaborative Notes

  If you want to use an Etherpad, go to

      http://pad.software-carpentry.org/YYYY-MM-DD-site

  where 'YYYY-MM-DD-site' is the identifier for your workshop,
  e.g., '2015-06-10-esu'.
{% endcomment %}
{% if page.collaborative_notes %}
<p id="collaborative_notes">
  We will use this <a href="{{page.collaborative_notes}}">collaborative document</a> for chatting, taking notes, and sharing URLs and bits of code.
</p>
{% endif %}

<hr/>

{% comment %}
  CURRICULA

  En inglés, syllabus. Muestra que tópicos van a ser cubiertos.

  1. Si tu taller es sobre R antes que Python, remove el comentario
     alrededor de esa sección y pon un comentario alrededor de la sección Python.
  2. Algunos talleres van a remover SQL.
  3. Por favor asegúrate que la lista de tópicos está sincronizada con lo que
     pretendes enseñar.
  4. Podría ser que necesites mover los campos div con class="col-md-6" alrededor
     dentro de los div con class="row" para balancear el diseño multi-columnar.

  Este es uno de los lugares donde la gente frecuentemente comete errores, así que
  por favor observa la previsualización del sitio antes de comitear, y asegúrate
  de ejecutar también 'tools/check'.
{% endcomment %}
<h2 id="syllabus">Currícula</h2>

{% if page.carpentry == "swc" %}
  {% include sc/syllabus.html %}
{% elsif page.carpentry == "dc" %}
  {% include dc/syllabus.html %}
{% elsif page.carpentry == "lc" %}
  {% include lc/syllabus.html %}
{% endif %}

<hr/>

{% comment %}
  CONFIGURACIÓN
 
  Borra las secciones irrelevantes de las instrucciones de configuración. Cada sección esta dentro de un 'div' que no contiene clases para que el comienzo y el final sean más fáciles de encontrar.
  Este es otro lugar en donde las personas cometen errores de forma mas frecuente, por favor previsualiza tu sitio antes de commitear y además asegurate de ejecutar 'tools/check'.
  
{% endcomment %}

<h2 id="setup">Setup</h2>

<p>
  To participate in a
  {% if page.carpentry == "swc" %}
  Software Carpentry
  {% elsif page.carpentry == "dc" %}
  Data Carpentry
  {% elsif page.carpentry == "lc" %}
  Library Carpentry
  {% endif %}
  workshop,
  you will need access to the software described below.
  In addition, you will need an up-to-date web browser.
</p>
<p>
  We maintain a list of common issues that occur during installation as a reference for instructors
  that may be useful on the
  <a href = "{{site.swc_github}}/workshop-template/wiki/Configuration-Problems-and-Solutions">Configuration Problems and Solutions wiki page</a>.
</p>

<div id="shell"> {% comment %} Start of 'shell' section. {% endcomment %}
  <h3>The Bash Shell</h3>

  <p>
    Bash is a commonly-used shell that gives you the power to do simple
    tasks more quickly.
  </p>

  <div class="row">
    <div class="col-md-4">
      <h4 id="shell-windows">Windows</h4>
      <a href="https://www.youtube.com/watch?v=339AEqk9c-8">Video Tutorial</a>
      <ol>
        <li>Download the Git for Windows <a href="https://git-for-windows.github.io/">installer</a>.</li>
        <li>Run the installer and follow the steps bellow:
          <ol>
            {% comment %} Git 2.8.2 Setup {% endcomment %}
            {% comment %} Information {% endcomment %}
            <li>Click on "Next".</li>
            {% comment %} Select Components {% endcomment %}
            <li>Click on "Next".</li>
            {% comment %} Adjusting your PATH environment {% endcomment %}
            <li>
              <strong>
                Keep "Use Git from the Windows Command Prompt" selected and click on "Next".
              </strong>
                If you forgot to do this programs that you need for the workshop will not work properly.
                If this happens rerun the installer and select the appropriate option.
            </li>
            {% comment %} Choosing the SSH executable {% endcomment %}
            <li>Click on "Next".</li>
            {% comment %} Configuring the line ending conversións {% endcomment %}
            <li>
              <strong>
                Keep "Checkout Windows-style, commit Unix-style line endings" selected and click on "Next".
              </strong>
            </li>
            {% comment %} Configuring the terminal emulator to use with Git Bash {% endcomment %}
            <li>
              <strong>
                Keep "Use Windows' default console window" selected and click on "Next".
              </strong>
            </li>
            {% comment %} Configuring experimental performance tweaks {% endcomment %}
            <li>Click on "Install".</li>
            {% comment %} Installing {% endcomment %}
            {% comment %} Completing the Git Setup Wizard {% endcomment %}
            <li>Click on "Finish".</li>
          </ol>
        </li>
        <li>
          If your "HOME" environment variable is not set (or you don't know what this is):
          <ol>
            <li>Open command prompt (Open Start Menu then type <code>cmd</code> and press [Enter])</li>
            <li>
              Type the following line into the command prompt window exactly as shown:
              <p><code>setx HOME "%USERPROFILE%"</code></p>
            </li>
            <li>Press [Enter], you should see <code>SUCCESS: Specified value was saved.</code></li>
            <li>Quit command prompt by typing <code>exit</code> then pressing [Enter]</li>
          </ol>
        </li>
      </ol>
      <p>This will provide you with both Git and Bash in the Git Bash program.</p>
    </div>
    <div class="col-md-4">
      <h4 id="shell-macosx">macOS</h4>
      <p>
        The default shell in all versións of macOS is Bash, so no
        need to install anything.  You access Bash from the Terminal
        (found in
        <code>/Applications/Utilities</code>).
        See the Git installation <a href="https://www.youtube.com/watch?v=9LQhwETCdwY ">video tutorial</a>
        for an example on how to open the Terminal.
        You may want to keep
        Terminal in your dock for this workshop.
      </p>
    </div>
    <div class="col-md-4">
      <h4 id="shell-linux">Linux</h4>
      <p>
        The default shell is usually Bash, but if your
        machine is set up differently you can run it by opening a
        terminal and typing <code>bash</code>.  There is no need to
        install anything.
      </p>
    </div>
  </div>
</div> {% comment %} End of 'shell' section. {% endcomment %}

<div id="git"> {% comment %} Start of 'Git' section. La compatibilidad de GitHub  
           esta en https://help.github.com/articles/supported-browsers/{% endcomment %}
  <h3>Git</h3>

  <p>
    Git es un sistema de versión de control que permite hacer un seguimiento de
    quien hiso que cambios, donde y cuando, tiene la opción de actualizar fácilmente
    una versión publica o compartida de tu codigo en <a href="https://github.com/">github.com</a>.
    Vas a neesitar un navegador web
    <a href="https://help.github.com/articles/supported-browsers/">soportado</a>
    (actualmente Chrome, Firefox, Safari, o Internet Explorer 9 para arriba)
  </p>
  <p>
    Vas a necesitar una cuenta en <a href="https://github.com/">github.com</a>
    para alguna partes de la lección de Git. Las cuentas basicas en GitHub son gratuitas.
    Te incentivamos a crear una cuenta en GitHub si todavia no tenes una.
    Por favor considera que información persional te gustaria hacer publica.
    Por  ejemplo, por ahi te gustaria revisar algunas de estas
    <a href="https://help.github.com/articles/keeping-your-email-address-private/">instrucciones
    para mantener tu dirección de email privada</a> escrita por GitHub.
  </p>

  <div class="row">
    <div class="col-md-4">
      <h4 id="git-windows">Windows</h4>
      <p>
        Git deberia estar instalado en tu computadora como parte
        de tu instalacion de Bash (escrito mas abajo).
      </p>
    </div>
    <div class="col-md-4">
      <h4 id="git-macosx">macOS</h4>
      <a href="https://www.youtube.com/watch?v=9LQhwETCdwY ">Video Tutorial</a>
      <p>
        <strong>Para OS X 10.9 y superiores</strong>, instala Git para Mac
        ejecutando el instalador mas reciente de "mavericks", podes descargarlo
        <a href="http://sourceforge.net/projects/git-osx-installer/files/">de esta lista</a>.
        Después de instalar Git, no vas a ver nada en tu carpeta <code>/Applications</code> por que
        Git es un programa de linea de comando.
        <strong>Para versiónes mas antiguas de OS X (10.5-10.8)</strong>
        Usa el instalador <a href="http://sourceforge.net/projects/git-osx-installer/files/"> disponible </a>
        mas reciente de "snow-leopard".
      </p>
    </div>
    <div class="col-md-4">
      <h4 id="git-linux">Linux</h4>
      <p>
        Si Git no esta ya en tu maquina podes tratar de instalarlo a través
        de los repositorios de tu distribución. Para Debian/Ubuntu corre
        <code>sudo apt-get install git</code> y para Fedora
        <code>sudo dnf install git</code>
      </p>
    </div>
  </div>
</div> {% comment %} End of 'Git' section. {% endcomment %}

<div id="editor"> {% comment %} Start of 'editor' section. {% endcomment %}
  <h3>Text Editor</h3>

  <p>
	Si accidentamente te encontraste a find yourself stuck in it, prueba typing la tecla 
escape, seguido por <code>:q!</code>(colon, olon, lower-case 'q',
    exclamation mark),
	...
	Cuando estás escribiendo código, es bueno tener un editor de texto que sea
    optimizado para escribir código, con características como automático
    código de color de las palabras clave. El editor de texto predeterminado en macOS y
    Linux usualmente se establece en Vim, que no es famoso por ser
    intuitivo. Si accidentalmente te encuentras atascado en él, intenta
    escribiendo la clave de escape, seguido de <code>: q! </code> (dos puntos, minúscula 'q',
    signo de exclamación), luego presionando Volver para regresar al intérprete de comandos.
</p>

  <div class="row">
    <div class="col-md-4">
      <h4 id="editor-windows">Windows</h4>
      <a href="https://www.youtube.com/watch?v=339AEqk9c-8">Video Tutorial</a>
      <p>
	nano es un editor básico y el predeterminado que usan los instructores en el taller.
	Para instalarlo,
	Descargas el<a href="{{site.swc_installer}}">
          {% if page.carpentry == "swc" %}
          Software Carpentry
          {% elsif page.carpentry == "dc" %}
          Data Carpentry
          {% elsif page.carpentry == "lc" %}
          Libreria Carpentry
          {% endif %}
          Instalador de Windowns
	</a>
	 y doble click en el archivo para correrlo.
        <strong>Esta instacion requiere una coneccion de Internet activa.</strong>
      </p>
      <p>
        Otros editores que puedes usar son
        <a href="http://notepad-plus-plus.org/">Notepad++</a> or
        <a href="http://www.sublimetext.com/">Sublime Text</a>.
        <strong>
	Tenga en cuenta que debe
        agregue su directorio de instalación a la ruta del sistema. </ strong>
        Por favor, Pídale a su instructor que lo ayude a hacer esto.
	</p>
    </div>
    <div class="col-md-4">
      <h4 id="editor-macosx">macOS</h4>
      <p>
	nano es un editor básico y el predeterminado que usan los instructores en el taller.
        Mira la instalacion de Git <a href="https://www.youtube.com/watch?v=9LQhwETCdwY ">video tutorial</a>
       	Para un ejemplo sobre cómo abrir nano.
        Debe estar preinstalado.
	</p>
      <p>
	Otros editores que puedes usar son
        <a href="http://www.barebones.com/products/textwrangler/">Text Wrangler</a> or
        <a href="http://www.sublimetext.com/">Sublime Text</a>.
      </p>
    </div>
    <div class="col-md-4">
      <h4 id="editor-linux">Linux</h4>
      <p>
	nano es un editor básico y el predeterminado que usan los instructores en el taller. 
	Para instalarlo,
      </p>
      <p>
	Otros editores que puedes usar son
        <a href="https://wiki.gnome.org/Apps/Gedit">Gedit</a>,
        <a href="http://kate-editor.org/">Kate</a> or
        <a href="http://www.sublimetext.com/">Sublime Text</a>.
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
          haciendo la  instalación por tu cuenta, detente aquí y pide ayuda en el taller)
        </li>
        <li>
          Abre una terminal.
        </li>
        <li>
          Escribe <pre>bash Anaconda3-</pre> presiona tab.
          El nombre del archivo que acabas de descargar debería aparecer
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
    especialmente poderoso para exploración de datos, visualización y  
    análisis estadístico. Para trabajar con R, usamos
    <a href="http://www.rstudio.com/">RStudio</a>.
  </p>

  <div class="row">
    <div class="col-md-4">
      <h4 id="r-windows">Windows</h4>
      <a href="https://www.youtube.com/watch?v=q0PjTAylwoU">Video Tutorial en inglés </a>
      <p>



        Instala R descargando e instalando
        <a href="http://cran.r-project.org/bin/windows/base/release.htm">este archivo .exe </a>
        desde <a href="http://cran.r-project.org/index.html">CRAN</a>.
        Además, instala el entorno de desarrollo integrado, en inglés Integrated Development Environment (IDE) 
        <a href="http://www.rstudio.com/ide/download/desktop">RStudio</a>.
        Ten en cuenta que si tienes cuentas separadas de usuario y administrador,
	debes correr los instaladores como administrador (haz click derecho en el 
        archivo .exe y selecciona "Ejecutar como administrador" en lugar de hacer doble click)  
        De lo contrario pueden ocurrir problemas, por ejemplo, cuando instales paquetes de R.


      </p>
    </div>
    <div class="col-md-4">
      <h4 id="r-macosx">macOS</h4>
      <a href="https://www.youtube.com/watch?v=5-ly3kyxwEg">Video Tutorial en inglés</a>
      <p>
        Instala R descargando e instalando
        <a href="http://cran.r-project.org/bin/macosx/R-latest.pkg">este archivo .pkg </a>
        desde <a href="http://cran.r-project.org/index.html">CRAN</a>.
        Además, instala el entorno de desarrollo integrado, en inglés Integrated Development Environment (IDE) 
        <a href="http://www.rstudio.com/ide/download/desktop">RStudio</a>.
      </p>
    </div>
    <div class="col-md-4">
      <h4 id="r-linux">Linux</h4>
      <p>
        Puedes descargar los archivos binarios para tu distribución
        desde <a href="http://cran.r-project.org/index.html">CRAN</a>. O
        puedes usar tu administrador de paquetes (por ejemplo: para Debian/Ubuntu
        corre <code>sudo apt-get install r-base</code> y para Fedora corre
        <code>sudo dnf install R</code>).  Además, por favor instala el entorno de desarrollo integrado, 
	en inglés Integrated Development Environment (IDE) 
        <a href="http://www.rstudio.com/ide/download/desktop">RStudio</a>.
      </p>
    </div>
  </div>
</div> {% comment %} End of 'R' section. {% endcomment %}

<div id="sql"> {% comment %} Start of 'SQLite' section. {% endcomment %}
  <h3>SQLite</h3>

  <p>
    SQL is a specialized programming language used with databases.  We
    use a simple database manager called
    <a href="http://www.sqlite.org/">SQLite</a> in our lessons.
  </p>

  <p>
    SQL es un lenguaje de programación usado en bases de datos.
    Nosotras en nuestras lecciones usamos
    <a href="http://www.sqlite.org/">SQLite</a>.
  </p>

  <div class="row">
    <div class="col-md-4">
      <h4 id="sql-windows">Windows</h4>
      <p>
        The <a href="{{site.swc_installer}}">
          {% if page.carpentry == "swc" %}
          Software Carpentry
          {% elsif page.carpentry == "dc" %}
          Data Carpentry
          {% elsif page.carpentry == "lc" %}
          Library Carpentry
          {% endif %}
          Windows Installer
	</a>
        installs SQLite for Windows.
        If you used the installer to configure nano, you don't need to run it again.
      </p>
    </div>
    <div class="col-md-4">
      <h4 id="sql-macosx">macOS</h4>
      <p>
        SQLite comes pre-installed on macOS.
      </p>
    </div>
    <div class="col-md-4">
      <h4 id="sql-linux">Linux</h4>
      <p>
        SQLite comes pre-installed on Linux.
      </p>
    </div>
  </div>

  <p><strong>If you installed Anaconda, it also has a copy of SQLite
    <a href="https://github.com/ContinuumIO/anaconda-issues/issues/307">without support to <code>readline</code></a>.
    Instructors will provide a workaround for it if needed.</strong></p>
</div> {% comment %} End of 'SQLite' section. {% endcomment %}

<div id="openrefine"> {% comment %} Start of 'OpenRefine' section. {% endcomment %}
  <h3>OpenRefine</h3>
  <p>
    For this lesson you will need <em>OpenRefine</em> and a
    web browser. <em>Note:</em> this is a Java program that runs on your machine (not in the cloud).
    It runs inside a web browser, but no web connection is needed.
  </p>

  <div class="row">
    <div class="col-md-4">
      <h4 id="openrefine-windows">Windows</h4>
      <p>
        Check that you have either the Firefox or the Chrome browser installed and set as your default browser.
        <strong>OpenRefine runs in your default browser.</strong>
        It will not run correctly in Internet Explorer.
      </p>
      <p>Download software from <a href="http://openrefine.org/">http://openrefine.org/</a></p>
      <p>Create a new directory called OpenRefine.</p>
      <p>Unzip the downloaded file into the OpenRefine directory by right-clicking and selecting "Extract ...". </p>
      <p>Go to your newly created OpenRefine directory.</p>
      <p>Launch OpenRefine by clicking <code>google-refine.exe</code> (this will launch a command prompt window, but you can ignore that - just wait for OpenRefine to open in the browser).</p>
      <p>If you are using a different browser, or if OpenRefine does not automatically open for you, point your browser at <a href="http://127.0.0.1:3333/">http://127.0.0.1:3333/</a> or <a href="http://localhost:3333">http://localhost:3333</a> to use the program.</p>
    </div>
    <div class="col-md-4">
      <h4 id="openrefine-mac">Mac</h4>
      <p>Check that you have either the Firefox or the Chrome browser installed and set as your default browser. <strong>OpenRefine runs in your default browser.</strong> It may not run correctly in Safari.</p>
      <p>Download software from <a href="http://openrefine.org/">http://openrefine.org/</a>.</p>
      <p>Create a new directory called OpenRefine.</p>
      <p>Unzip the downloaded file into the OpenRefine directory by double-clicking it.</p>
      <p>Go to your newly created OpenRefine directory.</p>
      <p>Launch OpenRefine by dragging the icon into the Applications folder.</p>
      <p>Use <code>Ctrl-click/Open ... </code> to launch it.</p>
      <p>If you are using a different browser, or if OpenRefine does not automatically open for you, point your browser at <a href="http://127.0.0.1:3333/">http://127.0.0.1:3333/</a> or <a href="http://localhost:3333">http://localhost:3333</a> to use the program.</p>
    </div>
    <div class="col-md-4">
      <h4 id="openrefine-linux">Linux</h4>
      <p>Check that you have either the Firefox or the Chrome browser installed and set as your default browser. <strong>OpenRefine runs in your default browser.</strong></p>
      <p>Download software from <a href="http://openrefine.org/">http://openrefine.org/</a>.</p>
      <p>Make a directory called OpenRefine.</p>
      <p>Unzip the downloaded file into the OpenRefine directory.</p>
      <p>Go to your newly created OpenRefine directory.</p>
      <p>Launch OpenRefine by entering <code>./refine</code> into the terminal within the OpenRefine directory.</p>
      <p>If you are using a different browser, or if OpenRefine does not automatically open for you, point your browser at <a href="http://127.0.0.1:3333/">http://127.0.0.1:3333/</a> or <a href="http://localhost:3333">http://localhost:3333</a> to use the program.</p>
    </div>
  </div>
</div> {% comment %} End of 'OpenRefine' section. {% endcomment %}

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
      Instalar <a href="https://www.virtualbox.org/">VirtualBox</a>.
    </li>
    <li>
      Descargue nuestra <a href="{{site.swc_vm}}">imagen de máquina virtual</a>.
      <strong>Advertencia:</strong> este archivo pesa 1.7 GByte, entonces por favor
      descárguelo <em>antes</em> de venir al taller.
    </li>
    <li>
      Cargue la máquina virtual en VirtualBox seleccionando "Importar dispositivo" 
      y cargando el archivo <code>.ova</code> .
    </li>
  </ol>
</div>
{% endcomment %}

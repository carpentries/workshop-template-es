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

{% comment %} See instructions in the comments below for how to edit specific sections of this workshop template. {% endcomment %}

{% comment %}
  HEADER

  Edit the values in the block above to be appropriate for your workshop.
  If the value is not 'true', 'false', 'null', or a number, please use
  double quotation marks around the value, unless specified otherwise.
  And run 'make workshop-check' *before* committing to make sure that changes are good.
{% endcomment %}

{% comment %}
  EVENTBRITE

  This block includes the Eventbrite registration widget if
  'eventbrite' has been set in the header.  You can delete it if you
  are not using Eventbrite, or leave it in, since it will not be
  displayed if the 'eventbrite' field in the header is not set.
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

<h4>This is the workshop template. Delete these lines and use it to customize your own website.
If you are running a self-organized workshop or have not put in a workshop request yet, please also fill in
<a href="{{site.amy_site}}/submit">this workshop request form</a> to let us know about your workshop
and our administrator may contact you if we need any extra information.</h4>

<h2 id="general">General Information</h2>

{% comment %}
  INTRODUCTION

  Edit the general explanatory paragraph below if you want to change
  the pitch.
{% endcomment %}
{% if page.carpentry == "swc" %}
  {% include sc/intro.html %}
{% elsif page.carpentry == "dc" %}
  {% include dc/intro.html %}
{% elsif page.carpentry == "lc" %}
  {% include lc/intro.html %}
{% endif %}

{% comment %}
  AUDIENCE

  Explain who your audience is.  (In particular, tell readers if the
  workshop is only open to people from a particular institution.
{% endcomment %}
{% if page.carpentry == "swc" %}
  {% include sc/who.html %}
{% elsif page.carpentry == "dc" %}
  {% include dc/who.html %}
{% elsif page.carpentry == "lc" %}
  {% include lc/who.html %}
{% endif %}

{% comment %}
  LOCATION

  This block displays the address and links to maps showing directions
  if the latitude and longitude of the workshop have been set.  You
  can use http://itouchmap.com/latlong.html to find the lat/long of an
  address.
{% endcomment %}
{% if page.latlng %}
<p id="where">
  <strong>Where:</strong>
  {{page.address}}.
  Get directions with
  <a href="//www.openstreetmap.org/?mlat={{page.latlng | replace:',','&mlon='}}&zoom=16">OpenStreetMap</a>
  or
  <a href="//maps.google.com/maps?q={{page.latlng}}">Google Maps</a>.
</p>
{% endif %}

{% comment %}
  DATE

  This block displays the date and links to Google Calendar.
{% endcomment %}
{% if page.humandate %}
<p id="when">
  <strong>When:</strong>
  {{page.humandate}}.
  {% include workshop_calendar.html %}
</p>
{% endif %}

{% comment %}
  SPECIAL REQUIREMENTS

  Modify the block below if there are any special requirements.
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
  ACCESSIBILITY

  Modify the block below if there are any barriers to accessibility or
  special instructions.
{% endcomment %}
<p id="accessibility">
  <strong>Accessibility:</strong> We are committed to making this workshop
  accessible to everybody.
  The workshop organizers have checked that:
</p>
<ul>
  <li>The room is wheelchair / scooter accessible.</li>
  <li>Accessible restrooms are available.</li>
</ul>
<p>
  Materials will be provided in advance of the workshop and
  large-print handouts are available if needed by notifying the
  organizers in advance.  If we can help making learning easier for
  you (e.g. sign-language interpreters, lactation facilities) please
  get in touch (using contact details below) and we will
  attempt to provide them.
</p>

{% comment %}
  CONTACT EMAIL ADDRESS

  Display the contact email address set in the configuration file.
{% endcomment %}
<p id="contact">
  <strong>Contact</strong>:
  Please email
  {% if page.email %}
    {% for email in page.email %}
      {% if forloop.last and page.email.size > 1 %}
        or
      {% else %}
        {% unless forloop.first %}
        ,
        {% endunless %}
      {% endif %}
      <a href='mailto:{{email}}'>{{email}}</a>
    {% endfor %}
  {% else %}
    to-be-announced
  {% endif %}
  for more information.
</p>

<hr/>

{% comment %}
  CRONOGRAMA

  Muestra el cronograma del taller. Edite los elementos y los tiempos de la tabla para que coincidan con sus planes. Quizás también quiera cambiar 'Día 1' y 'Día 2' para que coincidan con las fechas o los días de la semana.
{% endcomment %}
<h2 id="schedule">Cronograma</h2>

{% comment %} NO EDITAR LOS ENLACES A LAS ENCUESTAS {% endcomment %}
<p><em>Encuestas</em></p>
{% if page.carpentry == "swc" %}
<p>Por favor, asegúrese de completar estas encuestas antes y después del taller.</p>
<p><a href="{{ site.swc_pre_survey }}{{ site.github.project_title }}">Encuesta pre-taller</a></p>
<p><a href="{{ site.swc_post_survey }}{{ site.github.project_title }}">Encuesta post-taller</a></p>
{% elsif page.carpentry == "dc" %}
  <p>Por favor, asegúrese de completar estas encuestas antes y después del taller.</p>
<p><a href="{{ site.dc_pre_survey }}{{ site.github.project_title }}">Encuesta pre-taller</a></p>
<p><a href="{{ site.dc_post_survey }}{{ site.github.project_title }}">Encuesta post-taller</a></p>
{% elsif page.carpentry == "lc" %}
<p>Pregunta a tu instructor por los detalles de las encuestas pre- y post-taller.</p>
{% endif %}


{% if page.carpentry == "swc" %}
  {% include sc/schedule.html %}
{% elsif page.carpentry == "dc" %}
  {% include dc/schedule.html %}
{% elsif page.carpentry == "lc" %}
  {% include lc/schedule.html %}
{% endif %}

{% comment %}
  Notas colaborativas

  Si quiere usar un Etherpad, puede ir a

      http://pad.software-carpentry.org/YYYY-MM-DD-site

  donde 'YYYY-MM-DD-site' es el identificador para su taller,
  por ejemplo: '2018-06-10-esu'.
{% endcomment %}
{% if page.collaborative_notes %}
<p id="collaborative_notes">
  Usaremos este <a href="{{page.collaborative_notes}}">documento colaborativo</a> para conversar, tomar notas y compartir URLs y líneas de código.
</p>
{% endif %}

<hr/>

{% comment %}
  SYLLABUS

  Show what topics will be covered.

  1. If your workshop is R rather than Python, remove the comment
     around that section and put a comment around the Python section.
  2. Some workshops will delete SQL.
  3. Please make sure the list of topics is synchronized with what you
     intend to teach.
  4. You may need to move the div's with class="col-md-6" around inside
     the div's with class="row" to balance the multi-column layout.

  This is one of the places where people frequently make mistakes, so
  please preview your site before committing, and make sure to run
  'tools/check' as well.
{% endcomment %}
<h2 id="syllabus">Syllabus</h2>

{% if page.carpentry == "swc" %}
  {% include sc/syllabus.html %}
{% elsif page.carpentry == "dc" %}
  {% include dc/syllabus.html %}
{% elsif page.carpentry == "lc" %}
  {% include lc/syllabus.html %}
{% endif %}

<hr/>

{% comment %}
  SETUP

  Delete irrelevant sections from the setup instructions.  Each
  section is inside a 'div' without any classes to make the beginning
  and end easier to find.

  This is the other place where people frequently make mistakes, so
  please preview your site before committing, and make sure to run
  'tools/check' as well.
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
                Dejar seleccionado "Utilizar ventana de consola de Windows por defecto" y click en "Next".
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
              Estcribe la siguiente línea en la ventana de la terminal exactamente como sigue:
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
        Puedes ver el <a href="https://www.youtube.com/watch?v=9LQhwETCdwY ">video tutorial</a> de instalación de Git a modo de ejemplo de cómo abrir la Terminal. 
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

<div id="git"> {% comment %} Start of 'Git' section. GitHub browser compatability
           is given at https://help.github.com/articles/supported-browsers/{% endcomment %}
  <h3>Git</h3>
  <p>
    Git is a version control system that lets you track who made changes
    to what when and has options for easily updating a shared or public
    version of your code
    on <a href="https://github.com/">github.com</a>. You will need a
    <a href="https://help.github.com/articles/supported-browsers/">supported</a>
    web browser (current versions of Chrome, Firefox or Safari,
    or Internet Explorer version 9 or above).
  </p>
  <p>
    You will need an account at <a href="https://github.com/">github.com</a>
    for parts of the Git lesson. Basic GitHub accounts are free. We encourage
    you to create a GitHub account if you don't have one already.
    Please consider what personal information you'd like to reveal. For
    example, you may want to review these
    <a href="https://help.github.com/articles/keeping-your-email-address-private/">instructions
    for keeping your email address private</a> provided at GitHub.
  </p>

  <div class="row">
    <div class="col-md-4">
      <h4 id="git-windows">Windows</h4>
      <p>
        Git should be installed on your computer as part of your Bash
        install (described above).
      </p>
    </div>
    <div class="col-md-4">
      <h4 id="git-macosx">macOS</h4>
      <a href="https://www.youtube.com/watch?v=9LQhwETCdwY ">Video Tutorial</a>
      <p>
        <strong>For OS X 10.9 and higher</strong>, install Git for Mac
        by downloading and running the most recent "mavericks" installer from
        <a href="http://sourceforge.net/projects/git-osx-installer/files/">this list</a>.
        After installing Git, there will not be anything in your <code>/Applications</code> folder,
        as Git is a command line program.
        <strong>For older versions of OS X (10.5-10.8)</strong> use the
        most recent available installer labelled "snow-leopard"
        <a href="http://sourceforge.net/projects/git-osx-installer/files/">available here</a>.
      </p>
    </div>
    <div class="col-md-4">
      <h4 id="git-linux">Linux</h4>
      <p>
        If Git is not already available on your machine you can try to
        install it via your distro's package manager. For Debian/Ubuntu run
        <code>sudo apt-get install git</code> and for Fedora run
        <code>sudo dnf install git</code>.
      </p>
    </div>
  </div>
</div> {% comment %} End of 'Git' section. {% endcomment %}

<div id="editor"> {% comment %} Start of 'editor' section. {% endcomment %}
  <h3>Text Editor</h3>

  <p>
    When you're writing code, it's nice to have a text editor that is
    optimized for writing code, with features like automatic
    color-coding of key words.  The default text editor on macOS and
    Linux is usually set to Vim, which is not famous for being
    intuitive.  if you accidentally find yourself stuck in it, try
    typing the escape key, followed by <code>:q!</code> (colon, lower-case 'q',
    exclamation mark), then hitting Return to return to the shell.
  </p>

  <div class="row">
    <div class="col-md-4">
      <h4 id="editor-windows">Windows</h4>
      <a href="https://www.youtube.com/watch?v=339AEqk9c-8">Video Tutorial</a>
      <p>
        nano is a basic editor and the default that instructors use in the workshop.
        To install it,
        download the <a href="{{site.swc_installer}}">
          {% if page.carpentry == "swc" %}
          Software Carpentry
          {% elsif page.carpentry == "dc" %}
          Data Carpentry
          {% elsif page.carpentry == "lc" %}
          Library Carpentry
          {% endif %}
          Windows installer
	</a>
        and double click on the file to run it.
        <strong>This installer requires an active internet connection.</strong>
      </p>
      <p>
        Others editors that you can use are
        <a href="http://notepad-plus-plus.org/">Notepad++</a> or
        <a href="http://www.sublimetext.com/">Sublime Text</a>.
        <strong>Be aware that you must
          add its installation directory to your system path.</strong>
        Please ask your instructor to help you do this.
      </p>
    </div>
    <div class="col-md-4">
      <h4 id="editor-macosx">macOS</h4>
      <p>
        nano is a basic editor and the default that instructors use in the workshop.
        See the Git installation <a href="https://www.youtube.com/watch?v=9LQhwETCdwY ">video tutorial</a>
        for an example on how to open nano.
        It should be pre-installed.
      </p>
      <p>
        Others editors that you can use are
        <a href="http://www.barebones.com/products/textwrangler/">Text Wrangler</a> or
        <a href="http://www.sublimetext.com/">Sublime Text</a>.
      </p>
    </div>
    <div class="col-md-4">
      <h4 id="editor-linux">Linux</h4>
      <p>
        nano is a basic editor and the default that instructors use in the workshop.
        It should be pre-installed.
      </p>
      <p>
        Others editors that you can use are
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
    <a href="http://www.r-project.org">R</a> is a programming language
    that is especially powerful for data exploration, visualization, and
    statistical analysis. To interact with R, we use
    <a href="http://www.rstudio.com/">RStudio</a>.
  </p>

  <div class="row">
    <div class="col-md-4">
      <h4 id="r-windows">Windows</h4>
      <a href="https://www.youtube.com/watch?v=q0PjTAylwoU">Video Tutorial</a>
      <p>
        Install R by downloading and running
        <a href="http://cran.r-project.org/bin/windows/base/release.htm">this .exe file</a>
        from <a href="http://cran.r-project.org/index.html">CRAN</a>.
        Also, please install the
        <a href="http://www.rstudio.com/ide/download/desktop">RStudio IDE</a>.
        Note that if you have separate user and admin accounts, you should run the
        installers as administrator (right-click on .exe file and select "Run as
        administrator" instead of double-clicking). Otherwise problems may occur later,
        for example when installing R packages.
      </p>
    </div>
    <div class="col-md-4">
      <h4 id="r-macosx">macOS</h4>
      <a href="https://www.youtube.com/watch?v=5-ly3kyxwEg">Video Tutorial</a>
      <p>
        Install R by downloading and running
        <a href="http://cran.r-project.org/bin/macosx/R-latest.pkg">this .pkg file</a>
        from <a href="http://cran.r-project.org/index.html">CRAN</a>.
        Also, please install the
        <a href="http://www.rstudio.com/ide/download/desktop">RStudio IDE</a>.
      </p>
    </div>
    <div class="col-md-4">
      <h4 id="r-linux">Linux</h4>
      <p>
        You can download the binary files for your distribution
        from <a href="http://cran.r-project.org/index.html">CRAN</a>. Or
        you can use your package manager (e.g. for Debian/Ubuntu
        run <code>sudo apt-get install r-base</code> and for Fedora run
        <code>sudo dnf install R</code>).  Also, please install the
        <a href="http://www.rstudio.com/ide/download/desktop">RStudio IDE</a>.
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
  <h3>Virtual Machine</h3>

  <p>
    Some instructors prefer to have learners use a virtual machine (VM)
    rather than install software on their own computers.  If your
    instructors have chosen to do this, please:
  </p>
  <ol>
    <li>
      Install <a href="https://www.virtualbox.org/">VirtualBox</a>.
    </li>
    <li>
      Download our <a href="{{site.swc_vm}}">VM image</a>.
      <strong>Warning:</strong> this file is 1.7 GByte, so please
      download it <em>before</em> coming to your workshop.
    </li>
    <li>
      Load the VM into VirtualBox by selecting "Import Appliance" and
      loading the <code>.ova</code> file.
    </li>
  </ol>
</div>
{% endcomment %}

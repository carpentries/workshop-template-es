# workshop-template-es

**This template for workshop websites is functional and available for use.** 
**However, the repository is not actively maintained due to a lack of Spanish language expertise in The Carpentries Curriculum Team, 
and some content may be outdated.**
**Please contact us if you would like to help maintain and update this resource.**

Este repositorio contiene la plantilla con la cual puedes crear sitios web para los talleres de [Software Carpentry][swc-site] y [Data Carpentry][dc-site].

1. Por favor no hagas un **fork** de este repositorio desde GitHub, directamente.
    Utiliza el importador de GitHub siguiendo [las instrucciones](#creating-a-repository)
    para copiar el repositorio `workshop-template-es` y, así, editarlo de acuerdo a las necesidades de tu taller.

2. Trabaja en el **branch** `gh-pages` de tu repositorio,
    ya que este es el contenido que será
    [publicado automáticamente como un sitio web por GitHub][github-project-pages].

3. Una vez que hayas terminado, por favor avísanos [por medio de un email] cual será la URL de tu taller. Si se trata de un taller auto-organizado, también debes [completar el formulario para talleres autoorganizados][self-organised-workshop-form], para que podamos seguir el desarrollo de todos los talleres. En nuestro sitio web, construimos una lista de talleres a partir de los datos que incluyas en tu página `index.md`. Sólo podemos hacer eso si [editas][customization] tu página correctamente *y* nos informas sobre la URL del taller.

Si tienes problemas
o ideas sobre cómo hacer este proceso de una forma más simple,
por favor [ponte en contacto](#getting-and-giving-help).
Las páginas para [personalizar tu sitio web][customization],
las [FAQ][faq],
y las [notas de diseño][design] tienen más detalles sobre lo que hacemos y por qué.
Y ten en cuenta: si estás enseñando sobre Git,
por favor [crea un repositorio aparte](# setting-up-a-separate-repository-for-learners)
para que los estudiantes puedan practicar.

## Creating a Repository

1.  Log in to GitHub.
    (If you do not have an account, you can quickly create one for free.)
    You must be logged in for the remaining steps to work.

2.  Go to [GitHub's importer][importer].

3.  Paste the url of this repo as the old repository to clone:
    <https://github.com/carpentries-es/workshop-template-es>.

4.  Select the owner for your new repository.
    (This will probably be you, but may instead be an organization you belong to.)

5.  Choose a name for your workshop website repository.
    This name should have the form `YYYY-MM-DD-site`,
    e.g., `2016-12-01-miskatonic`,
    where `YYYY-MM-DD` is the start date of the workshop.

6.  Make sure the repository is public.

7.  At this point, you should have a page like this:

    ![](fig/using-github-import.png?raw=true)

    You can now click "Begin Import".
    When the process is done,
    you will receive a message like
    "Importing complete! Your new repository gvwilson/2016-12-01-miskatonic is ready."
    and you can go to the new repository by clicking on the name.

**Note:**
some people have had intermittent errors during the import process,
possibly because of the network timing out.
If you experience a problem, please re-try;
if the problem persists,
please [get in touch](#getting-and-giving-help).

## Customizing Your Website

1.  Go into your newly-created repository,
    which will be at `https://github.com/your_username/YYYY-MM-DD-site`.
    For example,
    if your username is `gvwilson`,
    the repository's URL will be `https://github.com/gvwilson/2016-12-01-miskatonic`.

3.  Ensure you are on the gh-pages branch by clicking on the branch under the drop 
    down in the menu bar (see the note below):

    ![](fig/select-gh-pages-branch.png?raw=true)

3.  Edit the header of `index.md` to customize the list of instructors,
    workshop venue, etc. 
    You can do this in the browser by clicking on it in the file view on GitHub
    and then selecting the pencil icon in the menu bar:

    ![](fig/edit-index-file-menu-bar.png?raw=true)
    
    Editing hints are embedded in `index.md`,
    and full instructions are in [the customization instructions][customization].
    
4.  Edit `_config.yml` to customize certain site-wide variables, such as: `carpentry` (to tell us which carpentry workshop this is), `title` (overall title for all pages), `repository` (so that URLs resolve correctly both locally and on GitHub), `workshop_repo` (the URL of the workshop repository on GitHub) and `workshop_site` (the repository's GitHub Pages URL).

    Editing hints are embedded in `_config.yml`,
    and full instructions are in [the customization instructions][customization].
    
5. Edit the `schedule.html` file to edit the schedule for your upcoming workshop. This file is located in the `_includes` directory, make sure to choose the one from the appropriate `dc` (Data Carpentry workshop), `lc` (Library Carpentry), or `sc` (Software Carpentry) subdirectory.

6.  Alternatively,
    if you are already familiar with Git,
    you can clone the repository to your desktop,
    edit `index.md`, `_config.yml`, and `schedule.html` there,
    and push your changes back to the repository.

    ~~~
    git clone -b gh-pages https://github.com/your_username/YYYY-MM-DD-site
    ~~~

    You should specify `-b gh-pages` to checkout the gh-pages branch because the imported 
    repository doesn't have a `master` branch.

    In order to view your changes once you are done editing,
    you must push to your GitHub repository:

    ~~~
    git push origin gh-pages
    ~~~

7.  When you are done editing,
    go to the GitHub Pages URL for your workshop and preview your changes.
    In the example above, this is `https://gvwilson.github.io/2016-12-01-miskatonic`.
    The finished page should look [something like this](fig/completed-page.png?raw=true).

8.  Optional: you can now change the README.md file in your website's repository, which contains these instructions, so that it contains a short description of your workshop and a link to the workshop website.

**Note:**
please do all of your work in your repository's `gh-pages` branch,
since [GitHub automatically publishes that as a website][github-project-pages].

**Note:**
this template includes some files and directories that most workshops do not need,
but which provide a standard place to put extra content if desired.
See the [design notes][design] for more information about these.

Further instructions are available in [the customization instructions][customization].
This [FAQ][faq] includes a few extra tips (additions are always welcome)
and these notes on [the background and design][design] of this template may help as well.

## Checking Your Changes

If you want to preview your changes on your own machine before publishing them on GitHub,
you can do so as described below.

1.  Install the software [described below](#installing-software).
    This may require some work,
    so feel free to preview by pushing to the website.

2.  Run the command

    ~~~
    make serve
    ~~~

    and go to <http://0.0.0.0:4000> to preview your site.
    You can also run this command by typing `make serve`
    (assuming you have Make installed).

3.  Run the command

    ~~~
    make workshop-check
    ~~~

    to check for a few common errors in your workshop's home page.
    (You must have Python 3 installed to do this.)

## (Optional) Linking to Your Page

At the top of your repository on GitHub you'll see

~~~
No description or website provided. — Edit
~~~

Click 'Edit' and add:

1.  A very brief description of your workshop in the "Description" box (e.g., "Miskatonic University workshop, Dec. 2016")

2.  The URL for your workshop in the "Website" box (e.g., `https://gvwilson.github.io/2016-12-01-miskatonic`)

This will help people find your website if they come to your repository's home page.

## Creating Extra Pages

In rare cases,
you may want to add extra pages to your workshop website.
You can do this by putting either Markdown or HTML pages in the website's root directory
and styling them according to the instructions give in
[the lesson template][lesson-example].
If you do this,
you *must* also edit `_config.yml` to set these three values:

1.  `carpentry` is either "dc" (for Data Carpentry), "swc" (for Software Carpentry),
    or "lc" (for Library Carpentry). This determines which logos are loaded.

2.  `title` is the title of your workshop (typically the venue and date).

3.  `email` is the contact email address for your workshop,
    e.g., `gvwilson@miskatonic.edu`.

Note: `carpentry` and `email` duplicate information that's in `index.md`,
but there is no way to avoid this
without requiring people to edit both files in the usual case
where no extra pages are created.

## Installing Software

If you want to set up Jekyll
so that you can preview changes on your own machine before pushing them to GitHub,
you must install the software described below.
(Note: Julian Thilo has written instructions for
[installing Jekyll on Windows][jekyll-windows].)

1.  **Ruby**.
    This is included with Linux and macOS;
    the simplest option on Windows is to use [RubyInstaller][ruby-installer].
    You can test your installation by running `ruby --version`.
    For more information,
    see [the Ruby installation guidelines][ruby-install-guide].

2.  **[RubyGems][rubygems]**
    (the package manager for Ruby).
    You can test your installation by running `gem --version`.

3.  **[Jekyll][jekyll]**.
    You can install this by running `gem install jekyll`.

## Setting Up a Separate Repository for Learners

If you are teaching Git,
you should create a separate repository for learners to use in that lesson.
You should not have them use the workshop website repository because:

*   your workshop website repository contains many files
    that most learners don't need to see during the lesson,
    and

*   you probably don't want to accidentally merge
    a damaging pull request from a novice Git user
    into your workshop's website while you are using it to teach.

You can call this repository whatever you like,
and add whatever content you need to it.

## Getting and Giving Help

We are committed to offering a pleasant setup experience for our learners and organizers.
If you find bugs in our instructions,
or would like to suggest improvements,
please [file an issue][issues]
or [mail us][email].

[email]: mailto:admin@software-carpentry.org
[customization]: https://swcarpentry.github.io/workshop-template/customization/
[dc-site]: http://datacarpentry.org
[design]: https://swcarpentry.github.io/workshop-template/design/
[faq]: https://swcarpentry.github.io/workshop-template/faq/
[github-project-pages]: https://help.github.com/articles/creating-project-pages-manually/
[importer]: https://github.com/new/import
[issues]: https://github.com/swcarpentry/workshop-template/issues
[jekyll-windows]: http://jekyll-windows.juthilo.com/
[jekyll]: https://jekyllrb.com/
[lesson-example]: https://swcarpentry.github.io/lesson-example/
[pyyaml]: https://pypi.python.org/pypi/PyYAML
[ruby-install-guide]: https://www.ruby-lang.org/en/downloads/
[ruby-installer]: http://rubyinstaller.org/
[rubygems]: https://rubygems.org/pages/download/
[self-organized-workshop-form]: https://amy.software-carpentry.org/workshops/submit/
[swc-site]: http://software-carpentry.org

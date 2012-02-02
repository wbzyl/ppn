# Przygotowywanie publikacji naukowych

Zaczynamy!


## LaTeX

* [Web Equation](http://webdemo.visionobjects.com/equation.html?locale=default)


## Blogowanie na GitHub-ie

Tworzymy bloga, korzystając z gotowego szablonu
Octopress. Publikujemy bloga, korzystając z  *github:pages*.

Blog będzie dostępny pod następującym url:

    http://wbzyl.github.com/ppn


### Tworzymy gałąź *gh-pages* w repozytorium *ppn*

* [Introduction to Pages](http://pages.github.com/)

Project Pages:

    cd ppn
    git symbolic-ref HEAD refs/heads/gh-pages
    rm .git/index
    git clean -fdx

### Instalujemy *Octopress*

- [Setup](http://octopress.org/docs/setup/)
- [Deploying to Github Pages](http://octopress.org/docs/deploying/github/)

Setup Octopress:

    git clone git://github.com/imathis/octopress.git ppn-pages
    cd ppn-pages
    bundle install --path=.gems --binstubs

Dopisujemy katalog */.gems* do pliku *.gitignore*,
wykonujemy commit, a następnie push na Github.

Deploying with Github Project pages (gh-pages):



Na koniec instalujemy lokalnie [Pygments](http://pygments.org/):

    sudo yum install python-setuptools  # Fedora
    easy_install --user Pygments
    export PATH=$PATH:$HOME/.local/bin  # dopisujemy do .bash_profile

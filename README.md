# Przygotowywanie publikacji naukowych

Zaczynamy!


## LaTeX

* [Web Equation](http://webdemo.visionobjects.com/equation.html?locale=default)


## Blog na GitHub:Pages

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
    rake install

Dopisujemy katalog */.gems* do pliku *.gitignore*.

Deploying with Github Project pages (gh-pages):

    rake setup_github_pages
    Enter the read/write url for your repository:

Wpisujemy:

    git@github.com:wbzyl/ppn.git

Na koniec wykonujemy:

    rake deploy

I już! Gotowe. Możemy wejść na stronę blog.
(Musimy poczekać ok. 10 minut.)


### Instalujemy lokalnie [Pygments](http://pygments.org/)

Przykładowo, w Fedorze wykonujemy:

    sudo yum install python-setuptools  # Fedora
    easy_install --user Pygments
    export PATH=$PATH:$HOME/.local/bin  # dopisujemy do .bash_profile

Niepotrzebne w wersji 2.0?

Kod na ciemnoniebieskim tle jest nieczytelny. Dlatego zmieniamy
tło na *solarized light*.

W tym celu w pliku *sass/custom/_colors.scss* odkomentowujemy:

    /* To use the light Solarized highlighting theme uncomment the following line */
    $solarized: light;

i w pliku *sass/partials/_syntax.scss* zmieniamy czarny kolor na biały:

    .highlight code { @extend .pre-code; background: white;}

Zmieniamy domyślną wielkość fontu */sass/custom/_styles.scss*:



## Konfiguracja bloga

*Uwaga:* Po zmianie pliku *config.yml* należy wykonać

    rake generate
    rake deploy

Podstawowe ustawienia bloga są zawarte w pliku *_config.yml*.
Wprowadzamy następujące zmiany w ustawieniach:

* url: http://wbzyl.github.com/ppn — **zostawiamy bez zmian!**
* title: Przygotowywanie Publikacji Naukowych
* subtitle: Blog hakerów TeX-owych
* author: Włodek Bzyl
* simple_search: http://google.com/search — **zostawiamy bez zmian!**
* description: Notatki do zajęć „Przygotowywanie publikacji naukowych”


## Pierwszy wpis na http://wbzyl.github.com/ppn/

Pierwszy wpis będzie o tym jak dodać MathJax do bloga:

    rake new_post["MathJax"]

Używając notacji [Markdown](http://www.ctrlshift.net/project/markdowneditor/)
oraz od czasu do czasu znaczników HTML wpisujemy
tekst postu.

Następnie wykonujemy:

    rake generate
    rake preview  # uruchamiamy serwer www na localhost:4000

Wygenerowany wpis oglądamy na stronie:

    http://localhost:4000/ppn

Jeśli wszystko jest ok, to wykonujemy:

    rake deploy


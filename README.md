# Przygotowywanie publikacji naukowych

Zaczynamy:

* Wiki
* Blog


## Blog na GitHub:Pages

Tworzymy bloga, korzystając z gotowego szablonu
Octopress. Publikujemy bloga, korzystając z  *github:pages*.


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


### Instalujemy lokalnie

Przykładowa instalacja [Pygments](http://pygments.org/) w Fedorze:

    sudo yum install python-setuptools
    easy_install --user Pygments
    export PATH=$PATH:$HOME/.local/bin  # dopisujemy do .bash_profile


## Konfiguracja bloga

Kod na ciemnoniebieskim tle jest nieczytelny.
Zmieniamy tło na *solarized light* odkomentowując
wiersz z `$solarized` w pliku *sass/custom/_colors.scss*:

    /* To use the light Solarized highlighting theme uncomment the following line */
    $solarized: light;

oraz zmieniając w pliku *sass/partials/_syntax.scss*
czarny kolor tła na biały:

    .highlight code { @extend .pre-code; background: white;}

Przy okazji zwiększamy domyślną wielkość fontu */sass/custom/_styles.scss*.

Podstawowe ustawienia bloga są zawarte w pliku *_config.yml*.
Wprowadzamy następujące zmiany w ustawieniach:

* url: http://wbzyl.github.com/ppn — **zostawiamy bez zmian!**
* title: Przygotowywanie Publikacji Naukowych
* subtitle: Blog hakerów TeX-owych
* author: Włodek Bzyl
* simple_search: http://google.com/search — **zostawiamy bez zmian!**
* description: Notatki do zajęć „Przygotowywanie publikacji naukowych”

Podstawowe polecenia:

    rake generate  # generuje nowe wersje stron
    rake preview   # lokalny podgląd na localhost:4000/ppn
    rake deploy    # wdrażanie nowej wersji na Githubie


## Pierwszy wpis na http://wbzyl.github.com/ppn/

Pierwszy wpis będzie o tym jak dodać MathJax do bloga:

    rake new_post["MathJax"]

Używając notacji [Markdown](http://www.ctrlshift.net/project/markdowneditor/)
oraz od czasu do czasu znaczników HTML wpisujemy
tekst postu.


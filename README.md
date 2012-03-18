# Przygotowywanie publikacji naukowych

Terminy spotkań:

* luty: 21, 28
* marzec: 6, 13, 27
* kwiecień: 17, 24
* maj 15, 22 (2 godz.)


## Blog PPN na GitHub:Pages

Blog PPN korzysta z gotowego szablonu
[Octopress](https://github.com/imathis/octopress) dla
[Jekylla](https://github.com/mojombo/jekyll).

Bloga wdrażamy w dwóch krokach.

### 1. Tworzymy gałąź *gh-pages* w repozytorium *ppn*

* [Introduction to Pages](http://pages.github.com/)

Project Pages:

    cd ppn
    git symbolic-ref HEAD refs/heads/gh-pages
    rm .git/index
    git clean -fdx

### 2. Instalujemy szablon *Octopress*

* [Setup](http://octopress.org/docs/setup/)
* [Deploying to Github Pages](http://octopress.org/docs/deploying/github/)

Setup Octopress:

    git clone git://github.com/imathis/octopress.git ppn-pages
    cd ppn-pages

Dopisujemy katalog */.gems* do pliku *.gitignore* i instalujemy gemy:

    bundle install --path=.gems --binstubs

Instalujemy domyślny wygląd (*theme*):

    bin/rake install # copies the default theme into the path of Jekyll's generator

Deploying with Github Project pages (gh-pages):

    bin/rake setup_github_pages

Na prośbę o wpisanie url-a:

    Enter the read/write url for your repository:

wpisujemy:

    git@github.com:wbzyl/ppn.git

Kończymy instalację wykonując polecenie:

    bin/rake deploy

I już! Gotowe. Możemy wejść na stronę bloga:

    http://wbzyl.github.com/ppn

Ale musimy poczekać minutkę zanim strona pojawi się na Githubie.


## Konfiguracja bloga

Kod na ciemnoniebieskim tle jest nieczytelny.
Zmieniamy tło na *solarized light* odkomentowując
wiersz z `$solarized` w pliku *sass/custom/_colors.scss*:

    /* To use the light Solarized highlighting theme uncomment the following line */
    $solarized: light;

oraz zmieniając w pliku *sass/partials/_syntax.scss* czarny kolor tła na biały:

    .highlight code { @extend .pre-code; background: white;}

Przy okazji zwiększamy domyślną wielkość fontu */sass/custom/_styles.scss*.
Domyślna wielkość jest zdecydowanie za mała.

Podstawowe ustawienia bloga są zawarte w pliku *_config.yml*.
Wprowadzamy następujące zmiany w domyślnych ustawieniach:

* url: http://wbzyl.github.com/ppn — **zostawiamy bez zmian!**
* title: Przygotowywanie Publikacji Naukowych
* subtitle: Blog hakerów TeX-owych
* author: Włodek Bzyl
* simple_search: http://google.com/search — **zostawiamy bez zmian!**
* description: Notatki do zajęć „Przygotowywanie publikacji naukowych”

Blog na co dzień:

    bin/rake generate  # generuje nowe wersje stron
    bin/rake preview   # lokalny podgląd na localhost:4000/ppn
    bin/rake deploy    # wdrażanie nowej wersji na Githubie


## Pierwszy wpis na http://wbzyl.github.com/ppn/

Pierwszy wpis będzie o tym jak dodać MathJax do bloga:

    rake new_post["MathJax"]

Używając notacji [Markdown](http://www.ctrlshift.net/project/markdowneditor/)
oraz od czasu do czasu znaczników HTML wpisujemy
tekst postu.


## Różne rzeczy…

Przykładowa instalacja [Pygments](http://pygments.org/) w Fedorze:

    sudo yum install python-setuptools
    easy_install --user Pygments        # instaluj lokalnie
    export PATH=$PATH:$HOME/.local/bin  # dopisujemy do .bash_profile


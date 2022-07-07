---
title: "Ripgrep" #Tytuł wpisu
subtitle: "Jak wyszukiwać wzorce w plikach" #krótki opis podtytuł
date: 2022-06-22
draft: false
author: "m0iga"
# authorLink: ""
description: "" # na potrzeby robotów
license: "" # licencja jeśli inna niż CC


tags: [grep, wyszukiwanie, konsola] #tagi artykułu
categories: [unixowo] #Kategorie artykułu [unixowo, radiowo, nijako]

featuredImage: "" # obraz główny wpisu - fotka /fofto.png dla katalogu static
featuredImagePreview: "" # obrazek do wyświetlenia na głównej moe by ten sam co główny

hiddenFromHomePage: false
hiddenFromSearch: false
twemoji: true           #włączone emotikony w markdown https://hugoloveit.com/emoji-support/
lightgallery: false  # włacz lub wyłącz galerię
ruby: true
fraction: true
fontawesome: true
linkToMarkdown: false
rssFullText: false

toc:
  enable: true
  auto: true
code:
  copy: true
  maxShownLines: 50
  # ...
share:
  enable: true
  # ...
comment:
  enable: true
---



### Ripgrep

Jest to narzędzie wiersza poleceń do wyszukiwania wzorców regularnych w plikach. Może również rekurencyjnie przeszukiwać zadany katalog w poszukiwaniu wzorca.

Tu przykładowe zapytanie o "regrep" w katalogu man ![regrep](/img/ripgrep/grep.png)

Osobiście używam go do bardzo trywialnych celów - czyli wyszukiwania potrzebnych mi kawałków kodu, które gdzieś przewalają się po różnych plikach :smail:

Oczywiście narzędzie te zawiera mnóstwo opcji i przełączników, które pozwalają nam uściślić i rozbudować zapytania, a których nie jestem w stanie zapamiętać . Po lekcje odsyłam do [bloga Andrew Galanta](https://blog.burntsushi.net/ripgrep/), oraz na oficjalne [repo na github](https://github.com/BurntSushi/ripgrep) Znajdziecie tam też info o repozytoriach i sposobach instalacji do wszystkich możliwych systemów, od FreeBsd, przez Windowsa, po MacOS.

Teraz szybka instalacja w moich ulubionych systemach.

* MacOS

Dla browarników:

`$ brew install ripgrep`
	
Dla portowców:

    $ sudo port install ripgrep

*  [Sparky Linux 7](https://sparkylinux.org/) 
	
`$sudo nala install ripgrep`

lub

`$ sudo apt-get install ripgrep`
	
P.S. lubiącym widzić co się dzieje w czasie instalacji i początkującym uzytkownikom, zdecydowanie polecam zainstalowanie  [Nala](https://gitlab.com/volian/nala). To taki frontend dla libapt-pkg, jak apt-get, czy aptitude, tylko ładniejszy. Wpis o Nala ukaże się wkrótce
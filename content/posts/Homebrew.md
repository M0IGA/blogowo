---
title: "Homebrew" #Tytuł wpisu
subtitle: "Co to jest homebrew i jak się nim posługiwać" #krótki opis podtytuł
date: 2022-06-30
lastmod: 
draft: false
author: "m0iga"
# authorLink: ""
description: "tutorial instalacja i używanie homebrew" # na potrzeby robotów
license: "" # licencja jeśli inna niż CC


tags: [homebrew, macos] #tagi artykułu
categories: [unixowo] #Kategorie artykułu [unixowo, radiowo, nijako]

featuredImage: "/img/brew/logo.png" # obraz główny wpisu - fotka /fofto.png dla katalogu static
featuredImagePreview: "/img/brew/logo.png" # obrazek do wyświetlenia na głównej moe by ten sam co główny

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




## Co to jest Homebrew

Homebrew to taka warzelnia piwa z programami. Znaczy nawarzymy sobie niezłego piwa w systemie ;).

W skrócie, jest to menedżer pakietów dla macOS (nie tylko MacOS, ale darujmy sobie resztę). Użyjemy go, aby instalować i usuwać opensourcowe Unixowe programy, zarówno konsolowe, jak i GUI. Ci którzy mieli do czynienia z linuxem, dobrze znają managery pakietów jak na przykład `apt`, gdzie z poziomu konsoli zarządza się programami. W MacOS oczywiście jest to rozwiązane inaczej, ale przecież to też Unix, więc czemu tego nie wykorzystać? Prawie każdy użyteczny program open source jest dostępny za pośrednictwem Homebrew, z jednym narzędziem do instalacji i zarządzania każdym z nich. Dodatkowo Homebrew dąży do tego, żeby użytkownik nie musiał się zbytnio wysilać przy instalacji i zarządzaniu.

No ok, ale przecież mogę ściagnąć obraz jakiegoś programu, np. Alfreda, kliknąć na niego, przeciągnąć do Aplikacji i zainstalowane. Dlaczego wobec tego miałbym chcieć robić to w wierszu poleceń?

Ok, zróby taką rozkminę.

##### Instalacja tradycyjna

1. Włączasz wyszukiwarkę, żeby znaleźć skąd można ściagnąć program, wpisujesz "alfred launcher" wywala ci jakieś śmieci, które każą sobie płacić za darmowy program.
2. Szukasz właściwej strony w wynikach albo ponawiasz wyszukiwanie  "alfred launcher download".
3. Wchodzisz na stronę Alfreda, klikasz download i zapisujesz `.dmg`na dysku.
4. Klikasz pobrany plik, który otwiera okienko instalacyjne
5. Przeciągasz plik programu do folderu Aplikacje i koniec, zainstalowano.
6. Uruchamiasz program

P.S. nie zapomnij odmontować obrazu dysku w Finderze ;)

No to teraz,

##### Instalacja piwna

1. Otwierasz konsolę
2. Wpisujesz `brew install alfred`
3. uruchamiasz program

No i jak? Jest sens?

* Co więcej, aktualizację wszystkich zainstalowanych poprzez Homebrew programów robimy przy pomocy dosłownie dwóch komend.

Dzięki brew możemy doinstalować sobie użyteczne narzędzia jak minight commander, wget, czy btop i inne, których nie da się pozyskać jakoobrazy dmg.

## O co chodzi z tym piwem?

![brew](/img/brew/logo1.png)

Homebrew posługuje się swoją charakterystyczną terminologią piwną/ browarniczą, którą trzeba chociaż z grubsza ogarniać.

Dla początkujących użytkowników najważniejsze w tej piwnej terminilogii są:
* `Tap`

Ten kranik, to nic innego jak repozytorium pakietów Git (taki git jak github). Pakiety takie sa gotowe i czekają aż wydasz odpowiednie polecenie instalacji.

*  `Cellar`

Piwnica, to miejsce gdzie instalowane są pakiety na twojej lkalnej maszynie. To miejsce znajduje się tylko i wyłącznie na dysku Twojego komputera.

* `Formula`  (lub Formulae)

`Formula`, to pakiet programu, który ściągasz i instalujesz z `Tap`.  Homebrew przechowuje w  `Cellar`  wiele formuł, każdą kolejną wersję instalowanego programu lub biblioteki, żebyś mógł łatwo zrobić downgrade, jeśli najnowsza wersja ma jakieś błędy lub coś miesza w systemie.

To są podstawowe pojęcia browarnictwa systemowego, ale dobrze by było gdybyś zapoznał się z resztą , które to znajdziesz [tutaj](https://docs.brew.sh/Formula-Cookbook)

Zasadniczo potrzebujesz znać tylko kilka poleceń. Ci którzy mieli w ręach linuxa powinni być w domu, a ci co konsoli używają sporadycznie, też nie muszą się martwić, bo jest to bardzo proste.

## Warzymy browara

Piwo programowe ważymy tak:

`Brew` to jest polecenie które nam waży nasze programy i od niego zawsze będziemy zaczynali i do niego dodawali to co chcemy uwarzyć, a więc...

Zobaczmy co i jak na podstawie znanego nam już Alfreda

`brew search alfred` - oczywiście wyszukuje czy taki program znajduje się w jakimś Tapie.

`brew install alfred` - instalacja. Brew zainstaluje wszystko co potrzeba, czasem nawet z dodatkowymi programami lub częściej bibliotekami, które są niezbędne do pracy instalowanego przez nas programu, a które jeszcze nie znajdują się w systemie i zrobi link w katalobu Aplikacje, żeby nasz program był widoczny w Lauchpadzie.

`brew uninstall alfred` - jeśli Alfred nie przypadnie nam do gustu i chcemy go odinstalować.

Niestety Homebrew nie aktualizuje automatycznie repozytorioów i programów, więc musimy to zrobić ręcznie, ale to też nie jest trudne

![Instalacja i usuwanie Alfreda](/img/brew/alfred.gif)


`brew update`  - Uaktualni informacje o pakietach i ich wersjach w Tapach, czyli repozytoriach.

`brew upgrade` zaktualizuje wszystkie zainstalowane przez brew programy i biblioteki do ich najnowszych wersji.

Jak już pisałem, brew nie usuwa starszych wersji programów, wobec czego z czasem może się nazbierać trochę nieużywanego śmiecia, który je posprząta i usunie z dysku.

`brew cleanup`i po chwili są już tylko najnowsze wersje programów. Jeśli chcemy zaś zobić to tylko dla jednego programu np. naszego nieszczęsnego Alfreda, to użyjemy znanego już polecenia odinstalowania, ale z operatorem `-f` -  `brew uninstal -f alfred`i tak jak przy cleanupie pozostaje tylko najnowsza wersja.

**Uzywajcie tych ostatnich poleceń**,  tylko gdy jesteście pewni, że wszystkie programy które czyścicie ze starych wersji, działają prawidłowo.

To z grubsza wystarczy do rozpoczęcia zabawy z własnoręcznym ważeniem softu na Maca, a ciekawskich i chcących zdobyć obszerniejszą wiedzę co jeszcze można "napsuć" w Homebrew, zapraszam do zapoznania się z jakże pasjonującą i ciekawa lekturą [dokumentacji](https://docs.brew.sh/)

 P.S. Nie wiem jak u Was, ale u mnie Alfred zostanie na dłużej. Zasłużył sobie swoją ciężką pracą jako model. Aha no i jeszcze zrobię kiedyś wpis o Alfredzie, to też ciekawy program z wieloma możliwościami.
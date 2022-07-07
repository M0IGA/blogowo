---
title: "Tor w MacOS" #Tytuł wpisu
subtitle: "Jak szybko i łatwo uruchomić sieć animizującą Tor na Macu" #krótki opis podtytuł
date: 2022-06-10
#lastmod: 2022-06-25
draft: false
author: "m0iga"
# authorLink: ""
description: "Jak szybko i łatwo uruchomić sieć animizującą Tor" # na potrzeby robotów
license: "" # licencja jesli inna ni CC


tags: [macos, tor] #tagi artykułi
categories: [unixowo] #Kategorie artykułu [unixowo, radiowo, nijako]

featuredImage: "/img/torosx/proxy-image.png" # obraz główny wpisu - fotka /fofto.png dla katalogu static
featuredImagePreview: "/img/torosx/torproject.png" # obrazek do wyświetlenia na głównej moe by ten sam co główny

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


Na podstawie tutoriala [deepdarkweb](https://deepdarkweb.github.io/)

### Co to jest i do czego służy Tor?
W uproszczeniu Tor jest programem zapewniającym względnie dużą anonimowość w sieci. Dane które wysyłamy przechodzą przez wiele losowych węzłów sieci Tor, dzięki czemu komputer z którego wyszły pozostaje dla serwera anonimowy i bardzo trudno jest namierzyć ten konkretny komputer.

![p1](/img/torosx/tor.png)

### Po co mi anonimowość w sieci?
Nie musisz być dilerem narkotyków, handlarzem bronią czy innym złoczyńcą, aby chcieć używać sieci anonimizującej Tor. Jest wiele przyczyn, dla których ludzie chcą się ukryć w sieci. Część z nich nosi foliowe czapeczki na głowach, bo uważają, że rządy ich podsłuchują. Inni mają dość wszechobecnej inwigilacji fundowanej nam przez korporacje jak Metaverse (facebook i inne przedsięwzięcia Pana Zuckenberga), czy Google. Tor uniemożliwia również Twojemu dostawcy usług internetowych, rządowi, hakerom lub firmom zajmującym się eksploracją danych (śledzenie reklam) zobaczenie i zapisanie odwiedzanych przez Ciebie witryn.

Tor Jest szczególnie przydatny dla ludzi, którzych mieszkają w krajach totalitarnych o ścisłej cenzurze informacji, jak Rosja, Chiny i inne. Dzięki sieci Tor, mogą oni ominąć rządowe blokady, a jednocześnie znalezienie ich przez władze jest bardzo trudne.

### Czy Tor jest dla Ciebie?
Jeśli jesteś przeciętnym użytkownikiem oglądającym kocie GIF-y i przeglądającym Facebooka, prawdopodobnie nie musisz się martwić, że rząd będzie szpiegował Twoją aktywność. Tor po prostu spowolni twoje połączenie. Bardziej prawdopodobne jest, że musisz zabezpieczyć swój internet, powiedzmy, gdy korzystasz z publicznej sieci Wi-Fi, a nie anonimizować go. W takim przypadku upewnij się, że używasz protokołu HTTPS we wszystkich witrynach, które go obsługują, a być może nawet VPN do szyfrowania całego ruchu, gdy jesteś poza domem.

### Najprostsze rozwiązanie.

Ściągasz i instalujesz [Tor Browser](https://www.torproject.org/dist/torbrowser/11.0.13/TorBrowser-11.0.13-osx64_en-US.dmg) z tego linku, lub jesli się boisz ściągac programy z nieznanych źródeł, tu jest oficjalna strona download: https://www.torproject.org/download.
Instalacja programu jest standardowa jak wszystkie inne i polega na skopiowaniu aplikacji do folderu Applications. Przeglądarka Tor Browser jest oparta na Firefoxie, więc mam znany dla wielu użytkowników interface. Po uruchomieniu należy dokonać kilku modyfikacji ustawień przeglądarki.

### Instalacja serwera
Mimo że przeglądarka Tor jest dostarczana z instalacją Tora, będzie działać tak długo, jak długo będziesz mieć ją otwartą i korzystasz wyłacznie z niej.

Poniższe instrukcje skonfigurują Tora bez interfejsu graficznego lub przeglądarki. Co może być lepsze dla użytkowników, którzy chcą, aby Tor działał przez cały czas, bez konieczności uruchamiania przeglądarki Tor. Może to być szczególnie przydatne, jeśli chcesz hostować usługi cebulowe na swoim Macu, przekazywać ruch innym użytkownikom Tora, lub użyć tych strasznych torrentów, żeby ściągnąć epizod serialu, który jest niedostępny w Twoim kraju.

**Czego potrzebujesz**

* Konsola (dostępna w każdym Macu, przecież to UNIX, a dokładnie jego pochodna czyli BSD :)
* Podstawowa znajomość posługiwania się wierszem poleceń (zakładam, że skoro uznałeś, że jest Ci potrzebny serwer Tor, to masz takie skilsy)
* Zainstalowany [Homebrew](https://brew.sh/index_pl)

Jeśli nie masz jeszcze Homebrew, to szybka instalacja wygląda tak:

Z poziomu konsoli wydajesz poniższe polecenie, które ściągnie za Ciebie i zainstaluje homebrew. (przy okazji polecam zainteresować się Homebrew w innych celach, ale o tym piszę w [Tym poście]({{< relref "Homebrew.md" >}})


    /bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"

Następnie wydajesz polecenie:

    brew install tor

No i voila, po chwili tor jest zainstalowany. Teraz trzeba nieco pogrzebać w konfiguracji.

    nano /usr/local/etc/tor/torrc.sample

Tu możesz pozmieniać ustawienia swojego Tora, chociaż dla większości wystarczy, że usuniesz rozszerzenie .sample. Oczywiście najszybciej zrobić to z konsoli :)

    mv /usr/local/etc/tor/torrc.sample /usr/local/etc/tor/torrc

Następnie trzeba uruchomić serwer. Po instalacji, konsola powinna wyświetlić coś takiego

    To restart tor after an upgrade:
    brew services restart tor
    Or, if you don't want/need a background service you can just run:
    /usr/local/opt/tor/bin/tor

Po uruchomieniu serwera, pozostał już ostatni krok. W ustawieniach sieciowych aplikacji, którym ruch sieciowy chcesz przepuścić przez sieć Tor musisz ustawić proxy jako SOCKS z serwerem proxy localhost lub 127.0.0.1 i portem 9050.
{{< figure align=center src="/img/torosx/proxy.png" title="ustawienia proxy">}}

Jesli chcesz cały ruch w komputerze puścić przez Tor, to należy ustawić powyższymi danymi proxy w ustawieniach systemowych > Sieć > Wybrany interfejs sieciowy > Zaawansowane i zakładka Proxy.


[![ko-fi](https://ko-fi.com/img/githubbutton_sm.svg)](https://ko-fi.com/N4N4DGJUL)

*<sub>Logo Tor i zakapturzona postać pochodzi ze strony [torproject](https;//torproject.org)</sub>
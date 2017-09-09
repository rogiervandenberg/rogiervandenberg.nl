---
layout: post
title: Statische websites zijn cool
---
Onlangs besloot ik mijn website weer nieuw leven in te blazen, daar kijk je nu naar. Wat echt nieuw is, is de manier waarop deze werkt. Het is namelijk een ‘statische website’, omdat ik denk dat de tijd waarbij een website standaard werd gemaakt op basis van een CMS (Wordpress, Ghost, etc.) in de meeste gevallen voorbij is.

## FTP’en
In de jaren ’90 waren er 2 manieren om je website te maken en te onderhouden:
* Je schreef zelf de HTML-code, wat door je browser werd weergegeven als een website
* Je maakte je website met een ‘tool’ als Dreamweaver. Je kon dan, alsof je een documentje in Word maakt, je site bij elkaar klikken.

Vervolgens kreeg je een hele verzameling .htm bestanden en plaatjes. Deze moest je vervolgens ergens uploaden.

Dit was complex (voor een niet-nerd), gaf gedoe, het was foutgevoelig, mensen overschreven elkaars werk, etc. Je had ook altijd een techneut nodig om iets aan te passen.

## CMS’en
Toen kwamen er CMS’en ([Content Management Systeem][1]). Daarvoor wordt één keer het ontwerp van een website gemaakt. De inhoud van je site komt uit een database. Je hebt een stukje software – het CMS – waarmee je je teksten kunt beheren en opslaan in de database.

Als iemand jouw website dan bezoekt, dan wordt aan de hand van de pagina die je bekijkt de juiste tekst uit de database gehaald, de website voor je samengesteld zoals hij er dan uit moet zien in die situatie voor die bezoeker en vervolgens getoond aan de bezoeker.

Er was een tijd dat iedere webbouwer zijn eigen CMS maakte, toen kreeg je een paar standaardoplossingen die heel populair werden (denk aan Joomla, Drupal) en tegenwoordig is het, naast die paar partijen waarbij het lukt een eigen systeem te onderhouden, bijna overal Wordpress wat gebruikt wordt.

### Voordelen
Een CMS is handig, omdat je zelf je content kunt beheren en niet steeds bestandjes hoeft te uploaden, zoals “vroeger”. Je bent dus onafhankelijk van je webbouwer en je kunt veel zelf doen.

### Nadelen
Maar een CMS heeft ook wat nadelen:

* het is relatief traag, omdat voor iedere keer dat iemand een pagina opent de juiste teksten uit een database gehaald moeten worden en de pagina eerst gegenereerd moet worden. Dat kost tijd.
* Het is kwetsbaar. Omdat een CMS veel toeters en bellen heeft, is hij ook meer kwetsbaar. Immers, als je je Wordpress niet op tijd updatet, weten kwaadwillenden precies wat er te hacken valt aan jouw site en versie. Sites op basis van een ‘traditioneel CMS’ moet je  altijd blijven onderhouden, anders gaat hij langzaam stuk.
* Je hebt altijd kosten. Omdat je website onderhouden moet worden kost dit tijd en/of geld. Daarnaast, omdat je website veel ‘overhead’ heeft, betaal je altijd ook hosting-kosten.

## ‘Nieuw’: Statische websites
Het bestaat al een tijd, maar het wordt steeds populairder: Een statische website, zoals in de jaren 90, maar zonder het gedoe van uploaden, de afhankelijkheid van techneuten, etc.

Dat werkt zo: Je gebruikt een “static site generator”, die de output maakt van jouw site, gebaseerd op de teksten, design, etc. Net zoals een CMS dat doet.

Echter, dit gebeurt niet iedere keer als iemand een pagina van jouw site bezoekt, maar **slechts 1x, nadat jij je website-pagina hebt opgeslagen**.

### Voordelen
Omdat je site niet bij ieder ‘*request*’ (bezoeker opent een pagina) wordt gemaakt, maar slechts 1x, is het **bere-snel**. Er komt geen database of verwerking bij te kijken. Het bestandje met wat je browser moet hebben staat al klaar en hij kan het direct krijgen.

Omdat je site is zoals hij is, is hij enorm robuust. Er kan niets stuk gaan. Als je je site vandaag maakt en vervolgens een half jaar niet updatet, is er niets aan de hand. Oude versies zijn niet aan de orde. Je ‘draait’ namelijk niet op een versie van een systeem, alleen bij het genereren gebruik je software (van een bepaalde versie), maar daarna is het klaar.

Er zijn wél CMS’en voor een statische site. Maar in plaats van dat deze iets wegschrijven in een database, dat wordt opgehaald bij ieder bezoek, zorgen ze ervoor dat bij het opslaan van content jouw website opnieuw wordt opgebouwd. Slechts 1x. Maar je kunt dus wel werken met een CMS, en dát is het grote verschil ten opzichte van de jaren 90!

Het is supergoedkoop, deze website kost mij bijvoorbeeld **niets**. Ik betaal alleen voor de domeinnaam. De hosting verloopt via “CDN’s” die mijn site gratis hosten omdat hij zo ‘weinig resources’ kost. Er hoeft immers niets te gebeuren, alleen af en toe een bestandje te worden teruggegeven. Geen database, moeilijke webservers, beveiligingen, etc.

Je bent CMS onafhankelijk. Momenteel gebruik ik mijn computer waarop ik teksten schrijf (in Markdown) en met 1 commando publiceer. Maar ik heb ook al gespeeld met het [Netlify CMS][2] en wil nog gaan kijken naar [Dato][3] en [Forestry.io][4]. Dat zijn online CMS’en, waarin je je content schrijft, zij slaan jouw werk op bij je website-bestanden. Vanaf daar wordt het weer automatisch live gezet (zie ‘Mijn opzet’).

### Nadelen
Natuurlijk zijn er ook wat nadelen te noemen:
* Extreem complexe websites, die bijvoorbeeld alternatieve inhoud bij verschillende soorten bezoekers tonen, zijn niet mogelijk. Denk aan webshops, interactieve websites of web-applicaties.
* Het opzetten van een statische website is initieel wat lastiger dan een account aanmaken op bv. [Wordpress][5], [Ghost][6] of [Wix][7] (waar ik overigens allemaal ervaring mee heb). Het is vergelijkbaar met het starten van een self hosted Wordpress qua complexiteit.

## Mijn opzet
Hoe werkt dit alles bij mij? Ik heb mijn site ontwerp (Ja, die is basic, maar voor mijn blog voldoende) gemaakt. Dit heb ik vervolgens in een [Jekyll][8]-project geïmplementeerd. Dat is zo’n *static site generator*. Maar je kunt bv. ook kijken naar [Hugo][9].

Alle bestandjes van opmaak, plaatjes, etc. en een map met “posts” zijn de ingrediënten voor mijn website. Deze sla ik gratis [online op in mijn GitHub-account][10].

Ik heb een account by [Netlify][11], deze is gekoppeld aan mijn Github-account. Als er iets wijzigt aan de bron-data van mijn site (een artikel, pagina of design wijziging) en ik sla het op op GitHub, dan maakt Netlify hier automatisch een nieuwe website van en zij zorgen voor de verdere hosting.

![][image-1]

## GitHub
Het enige wat ik dus hoef te doen, is zorgen dat wat ik live wil hebben op de goede manier op GitHub komt. Hoe doe ik dat? Dit kan op een aantal manieren:

* Ik maak een nieuwe blogpost als testbestand in de juiste map op mijn laptop en ‘push’ deze naar GitHub
* Ik gebruik een static-site CMS, die direct een artikeltje op mijn GitHub zet
* Ik maak direct op GitHub een nieuw tekstbestandje aan in de juiste map.

Net hoe het mij uitkomt dus! :)

## Zonder Netlify
Het is ook een stukje eenvoudiger te maken, **mits je Jekyll gebruikt** (niet bv. [Hugo of één van de andere vele generators][12]). [GitHub heeft namelijk ingebouwde build-methode voor Jekyll websites][13]. Dat betekent dat je alleen maar hoeft te zorgen dat je content op Github terecht komt, zij zorgen dan voor het builden en hosten. Ook weer kosteloos! En ja, hierbij werkt zo’n static site CMS net zo goed.

[1]:	https://nl.wikipedia.org/wiki/Contentmanagementsysteem
[2]:	https://www.netlifycms.org/
[3]:	https://www.datocms.com/
[4]:	https://forestry.io
[5]:	https://nl.wordpress.com/
[6]:	https://ghost.org/
[7]:	https://nl.wix.com/
[8]:	https://jekyllrb.com/
[9]:	https://gohugo.io/
[10]:	https://github.com/rogiervandenberg/rogiervandenberg
[11]:	https://www.netlify.com/
[12]:	https://www.staticgen.com/
[13]:	https://pages.github.com/

[image-1]:	https://docs.google.com/drawings/d/e/2PACX-1vTSTbHjV3_Tr6sjIvOFkYPNKWSgiAvDUTZUstfrRNYhL-fo3IlUDF-iGu87lr2y2m_6ZdiQsFSzi2mK/pub?w=930&amp;h=607
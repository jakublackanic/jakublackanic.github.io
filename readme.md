# Zadanie 1 - Webové publikovanie

Vytvorte webovú prezentáciu (webové sídlo) o sebe. Zamerajte sa jednak na vaše profesné záujmy (napr. projekty, ktoré riešite/riešili ste, čo vás v informatike najviac baví, fascinuje = váš developerský profil) a jednak vaše osobné záujmy, hobby.

V rámci developerského profilu vytvorte sekciu Webové publikovanie, kde budete publikovať všetky tri vaše vypracované zadania z predmetu.

Využite pritom technológie Git + GitHub Pages + Jekyll + Markdown. Využite potenciál statického generátora Jekyll a jeho templatovacích možností.

Podrobné požiadavky na vypracovanie a odovzdanie zadania (priemerná úroveň kvality):

* Sídlo musí obsahovať aspoň 5 podstránok, pri využití aspoň 3 rôznych rozložení (layout-ov)

* V rámci šablon musí byť použité:

	* aspoň 5 premenných
	* kolekcie alebo dátové súbory
	* aspoň 5 filtrov alebo tagov
	* aspoň 1 plugin (okrem pagination)


Stránka personálneho webu: [jakublackanic.github.io](https://jakublackanic.github.io/), testovaná na prehliadači Google chrome verzia 65.

V prípade problémov pri lokálnom spustení, pustiť cez príkaz `bundle exec jekyll serve`.

## Požiadavky:

### aspoň 5 podstránok:
* [Home](https://jakublackanic.github.io/) - úvodná stránka
* [About](https://jakublackanic.github.io/about/) - informácie o mne
* [CV](https://jakublackanic.github.io/cv/) - životopis
* [Blog](https://jakublackanic.github.io/blog/) - blog a jeho príspevky
* [Projects](https://jakublackanic.github.io/project/) - informácie o mojich projektoch
* [Content](https://jakublackanic.github.io/content/) - navigácia pomocou tagov pre projekty a príspevky v blogu 
* podstránky príspevkov blogu a podstránky projektov (napríklad [Another testing of tags](https://jakublackanic.github.io/blog/2016/05/24/another-testing-of-tags)  a [MODAC](https://jakublackanic.github.io/projects/modac/) )

### aspoň 3 layouty:
* default - základné rozloženie stránky, ktoré využívajú takmer všetky podstránky (náchadza sa v podstránkach [Home](https://jakublackanic.github.io/), [CV](https://jakublackanic.github.io/cv/), [Projects](https://jakublackanic.github.io/project/), [Content](https://jakublackanic.github.io/content/), [Blog](https://jakublackanic.github.io/blog/))
* sidebar - podobné rozloženie ako default, no obsahuje navyše bočný panel pre rýchlejšiu navigáciu na podstránke (v podstránke [About](https://jakublackanic.github.io/about/))
* post - rozloženie elementov v príspevkoch blogu, obsahuje informácie o konkrétnom príspevku (nachádza sa vo všetkých podstránkach príspevkov)
* projects - rozloženie elementov v podstránkach pre projekty, obsahuje informácie o konkrétnom projekte (nachádza sa vo všetkých podstránkach projektov)

### aspoň 5 premenných:
* tags
* category
* technologies
* description
* name
* url
* date - všetky spomenuté premenné sú použité pri kolekcii `_projects`.

### Kolekcie alebo dátové súbory:
Využité kolekcie pre moje projekty -> priečinok `_projects`.

### aspoň 5 filtrov alebo tagov:
Tagy a filtre sú využité hlavne v podstránke [Content](https://jakublackanic.github.io/content/)

Zoznam tagov:
* for / endfor
* assign 
* if / endif / endunless
* contains
* comment

Zoznam filtrov:
* date_to_string - zobrazenie dátumu
* slugify - lowercase pre string

### aspoň 1 plugin:
V projekte je využitý plugin `jemoji`, ktorý nám umožňuje využívať v texte smajlíkov (napríklad v príspevku blogu [Project Success](https://jakublackanic.github.io/blog/2017/07/11/project-success)).

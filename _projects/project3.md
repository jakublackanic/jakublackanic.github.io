---
layout: projects
name: "Assignment 3"
technologies: "XML, XSLT"
description: "Create XML structure for presentation."
url: /projects/project3
category: wp
tags: [wp]
---


Cieľom tohto zadania bolo navrhnúť a vytvoriť XSLT šablóny pre konverziu prezentácie z XML do XHTML+CSS a pre konverziu prezentácie z XML do PDF.

V prezentácií, ktorá má tvar XHTML sa nachádza navigácia na predchádzajúci a ďalší slajd. v PDF prezentácií je táto navigácia vykonávaná šípkami.

Prezentácia musí obsahovať koreňový element:

```xml
<presentation>
```

ktorého deti môžu byť:

```xml
<meta>
```

na uloženie nejakých meta dát alebo 

```xml
<slide>
```

na vloženie slajdu do prezentácie. Tento element môže mať atribút "id" pomocou ktorého sa na neho môžme v texte odkázať a atribút "type" pomocou ktorého môžme slajd označiť za začiatočný alebo záverečný. Element slide musí obsahovať titulok:

```xml
<title>
```

a môže obsahovať podtitulok:
```xml
<subtitle>
```

alebo text: 

```xml
<text>
```

V texte môžme využiť farebný text, tučné písmo, kurzívu alebo podčiarknutie elementami:

```xml
<color clr="red">...</color>
<bold>...</bold>
<em>...</em>
<underline>...</underline>
```


---

Pre vytvorenie slajdu s dvomi stĺpcami použijeme elementy:

```xml
<row>
	<col>
		...
	</col>
	<col>
		...
	</col>
</row>
```


---

Pre vytvorenie zoznamu použijeme elementy:

```xml
<list>
	<item>...</item>
	<item>...</item>
	<item>...</item>
</list>
```		
---

Špeciálne prípady:

* Úvodný slajd: musí obsahovať titulok, môže obsahovať podtitulok a názov autora. Text je v tomto slajde zarovnaný na stred a meno autora sa zobrazuje v pravom dolnom rohu.

```xml
<slide type="intro">
	<title>...</title>
	<subtitle>...</subtitle>
	<author>...</author>
</slide>
```		

* Záverečný slajd: musí obsahovať titulok, ktorý je vycentrovaný v strede slajdu.

```xml
<slide type="outro">
	<title>Ďakujem za pozornosť.</title>
</slide>
```		

* Obsah prezentácie: element "list" s atribútom "type", ktorý má hodnotu "toc", deti tohto elementu sú "item", ktorých atribút "ref" odkazuje na určité id slajdu prezentácie.

```xml
<list type="toc">
	<item ref="3">...</item>
	<item ref="4">...</item>
	<item ref="5">...</item>
	<item ref="6">...</item>
	<item ref="7">...</item>
</list>
```	

* Zarovnaný text do stĺpca: s týmto textom je možné pracovať ako s obyčajným textom. Jediným rozdielom je, že bude zarovnaný do stĺpca.

```xml
<text type="justify">...</text>
```	
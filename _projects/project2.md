---
layout: projects
name: "Assignment 2"
technologies: "DocBook, XML, XSLT"
description: "DocBook document creation."
url: /projects/project2
category: wp
tags: [wp]
---

Cieľom tohto zadania bolo napísať nejaký text(najlepšie bakalársku prácu) vo formáte DocBook. Pri vypracovaní bola použitá dostupná šablona, ktorá bola neskôr upravená. Finálny dokument bol validovaný v programe XMLMind.

Atribút *lang* elementu *book* bol nastavený na **sk**, keďže chceme v texte používať slovenčinu.

```xml
<book lang="sk">
```

---

## Úprava šablóny

V súboroch :
* thesis-tp-fo.xsl bol zakomentovaný riadok č. 47, 
* thesis.xsl bol zakomentovaný riadok č. 165,

ktoré načítavali nedostupný obrázok.

```xml
<!--  <fo:external-graphic src="url(kizi.pdf)" width="2cm" content-width="scale-to-fit"/> -->
```

---

V súbore thesis.xsl na riadkoch 306-318 bolo upravené formátovanie kapitol, aby nezobrazovalo napr. "Kapitola 1 Úvod" ale "1. Úvod".

```xml
<fo:block xsl:use-attribute-sets="chap.title.properties">
    <xsl:apply-templates select="$node" mode="label.markup"/>
    <xsl:text>. </xsl:text>
    <xsl:apply-templates select="$node" mode="title.markup"/>
</fo:block>
```

---

V súbore thesis.xsl bola vytvorená kópia šablóny *book.titlepage.before.recto*, ktorej bol v elemente *fo:block* pridaný argument **hyphenate="false"** kvôli nevhodnému zalámovaniu textu na úvodnej strane.

---

V súbore thesis.xsl na riadku 187 boli pridané argumenty *figure* a *table* pre vytvorenie zoznamu obrázkov a tabuliek na začiatku dokumentu.


```xml
<xsl:param name="generate.toc">
book      title,toc,figure,table
</xsl:param>
```

---

## Využité konštrukcie:

Na zvýraznenie textu bola použitá konštrukcia **emphasis** s atribútom *role* nastaveným na *bold* alebo *italic*.

```xml
<emphasis role="bold">
```

```xml
<emphasis role="italic">
```

---

Na členenie textu boli použité: **chapter** na kapitoly, **section** na podkapitoly a vnorené **section** na podpodkapitoly. Na podkapitoly, ktoré nie sú ukázané v obsahu bola použitá konštrukcia **simplesect**.

```xml
<chapter>
	kapitola
	<section>
		podkapitola
		<section>
			podpodkapitola
		</section>
	</section>
</chapter>
```

```xml
<simplesect></simplesect>
```

---

Vytvorenie zoznamov:

* nečislovaný zoznam pomocou **itemizedlist**,
* číslovaný zoznam pomocou **orderedlist**,

položky v týchto zoznamoch boli vytvorené pomocou **listitem**.

```xml
<itemizedlist>
	<listitem>
		<para>vec 1</para>
	</listitem>
	<listitem>
		<para>vec 2</para>
	</listitem>
</itemizedlist>
```

---

Vloženie obrázka, ktorý obsahuje v názve poznámku pod čiarou s citáciou na zdroj. Vďaka atribútu *id* v elemente *figure* dokážeme na tento obrázok odkazovať z textu.

```xml
<figure id="architecture_figure">
	<title>
		Základná architektúra MOD systému 
		<footnote>
			<para>
				<xref linkend="bib.mod"/><citetitle>(Funtoro, 2011)</citetitle>
			</para>
		</footnote>
	</title>
	<mediaobject>
		<imageobject>
			<imagedata fileref="figures/struktura_bus.jpg" scale="150"/>
		</imageobject>
	</mediaobject>
</figure>
```

---

Vloženie tabuľky, ktorej názov obsahuje poznámku pod čiarou s citáciou na zdroj. V elemente *tgroup* sme nastavili atribút *align* na left, kedže chceme zarovnávanie textu vľavo a atribút *cols* na hodnotu 2, keďže máme 2 stĺpce. Element **thead** obsahuje hlavičku tabuľky a **tbody** obsahuje telo tejto tabuľky.

```xml
<table frame="all">
	<title>
		Špecifikácia MOD servera 
		<footnote>
			<para>
				<xref linkend="bib.futureMOD"/>
				<citetitle>(Baránek, 2017)</citetitle>
			</para>
		</footnote>
	</title>
	<tgroup align="left" cols="2" colsep="1" rowsep="1">
		<colspec colname="c1"/>
		<colspec colname="c2"/>
		<thead>
			<row>
				<entry>Komponent</entry>
				<entry>Veľkosť/počet</entry>
			</row>
		</thead>
		<tbody>
			<row>
				<entry>RAM</entry>
				<entry>2GB</entry>
			</row>
		</tbody>
	</tgroup>
</table>
```

---

Odkazy na iné časti dokumentu, napr. tabuľky. Pomocou elementu *link* dokážeme odkazovať na iné časti dokumentu, stačí ako v atribúte *linkend* nastavíme id elementu, na ktorý chceme odkazovať.

```xml
<link linkend="html_comparison">tabuľka 2.2</link>
```

---

Vytváranie indexov. Termín pre index sa vytvára pomocou elementu *indexterm*. Tento element následne obsahuje podelementy *primary* a *secondary*. 

```xml
<indexterm>
	<primary>Výmena dát</primary>
	<secondary>JSON</secondary>
</indexterm>
```

Výpis týchto termínov sa následne uskutoční pomocou elementu *index*.

```xml
<index type="name"/>
```

---

Ukážka kódu:

```xml
<example>
	<title>Ukážka JSON</title>
	<programlisting>
		<![CDATA[
		{ 
			"firstname" :"Jan",
			"lastname" :"Mrkvicka",
			"age" :22,
			"city" :"Bratislava",
			"student" :"yes" 
		}
		]]>
	</programlisting>
</example>
```

---

Vytvorenie bibliografického odkazu:

```xml
<bibliomixed id="bib.mpeg-4">
	Richardson, I. E. G. 
	<title>
		H.264 and MPEG-4 video compression video coding for next-generation multimedia.
	</title>
	Willey, 2003. S. 1-3
</bibliomixed>
```

a následné citovanie v texte:

```xml
<xref linkend="bib.mpeg-4"/>
```
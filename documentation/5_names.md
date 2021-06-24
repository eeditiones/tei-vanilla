# Names, Entities, Indexes

## Introduction

An important element of editions are the indexes. Usually, one distinguishes between different indexes, e.g. an index of persons, places and terms. Other subdivisions (e.g. only an index of names) and further registers (e.g. organisations, biblical passages, cited literature, etc.) are possible and common.

In digital editions, the entries shown in the indexes can be provided with further information (e.g. dates of birth and death, geo-coordinates, etc.) and identified via so-called authority files  or databases (e.g. VIAF, GND). On the one hand, this makes it possible to make further information available in the editions from the external resources. On the other hand, the identified entities can be used to make one's own edition a web-resource for other editions and projects.

Working with TEI entities are tagged in the text. In the respective tag, the entity can be identified and it can be linked to a place where further information can be found.

### Simple Example

```xml
... y por otra de <name type="person" ref="#IDPe156">Gerónimo Sailer</name> que Vuestra Señoría havía obispado,
```

In this example `@ref` contains an XML-ID which can be found within the same document in the `<teiHeader>`:

```xml
<teiHeader>
    ...
    <profileDesc>
        ...
        <particDesc>
            <listPerson>
                ... <!-- more person entries -->
                <person xml:id="IDPe156">
                  <persName>Hieronymus Sailer</persName>
                  <note>(<persName>Hieronymus Seiler</persName>) (1495 – 1559-06-15); in 1524 agent
                     of the Welsers' company in Spain, and later, from 1528, in Venezuela. After his
                     return to Europe, he dealt with the Welsers' affairs at the Spanish court, in
                     1540 he became their agent in Antwerp. Son-in-law of Bartholomäus Welser (;
                     POCIECHA 4, p. 260; NDB, Bd. 22, p. 355-356).</note>
               </person>
               ... <!-- more person entries -->
            </listPerson>
        </particDesc>
    </profileDesc>
</teiHeader>
```

## Taging Entities in the Text

### `<rs>` referencing string

[TEI P5](https://tei-c.org/release/doc/tei-p5-doc/de/html/ref-rs.html)

The most generic element for tagging entities in the text is `<rs>`. With this element you can tag enities even if they are not explicitly named. You should add a `@type`and this type should correspondent with one of your indexes (eg. person, place, ...).

#### Example
```xml
... la <rs type="person" ref="#IDPe2777">marquesa</rs> ...
```

With `<rs>` and the attributes `@type` and `@subtype` you could construct a universe of different entities.

### `<name>` name, proper noun

[TEI P5](https://tei-c.org/release/doc/tei-p5-doc/en/html/ref-name.html)

If an entity has a name then you can use `<name>`. As for `<rs>` you should add a `@type` Attribute.

#### Example
```xml
... y por otra de <name type="person" ref="#IDPe156">Gerónimo Sailer</name> que Vuestra Señoría havía obispado,
```

### `<persName>` personal name

[TEI P5](https://tei-c.org/release/doc/tei-p5-doc/en/html/ref-persName.html)

TEI offers some special tags for tagging some types of entites. `<persName>` can be understood as a shortcut for `<name type="person">`. With the usage of `<persName>` the `@type` ist free to add further informations. That is why the TEI Guidelines prefer `<persName>`.

#### Examples

```xml
... <persName ref="#MzB">Michael de Buczacz</persName> ...
```

```xml
... <persName role="issuer" ref="per009962">Cuni am Wasen</persName> ...
```

### `<orgName>` organization name

[TEI P5](https://tei-c.org/release/doc/tei-p5-doc/en/html/ref-orgName.html)

`<orgName>` can be understood as a shortcut for `<name type="organziation">`.

To tag organzation you should have a clear understanding what in your edition is meant by the term "organization". That is sometimes hard to decide (eg. "Bishop of Konstanz").

### `<placeName>` place name

[TEI P5](https://tei-c.org/release/doc/tei-p5-doc/en/html/ref-placeName.html)

`<placeName>` can be understood as a shortcut for `<name type="place">`.

### `<origPlace>` origin place

[TEI P5](https://tei-c.org/release/doc/tei-p5-doc/en/html/ref-origPlace.html)

`<origPlace>` can be understood as a shortcut for `<name type="place" role="origin">`.

`<origPlace>` is usually used within manuscript descriptions (`<msDesc>`). For charters `<originPlace>` can also be used in the text.

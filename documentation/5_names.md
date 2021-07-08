# Names, Entities, Indexes

## Introduction

An important element of editions are the indexes. Usually, one distinguishes between different indexes, e.g. an index of persons, places and terms. Other subdivisions (e.g. only an index of names) and further registers (e.g. organisations, biblical passages, cited literature, etc.) are possible and common.

In digital editions, the entries shown in the indexes can be provided with further information (e.g. dates of birth and death, geo-coordinates, etc.) and identified via so-called authority files  or databases (e.g. VIAF, GND). On the one hand, this makes it possible to make further information available from external resources. On the other hand, the identified entities can be used to make one's own edition a web-resource for other editions and projects.

Working with TEI, entities are tagged in the text. In the respective tag, the entity can be identified and it can be linked to a place where further information can be found.

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

## Tagging Entities in the Text

For people (`<persName>`), organizations (`<orgName`) and places (`placeName`) there are special tags. It is common and recomended to use these tags. Other entities can be costructed with `<name>` and `<rs>` and the use of `@type`.


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

`<orgName>` can be understood as a shortcut for `<name type="organization">`.

To tag organzation you should have a clear understanding what in your edition is meant by the term "organization". That is sometimes hard to decide (eg. the "Bishop of Konstanz" as an instutition is neither a natural person nor an organization, so you would have to decide how to deal with it).

### `<placeName>` place name

[TEI P5](https://tei-c.org/release/doc/tei-p5-doc/en/html/ref-placeName.html)

`<placeName>` can be understood as a shortcut for `<name type="place">`.

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


### `<origPlace>` origin place

[TEI P5](https://tei-c.org/release/doc/tei-p5-doc/en/html/ref-origPlace.html)

`<origPlace>` can be understood as a shortcut for `<name type="place" role="origin">`. `<origPlace>` is usually used within manuscript descriptions (`<msDesc>`) in the `<teiHeader>`. For charters `<originPlace>` can also be used in the text as there the usually there is a designated place where the charter was issued.

## Registers, Indexes, Lists

If you just want a list of entries you could easily extract all entries with an xpath-expression an create dynamically an index (eg. `//persName`). This is usually not sufficient since in the text the names vary and so the list can become quite confusing. There is no official way to store a normalized form in an attribute (you could misuse `@key` for that) and it would be redunant as soon as a name occurs more than once. Therefore, it is advisable to normalise the entries in a list and refer to that. This also has the advantage that you can easily add further information th the entries. Unfortunately, there is no uniform method in TEI to create these lists.

### `<listPerson>` and `<listOrg>`

The indexes of people `<persList>` and organization `<orgList>` should reside within a `<particDesc>` (participation description) which itself is in `<profileDesc>` (text-profile description: provides a detailed description of non-bibliographic aspects of a text).

```xml
<teiHeader>
    ...
    <profileDesc>
        <particDesc>
            <listPerson>
                ...
            </listPerson>
            <listOrg>
                ...
            </listOrg>
        </particDesc>
    <profileDesc>
        ...
</teiHeader>
```

## Connecting the Tagged Entities with an index or an external Database

There different ways how you can link the tagged entity in the text with an external entry.

### `@ref`: `<persList>` in the `<teiHeader>`

A very simple approach to connect the tagged entries with list-entries is to have the lists within the same TEI file. This is specially a good solution for smaller editions. What do you


### `@ref`: `<persList>` in a separate file

### `@ref`: A key of a database

### `@ref` with a Url to a Authority Database

### `@key`: A key of a database

# common

Automatikusan generált `common` repository.

## Repository célja

A `common` repository az ÁNYK kivezetéséhez kapcsolódó új NAV M2M 4.0 bizonylatkezelési modell közös, több bizonylattípus által újrafelhasználható XML/XSD állományait tartalmazza.

A repository célja, hogy az űrlapspecifikus leíró repository-k:

- ne külön definiálják az általánosan használt szerkezeti elemeket,
- egységesen hivatkozhassanak közös sémaelemekre,
- közös enumerációkat és törzsadatokat használjanak,
- valamint konzisztens validációs logikát alkalmazzanak.

A repository központi szerepet tölt be az új NAV M2M 4.0 XML-alapú űrlapkezelési architektúrában.

---

## Kontextus

Az ÁNYK kivezetéséhez kapcsolódó NAV M2M 4.0 fejlesztések célja, hogy az ügyviteli szoftverek számára szabványosabb, automatizálhatóbb és könnyebben feldolgozható űrlapkezelési megoldás álljon rendelkezésre.

Az új NAV M2M bizonylat API-ban az űrlapok adatszerkezete XML alapon, űrlaponként saját XSD állományban kerülnek leírásra. Ezek az űrlapspecifikus XSD-k egységes szerkezeti elveket követnek, és közös elemekre, típusokra, enumerációkra, valamint metaséma-elemekre támaszkodhatnak.

Ez a repository ehhez a közös alapréteghez tartozik.



### A `common` repository szerepe az architektúrában

Az új generációs űrlapkezelési architektúra három fő repository-típusra épül:

| Repository név | Szerep |
| --- | --- |
| common | közös sémák, metasémák, enumerációk, törzsadatok |
| űrlapspecifikus repository-k | konkrét űrlapleírók |
| `catalog` | verzió- és érvényességi katalógus |

A `common` repository kizárólag közös, újrafelhasználható elemeket tartalmaz.


### Kapcsolat az űrlapspecifikus repository-kkal

Az űrlapspecifikus repository-k:

- az adott nyomtatvány konkrét XML struktúráját,
- UI modelljeit,
- validációs metaadatait,
- valamint üzleti szabályait

tartalmazzák.

Ezek az űrlapspecifikus repository-k a `common` repository által biztosított:

- közös típusokra,
- enumerációkra,
- metaséma-elemekre,
- valamint törzsadatokra

épülnek.

## Sémafüggőségek és validáció

Az űrlapspecifikus XSD állományok a `common` repository-ban található közös sémaelemekre `xs:import` vagy `xs:include` mechanizmuson keresztül hivatkozhatnak.

A közös sémák biztosítják, hogy:
- az azonos jelentésű adatszerkezetek egységesen kerüljenek leírásra,
- a validációs szabályok konzisztensen alkalmazhatók legyenek,
- a különböző űrlaptípusok közös XML szerkezeti elveket kövessenek,
- valamint a törzsadatok és enumerációk központilag karbantarthatók legyenek.


---

## A repository felépítése, állományai

A repository fő tartalmai a `content/` könyvtárban találhatók.

```text
common/
└── content/
    ├── xsd/
    │   ├── altalanos_enum.xsd
    │   ├── form_xsd_metaschema.xsd
    │   └── ...
    │
    └── xml/
        ├── altalanos_iranyitoszam.xml
        ├── altalanos_banknev.xml
        └── ...
```



---

## Kapcsolódó dokumentációk

Az új M2M bizonylatkezelési modellhez és az ÁNYK kivezetéséhez kapcsolódó háttéranyagok:

- [ÁNYK kivezetéshez kapcsolódó M2M fejlesztések](https://github.com/nav-gov-hu/M2M/wiki/%C3%81NYK-kivezet%C3%A9shez-kapcsol%C3%B3d%C3%B3-M2M-fejleszt%C3%A9sek)
- [Új bizonylat API](https://github.com/nav-gov-hu/M2M/wiki/%C3%9Aj-bizonylat-API)
- [Új bizonylat API: XML formátum](https://github.com/nav-gov-hu/M2M/wiki/%C3%9Aj-bizonylat-API:-XML-form%C3%A1tum)
- [Új bizonylat API: XML validáció](https://github.com/nav-gov-hu/M2M/wiki/%C3%9Aj-bizonylat-API:-XML-valid%C3%A1ci%C3%B3)


### Megjegyzések

- A repository közös sémaelemeket tartalmaz, nem egy konkrét űrlaptípus teljes leírását.
- Az űrlapspecifikus mezők, blokkok, ellenőrzési szabályok az adott űrlap saját leíró repository-jában találhatóak meg.


## Technikai jelleg

A repository technikai célú, gépi feldolgozásra optimalizált séma- és metasémaállományokat tartalmaz.

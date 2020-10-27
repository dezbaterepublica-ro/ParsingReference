Indicatii pentru robotul automat de parsare a dezbaterilor publice

# Structura folderelor
| Authority Type | Folder Structure | Example |
| -------------- | ---------------- | ------- |
| National Authority | "National"/[AutoritateaPublica] | National/Ministerul Afacerilor Externe |
| County Authorities | "Local"/[Judet]/[AutoritateaPublica] | Local/Arad/Consiliul Județean Arad |
| UAT-Authorities | "Local"/[Judet]/[UAT]/[AutoritateaPublica] | Local/Bacău/Municipiul Bacău/Primăria Municipiului Bacău |

# Exemple de formatare ale unitatiilor geografice
| Entity | Example Formats |
| ------ | -------------- |
| County | Județul Bacău, Județul Mureș |
| București | Municipiul București |
| Municipality | Municipiul Bacău |
| Town | Orașul Roznov |
| Village | Comuna Bragadiru |

# Example de formatare ale autoritatiilor publice
| Entity | Example Formats |
| ------ | --------------- |
| Primarie | Primaria Municipiului Cluj-Napoca, Primaria Comunei Bragadiru |
| Consilii judetene | Consiliul Judetean Arad |

# Fisierele din folderul unei autoritati publice

Formatul fisierelor este [JSON](https://www.json.org/json-ro.html). [Link catre un editor json in browser](https://jsoneditoronline.org/).

| File | Description |
| ---- | ----------- |
| list.txt | Instructiuni specifice descoperirii listei de dezbateri publice; contine pagina de inceput a scanarii, elementele link catre pagina de detaliu a dezbateri publice, elemente de paginare pentru indexarea tuturor paginilor |
| detail.txt | Instructiuni specifice elementelor dezbaterii publice; contine elementele dezbaterii publice din pagina de detaliu |

# Elemente list.txt
| Element | Tip | Descriere |
| ------- | --- | --------- |
| initial-url | string(link) | Pagina pe care bot-ul ca intra prima data in timpul procesului de indexare |
| detail-url-css-selector | string(css-selector) | Toate elementele <a> care contin link-uri catre dezbateri publice |
| next-page-css-selector | string(css-selector) | Un singur element <a> care contine link-ul catre urmatoarea pagina; acest selector trebuie sa returneze link-ul catre urmatoarea pagina indiferent de pagina de lista pe care se afla botul |
| page-css-selector | string(css-selector) | Toate elementele <a> care au ca "href" link-ul catre o pagina si ca textContent numarul pagini |
| details | object | Daca pe pagina de listare se afla expuse direct detaliile dezbaterii publice si nu exista o pagina speciala alocata fiecarei dezbateri, se poate completa acest obiect cu elementele de detaliu, asa cum sunt descrise in sectiunea `Elemente list.txt/details object` |

# Elemente details.txt
| Element | Tip | Descriere |
| ------- | --- | --------- |
| publish-date-css-selector | string(selector) | Un singur element de orice tip, botul va folosi continutul textContent ca si publish-date |
| publish-date-format-static | string(php-date-format) | Formatul datei asa cum este descris de PHP [in pagina help pentru date](https://www.php.net/manual/ro/function.date.php) |
| attachments | object | Un obiect care include selectori pentru atasamente. Proprietatile atasamentelor sunt luate in ordine. |
| attachments.title-css-selector | string(selector) | Elementele de orice tip, se preia textContent ca si titlu. |
| attachments.link-css-selector | string(selector) | Elementele de tip <a> care au ca href link-ul catre atasament. |
| attachment-css-selector | string(selector) | Elementele de tip <a> care au ca href link catre atasamente si textContent-ul ca titlu |
| description-css-selector | string(selector) | Un singur element de orice tip, botul va folosi continutul textContent ca si descriere |
| title-css-selector | string(selector) | Un singur element de orice tip, botul va folosi continutul textContent ca si titlu |
| contact-css-selector | string(selector) | Un singur element de orice tip, botul va folosi continutul textContent ca si contact |
| phone-contact-css-selector | string(selector) | Un singur element de orice tip, botul va folosi continutul textContent ca si phone-contact |
| email-contact-css-selector | string(selector) | Un singur element de orice tip, botul va folosi continutul textContent ca si email-contact |

# Elemente list.txt/details object

Elementele "relative" vor fi selectate concatenand elementul "main-css-selector" si selectorul relativ.

| Element | Tip | Descriere |
| ------- | --- | --------- |
| main-css-selector | string(selector) | Un singur element care contine detaliile despre o dezbatere publica. Celelalte elemente vor folosi acest selector ca baza pentru selectoarele lor |
| publish-date-css-selector-relative | string(selector) | Un singur element de orice tip, botul va folosi continutul textContent ca si publish-date |
| publish-date-format-static | string(php-date-format) | Formatul datei asa cum este descris de PHP [in pagina help pentru date](https://www.php.net/manual/ro/function.date.php) |
| attachments | object | Un obiect care include selectori pentru atasamente. Proprietatile atasamentelor sunt luate in ordine. |
| attachments.title-css-selector-relative | string(selector) | Elementele de orice tip, se preia textContent ca si titlu. |
| attachments.link-css-selector-relative | string(selector) | Elementele de tip <a> care au ca href link-ul catre atasament. |
| description-css-selector-relative | string(selector) | Un singur element de orice tip, botul va folosi continutul textContent ca si descriere |
| title-css-selector-relative | string(selector) | Un singur element de orice tip, botul va folosi continutul textContent ca si titlu |
| contact-css-selector-relative | string(selector) | Un singur element de orice tip, botul va folosi continutul textContent ca si contact |
| phone-contact-css-selector-relative | string(selector) | Un singur element de orice tip, botul va folosi continutul textContent ca si phone-contact |
| email-contact-css-selector-relative | string(selector) | Un singur element de orice tip, botul va folosi continutul textContent ca si email-contact |

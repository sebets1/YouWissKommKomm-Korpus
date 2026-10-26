# YouWissKommKomm - Korpus aus Youtube Kommentaren in Wissenschaftskommunikations-Videos

## Grunddaten
- Links:
  - Projektwebsite: https://eee-sciencedebates.digital/
  - Korpus auf internem Lehrstuhlserver und auf LCP
  - LCP Link: https://catchphrase.linguistik.uzh.ch/query/487/Science-Youtube-Comments-complete
  - Öffentliche Korpusbeschreibung auf Github: https://github.com/sebets1/YouWissKommKomm-Korpus
  - Öffentlicher Code und Demokorpus auf Github: https://github.com/sebets1/YouWissKommKomm-Erstellung-eines-Korpus-von-YouTube-Wissenschaftskommentaren
- Name: YouWissKommKomm 
- Quellen: Gescrapte Kommentare zu deutschsprachigen Youtube Videos mit Wissenschaftsthemen.
- Ersteller*innen: Seraina Betschart, Xenia Bojarski, Gunilla Kaibel 
- Nutzungsrechte: darf von angemeldeten Nutzer*innen verwendet werden

## Korpus Metadaten
- Anzahl Videos: 928
- Anzahl Kommentare: 1'267'126
- Anzahl Threads/Unterhaltungen (top-level comment + replies): 81'066
- Anzahl Tokens: 59'025'918
- Anzahl Types: 875'462

## Kurzbeschreibung
Das Korpus beinhaltet 1.26 Mio. Kommentare unter 928 Videos. 
Die durchschnittliche Kommentarlänge beträgt 46,6 Wörter, wobei die Länge von einem Wort bis hin zu 6.404 Wörtern pro Kommentar reicht.
Sämtliche ausgewählten Videos stammen von drei verschiedenen Youtube Kanälen, die alle im Bereich 
Wissenschaftskommunikation anzusiedeln sind: *MAITHINK X*, *MrWissen2go* und *Dinge erklärt – Kurzgesagt*.
Die Kommentare aus dem Zeitraum Mai 2012 bis April 2024. Scraping der Daten fand statt zwischen Januar und März 2024.
Bei der Aufbereitung des Korpus lag der Fokus auf der Nachverfolgung von Gesprächsmustern (wer antwortet wem, wie schnell etc.).

Das Korpus entstand im Rahmen des Projekts [eeeScienceDebates](https://eee-sciencedebates.digital/).


## Format und Metadaten
Das Korpus ist im CSV Format (kommagetrennte Spalten). 
Pro Zeile gibt es einen Kommentar mit allen Metadaten (ein Metadatum pro Spalte).
Im Folgenden sind alle Metadaten aufgelistet:

| Name                  | Erklärung                                                                                                                                                            | Name auf LCP*            |
| --------------------- |----------------------------------------------------------------------------------------------------------------------------------------------------------------------|--------------------------|
| `row_id`              | Zeilennummerierung                                                                                                                                                   | /                        |
| `id`                  | Eindeutig identifizierbare ID. Enthält Infos zu Videokanal, Typ und Sprecherzuweisung.                                                                               | `id`                     |
| `type`                | Mögliche Values: `comment` oder `reply`. Je nachdem, ob der Kommentar ein *top-level comment* oder eine Antwort auf einen Kommentar ist.                             | `type`                   |
| `old_id`              | Automatisch zugewiesene ID beim Scraping. Pro Thread eine ID.                                                                                                        | /                        |
| `channel_title`       | YouTube-Kanal, auf dem der Kommentar veröffentlicht wurde. Mögliche Values: `MAITHINK X`, `Dinge Erklärt - Kurzgesagt` oder `MrWissen2go`.                           | `channel`                |
| `video_title`         | Titel des Videos, unter dem der Kommentar veröffentlicht wurde.                                                                                                      | `title`                  |
| `author`              | Name des YouTube-Accounts, welcher den Kommentar geschrieben hat.                                                                                                    | `author`                 |
| `Sprecher_ID`         | Zugewiesener Handle, um zurückzuverfolgen, wer auf wen antwortet. Ein *top-level comment* erhält die Zuweisung `OC` (original comment), die folgenden nach Alphabet. | /                        |
| `num_replies`         | Anzahl Antworten, die ein Kommentar erhielt.                                                                                                                         | `num_replies`            |
| `Adressierung`        | Values `True` oder `False`, je nachdem, ob der Kommentar direkt an einen anderen Kommentar adressiert ist (`@author`) oder nicht.                                    | `direct_address`         |
| `Antwort_auf`         | Sprecher-ID des Kommentars, auf den geantwortet wird. Default ist `OC0` (Antwort auf den *top-level comment* des Threads).                                           | `replyto`                |
| `reply_type`          | Mögliche Values: `beteiligter_OC`, `unbeteiligter_OC`, `single_reply`, `ongoing_first`, `ongoing`, `ongoing_last`.                                                   | /                        |
| `reply_time-d`        | Anzahl vergangener Tage seit dem Kommentar, auf den geantwortet wird.                                                                                                | /                        |
| `reply_time-h`        | Anzahl vergangener Stunden (zusätzlich zu den Tagen) seit dem Kommentar, auf den geantwortet wird.                                                                   | /                        |
| `reply_time-s`        | Anzahl vergangener Sekunden (zusätzlich zu Stunden und Tagen) seit dem Kommentar, auf den geantwortet wird.                                                          | /                        |
| `reply_time_tot-in_s` | Insgesamt vergangene Zeit in Sekunden seit dem Kommentar, auf den geantwortet wird.                                                                                  | `reply_time_in_s`        |
| `error_code`          | Bei der Verarbeitung der Daten kamen einige Probleme auf. Einige mögliche Probleme wurden definiert und getaggt (siehe unten).                                                     | /                        |
| `prob_spam`           | Heuristik im Code, um Spam-Nachrichten zu erkennen, zu markieren und aus der Analyse auszuschließen.                                                                 | /                        |
| `pub_date`            | Datum der Veröffentlichung des Kommentars.                                                                                                                           | `date`                   |
| `updated`             | Falls ein Kommentar bearbeitet wurde, würde das Datum hier angepasst. Wir mussten jedoch feststellen, dass `updated` immer das gleiche Datum enthält wie `pub_date`. | /                        |
| `like_count`          | Anzahl Likes, die der Kommentar bekam.                                                                                                                               | `likes`                  |
| `body`                | Der eigentliche Inhalt des Kommentars.                                                                                                                               | `Comment`                |
| `tagged_body`         | Kommentar mit Part-of-Speech-Tagging nach dem Schema `token_pos`.                                                                                                    | *Suche nach POS möglich* |

*Das vollständige Korpus ist auf der Korpusplattform [LCP](https://lcp.linguistik.uzh.ch/) unter dem Namen `Science Youtube Comments` zugänglich (mit entsprechender Berechtigung). 
Nicht alle Metadaten wurden auf LCP übernommen.

## Dokumentation Auswahl, Download und Aufbereitung der Daten


### Auswahl und Scraping der Daten
Das Korpus besteht aus YouTube-Kommentaren von drei großen deutschsprachigen Wissenschaftskommunikationskanälen: 
*MAITHINK X* (ehemals *maiLab*), *MrWissen2go* und *Dinge erklärt – Kurzgesagt*. 
Die Kanäle behandeln unterschiedliche Themen und richten sich an verschiedene Altersgruppen.

***MAITHINK X*** behandelt vor allem naturwissenschaftliche Inhalte. 
Das Format dreht sich um die Chemikerin und Wissenschaftsjournalistin Mai Thi Nguyen-Kim. 
Die reichweitenstärksten Videos behandeln die Themen Corona, Gesundheit und Metathemen wie bspw. wissenschaftliche Berichterstattung oder Diskussionen im Internet. 
Der Kanal war bis 2024 ein Teil von *funk*, dem öffentlich-rechtlichen Netzwerk für Inhalte für Jugendliche und junge Erwachsene auf diversen Plattformen. 
Seit 2024 ist *MAITHINK X* Teil von *ZDFneo*.

***MrWissen2go*** behandelt politische und historische Inhalte. 
Der Historiker und Journalist Mirko Drotschmann tritt als in den Videos als MrWissen2go auf und erklärt Inhalte. 
Die Zielgruppe ist recht jung, einige Videos adressieren bspw. direkt Inhalte, die für Abiturprüfungen relevant sind, und erklären sie. 
Beliebte Videos thematisieren Wahlen und Parteien in Deutschland, konstruieren Szenarien (*Was wäre wenn…?*) oder ordnen Weltpolitik und Zeitgeschehen ein. 
Der Kanal ist im Grenzbereich zwischen Wissenschaftskommunikation, Erklärjournalismus (*Explainer*-Format) und Polit-Influencer zu verorten. 
Seit 2017 ist er auch Teil von *funk*.

***Dinge Erklärt – Kurzgesagt*** behandelt vorwiegend astronomische und philosophische Inhalte, aber auch gesellschaftlich-politische Themen.
Die Videos sind animiert. Die meistaufgerufenen Videos sind auch bei diesem Kanal Was wäre wenn-Szenarien. 
Von 2017 bis 2022 war auch dieser Kanal Teil von *funk*.

Von diesen Kanälen wurden alle Kommentarthreads gecrawlt, die aus mindestens fünf Kommentaren bestehen, da der Fokus auf Interaktionen liegt. 
Zu den automatisch erhobenen Metadaten gehören der Zeitstempel und der Name der kommentierenden Person.

### Verarbeitung
Für die Verarbeitung und Annotation des Korpus dient das Script `process_yt_corpus.py`.
Dieses erhält das rohe CSV Korpus vom Scraping als Input und gruppiert die Kommentare in Threads (in sich abgeschlossene Unterhaltungen), 
in dem es zu einem Kommentar des Types *comment* alle folgenden Kommentare des Types *reply* bis zum nächsten *comment* zuordnet.
Anschließend werden zusätzliche Metadaten automatisch annotiert:

- Zuweisung eindeutiger Sprecher-IDs innerhalb jedes Threads
- Identifizierung, auf welchen Kommentar sich jede Antwort bezieht
- Berechnung der Zeitspanne bis zur Antwort
- Klassifizierung verschiedener Antworttypen (ist der ursprünglich Kommentierende involviert in der Unterhaltung, 
meldet sich ein Antwortende nur einmal oder nimmt aktiv an der Unterhaltung teil usw.)
- Erkennung potenzieller Fehlklassifizierungen (gelöschte Antworten, Probleme mit Zeitstempeln usw.)

Schlussendlich speichert das Script das verarbeitete Korpus in ein neues CSV ab.

**Weitere Hinweise:**

Zum Zeitpunkt der Datenerhebung wiesen die Kommentarbereiche zwei Hierarchieebenen auf: 
Kommentare der ersten Ebene, die einen Thread eröffnen, und Kommentare der zweiten Ebene, die auf den Ausgangskommentar oder auf andere Kommentare der zweiten Ebene reagieren. 
Wenn Kommentierende auf einen Kommentar der zweiten Ebene reagieren und die Funktion „Antworten“ verwenden, erscheint der Name der Person, 
auf deren Kommentar sie Bezug nehmen, automatisch (in den gecrawlten Daten mit einer `@@`-Markierung versehen) am Anfang des neuen Kommentars. 
Das ist ungefähr seit 2018 der Fall. Zuvor wurden verschiedene Formen der Adressierung verwendet, darunter `*****username`, `+username` und `@username`. 
Auf der Grundlage dieser Informationen lassen sich für jeden Kommentar Metadaten dazu erstellen, auf welchen vorangegangenen Kommentar er Bezug nimmt.
Die Usernames sind anonymisiert und durch Buchstaben ersetzt. OC (*Original Commenter*) ist immer die Person, die den Thread-initialen Kommentar verfasst hat. 
Danach werden die Kommentierenden in der Reihenfolge ihres ersten Kommentars mit Buchstaben in alphabetischer Reihenfolge bezeichnet. 
Die Buchstaben werden für jeden Thread neu vergeben. Bei Person A handelt es sich also nicht über mehrere Threads hinweg um die gleiche Person, 
sondern immer um diejenige Person, die als erstes auf den jeweiligen Thread-initialen Kommentar von OC reagiert hat.

### Schwierigkeiten bei der Verarbeitung
Die Rekonstruktion von Gesprächsstrukturen auf YouTube basiert auf öffentlich verfügbaren Metadaten und expliziten 
Adressierungen innerhalb der Kommentare. 
Aufgrund von Besonderheiten der Plattform lassen sich Antwortbeziehungen jedoch nicht in allen Fällen eindeutig rekonstruieren.

Insbesondere treten folgende Probleme auf:

- Gelöschte Kommentare und Accounts. Wurde ein Kommentar oder der dazugehörige Account gelöscht, fehlen einzelne Elemente einer Unterhaltung. Antworten können dadurch scheinbar keinem Kommentar mehr zugeordnet werden.
- Änderungen von Nutzernamen. User können ihren Anzeigenamen ändern. Während neuere @-Verlinkungen automatisch aktualisiert werden, bleiben ältere Textnennungen unverändert. Dadurch können Kommentare derselben Person unter unterschiedlichen Namen erscheinen.
- Historische Änderungen der Plattform. Ältere Kommentare wurden teilweise vor Einführung der heutigen Reply-Funktion oder des @-Mentions-Systems erstellt. Antworten sind dort häufig nur über Freitext (z.B. den ausgeschriebenen Namen) erkennbar und lassen sich nicht immer eindeutig zuordnen.
- Unvollständige oder fehlerhafte Zeitstempel. Einzelne Kommentare besitzen ungültige oder fehlende Veröffentlichungsdaten (z.B. den Defaultwert 1970-01-01). Dadurch können Berechnungen der Antwortzeiten fehlerhaft werden.
- Adressierungen ohne @-Mention. Manche Antworten nennen lediglich den Klarnamen oder Teile des Nutzernamens einer Person. 

Aus diesen Gründen können einzelne Gesprächsverläufe unvollständig oder fehlerhaft rekonstruiert werden. 
Ein Mapping mit Levensthein Distanz ist implementiert und erhöht den Recall beim Erkennen von Addressierungen. 
Die Datenqualität verbessert sich dann insbesondere bei neueren Kommentaren (ab etwa 2019), da YouTube seitdem das 
heutige @-Mentions-System verwendet und dieses auch bei späteren Namensänderungen konsistenter aktualisiert.

#### Automatische Fehlererkennung

Da sich Gesprächsverläufe auf YouTube aufgrund gelöschter Kommentare, geänderter Nutzernamen oder inkonsistenter 
Metadaten nicht immer eindeutig rekonstruieren lassen, werden während der Verarbeitung potenziell problematische 
Fälle automatisch erkannt und in der Spalte `error_code` gekennzeichnet.

| Fehlercode | Bedeutung |
|------------|-----------|
| `ERR_DEL_REPLY` | Ein Kommentar antwortet auf einen Kommentar, der im Korpus nicht mehr vorhanden ist. Mögliche Ursachen sind gelöschte Kommentare oder Accounts sowie Inkonsistenzen in den von YouTube bereitgestellten Daten. |
| `ERR_NEG_REPLY_SPEED` | Die berechnete Antwortzeit ist negativ. Dies deutet auf fehlerhafte oder inkonsistente Zeitstempel hin. |
| `ERR_NEG_SPEED_X` | Kennzeichnet den Kommentar, auf den sich ein `ERR_NEG_REPLY_SPEED` bezieht und der vermutlich die fehlerhafte Zeitinformation verursacht. |
| `ERR_CHANGED_USER` | Wahrscheinlich wurde ein Nutzername geändert, wodurch die automatische Zuordnung einer Adressierung erschwert wird. |

Ein nachgestelltes **`b`** (z. B. `ERR_DEL_REPLY_b`) bedeutet, dass der betreffende Kommentar selbst keinen Fehler aufweist, 
sich jedoch innerhalb einer Unterhaltung befindet, in der zuvor bereits ein Fehler erkannt wurde. 
Solche Konversationen sollten mit entsprechender Vorsicht interpretiert werden.

Wird innerhalb einer Unterhaltung mindestens ein Fehler erkannt, erhält zusätzlich der ursprüngliche *top-level comment* (`OC`) eine Markierung. 
Dadurch können Konversationen mit erkannten Fehlern bei Bedarf einfach identifiziert oder von Analysen ausgeschlossen werden.


## Publikationen

[folgt]

## Code
Die Skripte für das Scraping, Aufbereitung und Verarbeitung der Daten befinden sich in folgendem Repository:

https://github.com/sebets1/YouWissKommKomm-Erstellung-eines-Korpus-von-YouTube-Wissenschaftskommentaren



---------
Zuletzt aktualisiert: 26.10.2026

Seraina Betschart
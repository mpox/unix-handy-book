# IMAP via TELNET

Connect to the server

	openssl s_client -connect mail.marekpoks.pl:993


Login to a user account

	LOGIN empox@marekpoks.pl <user's password here>



List all folders:

	LIST “<mailbox path>” “<search argument>”

Example command:

		? LIST "" "*"

Example response

```
* LIST (\HasChildren) "/" Archiwum
* LIST (\HasNoChildren) "/" Archiwum/Tidal
* LIST (\HasNoChildren) "/" Calendar
* LIST (\HasChildren) "/" Contacts
* LIST (\HasNoChildren \Trash) "/" "Deleted Items"
* LIST (\HasNoChildren \Drafts) "/" Drafts
* LIST (\Marked \HasNoChildren) "/" INBOX
* LIST (\HasNoChildren) "/" Journal
* LIST (\HasNoChildren \Junk) "/" "Junk Email"
* LIST (\HasChildren) "/" Kategorie
* LIST (\HasNoChildren) "/" Kategorie/Koledzy
* LIST (\HasNoChildren) "/" Kategorie/Mieszkanie
* LIST (\HasNoChildren) "/" Kategorie/Powiadomienia
* LIST (\HasNoChildren) "/" Kategorie/Praca
* LIST (\HasNoChildren) "/" Kategorie/Przesy&AUI-ki
* LIST (\HasNoChildren) "/" Kategorie/Rachunki
* LIST (\HasNoChildren) "/" Kategorie/Zakupy
* LIST (\HasNoChildren) "/" "NA POTEM"
* LIST (\HasNoChildren) "/" Notes
* LIST (\HasNoChildren) "/" Outbox
* LIST (\HasNoChildren \Sent) "/" "Sent Items"
* LIST (\HasNoChildren) "/" Tasks
* LIST (\HasChildren) "/" Tematy
* LIST (\HasNoChildren) "/" "Tematy/Dozowniki &AUE-azienkowe"
* LIST (\HasNoChildren) "/" Tematy/Makler
```


List folders which name contains word "**Marek**"

	? LIST "" "*Marek*"


List subscribed folders

	? LSUB "" "*"

Example response

```
* LSUB (\HasChildren) "/" Archiwum
* LSUB (\HasNoChildren) "/" "NA POTEM"
* LSUB (\HasChildren) "/" Kategorie
* LSUB (\HasNoChildren) "/" Kategorie/Koledzy
* LSUB (\HasNoChildren) "/" Kategorie/Mieszkanie
* LSUB (\HasNoChildren) "/" Kategorie/Praca
* LSUB (\HasNoChildren) "/" Kategorie/Przesy&AUI-ki
* LSUB (\HasNoChildren) "/" Kategorie/Rachunki
* LSUB (\HasNoChildren) "/" Kategorie/Zakupy
* LSUB (\HasChildren) "/" Tematy
* LSUB (\HasNoChildren) "/" "Tematy/Dozowniki &AUE-azienkowe"
* LSUB (\HasNoChildren) "/" Tematy/Makler
* LSUB (\HasNoChildren) "/" Tematy/Tidal
* LSUB (\Marked \HasNoChildren) "/" INBOX
* LSUB (\HasNoChildren \Trash) "/" "Deleted Items"
* LSUB (\HasNoChildren \Drafts) "/" Drafts
* LSUB (\HasNoChildren \Sent) "/" "Sent Items"
* LSUB (\HasNoChildren \Junk) "/" "Junk Email"
* LSUB (\HasNoChildren) "/" Kategorie/Powiadomienia
* LSUB (\HasNoChildren) "/" "INBOX/Sent Messages"
* LSUB (\HasNoChildren) "/" Archiwum/Tidal
```

Open `INBOX` folder

	? SELECT INBOX



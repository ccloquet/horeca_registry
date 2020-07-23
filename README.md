# HorecaRegistry
Proposal to register the email-adresses of the horeca-customers with privacy by design

**For the customer:**
 1. Scan the QR-code
 2. Type his/her email adress
 3. Confirm

**Security guarantees**
 1. the data are stored encrypted, and are solely decryptable with a private key, that could be shared between the place owner and the tracing centre
 2. the owner can also install the app on a private server


----------------------------------------------------------


**_In detail_**

**1. A database Une base de données, avec chiffrement de bout en bout à clé asymétrique.** De la sorte, elle est inexploitable si elle est compromise.

**2. Un QR code** - le QR code contient une clé de chiffrement 

- **Le/la client.e scanne le QR code, ce qui ouvre une page web. Il/elle introduit son email**
- À la premiière utilisation, il/elle confirme via un lien (éventuellement à son retour à la maison)
- La base de données enregistre l'email + l'heure (chiffrés), ainsi que le jour (non chiffré)
- Un script quotidien efface tout ce qui date d'il y a plus de 14 jours 

- La clé de déchiffrement peut être scindée en deux : une partie pour l'exploitant et une partie pour le centre de tracing. De la sorte, aucun des deux ne peux exploiter les données de manière arbitraire.

**3. Le code en open source**
Une solution centralisée serait offerte.
Pour tous ceux qui n'ont pas confiance en cette solution malgré le chiffrement de bout en bout et la possibilité d'auditer l'infrastructure, le code serait disponible en open-source. De la sorte, chacun.e peut installer le programme par soi-même (sur un Raspberry Pi, un serveur OVH, Amazon, Heroku, ...)

**Autres notes**
- Le moteur peut être PostgreSQL, SQLite, voire un simple fichier texte
- La base de données peut être hébergée sur un serveur classique ou virtuel, sur un Raspberry Pi ou sur service de stockage de type Dropbox ou Google Drive
- Le client peut aussi s'enregistrer depuis la maison
- + tard : si l'exploitant dispose déjà d'une partie des données (ex: via une réservation), les données pourraient être reçues au moyen d'une API (push ou pull)
- Trouver une manière de le rendre ludique

Si on s'y met, il y en a pour quelques jours de travail. Les défis sont humains, pas tellement techniques.

Qu'est-ce qui pourrait coincer avec cette approche ?

# HorecaRegistry
Proposal to register the email-adresses of the horeca-customers with privacy by design

**Fonctionnement pour le client :**
 1. Scanner le QR-code
 2. Encoder son adresse email
 3. Confirmer

**Garantie de sécurité**
 1. les données sont stockées chiffrées et décodables seulement avec une clé, qui serait partagée entre l'exploitant.e et le centre de tracing
 2. s'il/elle le souhaite, l'exploitant.e peut installer l'application sur un serveur privé


----------------------------------------------------------


**_En détail :_*

**1. Une base de données, avec chiffrement de bout en bout à clé asymétrique.** De la sorte, elle est inexploitable si elle est compromise.

**2. Un QR code** - le QR code contient une clé de chiffrement 

- **Le/la client.e scanne le QR code, ce qui ouvre une page web. Il/elle introduit son email**
- À la premiière utilisation, il/elle confirme via un lien (éventuellement à son retour à la maison)
- La base de données enregistre l'email + l'heure, chiffrés, ainsi que le jour (non chiffré)
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


Qu'est-ce qui pourrait coincer avec cette approche ?

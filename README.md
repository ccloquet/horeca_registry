# HorecaRegistry
Proposal to register the email-adresses of the horeca-customers, respecting both the privacy of the customers and the discretion of the place owner

**For the customer:**
 1. Scan the QR-code
 2. Type his/her email adress
 3. Confirm

**Security guarantees**
 1. the data are stored encrypted, and are solely decryptable with a private key, that could be split between the place owner and the tracing centre
 2. the owner can also install the app on a private server
 3. random data are added so that it is not possible to infer the frequentation of the place from the encrypted data

There is for a couple of days of work. 

What could be wrong with this approach?

----------------------------------------------------------


**_In detail_**

**1. A database, where all the personal data stored are encrypted with the public part of an asymetrical key.** Thereby, it is unexploitable if it is compromised.

**2. A QR code** - the QR code contains/points to the public encryption key
under the QRcode, a tiny url for those who do not have a QR-code reader

- **The customer scans the QR code. A web page opens. The customer types his/her email adress**
- On the first use, he/she confirms by clicking on a link in an email (may be done when he/she is back home)
- The database records the place id + customer email + a timestamp (both salted/encrypted), and the day (unencrypted)
- A daily script wipes everything dating back from more than 14 days
- Random data is added continuously, so that no information can be inferred about the frequentation of the place from the encrypted data
- The private (decryption) key can be cut in two : a part for the place owner and a part for the tracing center. Thereby, none of them can exploit the data alone.
- If no QR code is available, the customer can still register, but would have to enter the details manually

**3. The code in open source**
A centralized solution would be offered.
For the place owners who does't trust it (and no one should), despite the encryption and the possibility to audit the infrastructure, the code would be available in open source. Thereby, anyone can deploy and run it by him/herself (on a Raspberry pi, an OVH server, Heroku, ...)

**Additional notes**
- The database engine can be PostgreSQL, SQLite, or even a simple text file
- The database can be hosted on a classical/virtual server, a Raspberry Pi, or any cloud storage service like Dropbox or Google Drive
- The customer can also register him/herself from home
- Let's find a way to make it fun!
- Later: an API to retrieve data from other systems (eg: reservation systems)

**Alternative**
A service that is not managed by the place owners. 
Through a web app (or later, the tracing app), everyone can post there his/her email adress + the place where he/she went.
Everything is stored encrypted (like above)


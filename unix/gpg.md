# Encryption

### Encryption using public key (GPG)

Generate key pair - private/public

	gpg --gen-key

Export user's public key

	gpg --export --armor user@marekpoks.pl > MarekPoksValueLogic.asc

Import someone's public key

	gpg --import theirpubkey.asc

> Once you have imported the other person’s public key, 
you must now set the trust level of the key. This prevents 
GPG from warning you every time you encrypt something with 
that public key.

	gpg --edit-key <name or email>

	> trust (invoke trust subcommand on the key)
	> 5 (ultimate trust)
	> y (if prompted)
	> quit

List public keys

	gpg --list-keys

List private keys

	gpg --list-secret-keys

Encrypt file

	gpg --encrypt --recipient <user> filename.txt

> public key of a **user** must be imported previously

or

	gpg -e -r <user> filename.txt

Decrypt and print to stdout

	gpg --decrypt filename.txt.gpg

Decrypt to disk

	gpg filename.txt.gpg

> **filename.txt.gpg** will be decrypted to **filename.txt**

### Encryption with password (GPG)

Encrypt file (GPG)

	cat plik | gpg --batch -q --passphrase <password> --cipher-algo AES256 -co - > plik.enc

Decrypt file (GPG)

	cat plik.enc | gpg --batch -q --passphrase <password> --cipher-algo AES256 -do - > plik2

Generate random password

	xxd -l 512 -p /dev/random

> 512 hexadecimal characters, 30 per line

	< /dev/urandom tr -dc "_A-Z-a-z-0-9)(\!@#$%^&*()" | head -c${1:-512}

> 512 characters from given realm, single line

### Encryption with password (OpenSSL)

Encrypt file (OpenSSL)

	openssl des3 -e -pbkdf2 -kfile passwd.bin < plik > plik.enc

Decrypt file (OpenSSL)

	openssl des3 -d -pbkdf2 -kfile passwd.bin < plik.enc > plik2

> The encryption format used by OpenSSL is non-standard: 
it is "what OpenSSL does", and if all versions of OpenSSL 
tend to agree with each other, there is still no reference 
document which describes this format except OpenSSL source 
code. The header format is rather simple:

> magic value (8 bytes): the bytes 53 61 6c 74 65 64 5f 5f 
salt value (8 bytes)

> Hence a fixed 16-byte header, beginning with the ASCII 
encoding of the string "Salted__", followed by the salt 
itself. That's all ! No indication of the encryption 
algorithm; you are supposed to keep track of that yourself.

> The process by which the password and salt are turned 
into the key and IV is not documented, but a look at the 
source code shows that it calls the OpenSSL-specific 
EVP_BytesToKey() function, which uses a custom key derivation 
function with some repeated hashing. This is a non-standard 
and not-well vetted construct (!) which relies on the MD5 
hash function of dubious reputation (!!); that function can 
be changed on the command-line with the undocumented -md 
flag (!!!); the "iteration count" is set by the enc command 
to 1 and cannot be changed (!!!!). This means that the first 
16 bytes of the key will be equal to MD5(password||salt), 
and that's it.

> This is quite weak! Anybody who knows how to write code on 
a PC can try to crack such a scheme and will be able to "try" 
several dozens of millions of potential passwords per second 
(hundreds of millions will be achievable with a GPU). If you 
use "openssl enc", make sure your password has very high 
entropy! (i.e. higher than usually recommended; aim for 80 
bits, at least). Or, preferably, don't use it at all; 
instead, go for something more robust (GnuPG, when doing 
symmetric encryption for a password, uses a stronger KDF 
with many iterations of the underlying hash function).

# pkcs11-tools

pkcs11-tools is a toolkit containing a bunch of small utilities to perform key management tasks on cryptographic tokens implementing a PKCS#11 interface. 
It features a number of commands similar to the Unix CLI utilities, such as ls , mv, rm, od, and more. 
It also has specific commands to generate keys, generate CSRs, import certificates and other files, in a fashion compatible with many implementations, including both IBM and Oracle JVMs. 
It is also able to interface with software tokens, such as SoftHSM, NSS, and Kryoptic.

PKCS#11 (Public-Key Cryptography Standards #11) est une norme industrielle définissant une interface de programmation (API) indépendante de la plateforme pour interagir avec des modules cryptographiques matériels ou logiciels, tels que les cartes à puce, les clés USB de sécurité (HSM) ou les tokens.
Elle permet aux applications d'effectuer des opérations cryptographiques (chiffrement, signature, authentification) et de gérer des objets (clés, certificats) sans connaître les détails internes du matériel sécurisé, agissant comme un pilote universel pour la sécurité matérielle.


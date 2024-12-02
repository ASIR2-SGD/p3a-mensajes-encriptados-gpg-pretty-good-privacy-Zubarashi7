# Práctica 3a. GPG Pretty Good Privacy

## Contexto
El término criptografía proviene del griego *kyptós* 'oculto' y *grafé* 'escritura' y es definida como el arte de escribir con clave secreta o de un modo enigmático.

Gracias al uso de la criptografía se puede obtener una seria de ventajas de gran utilidad en el ámbito de la seguridad informáticfa como son:
* Confidencialidad
* Integridad
* Autenticidad
* No repudio
    

En esta práctica se trabajará sobre estos cuatro conceptos mediante la herramienta de comandos gpg (Pretty Good Privacy)

## Objetivos
* Entender la *confidencialidad, Integridad, Autenticidad* y no repudio mediante el uso de la herramienta *gpg*.
* Entender y poner en práctica la criptografía simetrica
* Entender y poner el práctica la criptografía asimétrcia
* Saber cifrar y descifrar mensajes mediante criptografía simétrica.
* Saber cifrar y descifrar mensajes mediante criptografía asimétrica.
* Saber firmar otras llaves generando así una relación de confianza entre usuarios de la comunidad.
* Ser capaces de firmar un documento y verificar que este ha sido firmado por quien dice ser.
* Ser capaces de importar/exportar claves a un servidor público
* Saber enviar correos cifrados y descifrar correos privados

## Desarrollo

 1. **Cifrar y descifrar un mensaje mediante criptografía simétrica**
```bash
 echo "Hola" | gpg --symmetric --armour --batch --passphrase asir2 | xsel -ib
```

```bash
 -----BEGIN PGP MESSAGE-----

jA0ECQMCyzvnGuhFLP//0joB8lFUsEyKJenh6g3CD3A8hDb1/OFnUlzijlAM3bKt
zJxr1NY1MPUlAKzPcXDFUYZVAj3wjveSqLRZ
=fZzn
-----END PGP MESSAGE-----
```

 2. **Crear par de claves**

 ```bash
 gpg --full-gen-key
 ```
 3. **Listar claves pública/privada**

Claves publicas:

 ```bash
gpg --list-public-keys
 ```

 Claves privadas:
  ```bash
gpg --list-secret-keys
 ```

```bash
/home/alumnom/.gnupg/pubring.kbx
--------------------------------
sec   rsa3072 2024-11-19 [SC] [caduca: 2025-11-19]
      010EC37EF56498877F71772C665AB50F6FF81B7B
uid        [  absoluta ] sad_alumno <juacasgon3@alu.edu.gva.es>
ssb   rsa3072 2024-11-19 [E] [caduca: 2025-11-19]

sec   rsa3072 2024-11-20 [SC]
      2C1C9D6104107480903F3F8F86F2B52DCA8429D1
uid        [   total   ] Notario SAD asir2 (Notario para practicas SAD) <notario-sad@iesgrao.es>
ssb   rsa3072 2024-11-20 [E]

```

 4. **Importar/exportar claves publicas y privadas**
 ```bash
 gpg --import [archivo_key.asc]
 ```

 ```bash
 gpg --export [archivo]
 ```
 5. **Importar y exportar de un servidor de claves**
```bash
gpg --keyserver keyser.ubuntu.com --reiceve key [CLAVE]
```
```bash
gpg --keyserver keyserver.ubuntu.com --send-keys [CLAVE]
```
 6. **Encriptar un documento con clave pública de destinatario**
```bash
gpg --encrypt --recipient "email_del_destinatario/id_de_la_clave"
```
```bash
gpg --encrypt --recipient "email_del_destinatario/id_de_la_clave"
```
 7. **Desencriptar un documento cifrado con nuetra clave publica haciendo uso de clave privada**
```bash
gpg --decrypt [archivo.asc]
```
```bash
gpg --decrypt --output [archivo.asc]
```
 8. **Firmar un mensaje y verificar la autoria de un mensaje**

gpg --sign 

 9. **Mailevelope**
    1.  Importar clave privada
    ```bash
    gpg --import [archivo_key.asc]
    ```

    2.  Subir clave pública al keyserver de mailevelope
Accedemos al servidor de Mailevelope y subimos la clave.
    3.  Importar claves publicas

    4.  Enviar un mensaje cifrado y descifrar mensaje.

 
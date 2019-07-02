Ejercicio 2 - IPFS (3 puntos)

A partir de un truffle project como puede ser la pet-shop utilizada en bloques anteriores.
*También puede utilizar otro truffle project.
Haga una pequeña modificación en su frontend para mostrar su nombre al ejecutar la
aplicación. (Puede editar cualquier parámetro adicional, siempre y cuando el nombre sea
visible).
Suba el truffle project a GitHub manteniendo su estructura. (No incluya la carpeta
node_modules).
Arranque un daemon de IPFS y aloje la DApp (Proyecto truffle elegido).
Una vez alojada la DApp, debe ser capaz de utilizar la aplicación al igual que en localhost,
es decir, firmando transacciones mediante MetaMask.
Describa todo el procedimiento adjuntando las instrucciones utilizadas y sus outputs,
además adjunte el hash de IPFS. Se recomienda realizar la carga (o recarga si ya ha
realizado la carga en IPFS) en una fecha cercana a la entrega. Esto es debido a que si
realiza la carga en una fecha temprana, puede que el contenido tarde o no llegue incluso
a cargar. También debe indicar si los contratos están desplegados en Ganache o
Rinkeby.
*Se recomienda alojar el contenido a subir en IPFS en una única carpeta, ésta también
debe alojarse en GitHub.

----IPFS ----

Install IPFS:
sudo apt-get update
sudo apt-get install golang-go -y
wget https://dist.ipfs.io/go-ipfs/v0.4.10/go-ipfs_v0.4.10_linux-386.tar.gz
tar xvfz go-ipfs_v0.4.10_linux-386.tar.gz
sudo mv go-ipfs/ipfs /usr/local/bin/ipfs


cesar@cesar-VirtualBox:~/master/go-ipfs$ ipfs init
initializing IPFS node at /home/cesar/.ipfs
generating 2048-bit RSA keypair...done
peer identity: QmVmC532VT24KgaU5rbeK5V1bN7W8qBh9F2SUdF5hUVqz4
to get started, enter:

        ipfs cat /ipfs/QmVLDAhCY3X9P2uRudKAryuQFPM5zqA3Yij1dY8FpGbL7T/readme




--- GANACHE ----

$ mkdir ~/ganache
$ git clone https://github.com/trufflesuite/ganache.git
$ npm install
$ npm start


cesar@cesar-VirtualBox:~/master$ ipfs add -r webpack/app/dist/
added QmVd3QEJ5gsaGzctKXXWQ1UgkxKWSy7yNyhcNApwpLEu5E dist/index.html
added QmWYECuWGk2ugt2btiKoaGBHVEqEAUSNYY2Ftf8MQu3nFv dist/index.js
added QmaB8LK4YSThm3DtmDaw1okWLFHNQtEorh4wG8pjLt6Jr5 dist
cesar@cesar-VirtualBox:~/master$ 



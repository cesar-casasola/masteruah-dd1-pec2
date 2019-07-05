# Ejercicio 1 - ENS (1 punto)
Adquiera un dominio bajo el TLD ‘.test’ en la testnet Rinkeby.
Describa el procedimiento seguido paso a paso.
Demuestre que es usted poseedor del dominio adquirido y obtenga la dirección del
Resolver utilizado. (Adjunte un pantallazo con todas las instrucciones utilizadas y sus
outputs).
*Tenga en cuenta que la duración

----

- Cuenta utilizada: 
  - "0x148157cef85ffa1f0bac483c2a75e0f3baff0278"

Metamask Rinkeby: 0xCc96735af99781E494BcBef3d90825B6FEcb7327

>ENS on Rinkeby: 0xe7410170f87102df0055eb195163a03b7f2bff4a

- Descargamos el fichero ensutils-rinkeby.js, que contiene la dirección de ENS para Rinkeby
- Cargamos el script en una consola de Rinkeby

~~~
> loadScript("./ensutils-rinkeby.js")
true
~~~

- Comprobamos que el nombre que voy a subir no está dado de alta
~~~
> new Date(testRegistrar.expiryTimes(web3.sha3('cesarcasasola')).toNumber() * 1000)
<Date Thu, 01 Jan 1970 01:00:00 CET>
~~~

- Desbloqueamos la cuenta "0x148157cef85ffa1f0bac483c2a75e0f3baff0278"
~~~~
> personal.unlockAccount(eth.accounts[0])
Unlock account 0x148157cef85ffa1f0bac483c2a75e0f3baff0278
Passphrase: 
true
> 
~~~~

- Registramos el dominio cesarcasasola utilizando primera cuenta
  >eth.accounts[0]: 0x148157cef85ffa1f0bac483c2a75e0f3baff0278
~~~~
> testRegistrar.register(web3.sha3("cesarcasasola"), eth.accounts[0], {from: eth.accounts[0]})
"0x34679d619c5fee9fa07b0d3dd9e2651f8c8ffb4d3b8561b0be4cf76dfad5678d"
> 
~~~~

- Volvemos a comprobar el registro:
~~~~
> testRegistrar.expiryTimes(web3.sha3("cesarcasasola"))
1564683179
> 
~~~~

> new Date(testRegistrar.expiryTimes(web3.sha3('cesarcasasola')).toNumber() * 1000)
<Date Thu, 01 Aug 2019 20:12:59 CEST>

El nombre está registrado hasta el 1 de Agosto


-- Next, tell the ENS registry to use the public resolver for your name:

> namehash('cesarcasasola.test')
"0x50fb09877c808c4d0377f904a996050e242d532da5c1f53c6430e9f8482033fb"
> 

> publicResolver.address
"0x5d20cf83cb385e06d2f2a892f9322cd4933eacdc"


ens.setResolver(namehash('cesarcasasola.test'), publicResolver.address, {from: eth.accounts[0]});


> ens.setResolver(namehash('cesarcasasola.test'), publicResolver.address, {from: eth.accounts[0]});
"0x0d4c35a79cfec913f555bf301b6ac40bad57337b45334bba58f15db521ed5cf9"
> 

---Transaccion: 0x0d4c35a79cfec913f555bf301b6ac40bad57337b45334bba58f15db521ed5cf9
-- Contrato del Resolver:  0xe7410170f87102DF0055eB195163A03B7F2Bff4A


Una vez que la transacción se ha confirmado se le indica al resolver resuelva la dirección de la cuenta eth.accounts[0] para devolver el nombre cesarcasasola.test 
 
publicResolver.setAddr(namehash('cesarcasasola.test'), eth.accounts[0], {from: eth.accounts[0]});

> publicResolver.setAddr(namehash('cesarcasasola.test'), eth.accounts[0], {from: eth.accounts[0]})
"0xa1fec0467d327632caade76a2bff9b882b845c9a9fc71a0ea251f0ea32493c6a"

- Prueba de resolución del dominio: Debe recuperar la cuenta "0x148157cef85ffa1f0bac483c2a75e0f3baff0278"
~~~~
> getAddr('cesarcasasola.test')
"0x148157cef85ffa1f0bac483c2a75e0f3baff0278"
~~~~

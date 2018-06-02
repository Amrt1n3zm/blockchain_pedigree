# blockchain_pedigree
las raices del block chain son profundas ya que reposa en hombros de gigantes


Pedigrí académico de las criptomonedas.

El concepto de criptomonedas se basa en ideas olvidadas en la literatura de investigación.

Arvind Narayanan y Jeremy Clark

Traducción de Alex Martin como ejercicio del curso http://bitcoinbook.cs.princeton.edu/  

Si ha leído acerca de bitcoin en la prensa y está familiarizado con la investigación académica en el campo de la criptografía, 
es probable que tenga la siguiente impresión: varias décadas de investigación en efectivo digital, comenzando con David Chaum, 
10, 12 no condujo al éxito comercial porque requería un servidor centralizado y bancario que controlara el sistema,
y ningún banco quería registrarse. A lo largo vino bitcoin, una propuesta radicalmente diferente para una criptomoneda descentralizada
que no necesitaba los bancos, y el efectivo digital finalmente tuvo éxito. Su inventor, el misterioso Satoshi Nakamoto, 
era un extraño académico, y bitcoin no se parece en nada a las propuestas académicas anteriores.
Este artículo desafía esa visión al mostrar que casi todos los componentes técnicos de bitcoin se originaron en la literatura académica 
de los años ochenta y noventa (ver figura 1). Esto no es para disminuir el logro de Nakamoto, sino para señalar que se parió sobre 
los hombros de los gigantes. De hecho, al rastrear los orígenes de las ideas en bitcoin, podemos centrarnos en el verdadero 

salto de visión de Nakamoto: la forma específica y compleja en que se combinan los componentes subyacentes.
Esto ayuda a explicar por qué el bitcoin tardó tanto en ser inventado. Los lectores que ya están familiarizados con la forma en que
funciona Bitcoin pueden obtener una comprensión más profunda de esta presentación histórica. (Para una introducción, vea Bitcoin y 
Cryptocurrency Technologies por Arvind Narayanan et al.36) La historia intelectual de Bitcoin también sirve como un estudio de caso 
que demuestra las relaciones entre el mundo académico, investigadores externos y profesionales, y ofrece lecciones sobre cómo estos 
grupos pueden beneficiarse uno del uno otro.
El libro mayor
Si tiene un libro mayor seguro, el proceso para aprovecharlo en un sistema de pago digital es sencillo. Por ejemplo, 
si Alice envía Bob $ 100 por PayPal, PayPal carga $ 100 de la cuenta de Alice y acredita $ 100 a la cuenta de Bob. 
Esto también es más o menos lo que sucede en la banca tradicional, aunque la ausencia de un libro único compartido entre bancos complica
las cosas.
Esta idea de un libro mayor es el punto de partida para entender Bitcoin. Es un lugar para registrar todas las transacciones que suceden 
en el sistema, y todos los participantes del sistema están abiertos y son de confianza. Bitcoin convierte este sistema para registrar 
pagos en una moneda. Mientras que en la banca, un saldo de cuenta representa el efectivo que puede exigirse al banco, ¿qué representa una 
unidad de bitcoin? Por ahora, suponga que lo que se tramita tiene un valor inherente.
¿Cómo se puede construir un libro de contabilidad para su uso en un entorno como Internet donde los participantes pueden no confiar el
uno en el otro? Comencemos con la parte fácil: la elección de la estructura de datos. Hay algunas propiedades deseables. 
El libro mayor debe ser inmutable o, para ser más precisos, solo anexar: debe poder agregar nuevas transacciones pero no eliminar, 
modificar ni reordenar las existentes. También debería haber una forma de obtener un compendio criptográfico sucinto del estado 
del libro en cualquier momento. Un resumen es una cadena corta que permite evitar almacenar todo el libro, sabiendo que si 
el libro mayor fuera manipulado de alguna manera, el resumen resultante cambiaría y, por lo tanto, se detectaría la alteración. 
El motivo de estas propiedades es que, a diferencia de una estructura de datos normal que se almacena en una sola máquina, 
el libro mayor es una estructura de datos global mantenida colectivamente por un conjunto de participantes mutuamente desconfiado.
Esto contrasta con otro enfoque para la descentralización de los libros digitales, 7,13,21 en el que muchos participantes mantienen 
libros contables locales y le corresponde al usuario consultar este conjunto de libros mayores para resolver cualquier conflicto.
Tiempos sellados vinculados
La estructura de datos del libro mayor de Bitcoin se toma prestada, con modificaciones mínimas, de una serie de documentos de
Stuart Haber y Scott Stornetta escritos entre 1990 y 1997 (su artículo de 1991 tenía otro coautor, Dave Bayer) .5,22,23 
Sabemos esto porque Nakamoto lo dice en su libro blanco de bitcoin.34 El trabajo de Haber y Stornetta abordó el problema 
del sellado del tiempo de los documentos: tenían como objetivo construir un servicio de "notario digital". Para patentes,
contratos comerciales y otros documentos, uno puede querer establecer que el documento fue creado en un momento determinado, 
y no más tarde. Su noción de documento es bastante general y podría ser cualquier tipo de datos. Mencionan, de paso, las transacciones
financieras como una posible aplicación, pero no era su foco.
En una versión simplificada de la propuesta de Haber y Stornetta, los documentos se crean y difunden constantemente.
El creador de cada
documento afirma el momento de la creación y firma el documento, su marca de tiempo y el documento emitido anteriormente
Merkle trees, por cierto, llevan el nombre de Ralph Merkle, un pionero de la criptografía asimétrica que propuso la idea en su 
artículo de 1980.33 Su intención era producir un resumen para un directorio público de certificados digitales. Cuando un sitio web,
por ejemplo, le presenta un certificado, también podría presentar una prueba corta de que el certificado aparece en el directorio
global. Puede verificar la prueba de manera eficiente siempre que conozca el hash de raíz del árbol Merkle de los certificados en 
el directorio. Esta idea es antigua según los estándares criptográficos, pero su poder se ha apreciado solo en los últimos tiempos. 
Está en el núcleo del sistema de transparencia de certificados recientemente implementado.30 Un documento de 2015 propone CONIKS, que
aplica la idea a directorios de claves públicas para correos electrónicos encriptados de extremo a extremo.32 La verificación eficiente
de partes del estado global es una de las funcionalidades clave proporcionadas por el libro mayor en Ethereum, una nueva criptomoneda.
Bitcoin puede ser la creación de instancias del mundo real más conocida de las estructuras de datos de Haber y Stornetta, pero no es 
la primera. Al menos dos compañías -seguros que comienzan a mediados de los 90 y Guardtime desde el año 2007- ofrecen servicios 
de sello de tiempo. Un giro interesante presente en ambos servicios es una idea mencionada por Bayer, Haber y Stornetta, 5 que consiste 
en publicar periódicamente las raíces de Merkle en un periódico mediante la publicación de un anuncio. La Figura 3 muestra una raíz de
Merkle publicada por Guardtime.
Tolerancia a fallas bizantina
Por supuesto, los requisitos para una moneda de Internet sin una autoridad central son más estrictos. Un ledger distribuido inevitablemente 
tendrá bifurcaciones, lo que significa que algunos nodos pensarán que el bloque A es el último bloque, mientras que otros nodos pensarán que 
es el bloque B. Esto podría deberse a que un adversario intente interrumpir la operación del libro o simplemente debido a la red latencia, 
lo que resulta en bloques ocasionalmente generados casi simultáneamente por diferentes nodos que desconocen los bloques de los demás.
El sellado de tiempo vinculado por sí solo no es suficiente para resolver los tenedores, como lo demostró Mike Just en 1998.26
Un campo de investigación diferente, la computación distribuida tolerante a fallas, ha estudiado este problema, donde recibe diferentes
nombres, incluida la replicación de estado. Una solución a este problema es aquella que permite que un conjunto de nodos aplique las
mismas transiciones de estado en el mismo orden; por lo general, el orden preciso no importa, solo que todos los nodos son consistentes.
Para una moneda digital, el estado que se replicará es el conjunto de saldos, y las transacciones son transiciones de estado. 
Las primeras soluciones, incluida Paxos, propuestas por Leslie Lamport, ganador del premio Turing en 1989,28,29, consideran 
la replicación del estado cuando los canales de comunicación no son confiables y cuando una minoría de nodos presenta ciertas fallas
"realistas", como desconectarse para siempre o reiniciar y enviar mensajes obsoletos desde la primera vez que se desconectó.
Una literatura prolífica siguió con ajustes más adversos y compensaciones de eficiencia.
Una línea de trabajo relacionada estudió la situación donde la red es en su mayoría confiable (los mensajes se entregan con retardo 
limitado), pero donde la definición de "falla" se amplió para manejar cualquier desviación del protocolo. Tales fallas bizantinas
incluyen tanto fallas naturales como comportamientos maliciosos. Primero fueron estudiados en un documento también por Lamport,
coescrito con Robert Shostak y Marshall Pease, ya en 1982.27 Mucho más tarde, en 1999, un documento histórico de Miguel Castro y
Barbara Liskov introdujo el PBFT (tolerancia a fallas bizantina práctica), que se adaptaba a ambos Fallas bizantinas y una red
no confiable.8 En comparación con el sellado de tiempo vinculado, la literatura de tolerancia a fallas es enorme e incluye cientos 
de variantes y optimizaciones de Paxos, PBFT y otros protocolos fundamentales.
En su libro blanco original, Nakamoto no cita esta literatura ni usa su lenguaje. Utiliza algunos conceptos, refiriéndose 
a su protocolo como un mecanismo de consenso y considerando fallas tanto en forma de atacantes como de nodos que se unen y
abandonan la red. Esto está en contraste con su dependencia explícita de la literatura en sellos de tiempo vinculados
(y prueba de trabajo, discutida a continuación). Cuando se le preguntó en una discusión de la lista de correo sobre
la relación de bitcoin con el problema de los generales bizantinos (un experimento de pensamiento que requiere BFT para resolver), 
Nakamoto afirma que la cadena de prueba de trabajo resuelve este problema.
En los años siguientes, otros académicos han estudiado el consenso de Nakamoto desde la perspectiva de los sistemas distribuidos.


Bibliografia :

Arvind Narayanan is an assistant professor of computer science at Princeton. He leads the Princeton Web Transparency and Accountability Project to uncover how companies collect and use our personal information. Narayanan also leads a research team investigating the security, anonymity, and stability of cryptocurrencies, as well as novel applications of blockchains. He co-created a massive open online course, and a textbook on bitcoin and cryptocurrency technologies. His doctoral research showed the fundamental limits of de-identification, for which he received the Privacy Enhancing Technologies Award. Narayanan is an affiliated faculty member at the Center for Information Technology Policy at Princeton and an affiliate scholar at Stanford Law School's Center for Internet and Society. You can follow him on Twitter at @random_walker. https://queue.acm.org/detail.cfm?id=3136559 


References
1. Aspnes, J., et al. 2005. Exposing computationally challenged Byzantine imposters. Yale University Department of Computer Science; http://cs.yale.edu/publications/techreports/tr1332.pdf.
2. Back, A. 1997. A partial hash collision based postage scheme; http://www.hashcash.org/papers/announce.txt.
3. Back, A. 2001. Hash cash; https://web.archive.org/web/20010614013848/http://cypherspace.org/hashcash/.
4. Back, A. 2002. Hashcash—a denial of service counter measure; http://www.hashcash.org/papers/hashcash.pdf.
5. Bayer, D., Haber, S., Stornetta, W. S. Improving the efficiency and reliability of digital time-stamping. Proceedings of Sequences 1991; https://link.springer.com/chapter/10.1007/978-1-4613-9323-8_24.
6. Benaloh, J., de Mare, M. 1991. Efficient broadcast timestamping; http://citeseerx.ist.psu.edu/viewdoc/summary?doi=10.1.1.38.9199.
7. Boyle, T. F. 1997. GLT and GLR: Component architecture for general ledgers; https://linas.org/mirrors/www.gldialtone.com/2001.07.14/GLT-GLR.htm.
8. Castro, M., Liskov, B. 1999. Practical Byzantine fault tolerance. Proceedings of the Third Symposium on Operating Systems Design and Implementation; http://pmg.csail.mit.edu/papers/osdi99.pdf.
9. Chaum, D. 1981. Untraceable electronic mail, return addresses, and digital pseudonyms. Communications of the ACM 24(2): 84-90; https://dl.acm.org/citation.cfm?id=358563.
10. Chaum, D. 1983. Blind signatures for untraceable payments. Advances in Cryptology: 199-203.
11. Chaum, D. 1985. Security without identification: transaction systems to make Big Brother obsolete. Communications of the ACM 28(10): 1030-1044; https://dl.acm.org/citation.cfm?id=4373.
12. Chaum, D., et al. 1988. Untraceable electronic cash. Advances in Cryptology: 319-327; https://dl.acm.org/citation.cfm?id=88969.
13. Dai, W. 1998; http://www.weidai.com/bmoney.txt.
14. Douceur, J. R. 2002. The Sybil attack; https://dl.acm.org/citation.cfm?id=687813.
15. Dwork, C., Naor, M. 1992. Pricing via processing or combatting junk mail; https://dl.acm.org/citation.cfm?id=705669.
16. Felten, E. 2017. Smart contracts: neither smart nor contracts? Freedom to Tinker; https://freedom-to-tinker.com/2017/02/20/smart-contracts-neither-smart-not-contracts/.
17. Franklin, M. K., Malkhi, D. 1997. Auditable metering and lightweight security; http://www.hashcash.org/papers/auditable-metering.pdf.
18. Gabber, E., et al. 1998. Curbing Junk E-Mail via Secure Classiffication. http://www.hashcash.org/papers/secure-classification.pdf.
19. Garay, J. A., et al. 2015. The bitcoin backbone protocol: analysis and applications. Advances in Cryptology: 281-310; https://eprint.iacr.org/2014/765.pdf.
20. Goldberg, I. 2000. A pseudonymous communications infrastructure for the Internet. Ph.D. dissertation, University of California Berkeley; http://moria.freehaven.net/anonbib/cache/ian-thesis.pdf.
21. Grigg, I. 2005. Triple entry accounting; http://iang.org/papers/triple_entry.html.
22. Haber, S., Stornetta, W. S. 1991. How to timestamp a digital document. Journal of Cryptology 3(2): 99-111; https://link.springer.com/chapter/10.1007/3-540-38424-3_32.
23. Haber, S., Stornetta, W. S. 1997. Secure names for bit-strings. In Proceedings of the 4th ACM Conference on Computer and Communications Security: 28-35; http://dl.acm.org/citation.cfm?id=266430.
24. Jakobsson, M., Juels, A. 1999. Proofs of work and bread pudding protocols; http://www.hashcash.org/papers/bread-pudding.pdf.
25. Juels, A., Brainard, J. 1999. Client puzzles: a cryptographic countermeasure against connection completion attacks. Proceedings of Networks and Distributed Security Systems: 151-165; https://www.isoc.org/isoc/conferences/ndss/99/proceedings/papers/juels.pdf.
26. Just, M. 1998. Some timestamping protocol failures; http://www.isoc.org/isoc/conferences/ndss/98/just.pdf.
27. Lamport, L., et al. 1982. The Byzantine Generals Problem. ACM Transactions on Programming Languages and Systems 4(3): 382-401; https://dl.acm.org/citation.cfm?id=357176 .
28. Lamport, L. 1989. The part-time parliament. Digital Equipment Corporation; https://computerarchive.org/files/mirror/www.bitsavers.org/pdf/dec/tech_reports/SRC-RR-49.pdf.
29. Lamport, L. 2001. Paxos made simple; http://lamport.azurewebsites.net/pubs/paxos-simple.pdf.
30. Laurie, B. 2014. Certificate Transparency. acmqueue 12(8); https://queue.acm.org/detail.cfm?id=2668154.
31. Levy, K. E. C. 2017. Book-smart, not street-smart: blockchain-based smart contracts and the social workings of law. Engaging Science, Technology, and Society 3: 1-15; http://estsjournal.org/article/view/107.
32. Melara, M., et al. 2015. CONIKS: bringing key transparency to end users. Proceedings of the 24th Usenix Security Symposium; https://www.usenix.org/system/files/conference/usenixsecurity15/sec15-paper-melara.pdf.
33. Merkle, R. C. 1980. Protocols for public key cryptosystems. IEEE Symposium on Security and Privacy; http://www.merkle.com/papers/Protocols.pdf.
34. Nakamoto, S. 2008. Bitcoin: a peer-to-peer electronic cash system; https://bitcoin.org/bitcoin.pdf.
35. Nakamoto, S. 2008. Re: Bitcoin P2P e-cash paper; http://satoshi.nakamotoinstitute.org/emails/cryptography/11/.
36. Narayanan, A., et al. 2016. Bitcoin and Cryptocurrency Technologies: A Comprehensive Introduction. Princeton University Press; http://bitcoinbook.cs.princeton.edu/.
37. Pass, R., et al. 2017. Analysis of the blockchain protocol in asynchronous networks. Annual International Conference on the Theory and Applications of Cryptographic Techniques; https://link.springer.com/chapter/10.1007/978-3-319-56614-6_22.
38. Pinkas, B., Sander, T. 2002. Securing passwords against dictionary attacks. Proceedings of the Ninth ACM Conference on Computer and Communications Security: 161-170; https://dl.acm.org/citation.cfm?id=586133.
39. Reuters. 2014. Mind your wallet: why the underworld loves bitcoin; http://www.cnbc.com/2014/03/14/mind-your-wallet-why-the-underworld-loves-bitcoin.html.
40. Sirer, E. G. 2016. Bitcoin guarantees strong, not eventual, consistency. Hacking, Distributed; http://hackingdistributed.com/2016/03/01/bitcoin-guarantees-strong-not-eventual-consistency/.
41. Szabo, N. 1994. Smart contracts; http://www.fon.hum.uva.nl/rob/Courses/InformationInSpeech/CDROM/Literature/LOTwinterschool2006/szabo.best.vwh.net/smart.contracts.html.
42. Szabo, N. 2008. Bit gold. Unenumerated; https://unenumerated.blogspot.com/2005/12/bit-gold.html.
43. Wattenhofer, R. 2016. The Science of the Blockchain. Inverted Forest Publishing.
44. Rivest, R. L., Shamir, A. 1996. PayWord and MicroMint: Two simple micropayment schemes. International Workshop on Security Protocols.
Arvind Narayanan is an assistant professor of computer science at Princeton. He leads the Princeton Web Transparency and Accountability Project to uncover how companies collect and use our personal information. Narayanan also leads a research team investigating the security, anonymity, and stability of cryptocurrencies, as well as novel applications of blockchains. He co-created a massive open online course, and a textbook on bitcoin and cryptocurrency technologies. His doctoral research showed the fundamental limits of de-identification, for which he received the Privacy Enhancing Technologies Award. Narayanan is an affiliated faculty member at the Center for Information Technology Policy at Princeton and an affiliate scholar at Stanford Law School's Center for Internet and Society. You can follow him on Twitter at @random_walker.
Jeremy Clark is an assistant professor at the Concordia Institute for Information Systems Engineering. He obtained his Ph.D. from the University of Waterloo, where his gold medal dissertation was on designing and deploying secure voting systems, including Scantegrity—the first cryptographically verifiable system used in a public-sector election. He wrote one of the earliest academic papers on bitcoin, completed several research projects in the area, and contributed to the first textbook. Beyond research, he has worked with several municipalities on voting technology and testified to the Canadian Senate on bitcoin. You can follow him on Twitter at @PulpSpy.

# h2 Demoni
 
# Sisältö
* [x) Artikkeli](#x-artikkeli)
* [a) Apassi](#a-apassi)
* [b) Moottorix](#b-moottorix)
* [c) Automoottorix](#c-automoottorix)
* [d) Vapaaehtoinen bonus](#d-vapaaehtoinen-bonus)





### Koneen tekniset tiedot
* Prosessori: Intel Core i5-8265U CPU @ 1.60 GHz (1.80 GHz turbo, 8 ydintä)
* RAM: 16 GB (15,7 GB käytettävissä)
* Järjestelmä: Windows 11 Pro 64-bittinen (x64-suoritin)
* Näytönohjain: Intel UHD Graphics 620
* Tallennustila: 237 GB, josta 158 GB vapaana
* DirectX-versio: DirectX 12


## x) Artikkeli

### Karvinen 2026: Apache installed with Ansible - quick notes


### Ansible Community Documentation Handlers: running operations on change

a) Handlers: running operations on change (johdantokappale pääotsikon alta)
-Notifying handlers

b) 'ansible-doc service':
-johdantokappale (MODULE alta)
-enabled
-name
-state
-EXAMPLES


## a) Apassi 

Lähdin tekemään raporttia 11.4.2026 kello 18:21. Aloitetaan asentamalla Apache2 käsin, eli ei Ansibleen - jonne erheellisesti ensin lähdin eksymään.

Ohjeistuksena oli, että Weppisivun tulee näkyä palvelimen etusivulla ja että sivun tulee olla tavallisen käyttäjän muokattavissa ilman root- tai sudo-oikeuksia.

Tässä tehtäväosiossa käytin apuna Karvisen (2026) Apache installed with Ansible - quick notes -ohjetta.

#### Siirryin ensin:

* **`ls -la`** - tarkastelin kaikkia tietoja ja oikeuksia
  
* **`sudo apt-get update`** - päivitetään paketit
  
* **`sudo apt-get install apache2`** - asensin varuiksi apache2 - tuli virheilmoitus: "apache2 is already the newest version (2.4.66-1~deb13u2)." Eli oli asennettu jo.

Tässä kohtaa tein välillä paluuta edeltävään raporttiini h2 Voileipä (Sharifi, 2026), jotta sain muisteltua etenemisaskeleet.

Koska olin jo asentanut manuaalisesti aiemmin apache2:n ja weppisivun, niin lähden kertauksen vuoksi tarkistelemaan tiedostojen sisältöjä ja muokkaamaan niitä tarvittaessa. 

### Tarkistetaan tietojen ja tiedostojen sisällöt

* Avasin selaimen ja menin Apachen sivustolle `http://localhost` -sivusto näkyi eli se toimi.

_![29](images/29.png)

_Apache pyörii - localhost toimii_
  
### Oikeudet 

Lähdin tarkistamaan oikeuksia, eli tehtävänantona oli, että tavallinen käyttäjä pääsee muokkaamaan sivua ilman sudoa.
  
Tehtävän ohjeistuksessa olikin Vinkit -osiossa tähän vihje. 

**Tässä oli tärkeää hahmottaa, että uusi tiedosto tehdään kotihakemistossa, ei ansible-hakemistossa.**

Lähdin tarkistamaan tiedostoa 000-default.conf jotta voin tarkistaa, olinko luennon aikana onnistunut muuttamaan asetuksia niin, että tavallinen käyttäjä voi tehdä muutoksen. 

Tässä oli tärkeää, että ei käyttänyt chmod + numeroita Teron ohjeen mukaan, mikäli sitä tulisikin muuttaa.

Yritin tässä tehtävänannossa kovin itse muistella komentoja ja ymmärtää, mitä teen, joten tässä tehtävässä olikin tarkoitus viettää enemmän aikaa.

* **`ls /etc/`** - täältä etsin apache2 -kansion

* **`ls /etc/apache2/`** Apache kansio
 
* **`ls /etc/apache2/sites-enabled/`** - katsoin sites-enabled hakemiston sisällön
 
* **`cat /etc/apache2/sites-enabled/000-default.conf`** - katsoin tiedoston sisällön - tässä kohtaa ei näe vielä omistajatietoja - löysin tässä tiedon, että DocumentRoot on /var/www/html/ josta pitää tarkistaa oikeudet.
 
* **`ls -la /var/www/html/`** - tarkistetaan oikeudet

![28](images/28.png)

_DocumentRoot /var/www/html/ oikeudet_

Yllä olevan kuvan mukaisesti käyttäjällä `liljas` eli tavallisella käyttäjällä oli oikeudet muokata tiedostoja. 

Sivu näkyi localhostissa ja minä (liljas) omistin tiedostot. 

Lähdin seuraavaksi etenemään testaamisen merkeissä.


### Testaaminen

Tarkoitukseni oli muokata nyt index.html -tiedostoa ilman sudoa, jotta voidaan testata onko tosiaan tavallisella käyttäjällä oikeudet.

**Tässä kohtaa oli tärkeää ymmärtää, että alla olevassa kuvassa on Apache-konfiguraatiotiedosto – ei index.html-tiedosto.** 

Aloittelijana tässäkin kohtaa sai hetken tuijotella.

![31](images/31.png)

_Apache konfiguraatiotiedosto_

Tarkoitus on päästä `index.html` -tiedostoon muokkaamaan tietoja.

Konfiguraatiotiedostosta selvisi, että `DocumentRoot` on `/var/www/html/`, jonne pitää navigoida.

### Sivuston muokkaamiseen etenin seuraavin komennoin:

* **`micro /var/www/html/index.html`**

![32](images/32.png)

Vihdoin pääsin muokkaamaan sivun sisältöä, eli testaamaan, onko oikeudet tavallisella käyttäjällä.

Kävin poistamassa epämääräiset värit sivuilta testiksi.

![33](images/33.png)

_Apachen sivusto päivitetty_

Ja kuten yllä näkyy - muokkaus onnistui ongelmitta.

Mikäli tässä kohtaa olisi ilmennyt ongelma, olisi tullut edetä komennoin:

### Omistajuuden vaihtaminen

* **`chown`** = changing owner

* **`chown -R liljas /var/www/html/`**  - liljas kohtaan oma käyttäjänimesi ja DocumentRoot.



## b) Moottorix

Lähdin tähän osioon 21.02 samana iltana tauon jälkeen. 

Aloitin asentamalla Nginx:n jonka muistelin kuitenkin asentaneeni jo luennon aikana. 

Nginx täytyi asentaa käsin ja Weppisivun tuli näkyä palvelimen etusivulla.

### Asennettiin Nginx

![34](images/34.png)

_Nginx olikin jo asennettu_

Sama ohjeistus tässä kuten Apachella, eli tuli olla tavallisen käyttäjän muokattavissa sivut ilman root -tai sudo-oikeuksia. 

**Oli tärkeää muistaa sammuttaa Apache käsin.**

Olisin tässä käyttänyt Karvisen (2008) Apachen asennus ohjetta, mutta sivustoa ei saanut auki. 

Lehdon (2022) ohjeen löysin kuitenkin, jota myös käytimme Linux-palvelimet kurssilla ohjeena.

Löysin onnekseni myös luennolla kirjoittamani muistiinpanot, jolla lopulta etenin.

### Stopattiin Apache 

* **`sudo apt-get update`** - päivitin paketit

* **`sudo systemctl stop apache2`** - stoppasin Apachen

* **`curl localhost`** - tarkistin tilanteen

![35](images/35.png)

_Kuvan mukaisesti onnistunut Apachen stoppaus_

### Potkaistiin Nginx 

* **`sudo apt-get update`** - päivitin paketit tähän väliin

* **`sudo systemctl restart nginx`** - potkaistaan Nginx päälle

### Tarkistaminen - menikö Nginx päälle

Kuvan mukaisesti Nginx potkaistiin onnistuneesti käyntiin.

![36](images/36.png)

_Nginx käynnistyi ja sivu nousi pystyyn_

### Oikeuksien muokkaaminen tavalliselle käyttäjälle

Lähdin selvittämään alkuun DocumentRootin. 

Tässä kohtaa etenin hyvin pitkälti samalla tavalla, kuin Apachen kanssa:

* **`ls -la /etc/nginx/`** - Etsitään Nginxin konfiguraatiotiedosto josta etsitään DocumentRoot

![37](images/37.png)

_Nginx konfiguraatiotiedoston etsimistä_

#### Virhetilanne 

Tässä kohtaa kävi klassinen virhe eli etsin väärällä komennolla `cat` eikä oikealla `ls`. 

`cat` - on tarkoitettu tiedoston sisällä olevan tiedon näyttämiseen

`ls` - on tarkoitettu hakemiston sisällä olevan tiedon näyttämiseen.

![38](images/38.png)

_Etsimisen sekoilua_

Sisältä löytyi default - tiedosto. Lähdin availemaan sitä, jotta näen DocumentRootin.

* **`cat /etc/nginx/sites-enabled/default`** - katsoin tiedoston sisälle
  
Löytyi mitä tarvitsin eli ` /var/www/html/` on Nginxin DocumentRoot.

Tässä pääsin onneksi hieman sekoilemaan myös kun koitin muistella komentoa.

![39](images/39.png)

_komentojen sekoilu ja itse oikeudet_


* **`ls -la /var/www/html/`** - tällä oikealla hakukomennolla ja DocumentRootilla päästiin oikeuksia tarkistelemaan.

Olin luennon aikana kerennyt muokkaamaan tähänkin jo oikeudet ilman sudoa. 

### Testaaminen Nginx ilman sudoa ja oikeuksien tarkistus

Lähdin testaamaan kuten Apachellakin, että voin tosiaan muokata ilman sudoa.

* **`micro /var/www/html/index.html`** - microlla muokkaamaan tiedostoa eli sivun sisältöä
 
* **`ctrl + s` ja `ctrl + Q`** - tallennetaan muutokset

Muokkasin sisältöön "Hei vaan hei" aiemman "Hei vaan pitkästä aikaa!" - tekstin tilalle.

Sitten sivuston päivitystä ja alla olevan kuvan mukaisesti pääsin onnistuneesti muokkaamaan tiedostoa ilman sudoa.

![40](images/40.png)

_Uusi teksti oli päivittynyt sivustolle_


`-rwxr-xr-x 1 liljas liljas 239 11. 4. 19:51 index.html` - tämä kertoo, että käyttäjällä `liljas` on oikeudet index.html tiedostoon.

Tämä tehtäväosio oli onnistunut ja pääsinkin jo ennen kello 22 etenemään seuraavaan.

## c) Automoottorix

Tässä tehtävänosiossa oli tarkoituksena automatisoida Nginx asennus Ansiblella, jossa riitti vain ylläpitäjän osuus ja HTML-weppisivut pystyi tehdä käsin.

Lähdin tekemään tarkistusta seuraavasti:

* **`cd ansible`** - Ansiblen hakemistoon
* **`ls -la`** - tarkistin tiedostot
* **`cat site.yml`** - tarkistin roolit hakemistosta, löytyykö Nginx sieltä jo entuudestaan

![41](images/41.png)

_Nginx roolia ei löytynyt_ 

Nginx rooli ei löytynyt `roles`-hakemistosta, joten lähdin luomaan sen.

Käytin tässä apuna omaa h2 Voileipä -raporttiani (Sharifi, 2026).

### Nginx roolin luominen

* **`mkdir -p roles/nginx/tasks/`**  - luodaan rooli

### Nginx roolille sisällön luominen
  
* **`micro roles/nginx/tasks/main.yml`** - luodaan sisältö

Tässä kohtaa minun piti hieman miettiä, mitä laitan `main.yml` sisältöön. Karvisen (2026) ohjeissa onneksi oli esimerkki sisällöstä. 

Muokkasin `Nginx` -tietojen mukaisesti muuttaen hakemistot ja tiedoston nimet ja muutoin sama sisältö.

![42](images/42.png)

_main.yml sisältö jonka muokkasin_ 

Lopuksi vielä `ctrl + s` ja `ctrl + Q` jolla tallensin muutokset.

* **`micro site.yml`** - lähdin lisäämään roolin site.yml listalle ja tallennus

 ### Tarkistaminen

* **`cat site.yml`** - tarkistin että rooli oli onnistuneesti lisätty listalle

* **`ansible-playbook site.yml -k -K`** - ajetaan playbook



![41](images/41.png)

_Rooli lisätty onnistuneesti listalle_ 

## d) Vapaaehtoinen bonus

 Vapaaehtoinen bonus: Osiris-T. Osiris-T asentaa Wazuhin ja tarvittavat virtuaalikoneet. Voit lähettää vihamielistä verkkoliikennettä (tcpreplay), siepata sen (suricata) ja saat tulokset suoraan dashboardille (wazuh). 
 Enemmän alpha kuin se kreikkalainen kirjain. Mutta Oskari, Nico ja Arttu ilahtuvat, jos kokeilet. Häkämies, Saario, Mukkula 2026: Osiris-T. Häkämies etal 2026: How to Install.






# Lähteet 


Ansible Community Documentation. Dokumentti. Luettavissa: https://docs.ansible.com/projects/ansible/latest/collections/ansible/builtin/package_module.html/ Luettu: 05.04.2026.

Ansible Community Documentation. Dokumentti. _Handlers: running operations on change_ Luettavissa: https://docs.ansible.com/projects/ansible/latest/playbook_guide/playbooks_handlers.html/ Luettu: 11.04.2026.

Karvinen, T.2026. Verkkosivu. _Apache installed with Ansible - quick notes_ Luettavissa: https://terokarvinen.com/apache-ansible/ Luettu: 11.04.2026.

Karvinen, T. 2020. Verkkosivu. _Command Line Basics Revisited_ Luettavissa: https://terokarvinen.com/2020/command-line-basics-revisited/ Luettu: 05.04.2026.

https://linuxize.com/post/linux-chown-command/

https://www.youtube.com/watch?v=moNTR6zCLUc

https://www.youtube.com/watch?v=LnKoncbQBsM&t=171s

https://terokarvinen.com/2008/05/02/install-apache-web-server-on-ubuntu-4/index.html - 2008

https://susannalehto.fi/2022/apache-weppipalvelin-h3/

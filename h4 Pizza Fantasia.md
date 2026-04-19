# h3 Pizza Fantasia
 
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

Vinkit

CM: configuration management
DSL: domain specific language. Yhteen käyttötarkoitukseen tehty kieli. Esim Ansiblen oma kieli, jolla määrittelemme konfiguraatiota.
Kannattaa valita demoni, joka löytyy suoraan Debian 13 varastoista apt-get:lla.
Esimerkkejä: postgresql, caddy, mariadb, haproxy, varnish
Nämä voivat olla mutkikkaampia: samba, nfs, jokin ftp-palvelin, jokin vaihtoehtoinen ssh, jokin dhcpd, jokin tftpd


## x) Artikkeli

### Karvinen 2023: Configuration Management of Distributed Systems over Unreliable and Hostile Networks

#### 4.12.1 Size and Complexity of Some DSLs (112. Ominaisuuksien määrä.)
- DSL-kielet voivat olla monimutkaisia ja laajoja. Karvinen analysoi johtavien konfiguraatiotyökalujen Saltin sekä Puppetin monimutkaisuutta.
- Analysoinnissa Karvinen käytti ja tutki automaattisesti generoituja manuaaleja lähdekoodista.
- Saltilla oli 510 toimintoa, 20 000 riviä dokumentaatiota ja yli 75 000 sanaa. Puppetilla on 113 toimintoa ja se käyttää omia erikoiskäsitteitä ja ohjausrakenteita, toisin kuin perinteisimmät ohjelmointikielet, kuten C, Go tai Python.
Kysymys: Arvioiko juuri manuaalin koko monimutkaisuutta?

#### 4.12.2 Use of DSL Functions in Case Configuration (112-115. Mitä oikeasti käytetään.)
- Tutkimuksen laajuuden analysointia varten valikoitui United States Government Configuration baseline (NIST,2016) ja Mozilla Release Engineering Puppet Manifests (Mitchell et al., 2020).
- Pieni joukko komentoja kattaa 87% kaikista komennoista ja ohjausrakenteista. Yleisimpinä myös alla mainitut `file`, `package`, `exec` ja `service`.
Kommentti: Miksi tehdä vaikeasti, kun voi tehdä yksinkertaisesti?


#### 4.12.3.1 Dependencies Between Main Functions (115-117. Tärkeimmät rakennuspalikat.)
- Muutama komento kattaa suurimman osan konfiguraatioista.
- Tärkeimmät perustoiminnot ovat kaiken perusta: `exec`, joka kutsuu muita ohjelmistoja, ja `file` tiedostojen hallintaan joiden pohjalle yllä olevat funktiot rakentuvat
Kommentti: Miksi sitten muita komentoja on niin paljon, jos tarvitaan vain perustoiminnot?







## a) Räpylä

Lähdin tekemään raporttiosiota 19.4. kello 14.20. Meni hetki valita mieluinen demoni.

### fail2ban

#### Mikä se on? 

Päätin asentaa fail2banin, eli tunkeutumisen estoon kehitetty järjestelmä, joka suojelee Linux-servereitä automaattisilta hyökkäyksiltä.  

Työkalu toimii `jails`:ien eli vankiloiden avulla. Näitä kutsutaan valvontasäännöiksi tietyille palveluille. 

Sitä voidaan ajatella eräänlaisena vartijana, joka tutkii ja tarkistelee palvelimen lokitietoja kellon ympäri ja tutkii merkkejä haitallisesta toiminnasta, kuten epäonnistuneet kirjautumisyritykset, toistuvat yritykset, skannausyritykset, salasanan arvaukset ja niin edelleen. 

Epäilyttävän toiminnan vuoksi se estää automaattisesti hyökkääjän IP-osoitteen lisäämällä palomuuriin uusia sääntöjä estäen pääsyn tietyksi määräajaksi.

Löysin tähän erittäin selkeän ohjeen (James, J.). Lähdin aloittamaan seuraavin askelin.

#### Asennetaan Fail2Ban 

Ennen asennusta tehdään tärkein asia: Päivitetään paketit.

* **`sudo apt-get update`** - päivitetään paketit 

* **`sudo apt install fail2ban`** - asennetaan fail2ban

* **`fail2ban-client --version`** - katsotaan että asennus on onnistunut tarkistamalla versio


_








 
## b) Automaatti
Automaatti. Automatisoi valitsemasi demonin asennus Ansiblella.


## c) Asetus
Muuta asetustiedostoa herralla (master, "control node") ja aja ansible uudestaan. Osoita, että asetukset tulivat käyttöön.

## d) Paikka remonttiin
Riko jotain asetuksia. Voit esimerkiksi poistaa demonin 'sudo apt-get purge foobar' (purge poistaa myös asetustiedostoja), poistaa asennuksen yhteydessä tulevan kansion (sudo rm -r /etc/foobar/ # vaarallista) tms. Ja sitten ajaa ansible-roolisi uudestaan ja todeta, että se korjaa tilanteen.

## e) Idempotentti
Osoita, että tilasi on idempotentti.


## Lähteet 

Karvinen, T. 2024. Opinnäytetyö. _Configuration Management of Distributed Systems over Unreliable and Hostile Networks._ Luettavissa: https://westminsterresearch.westminster.ac.uk/item/w7vvz/configuration-management-of-distributed-systems-over-unreliable-and-hostile-networks/ Luettu: 19.4.2026.

Dhandala, N. 2026. Verkkosivu. _How to Use Ansible local Connection Plugin_ Luettavissa: https://oneuptime.com/blog/post/2026-02-21-how-to-use-ansible-local-connection-plugin/view/ Luettu: 19.4.2026

James, J. Verkkosivu. _How to Install Fail2Ban on Debian (13, 12, 11)_ Luettavissa: https://linuxcapable.com/how-to-install-fail2ban-on-debian-linux/ Luettu: 19.4.2026.

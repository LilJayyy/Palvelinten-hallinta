# h2 Voileipä
 
## Sisältö
* [x) Artikkeli](#x-artikkeli)
* [a) Sudoless](#a-sudoless)
* [b) Antero](#b-antero)
* [c) Package](#c-package)
* [d) File](#d-File)
* [e) Jotain muuta](#e-jotain-muuta)


## x) Artikkeli 

## Karvinen 2026: Sudo without password
-Artikkelissa ohjeistetaan sallimaan sudo-komennon käyttäminen ilman salasanaa. 
-Luodaan uusi käyttäjä ja lisätään se "sudoless" -ryhmään hyvällä salasanalla. Muistutetaan hyvien salasanojen käyttämisestä.
-Avataan root-shell vakuutuksena eli turvaksi sen varalta, että sudo menee rikki, jotta sen voi avata shellistä. Tämä tehdään ennen sudoers-tiedoston muokkaamista.
-Syötetään komento`sudo visudo /etc/sudoers.d/sudoless`ja tiedostoon sääntö `%sudoless ALL = (ALL) NOPASSWD: ALL` sallien ryhmälle käytön ilman salasanaa.
Oma huomio: Selkeä ohje, jossa tulee kuitenkin olla tarkkana, jotta prosessia ei tarvitse monesti toistaa.

## Munroe 2006: xkcd 149: Sandwitch
Mitä sarjakuvassa tapahtuu? Mitä yhteistä sillä on Karvisen artikkeliin?
-Sarjakuvassa on hauskasti kuvailtu miten sudo-komento toimii. On pakko totella ja tehdä se voileipä!
-Sudolla toimitaan pääkäyttäjän oikeuksilla (root) eikä userin, eli tavallisen käyttäjän oikeuksilla.
-Siinä on kuvailtu kuvituksen muodossa, millainen merkitys komennolla on. Sudolla "pakotetaan" suorittamaan tiettyjä komentoja ja on äärimmäisen tärkeä ellei yksi tärkeimmistä komennoista muistaa.
Kysymys/huomio: Miksi juuri voileipä? 

## Karvinen 2026: Passwordless with Ansible
-Ansiblessa rooli (role) on luoda "sudoless" ryhmä. Lisää säännön `sudoers.d/ NOPASSWD` ryhmälle.
-Teron sääntö numero 1: Manuaalinen ennen automaattista. Tällä tarkoitetaan sitä, että tehdään ensin salasanaton sudo manuaalisesti ensin.
-`Tree-komennolla` hakemiston rakenne tarkistetaan ja `cat`- komennolla tiedoston sisältö.
-Alkuun ei ole sudoa ilman salasanaa, joten sitä työstetään ensin. Pitää ensin lisätä `become: true`oikeaan kohtaan blockissa site.yml:ssä. lopuksi `playbook` ajetaan ja tarvittaessa sudo annetaan -K lisäyksellä.
Kysymys/huomio: Kumpi tuli ensin, muna vai kana?

## Ansiblen sisäänrakennettu dokumentaatio ansible-doc -kommennolla
Ansiblen sisäänrakennettu dokumentaatio ansible-doc -kommennolla.
Kustakin vain
Johdantokappale (Usein MODULE alla, päättyy OPTIONS alkuun)
Nimetyt optiot selityksineen
Esimerkeistä (EXAMPLES) jokin helppo ja keskeinen esimerkki
'ansible-doc copy': content, dest, src; owner, group, mode;
'ansible-doc apt': name, state, update_cache.
'ansible-doc file': path, recurse, src, state. owner, group, mode;
'ansible-doc user': name; create_home, comment, groups, shell, state, system.
'ansible-doc authorized_key': user, key.

### Koneen tekniset tiedot
* Prosessori: Intel Core i5-8265U CPU @ 1.60 GHz (1.80 GHz turbo, 8 ydintä)
* RAM: 16 GB (15,7 GB käytettävissä)
* Järjestelmä: Windows 11 Pro 64-bittinen (x64-suoritin)
* Näytönohjain: Intel UHD Graphics 620
* Tallennustila: 237 GB, josta 158 GB vapaana
* DirectX-versio: DirectX 12

## a) Sudoless





## b) Antero





## c) Package




## d) File




## e) Jotain muuta




# LÄHTEET 


Sharifi, L. 2026. Verkkosivu. _h1 Hei Ansiblen maailma_. Luettavissa: https://github.com/LilJayyy/Palvelinten-hallinta/blob/main/h1.md/ Luettu: xx.04.2026

Karvinen, T. 2026. Verkkosivu. _Sudo without password_ Luettavissa: https://terokarvinen.com/passwordless-sudo/ Luettu xx.04.2026.

Karvinen, T. 2026. Verkkosivu. _Passwordless Sudo with Ansible_ Luettavissa: https://terokarvinen.com/passwordless-sudo-with-ansible/ Luettu xx.04.2026.

Karvinen, T. 2020. Verkkosivu. _Command Line Basics Revisited_ Luettavissa: https://terokarvinen.com/2020/command-line-basics-revisited/ Luettu: xx.04.2026.

Munroe. 2006. Verkkosivu. _xkcd 149: Sandwitch_ Luettavissa: https://xkcd.com/149/ Luettu: xx.04.2026.


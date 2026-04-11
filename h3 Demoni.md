# h2 Demoni
 
## Sisältö
* [x) Artikkeli](#x-artikkeli)
* [a) Apassi](#a-apassi)
* [b) Moottorix](#b-moottorix)
* [c) Automoottorix](#c-automoottorix)
* [d) Vapaaehtoinen bonus](#d-vapaaehtoinen-bonus)


### Koneen tekniset tiedot
Prosessori: Intel Core i5-8265U CPU @ 1.60 GHz (1.80 GHz turbo, 8 ydintä)
RAM: 16 GB (15,7 GB käytettävissä)
Järjestelmä: Windows 11 Pro 64-bittinen (x64-suoritin)
Näytönohjain: Intel UHD Graphics 620
Tallennustila: 237 GB, josta 158 GB vapaana
DirectX-versio: DirectX 12


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

Lähdin tekemään raporttia 11.4.2026 kello 18:21. Aloitetaan asentamalla Apache2 käsin. Ohjeistuksena oli, että Weppisivun tulee näkyä palvelimen etusivulla ja että sivun tulee olla tavallisen käyttäjän muokattavissa ilman root- tai sudo-oikeuksia.

## b) Moottorix
Asenna Nginx käsin. Weppisivun tulee näkyä palvelimen etusivulla. Sivun tulee olla tavallisen käyttäjän muokattavissa, ilman root- tai sudo-oikeuksia. (Muista sammuttaa Apache ensin.)

## c) Automoottorix
 Automatisoi Nginx asennus Ansiblella. Ylläpitäjän osuus Ansiblella riittää, itse HTML-weppisivut voi tehdä käsin.
 
## d) Vapaaehtoinen bonus

 Vapaaehtoinen bonus: Osiris-T. Osiris-T asentaa Wazuhin ja tarvittavat virtuaalikoneet. Voit lähettää vihamielistä verkkoliikennettä (tcpreplay), siepata sen (suricata) ja saat tulokset suoraan dashboardille (wazuh). 
 Enemmän alpha kuin se kreikkalainen kirjain. Mutta Oskari, Nico ja Arttu ilahtuvat, jos kokeilet. Häkämies, Saario, Mukkula 2026: Osiris-T. Häkämies etal 2026: How to Install.






# Lähteet 


Ansible Community Documentation. Dokumentti. Luettavissa: https://docs.ansible.com/projects/ansible/latest/collections/ansible/builtin/package_module.html/ Luettu: 05.04.2026.

Ansible Community Documentation. Dokumentti. _Handlers: running operations on change_ Luettavissa: https://docs.ansible.com/projects/ansible/latest/playbook_guide/playbooks_handlers.html/ Luettu: 11.04.2026.

Karvinen, T.2026. Verkkosivu. _Apache installed with Ansible - quick notes_ Luettavissa: https://terokarvinen.com/apache-ansible/ Luettu: 11.04.2026.

Karvinen, T. 2020. Verkkosivu. _Command Line Basics Revisited_ Luettavissa: https://terokarvinen.com/2020/command-line-basics-revisited/ Luettu: 05.04.2026.




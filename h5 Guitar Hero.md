# Sisältö
* [x) Artikkeli](#x-artikkeli)
* [a) Online ](#a-online)
* [b) Dolly](#b-dolly)
* [c) Doh!](#c-doh!)
* [d) Tukki](#d-tukki)
* [e) Gitanible](#e-gitanible)
* [f) Hae pari projektiin](#f-hae-pari-projektiin)
* [g) Se toinen järjestelmä](#g-se-toinen-jarjestelmä)
* [h) Yhteistyötä](#h-yhteistyötä)

### Koneen tekniset tiedot
* Prosessori: Intel Core i5-8265U CPU @ 1.60 GHz (1.80 GHz turbo, 8 ydintä)
* RAM: 16 GB (15,7 GB käytettävissä)
* Järjestelmä: Windows 11 Pro 64-bittinen (x64-suoritin)
* Näytönohjain: Intel UHD Graphics 620
* Tallennustila: 237 GB, josta 158 GB vapaana
* DirectX-versio: DirectX 12

# x) Artikkeli

#### What is Git?
-Versionhallintajärjestelmä, joka ottaa valokuvia projektin jokaisesta vaiheesta commitilla.
 
-Muutokset ja sisältö luodaan paikallisesti omalta koneelta ja ne siirtyvät etäpalvelimelle (Githubiin) kun on tehty push komento eli `git push`. Aina ennen tätä on suositeltavaa suorittaa komento `git pull`.

#### 'git add --all && git commit; git pull && git push'.
* **`git add`** -komento siirtää työhakemistosta staging-alueelle muutokset snapshotin ottamista varten. 

* **`git commit`** - komento ottaa snapshotin eli valokuvan projektin Git-tietokantaan.
  
* **`git pull`** - komento on automatisoitu versio fetch-komennosta. Haara ladataan etärepositorysta ja yhdistetään eli "mergataan" se nykyiseen haaraan Git-tietokantaan.

* **`git push`** -komento lähettää muutokset etäpalvelimelle eli siirtää paikallisen haarakkeen toiseen repositoryyn jossa se julkaistaan.

# a) Online.

Lähdin alkuun luomaan repositorya eli varastoa:

1. Kirjauduin: www.github.com
2. Loin uuden varaston oikeasta yläkulmasta `+` ja new repository. Julkinen ja "Add readme" valittuna.
3. Add a license ja sieltä `GNU General Public License v3.0`
4. Lopuksi vielä "Create" -painikkeesta.

![84](images/84.png)

_Varasto (repository) luotu onnistuneesti_

# b) Dolly
# c) Doh!
# d) Tukki
# e) Gitanbile
# f) Hae pari projektiin

Pari on hankittu.

# g) Se toinen järjestelmä
# h) Yhteistyötä






![60](images/60.png)

## Lähteet 

Ansible Docs. Dokumentti. _Connection methods and details._ Luettavissa: https://docs.ansible.com/projects/ansible/latest/inventory_guide/connection_details.html/ Luettu: 28.4.2026

Ansible Docs. Dokumentti. _Handlers: running operations on change._ Luettavissa: https://docs.ansible.com/projects/ansible/latest/playbook_guide/playbooks_handlers.html/ Luettu: 28.4.2026

Ansible Docs. Dokumentti. _Getting started._ Luettavissa: https://docs.ansible.com/projects/ansible/latest/getting_started/get_started_playbook.html/ Luettu: 28.4.2026.

Atlassian. Dokumentti. _Git Glossary_ Luettavissa: https://www.atlassian.com/git/glossary/ Luettu: 28.4.2026.

Chacon and Straub 2014: _Pro Git, 2ed: 1.3 Getting Started - What is Git?._ Luettavissa: https://git-scm.com/book/en/v2/Getting-Started-What-is-Git%3F/ Luettu: 28.4.2026.

Karvinen, T. 2026. Verkkosivu. _Apache installed with Ansible - quick notes._ Luettavissa: https://terokarvinen.com/apache-ansible/ Luettu: 28.4.2026.

Karvinen, T. 2020. Verkkosivu. _Command Line Basics Revisited._ Luettavissa: https://terokarvinen.com/2020/command-line-basics-revisited/ Luettu: 28.4.2026.

Sharifi, L. 2026. Verkkosivu. _h2 Voileipä_. Luettavissa: https://github.com/LilJayyy/Palvelinten-hallinta/blob/main/h2%20Voileip%C3%A4.md/ Luettu: 28.4.2026.

Sharifi, L. 2026. Verkkosivu. _h3 Demoni_. Luettavissa: https://github.com/LilJayyy/Palvelinten-hallinta/blob/main/h3%20Demoni.md/ Luettu: 28.4.2026.

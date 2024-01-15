# Uitbreiding en kennis

## Uitbreiding Scope

Indien er nog extra sites zouden toegevoegd worden, zonder Dark Fiber dan zou ik het volgende doen.

- Hub-and-Spoke: Ons origineel design is een hub-and-spoke design, dit houd in dat andere sites hun breakout via het hoofdkwartier krijgen, dit zou behouden kunnen blijven.
- VPN: De extra sites zouden hun toegang tot het internet nog steeds krijgen via het hoofdkwartier. Zij zouden connecteren met het hoofdkantoor door een vpn tunnel en hun breakout naar het internet zou dus via de router/firewall van het hoofdkwartier gaan.
- Firewall cluster (zoals Palo Alto): De extra sites gaan dus voor extra trafiek op het hoofdkwartier zorgen. Om dit tegemoet te komen zou ik dan bijvoorbeeld een Palo Alto firewall cluster gebruiken op het hoofdkantoor. Dit zou voor high availability, load balancing en redundancy zorgen.
- IPS: Aangezien de trafiek van alle locaties dus via het hoofdkwartier gaan, kan men dan de trafiek van alle locaties monitoren met een IPS op het hoofdkwartier.

## Functionaliteit IPS

Een intrusion prevention system maakt gebruik van SSL inspectie om https geëncrypteerde trafiek te monitoren en beveiligen. Dit kan men doen door een trusted root certificaat te installeren op het client toestel, waardoor het SSL inspectie toestel (IPS) het SSL/TLS trafiek kan onderscheppen en decrypteren. Eenmaal het trafiek is gedecrypteerd kan het geïnspecteerd worden op malicious inhoud. Eenmaal dit soort kwaadwillend trafiek wordt gedetecteerd kan de IPS dit verkeer dan tegengaan.

De detectie kan op verschillende manier gebeuren, één daarvan is detectie op basis van signatures, een ips kan de bitstroom van gedecrypteerd https trafiek vergelijken met een interne database van signatures/handtekeningen. Sommige IPS-en maken gebruik van online databases van handtekeningen/signatures of aanvalstechnieken zoals die van [Mitre](https://attack.mitre.org/).

IPS kunnen ook meer geavanceerde technieken voor inspectie gebruiken zoals:
- Address matching
- HTTP string and substring matching
- Generic pattern matching
- TCP connectie analyse
- Packet afwijking detectie
- Trafiek afwijking detectie
- TCP/UDP poort matching

Eenmaal gedetecteerd kan een IPS de volgende response technieken gebruiken:
- Het kan zelf de firewall aanpassen voor toegevoegde bescherming voor vooraf ongekende zwakheden
- De inhoud van de aanval aanpassen bijvoorbeeld door kwaadwillige trafiek te vervangen door waarschuwingen van de gedelete inhoud
- Automatische alarmen sturen naar sysadmins, om hen op de hoogte te stellen van mogelijke security breaches
- Het kan kwaadwillige packets gewoon droppen
- De connectie die dit packet stuurt resetten
- Trafiek van het kwaadwillige ip adres afblokken

Indien een IPS detecteert dat er niets kwaadmoedig aan de hand is met de trafiek kan hij dit ook herencrypteren vooraleer dit naar het destination adres te versturen.

## Functionaliteit inter-campus-links

Momenteel hebben wij in ons netwerk design een core switch en een access laag switch. De poorten van de core switch zijn allemaal als trunk poort ingesteld. Op deze manier kan men een access laag switch insteken en kan deze gebruikt worden voor alle vlans. De poorten van deze access laag switchen zijn dan natuurlijk in access modus gezet, buiten de poort geconnecteerd met de core switch.

Dit geeft als voordeel dan men gewoon een access laag switch in de core switch kan steken en dat deze voor alle vlans kan gebruikt worden.

Voor onze routers hebben wij sub-interfaces voor de vlans op deze netwerken. Echte trunk poorten kan men op routers volgens mij niet instellen.

Trunks tussen routers instellen is dan ook niet mogelijk en helemaal niet noodzakelijk. Routers op andere sites krijgen de netwerken van andere locaties dynamisch doorgespeeld door de OSPF setup. Dus indien clienten of applicaties op de vlans van dit netwerk trafiek naar een andere site sturen gaan zij eerst (door hun dhcp instellingen van default router) deze trafiek versturen naar hun eigen router en deze neemt de routering naar het andere netwerk dan over en zal deze trafiek dan versturen naar de router op de andere site. Wanneer de trafiek dan aankomt op deze locatie zal de router hier de routering naar de correcte vlan overnemen aangezien hij de kennis heeft van de vlans op zijn netwerk via zijn sub-interfaces.

### Voor- en nadelen van enkel trunks tussen alle switches
Enkele voordelen die ik teruggevonden heb in mijn onderzoek:
- Scalability: Door alle switches te trunken maakt het het scalen van het netwerk simpeler, dit omdat men makkelijk vlans kan toevoegen zonder veel aanpassingen te doen aan de fysieke opstelling en configuratie van het netwerk.
- Het maakt het organiseren en segmenteren ook gemakkelijker.

Enkele nadelen die ik teruggevonden heb in mijn onderzoek:
- Broadcasts: Indien men alle switches met elkaar trunked kan een enkele end-device op een vlan een broadcast storm starten en deze broadcast wordt dan naar alle vlans gestuurd in plaats van enkel zijn eigen vlan.
- Spanning Tree: Om op broadcast storms terug te komen. De spanning tree configuratie indien men een grote hoeveelheid switches gebruikt zal indien alle switches getrunked zijn dan enorm complex worden.
- Flat Network: Dit zou kunnen leiden tot platte netwerkstructuur. Dit heeft verschillende nadelen als het moeilijker traceren van netwerk fouten omdat alle toestellen kunnen aangetast worden en gelimiteerde isolatie van het netwerk waardoor toestellen in hetzelfde broadcast domein met elkaar kunnen communiceren.

### Conclusie

Bij onderzoek naar de voor- en nadelen van het trunken van alle switches in een netwerk kwam ik op zeer beperkte voordelen (mogelijk heb ik de echte voordelen niet gevonden) en enorm veel nadelen. De voordelen zijn zo miniem in vergelijking met de grote risico's dat de nadelen met zich meebrengen. In mijn mening lijkt het niet logisch om alle switches met elkaar te trunken verder dan de switches die met de core switch zijn verbonden. Dit wilt niet zeggen dat onze huidige setup volledig correct is en ik ga ervan uit dat poorten trunken op de core switch ook met zijn voor- en nadelen komt.
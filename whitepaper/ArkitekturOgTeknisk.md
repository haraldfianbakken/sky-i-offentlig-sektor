# Referansearkitektur

Rent overordnet kan man se på en helhetlig arkitektur hvor vi  bør skille på hva som lovmessig må ligge i egne datasentere (lovmessig reguleringer/krav) og hvordan vi klassifiserer ulike applikasjoner.

![High-level](illustrations/high-level-architecture.png)

## Klassifiseringmatrise for applikasjoner
Her er et forsøk på hvordan vi kan tenke rundt klassifisering/skille av applikasjoner:

- Publikumstjeneste/Applikasjon (Internet exposed)
- Intern applikasjon (interne ansatte)
- PII
- Ikke PII
- Ikke sammfunnskritisk (tåler noe nedetid) 
- Sammfunnskritisk - delte tjenester (nasjonale)

Sammfunnskritiske tjenester som må kjøre og være tilgjengelig som er delt på tvers av lokasjoner/uavhengig av lokasjon.

Sluttbrukere/systemer bruker internet (VPN eller MPLS).

- Sammfunnskritiske - lokale tjenster (edge)
Sammfunnskritiske tjenester må fungere i nødssituasjon hvor deler faller ut og tåler lite/eller ingen nedetid eller er svært sensitive til latens.

Sluttbrukere/systemer befinner seg lokalt (e.g. et sykehus/sykebil) mm.

- Særskilte lover (hvor public cloud gjør det umulig)

## On-premises
Dette er servere (virtualisert eller bare-metal) du har i dine egne datasentere hvor du kan drifte deler av applikasjonsporteføljen.

## Nettverk

Du kan sikkert knytte ditt kontor til Azure ved hjelp av f.eks Site-to-Site VPN eller Azure Express Route.

Dersom det er behov for svært mange klienter tilknyttet et virtuelt nettverk og/eller det er mange kontorer som skal tilknyttes - så bør man vurdere å kombinere dette med Azure Virtual WAN.

## Sikring av nettverk

I Azure finnes det mange aspekter av nettverkssikkerhet. På mange måter kan man designe en nettverkstopolgi som ligner et tradisjonelt datasenter med segmentering mm. 

Man kan sikre trafikkflyt og nettverk i Azure med blant annet NSGs (Network security groups), Application Security groups, Brannmurer (Azure Firewall - eller tredjeparter slik som Barracuda, BigIp/F5 mm.). 

I tillegg bør du basere sikkerhetsmodellen din på en "Zero Trust" modell (Se Zero trust in Azure her). 

## Tekniske komponenter for sikring og compliance

 - Azure Datasenter sikring
 - Customer Lockbox
 - Confidential computing
 - Azure Policy
 - Customer managed Keys (Kryptering og Bring-Your-Own-Key)
 - Azure Dedicated HSM
 - Azure ARC
 - Azure Dedicated Hosts

## Utvalgte sikkerhetselementer

 - Security baseline
 - Security baseline (Azure Stack Edge)
 - [Security baseline (Azure Stack HCI)](https://docs.microsoft.com/en-us/azure-stack/hci/concepts/security)
 - Azure Active Directory : Conditional access
 - Azure Active Directory : Privileged identity management (PIM)
 - Microsoft Defender for Cloud
 - Azure DDOS Protection

## Krisesituasjoner

I en særskilt krisesituasjon bør vi stille oss følgende spørsmål:

 - Hvor lang tid tar det før ditt eget utstyr begynner å feile?
 - Hvilke 'skjulte' avhengigheter har dine systemer?
 - Hvordan skal sluttbrukere nå applikasjoner som er eksponert på internett? (DNS/Sertifikater mm.)

## Særskilte norske krav (som man bør ta stilling til)

- [Arkivloven](https://www.arkivverket.no/for-arkiveiere/skylagring-og-skanning-i-utlandet#:~:text=Arkivloven%20inneholder%20ingen%20bestemmelser%20som,for%20bruk%20av%20slike%20l%C3%B8sninger.&text=Arkivloven%20%C2%A7%207%20forplikter%20Riksarkivaren,med%20arkivarbeidet%20i%20offentlige%20organ.): *"Arkivloven inneholder ingen bestemmelser som direkte regulerer lagring av arkiv i skytjenester, og er i utgangspunktet ikke til hinder for bruk av slike løsninger. Det følger likevel av arkivloven § 9 b at arkivmateriale ikke kan «førast ut or landet, dersom dette ikkje representerer ein naudsynt del av den forvaltningsmessige eller rettslege bruken av dokumenta.” Når det er lagt til grunn at den fysiske lagringsplassen avgjør hvor data er å finne, følger det naturlig av denne bestemmelsen at overføring av arkivmateriale til servere i utlandet bryter med forbudet mot å føre arkiv ut av landet."*

- [Bokføringsloven]
- [Sikkerhetsloven]
- [NKOM]
- [NSM]

NSM har en rekke råd og anbefalinger for IKT sikkerhet.
I følgende artikkel: [Grunnprinsipper for IKT-sikkerhet 2.0](https://nsm.no/regelverk-og-hjelp/rad-og-anbefalinger/grunnprinsipper-for-ikt-sikkerhet-2-0) kan du finne detaljert informasjon og guidelines.

En rekke av disse kan automatiseres og rapporteres på ved hjelp av Azure Policies som kan implementeres og rulles ut i storskala.

Vi tenker å påbegynne noe av arbeidet her med å utarbeide noen slike policies som kan rapporters på tvers av en enterprise.
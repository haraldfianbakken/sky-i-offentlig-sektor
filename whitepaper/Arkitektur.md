# Referansearkitektur

![High-level](illustrations/high-level-architecture.png)

## On-premises
Dette er servere (virtualisert eller bare-metal) du har i dine egne datasentere hvor du kan drifte deler av applikasjonsporteføljen.

## Plassering av applikasjoner

## Nettverk

Du kan sikkert knytte ditt kontor til Azure ved hjelp av f.eks Site-to-Site VPN.

Dersom det er behov for svært mange klienter tilknyttet et virtuelt nettverk og/eller det er mange kontorer som skal tilknyttes - så bør man vurdere å kombinere dette med Azure Virtual WAN.

## Tekniske komponenter for sikring og compliance

 - Azure Datasenter sikring
 - Customer Lockbox
 - Confidential computing
 - Azure Policy
 - Customer managed Keys
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
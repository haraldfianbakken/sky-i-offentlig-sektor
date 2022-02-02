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

 - Azure Security Center
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


# Referansearkitektur

Rent overordnet kan man se på en helhetlig arkitektur hvor vi bør skille på hva som lovmessig må ligge i egne datasentere/edge (lovmessig reguleringer og krav eller sammfunnskritisk) og hvordan vi klassifiserer ulike applikasjoner som kan  plasseres i sky, edge eller on-premises.

![High-level](illustrations/high-level-architecture.png)

// TODO:
    Bør vi ha en forenklet modell for 'most common' scenarios? Iom. at det er få offentlige som er underlagt sikkerhetsloven? 

    Eks. 2-3 scenarier: Sykehus med 2-3 lokasjoner? Kommune med x antall avdelinger/publikumstjenester, interne tjenester mm.
// END TODO

## Klassifiseringmatrise for applikasjoner
Her er et forsøk på hvordan vi kan tenke rundt klassifisering/skille av applikasjoner:

- Publikumstjeneste/Applikasjon (Internett eksponert)
- Intern applikasjon (interne ansatte)
- Ikke PII/sensitivt 
- PII/Sensitivt 
- Begrenset (Sikkerhetsloven)
- Konfidensielt (Sikkerhetsloven)
- Hemmelig (Sikkerhetsloven)
- Strengt hemmelig (Sikkerhetsloven)
- Særskilte lover / krav *(Eks. EKOM)
- Ikke sammfunnskritisk (tåler noe nedetid) 
- Sammfunnskritisk - delte tjenester (nasjonale)

Sammfunnskritiske tjenester som må kjøre og være tilgjengelig som er delt på tvers av lokasjoner/uavhengig av lokasjon. 

Sluttbrukere eller systemer - bruker internet (VPN eller MPLS) eller telefoni for å nå tjenester.

- Sammfunnskritiske - lokale tjenster (edge & hybrid)
Sammfunnskritiske tjenester må fungere i nødssituasjon hvor deler faller ut og tåler lite/eller ingen nedetid eller er svært sensitive til latens.

Sluttbrukere/systemer befinner seg lokalt (e.g. et sykehus/sykebil) mm.

// TODO  - Klarer vi å lage en visualisering/ decision tree?
# Matrise

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

 - Hvor lang tid tar det før ditt eget utstyr begynner å feile (on-premises utstyr)?
 - Hvilke 'skjulte' avhengigheter har dine systemer? (eks. DNS/CA mm)
 - Hvordan skal sluttbrukere nå applikasjoner som er eksponert på internett? 

## Særskilte norske lover, krav og anbefalinger(som man bør ta stilling til)

- [Arkivloven](https://www.arkivverket.no/for-arkiveiere/skylagring-og-skanning-i-utlandet#:~:text=Arkivloven%20inneholder%20ingen%20bestemmelser%20som,for%20bruk%20av%20slike%20l%C3%B8sninger.&text=Arkivloven%20%C2%A7%207%20forplikter%20Riksarkivaren,med%20arkivarbeidet%20i%20offentlige%20organ.): *"Arkivloven inneholder ingen bestemmelser som direkte regulerer lagring av arkiv i skytjenester, og er i utgangspunktet ikke til hinder for bruk av slike løsninger. Det følger likevel av arkivloven § 9 b at arkivmateriale ikke kan «førast ut or landet, dersom dette ikkje representerer ein naudsynt del av den forvaltningsmessige eller rettslege bruken av dokumenta.” Når det er lagt til grunn at den fysiske lagringsplassen avgjør hvor data er å finne, følger det naturlig av denne bestemmelsen at overføring av arkivmateriale til servere i utlandet bryter med forbudet mot å føre arkiv ut av landet."*

### Bokføringsloven
// TODO - Noen skrive noe smart rundt bokføringsloven
### Sikkerhetsloven
// TODO - Noen skrive noe smart rundt sikkerhetsloven
### NKOM
// TODO - Noen skrive noe smart rundt NKOM
### NSM - Råd og anbefalinger for IKT sikkerhet

NSM har en rekke råd og anbefalinger for IKT sikkerhet. [Grunnprinsipper for IKT-sikkerhet 2.0](https://nsm.no/regelverk-og-hjelp/rad-og-anbefalinger/grunnprinsipper-for-ikt-sikkerhet-2-0) er et supplement til eksisterende nasjonale og internasjonale regelverk, standarder og rammeverk innen IKT-sikkerhet og er inspirert av mange av disse.

Tekniske tiltak fra grunnprinsippper for IKT-sikkerhet kan knyttes mot Azure Policies for en automatisert overvåkning og rapportering av compliance på tvers av hele virksomhetens digitale eiendom. Azure har over 700 eksisterende innebygde policies for IaaS, PaaS og hybrid i tillegg til muligheten for å lage egne tilpassede policies. En samling av Azure policies som er gruppert etter et felles formål kalles en Policy Initative. Tilsvarende samlinger av Azure policies finnes og vedlikeholdes av Microsoft for anerkjente internasjonale regelverk som: [ISO 27001:2013](https://docs.microsoft.com/en-us/azure/governance/policy/samples/iso-27001) og [CIS 1.3.0](https://docs.microsoft.com/en-us/azure/governance/policy/samples/cis-azure-1-3-0).

Under vises et skjermbilde fra Azure Policy sin compliance oversikt hvor utvalgte NSM prinsipper er knyttet inn. Merk at dette kan gi en oversikt på tvers av tjenester og infrastruktur, med Azure Arc kan man også evaluere policy tilstand mot hybrid og multisky.

![Policy initative](illustrations/az-policy-initative.png)

> Compliance i Azure Policy viser tilstanden for de spesifikke policy definisjonene man har knyttet opp og det vil sjeldent være et en-til-en forhold mellom en kontroll i et rammeverk og en policy. Et rammeverk eller en standard vil også inneholde prosess og organisatoriske tiltak som ikke kan knyttes opp mot en teknisk policy. Derfor vil compliance mot feks NSM grunnprinsipper, ISO 27001:2013 eller CIS 1.3.0 i Azure Policy kun gi en delvis oversikt over det totale bildet.

Under vises et eksempel på sikkerhetstiltak fra ulike kategorier i NSM grunnprinsipper som er knyttet mot relevante Azure Policies. Et sikkerhetstiltak kan ha flere Azure Policies for en bredere dekning og eksempelet viser muligheten for kombinasjon på tvers av IaaS, PaaS i Azure og hybrid/multisky.
### Eksempel: NSM grunnprinsipper for IKT-sikkerhet 2.0 policy initiative

| Sikkerhetstiltak | Grunnprinsipp | Kategori | Azure Policy referanse | Kommentar |
| ------------- |-------------| -----| -----| -----|
| 2.3.1 Installer sikkerhetsoppdateringer så fort som mulig. | 2.3 Ivareta en sikker konfigurasjon | 2. Beskytte og opprettholde | [System updates should be installed on your machines](https://portal.azure.com/#blade/Microsoft_Azure_Policy/PolicyDetailBlade/definitionId/%2Fproviders%2FMicrosoft.Authorization%2FpolicyDefinitions%2F86b3d65f-7626-441e-b690-81a8b71cff60) | IaaS i Azure |
| 2.3.8 Ikke deaktiver kodebeskyttelsesfunksjoner. | 2.3 Ivareta en sikker konfigurasjon | 2. Beskytte og opprettholde | [Windows Defender Exploit Guard should be enabled on your machines](https://portal.azure.com/#blade/Microsoft_Azure_Policy/PolicyDetailBlade/definitionId/%2Fproviders%2FMicrosoft.Authorization%2FpolicyDefinitions%2Fbed48b13-6647-468e-aa2f-1af1d3f4dd40) | IaaS i Azure eller hybrid- og multisky med Azure Arc |
| 2.5.1 Styr dataflyt mellom nettverks-soner. | 2.5 Kontroller dataflyt | 2. Beskytte og opprettholde | [Subnets should be associated with a Network Security Group](https://portal.azure.com/#blade/Microsoft_Azure_Policy/PolicyDetailBlade/definitionId/%2Fproviders%2FMicrosoft.Authorization%2FpolicyDefinitions%2Fe71308d3-144b-4262-b144-efdc3cc90517) | Azure nettverk |
| 2.6.7 Bruk MFA for å autentisere brukere. | 2.6 Ha kontroll på identiteter og tilganger | 2. Beskytte og opprettholde | [MFA should be enabled on accounts with write permissions on your subscription](https://portal.azure.com/#blade/Microsoft_Azure_Policy/PolicyDetailBlade/definitionId/%2Fproviders%2FMicrosoft.Authorization%2FpolicyDefinitions%2F9297c21d-2ed6-4474-b48f-163f75654ce3) | Azure AD |
| 2.7.2 Aktiver kryptering i de tjenestene som tilbyr slik funksjonalitet. | 2.7 Beskytt data i ro og i transitt | 2. Beskytte og opprettholde | [Storage accounts should have infrastructure encryption](https://portal.azure.com/#blade/Microsoft_Azure_Policy/PolicyDetailBlade/definitionId/%2Fproviders%2FMicrosoft.Authorization%2FpolicyDefinitions%2F4733ea7b-a883-42fe-8cac-97454c2a9e4a) | PaaS i Azure |
| 2.7.2 Aktiver kryptering i de tjenestene som tilbyr slik funksjonalitet. | 2.7 Beskytt data i ro og i transitt | 2. Beskytte og opprettholde | [Transparent Data Encryption on SQL databases should be enabled](https://portal.azure.com/#blade/Microsoft_Azure_Policy/PolicyDetailBlade/definitionId/%2Fproviders%2FMicrosoft.Authorization%2FpolicyDefinitions%2F17k78e20-9358-41c9-923c-fb736d382a12) | PaaS i Azure |
| 3.1.1 Gjennomfør jevnlig sårbarhetskartlegging. | 3.1 Oppdag og fjern kjente sårbarheter og trusler | 3. Oppdage | [A vulnerability assessment solution should be enabled on your virtual machines](https://portal.azure.com/#blade/Microsoft_Azure_Policy/PolicyDetailBlade/definitionId/%2Fproviders%2FMicrosoft.Authorization%2FpolicyDefinitions%2F501541f7-f7e7-4cd6-868c-4190fdad3ac9) | IaaS i Azure eller hybrid- og multisky med Azure Arc |
| 3.1.1 Gjennomfør jevnlig sårbarhetskartlegging. | 3.1 Oppdag og fjern kjente sårbarheter og trusler | 3. Oppdage | [Vulnerability assessment should be enabled on SQL Managed Instance](https://portal.azure.com/#blade/Microsoft_Azure_Policy/PolicyDetailBlade/definitionId/%2Fproviders%2FMicrosoft.Authorization%2FpolicyDefinitions%2F1b7aa243-30e4-4c9e-bca8-d0d3022b634a) | PaaS i Azure |
| 3.1.3 Benytt automatisert og sentralisert verktøy for å håndtere kjente trusler (som skadevare). | 3.1 Oppdag og fjern kjente sårbarheter og trusler | 3. Oppdage | [Endpoint protection should be installed on your machines](https://portal.azure.com/#blade/Microsoft_Azure_Policy/PolicyDetailBlade/definitionId/%2Fproviders%2FMicrosoft.Authorization%2FpolicyDefinitions%2F1b7aa243-30e4-4c9e-bca8-d0d3022b634a) | IaaS i Azure eller hybrid- og multisky med Azure Arc |
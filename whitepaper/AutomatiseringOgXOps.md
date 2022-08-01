# Automatisering og xOps

Mulighetene for automatisering i allmenn sky bidrar til å øke potensialet til DevSecOps og en xOps-tilnærming.

Uten automasjonsprosesser vil mange etablerings- og vedlikeholdsoppgaver måtte gjøres manuelt. Dette bidrar til at oppgavene tar lengere tid, og kan medføre at miljøene blir får flere feil enn det ville fått med automatiske prosesser.

Automatisering i seg selv ikke er målet, da feil bruk av automatisering kan skape like mange problemer som det løser. Derimot skal det påpekes at automatisering er en styrkemultiplikator som kan bidra til at oppgaver kan gjøres raskere og feilfritt.

De viktigste områdene der automasjon bidrar inkluderer

Konsistens: Skala- og stordriftsfordeler krever at systemer og løsninger etableres på en konsistent og enhetlig måte. Gjennom bruk av automasjon sikrer organisasjonen seg for at standarder følges og at like systemer forblir like, også over tid.

Felles metodeverk og plattform: Gjennom bruk av automasjon ser man at oppgaver som utføres andre steder i IT-miljøet eller organisasjonen kan gjenbruke de samme prinsippene som tas i bruk i allmenn sky. Dermed oppnår man etter hvert å gjennomføre samme metoder på tvers av plattformer og miljø, noe som er med til å forbedre organisasjonens verdi og leveransekraft.

Raskere utførelse og feilretting: Når man benytter automasjon og kodebasert infrastruktur vil tiden man får igjen fra manuelle prosesser kunne benyttes til mer produktive aktiviteter. Samtidig blir feilsøking enklere gitt at man har en baseline å forholde seg til, hva har gått feil underveis.

## xOps
Det er ikke bare tradisjonelle driftsprosesser (Operations – derav Ops) som er aktuelle for sky, men man ser at det er flere navn på moderne driftsformer som for eksempel AgileOps og DevOps/DevSecOps. I bunn og grunn betyr det en tettere knytning mellom utviklere, de som jobber med infrastrukturen og de som følger opp infrastrukturen og applikasjonene i etterkant. For å få opp hastigheten og kontrollen av dette kommer punktene under som en nødvendighet for å lykkes med xOps

Det viktigste med disse er at de er mer agile enn tradisjonelle driftsformer, og noen av metodene for å få opp takten samtidig som man øker tilgjengelighet og reduserer TTR (time to resolve) inkluderer:

* Høy grad av automatisering.
* Definere infrastruktur med script eller kode.
* Feiltolerant arkitektur.
* Resistente applikasjoner som tåler feil.

Dette er ikke noe nytt, men denne type metodikker gjør seg stadig mer aktuelle ved bruk av sky samtidig som hele skyplattformen er mulig å programmere mot; både som administrator og utvikler.

Med høy grad av automatisering kreves standarder, prinsipper og ikke minst forståelse som gjenspeiler seg i organisasjonens kultur. Det handler om hvordan en IT- eller utviklingsavdeling benytter de tilgjengelige verktøyene på best mulig måte, satt i et system som fungerer på tvers av roller og miljø i organisasjonen.

En annen grunn til at det er viktig å drive denne kulturendringen er å kunne senke listen for å få gjort endringer og publisert ny kode eller nye løsninger.

## Infrastruktur som kode / Infrastructure as code (IaC)

Det er ofte lett å opprette nye ressurser i en allmenn skytjeneste gjennom selvbetjeningsportaler. Det opprettes da gjerne manuelt, og manuelle prosesser kan lede til feil over tid. I tillegg vil manuelle prosesser ofte være dårligere dokumentert slik at når man skal gjenskape en løsning så vil den ikke bli gjenskapt helt likt.

Infrastruktur som kode (IaC), sørger for å opprette/provisjonere ressurser ved bruk av kode.

IaC, i kombinasjon med et system for versjonskontroll (typisk Git), gir oss fordeler som:

* Informasjon om hvem, hva og hvorfor en endring ble gjort.
* Det kan settes arbeidsflyter som f.eks. at en endring skal godkjennes av andre.
* Understøtter DevSecOps.
* Gjenbruke kode på tvers av miljøer (som dev, test, qa og prod) – og dermed få et helt likt miljø på tvers.
* Man kan enkelt opprette midlertidige miljøer for test, for så å rive det ned, noe som utnytter de økonomiske mulighetene som ligger i bruk av allmenn sky.
* Enklere etablere miljøet på nytt ved et disaster recovery-scenario.
* Ved et konfigurasjonsendring som ikke fungerte som tiltenkt kan du rulle tilbake til en tidligere versjon av koden.
* Vi har full oversikt over endringer, og vi ser hva som er gjort av hvem når.
* Vi ser ofte at man får et ryddigere miljø, der navnestandarder følges i større grad og valg gjort i infrastrukturen er i større grad gjennomtenkte.

### Valg av verktøy

Det finnes flere løsninger/språk for infrastruktur som kode. Noen av de mest populære er:

* Terraform (cloud agnostic)
* Pulumi (cloud agnostic)
* Bicep (kun for Azure)

## Prinsipper for bruk av infrastruktur som kode

For at infrastruktur som kode (IaC) skal fungere optimalt i organisasjonen bør noen prinsipper følges:

* *Lagre koden i et system for versjonshåndtering* (Version Control System – VCS). Dette er kilden og dokumentasjonen over infrastrukturen. Endringer i infrastrukturen er drevet av endringer gjort i versjonshåndteringen. På denne måten får vi:
    * Vi ser hvem som har gjort hva, og aller helst med en kommentar om hvorfor.
    * En kollega kan gå gjennom endringen og godkjenne før endringen rulles ut.
    * Det er ofte lett å endre systemet tilbake.
    * Det er lett for alle i teamet å se hvilke endringer som gjøres.
    * Når en endring er gjennomført kan det automatisk trigge andre hendelser. For eksempel en trigger som kjører en automatisk test av at systemet fungerer som planlagt.

* *Bygg alt med kode*. Ikke ta snarveier ved å lage noe manuelt. Man vil da miste fordelene med å få en fullstendig oversikt ved å se på koden.
    * Lås gjerne ned muligheten for å endre konfigurasjon og etablere nye ressurser ved å la brukerne kun ha lesetilgang til miljøet. Prosessen for infrastruktur som kode bør kjøre som en service-konto i en eller annen form.

* *Dokumenter minimumet*. For å hindre at dokumentasjonen blir utdatert, dokumenter bare det aller nødvendigste av infrastrukturen andre steder. Koden er alltid den oppdaterte dokumentasjonen.

* *Benytt organisasjonens prefererte verktøy for infrastruktur som kode*. Ved at alle benytter det samme kan enklere dele kunnskap, arbeidsmetodikk og jobbe på tvers av teams. Bli også enig om et sett med standarder for navngiving og struktur.

* Gjør små endringer, istedenfor store bolker med endringer. Noen fordeler:
    * Lettere å teste
    * Lettere å rulle tilbake endringen
    * Lettere å feilsøke
    * Et lite problem kan forsinke en stor utrulling. Når man tar det i mindre bolker, kan fortsatt andre endringer gjennomføres.
    * Det er mer motiverende å gjøre unna små endringer, fremfor store endringer som kan føles uoverkommelig.

## Konfigurasjonshåndtering

Konfigurasjonshåndtering, eller Configuration management, håndterer konfigurasjonsstyring på OS- og applikasjonsnivå. Dette sørger for førstegangsoppsett av OS og applikasjon og senere konfigurasjonsendringer.

Eksempel på slike verktøy:

* Chef
* Puppet
* Ansible
* Microsoft DSC (PowerShell Desired State Configuration)

Disse verktøyene integrerer godt med løsninger for infrastruktur som kode og det bør være et mål at tjenester som har behov for VM-er i sky benytter en form for automatisering av konfigurasjonen.

\newpage
# Landingssoner 

Landingssoner i Azure består av flere abonnementer i satt opp på en skalerbar måte og som samtidig ivaretar sikkerhet og tilhørende tjenester som nettverk og identitet.

Landingssoner muliggjør migrering, modernisering og innovasjon i stor-skala i Azure.

Sonene som etableres tar høyde for alle plattformressurser som er nødvendig for å understøtte en bedrift`s applikasjons-portefølje og differensierer ikke mellom infrastruktur som tjeneste og plattform som en tjeneste.

![Landingssone](illustrations/lz-design.png)

# Tilgjengelighet (SLA)
- Høy tilgjengelighet (E.g - Konsumenttjeneste)
99.99 eller 99.95% oppetid. Noe nedetid (minutter) per år aksetabelt. Redundante server(e) og lagringskopier - men ikke på tvers av datasentere. 

- Meget høy tilgjengelighet (e.g. pasientsystem)
99.99% eller høyere. Redundante servere og kopier av data på tvers av datasentere (med mer enn 10 km avstand). 

- Unntakssituasjon (Disaster scenario)
En hel region går ned og blir utilgjengelig. 

- Fullstendig suverenitet/autonomitet (autonomity/soveriginity)
Skyleverandør går konkurs, Norge mister all kommunikasjon med omverden, systemer som må fungere uavhengig av skyleverandør.

# Gjenopprettingspunkt (RPO)


# Tradisjonell sonemodell 
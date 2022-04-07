# Klassifisering
 - Ikke sensitivt (Ikke PII)
 - Sensitivt (PII mm.)
 - Begrenset (Sikkerhetsloven)
 - Konfidensielt (Sikkerhetsloven)
 - Hemmelig (Sikkerhetsloven)
 - Strengt hemmelig (Sikkerhetsloven)

## Klassifiseringmatrise for applikasjoner
Her er et forsøk på hvordan vi kan tenke rundt skille av applikasjoner:

- Publikumstjeneste (applikasjon) (Internet exposed)
- Intern applikasjon (interne ansatte, lokalt LAN eller VPN)
- Ikke sammfunnskritisk (tåler noe nedetid) 
- Sammfunnskritisk - delte tjenester (nasjonale)

Sammfunnskritiske tjenester som må kjøre og være tilgjengelig som er delt på tvers av lokasjoner/uavhengig av lokasjon.

Sluttbrukere/systemer bruker internet (VPN eller MPLS).

- Sammfunnskritiske - lokale tjenster (edge)
Sammfunnskritiske tjenester må fungere i nødssituasjon hvor deler faller ut og tåler lite/eller ingen nedetid eller er svært sensitive til latens.

Sluttbrukere/systemer befinner seg lokalt (e.g. et sykehus/sykebil) mm.

# Risikoklassifisering av systemer
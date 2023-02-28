# Service-based Economy

Il Trend dell'economia è passato da essere basato sui *beni* a essere basato sui *servizi*. (Everything as a Service)

## Contratto del servizio

Al customer non interessa sapere tanto come è implementato il servizio che sta utilizzando, ma dovrebbe scegliere il servizio in base al contratto che è stato presentato dal provider di esso. 

# QoS e SLAs

## QoS

La QoS (Quality of Service) è un insieme di meccanismi molto importanti utilizzati dalle reti informatiche per garantire un livello di prestazioni adeguato a determinati flussi di traffico. Questo è particolarmente importante quando si offre un servizio in tempo reale (ex. chiamate vocali/video) dove la qualità del servizio proposta influenza l'esperienza dell'utente finale. 

La QoS si concentra su diverse metriche di prestazione, tra cui la latenza, la banda, la perdita di pacchetti, la congestione e il jitter (irregolarità della latenza).

## SLAs

Il SLA (Service Level Agreement) è un accordo contrattuale tra un fornitore di servizi e il cliente che stabilisce i livelli di servizio garantiti, i requisiti operativi e le metriche di prestazione richieste. L'obbiettivo dello SLA è di definire i termini e le condizioni del servizio, nonchè le conseguenze in caso di violazione degli impegni presi. 

Le violazioni possono essere risarcite a stampo economico attraverso sconti al servizio, crediti, risarcimento danni subiti dal cliente o addirittura la risoluzione del contratto.  

#### Google Compute Engine SLA
Il Covered Services fornirà al cliente una Monthly Uptime (MUP) Percentage come segue (Service Level Objective):	
 | Covered Services  | MUP     |
 | ----------------- | ------- |
 | A single instance | >=99.5% |

Se Google non soddisfa la SLO e se il customer rispetta i propri obblighi ai sensi del presente SLA, il customer avrà diritto a ricevere i crediti finanziari come descritti in seguito:

| MUP               | Percentage of monthly bill for a single instance in the Region that did not meet SLO that will be credited to customer's future monthly bills |
| ----------------- | --------------------------------------------------------------------------------------------------------------------------------------------- |
| 95.00% - < 99.50% | 10%                                                                                                                                           |
| 90.00% - < 95.00% | 25%                                                                                                                                           |
| < 90.00%          | 100%                                                                                                                                          |

- *MUP*: minuti totali in un mese, meno il numero di minuti di inattività subiti da tutti i periodi di inattività (Downtime Period) in un mese, diviso per il numero totale di minuti in un mese
- *Downtime Period*: Indica un periodo di uno o più minuti di downtime. I minuti parziali o i tempi di inattività intermittenti per un periodo inferiore a un minuto non vengono conteggiati ai fini di eventuali Downtime Period. 

Il cliente dovrà richiedere il risarcimento portando dei log a Google dove dimostra la perdita di connessione e quanto tempo è stato persop entro 60 giorni dall'accaduto, sennò rinucnia volontariamente al rimborso in crediti.

# Cloud Computing 101

Il servizio richiede cambiamenti col tempo, ma nessuno sa prevedere come.

*Overprovisioning*: Garantire in anticipo l'approvigionamento per i picchi di domanda previsti porta a uno spreco di risorse.

*Underprovisioning*: Se il picco viene sottovalutato, l'Underprovisioning potrebbe accidentalmente allontanare gli utenti in eccesso. I due costi (O/U) sono gravi alla stessa maniera, ma nell'Under gli utenti respinti generano entrate pari a zero e potrebbero addirittura non tornare mai più.

## Idee Chiave

- Pooling efficiente di infrastutture virtuali on-demand autogestite, consumed as a service.
- Fornitura di risorse virtualizzate scalabili dinamicamente su internet a più client
- Disaccoppiamento della fornitura di servizi informatici dalla tecnologia sottostante

<img src=https://i.imgur.com/mMT8wpj.png width=70% />

> Modelli di servizi:
> [[IaaS]]
> [[FaaS]]
> [[PaaS]]
> [[SaaS]]

![](https://i.imgur.com/qOwYUkD.png)


# Possibili Ostacoli

- *Data Confidentiality*: 
	- Dove saranno storati i miei dati?
	- Sarà garantita l'integrità e la privacy?
	- Come fare se ci dovesse essere un problema?
- *Business Continuity/ Service Availability*:
	- Cosa succede se il mio fornitore Cloud fallisce?


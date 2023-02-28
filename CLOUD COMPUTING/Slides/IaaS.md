# Server virtualization & hypervisors

## Definizione di virtualizzazione

- La Visrtualizzazione è un "abstract layer"
- Il SO non è più legato al dispositivo (PC/Server) su cui sta girando
- Il SO non è installato direttamente sull'HardWare (HW)

## Virtualizzazione dei Server

- Livello di virtualizzazione tra il server fisico e il sistema operativo che normalmente installeresti
- Macchine virtuali: dove installi il SO e le App che di solito installeresti

## Definizone di Hypervisor

- Crea il livello di vitualizzazione
- Contiene il Vistual Machine Manager (VMM)

## Hypervisor di Tipo 1 VS Tipo 2

- Tipo 1 caricato direttamente sull' HW, Tipo 2 caricato su un SO che gira su HW
- Il tipo 2 ha un rapporto di consolidamento maggiore/inferiore rispetto al tipo 1
- Tipo 1 per Data Center, Tipo 2 su Desktop/laptop

# IaaS/Compute: Amazon EC2

## Amazon Elastic Compute Cloud (EC2)

- Mette a disposizione server virtuali (istanze) in modo semplice, veloce ed economico 
- Scelta tipo istanza e template da utilizzare (Windows/Linux) e numero istanze con AWS management console (o librerie SDK)    
- Ampia gamma di istanze (CPU, memoria, storage, GPU)   
- Opzioni di pagamento: on demand, istanze riservate, istanze spot   
- Sicurezza (Virtual Private Cloud - VPC) 
- Storage persistente: Amazon Elastic Block Store (EBS)   
- Autoscaling

# IaaS market share

![](https://i.imgur.com/BYKiPPH.png)

# IaaS/Storage: Amazon S3

## Amazon Simple Sorage Server (S3)

- Fornisce uno storage sicuro e facile da usare • "Bucket"
- Diverse classi di memorizzazione (standard / standard infrequent access / glacier)  
- Controllo configurabile accesso ai dati

## Amazon Elastic Block Store (EBS)

- Volumi di storage a blocchi persistenti da utilizzare con le istanze Amazon EC2 nel cloud AWS  
- Ogni volume Amazon EBS viene replicato automaticamente all'interno della propria zona di disponibilità per proteggerti dai guasti dei componenti, offrendo elevata disponibilità e durabilità
- Progettato per i carichi di lavoro delle applicazioni che traggono vantaggio dalla messa a punto di prestazioni, costi e capacità (ad es. analisi dei big data, elaborazione dei flussi, data warehousing)

# Dropbox

> What if ...  
  we provide free storage to everybody?

Per i primi otto anni della sua vita, Dropbox ha archiviato miliardi e miliardi di file su Amazons S3

## Dropbox’s exodus

- Tra il 2014 e il 2016, Dropbox ha costruito la propria vasta rete di computer e ha spostato il proprio servizio su una nuova generazione di macchine progettate dai propri ingegneri
- Sfide tecniche e logistiche:
	- Hardware personalizzato ("Diskotech") contenente un petabyte di dati
	- Nuovo codice ("Magic Pocket")
	- Muovere così tanti dati:
		- Petabyte di dati su Internet (» 1 giorno per trasferire 4 petabyte di dati)
	- Spostare così tante macchine nei data center:
		- Installazione di 40-50 rack di hardware al giorno
		- Incidenti intempestivi: in un periodo di ventiquattro ore, i camion che trasportavano macchine ai data center Dropbox in diverse parti del paese hanno avuto incidenti
	- Necessità di completare l'esodo prima della scadenza dei contratti principali con Amazon (per evitare il rinnovo)
	- è stato come cambiare una gomma mentre stai ancora guidando
	- Magic Pocket non si adattava perfettamente al nuovo hardware, Magic Pocket è stato ricostruito
	- Dropbox ce l'ha fatta!

## Revenue
| Dropbox annual revenue | Millions of $ |
| ---------------------- | ------------- |
| 2021                   | $2,158        |
| 2020                   | $1,946        |
| 2019                   | $1,661        |
| 2018                   | $1,329        |
| 2017                   | $1,107        |
| 2016                   | $845          |
| 2015                   | $604          |

## Leading vendors' share in the file sharing software market worldwide in 2022

<img src=https://i.imgur.com/6x7kPdJ.png width=70% /> 




# Virtualization and containers

## Da VMs a Containers

### VMs:
- Virtualizzazione dei server
- Più macchine virtuali (con proprio sistema operativo) che girano sullo stesso server
- Hypervisor di Tipo 1 caricato direttamente sull'HW

### Containers:
Idea chiave dei contenitori: sfruttare la capacità del kernel del sistema operativo di consentire più istanze isolate dello spazio utente:
- (+) meno risorse utilizzate
- (+) più veloce a partire
- (-) condividono lo stesso [[OS]]

## Quanto son vecchi i containers?

- Prima di tutto c'era il comando `chroot` di Unix che garantiva una forma semplice di isolamento dei filesystem
- Nel 1988 *FreeBSD* estente `chroot` con `jail` 
- Nel 2005 *Google* iniziò a sviluppare CGroups per il kernel di Linux e ha iniziato a muovere le sue infrastutture nei Container
- Nel 2013 Docker implementò anche il trasferimento di [[images]] e una UI semplice.

La ==piattaforma== Docker consiste nel:
- *Docker Engine* (per creare e eseguire container)
- *Docker Hub* (per distribuire container)

# Docker

## Cos'è Docker

Docker è un' applicazione che ci permette di far girare applicazioni in ambienti isolati.
Docker ci consente di sviluppare ed eseguire applicazioni portatili sfruttando i container.

Docker utilizza la virtualizzazione basata sui container per far girare istanze isolate ospiti sul [[OS]].
Le componenti software sono impacchettate dentro [[images]], utilizzate come read-only template per creare e eseguire container.
[[Volumes]] esterni possono essere montati per assicurare persistenza dei dati.

> “Build, ship, and run any app, anywhere”

## Docker images

- Template read-only usati per creare container
- Storato in un [[registry]] di Docker privato
	- i registry sono strutturati in repository
	- ogni repo contiene un set di [[images]] 
	- le immagini sono identificate dalla coppia -> repository:tag
	- [Docker Hub](https://hub.docker.com/)

![](https://i.imgur.com/injY8VJ.png)

[Tutorial Docker](https://www.youtube.com/watch?v=YFl2mCHdv24)

## Vantaggi del Docker
- Stesso ambiente
- Progetti Sandbox
- Funziona bene

## Vantaggi Container
- Più leggero e veloce che far girare una VM
- Condivide il SO
- Images definite da Dockerfile
- Build and run

# Swarm Mode

I nodi dello Swarm possono agire come managers (delegando compiti ai lavoratori) e workers (eseguendo i compiti loro assegnati)

È possibile definire lo stato desiderato dei vari servizi nello stack dell'applicazione, incluso il numero di attività da eseguire in ogni servizio

I nodi Swarm Manager assegnano a ogni servizio nello Swarm un nome DNS univoco e bilanciano il carico dei container in esecuzione

I nodi Swarm Manager monitorano costantemente lo stato del cluster e riconciliano eventuali differenze tra lo stato effettivo e lo stato desiderato espresso
- Ad esempio, se configuri un servizio per eseguire 10 repliche di un contenitore e una macchina worker che ospita due di tali repliche si arresta in modo anomalo, vengono create due nuove repliche e assegnate ai worker in esecuzione e disponibili

> Quindi se il lavoro di un Manager fallisce, viene assegnato il suo lavoro ad un altro manager
> Se un Worker fallisce, viene assegnato il suo container ad un altro Worker


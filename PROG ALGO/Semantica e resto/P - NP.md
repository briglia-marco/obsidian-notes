# Definizioni 

## Classe P

Algoritmo poliniomiale: 
- ∃ 2 costanti -> c, n0 > 0 tale che il numero di celle di memoria utilizzate è al più n^c ∀ input di dim=n e ∀ n>n0

> La classe P è la classe dei problemi risolvibili in *tempo poliniomiale* delle dimensione n dell'istanza di ingresso

## Classe NP

Classe di problemi decisionali che ammettono [[certificati]] verificabili in tempo poliniomiale

- In un problema decisionale siamo interessati a verificare se un'istanza del problema soddisfa una certa proprietà
- Si richiede di fornire anche un oggetto y, dipendente da x e dal problema, che attesti il fatto che x rispetti la proprietà

# NP completi e NP-Arduo

se ∃ problema P che risolve uno solo di questi problemi => P=NP
==> o tutti o nessuno

## NP-Completo

Un prolema decisionale P1 = NP-Completo se:
- P1 ∈ a NP
- P1 => NP-Arduo

## NP-Arduo

Un problema decisionale P1 = NP-Arduo se:
		- ∀q ∈ NP -> riducibile a P1
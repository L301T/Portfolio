# Descrizione del progetto

Progettazione e simulazione di un’infrastruttura di rete per una piccola azienda in espansione, composta da una sede principale (LAN rossa) e un ufficio distaccato (LAN verde), interconnessi tramite collegamento WAN simulato.

La topologia è stata realizzata in Cisco Packet Tracer con l’obiettivo di garantire:

- Comunicazione interna nella stessa sede (intranet locale).
- Comunicazione affidabile tra le due sedi, compreso l’accesso ai servizi di rete (es. server) da qualsiasi endpoint.

## Componenti principali

- Router per ciascuna sede con configurazione IP e instradamento statico.
- Switch per segmentare la rete locale e ottimizzare la distribuzione del traffico.
- Server centralizzato presso la sede principale (servizi condivisi).
- Stampanti di rete per entrambe le sedi.
- WAN simulata per collegamento tra router.

## Configurazione IP

- Sede principale: `192.168.1.0/24`
- Ufficio distaccato: `192.168.2.0/24`
- Collegamento WAN: rete point-to-point `192.168.12.0/30`

## Risultati dei test

- Ping riuscito tra i dispositivi delle due sedi (es. `192.168.1.3 → 192.168.2.2`).
- Nessuna perdita di pacchetti, tempi di risposta medi inferiori a 5 ms.

## Competenze dimostrate

- Progettazione topologia di rete.
- Configurazione di router e switch in Packet Tracer.
- Gestione subnetting e instradamento statico.
- Test e troubleshooting con strumenti di diagnostica (Ping).

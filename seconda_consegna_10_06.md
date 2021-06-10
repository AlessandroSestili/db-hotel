# Query con JOIN

<!-- 1.Come si chiamano gli ospiti che hanno fatto più di due prenotazioni? -->
SELECT `ospite_id` , COUNT(`ospite_id`) AS `numero_prenotazioni`, `ospiti`.`name` , `ospiti`.`lastname` 
FROM `prenotazioni_has_ospiti`

JOIN `ospiti`
ON `ospiti`.`id` = `ospite_id`

GROUP BY `ospite_id`

HAVING `numero_prenotazioni` > 2

<!-- 2.Stampare tutti gli ospiti per ogni prenotazione -->
SELECT `ospite_id` , `ospiti`.`name` , `ospiti`.`lastname`  
FROM `prenotazioni_has_ospiti`

JOIN `ospiti`
ON `ospiti`.`id` = `ospite_id`

<!-- 3.Stampare Nome, Cognome, Prezzo e Pagante per tutte le prenotazioni fatte a Maggio 2018 -->

<!-- 4.Fai la somma di tutti i prezzi delle prenotazioni per le stanze del primo piano -->

<!-- 5.Prendi i dati di fatturazione per la prenotazionecon id=7 -->

<!-- 6.Le stanze sono state tutte prenotate almeno una volta? 
(Visualizzare le stanze non ancora prenotate) -->
# QUERY CON "JOIN"

# <!-- 1.Come si chiamano gli ospiti che hanno fatto più di due prenotazioni? -->
SELECT `ospite_id` , COUNT(`ospite_id`) AS `numero_prenotazioni`, `ospiti`.`name` , `ospiti`.`lastname` 
FROM `prenotazioni_has_ospiti`

JOIN `ospiti`
ON `ospiti`.`id` = `ospite_id`

GROUP BY `ospite_id`

HAVING `numero_prenotazioni` > 2


# <!-- 2.Stampare tutti gli ospiti per ogni prenotazione -->
SELECT `ospite_id` , `ospiti`.`name` , `ospiti`.`lastname`  
FROM `prenotazioni_has_ospiti`

JOIN `ospiti`
ON `ospiti`.`id` = `ospite_id`


# <!-- 3.Stampare Nome, Cognome, Prezzo e Pagante per tutte le prenotazioni fatte a Maggio 2018 -->
#3.Stampare Nome, Cognome, Prezzo e Pagante per tutte le prenotazioni fatte a Maggio 2018
SELECT `name` , `lastname` , `price` , `prenotazioni`.`created_at`
FROM `paganti`
JOIN `pagamenti`
ON `paganti`.`id` = `pagante_id`
JOIN `prenotazioni`
ON `pagamenti`.`prenotazione_id` = `prenotazioni`.`id`
 <!-- WHERE `prenotazioni`.`created_at` = DATE("2018-05-20") -->

<!-- 4.Fai la somma di tutti i prezzi delle prenotazioni per le stanze del primo piano -->

<!-- 5.Prendi i dati di fatturazione per la prenotazionecon id=7 -->

<!-- 6.Le stanze sono state tutte prenotate almeno una volta? 
(Visualizzare le stanze non ancora prenotate) -->






# QUERY CON "GROUP BY"

# <!--  1.Conta gli ospiti raggruppandoli per anno di nascita -->
SELECT YEAR(`date_of_birth`) AS `year`, COUNT (`id`) AS `ospiti_totali`
FROM `ospiti`
GROUP BY `year`

# <!--  2.Somma i prezzi dei pagamenti raggruppandoli per status -->
SELECT SUM(`price`)
FROM `pagamenti`
GROUP BY `status`

# <!-- 3.Conta quante volte è stata prenotata ogni stanza -->
SELECT `stanza_id`, COUNT (`id`) AS `prenotazioni_totali` DESC
FROM `prenotazioni`
GROUP BY `stanza_id`

# <!-- 4.Fai una analisi per vedere se ci sono ore in cui leprenotazioni sonopiù frequenti -->
SELECT HOUR(`created_at`) AS `ora` , COUNT(`id`) AS `prenotazioni`
FROM `prenotazioni`
GROUP BY `ora`
ORDER BY `prenotazioni` DESC

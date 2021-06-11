# ------------------------------ QUERY CON "JOIN ------------------------------"

# <!-- 1.Come si chiamano gli ospiti che hanno fatto più di due prenotazioni? -->
SELECT `ospite_id` , COUNT(`ospite_id`) AS `numero_prenotazioni`, `ospiti`.`name` , `ospiti`.`lastname` 
FROM `prenotazioni_has_ospiti`

INNER JOIN `ospiti`
ON `ospiti`.`id` = `ospite_id`

GROUP BY `ospite_id`

HAVING `numero_prenotazioni` > 2


# <!-- 2.Stampare tutti gli ospiti per ogni prenotazione -->
SELECT `ospite_id` , `ospiti`.`name` , `ospiti`.`lastname`  
FROM `prenotazioni_has_ospiti`

INNER JOIN `ospiti`
ON `ospiti`.`id` = `ospite_id`


# <!-- 3.Stampare Nome, Cognome, Prezzo e Pagante per tutte le prenotazioni fatte a Maggio 2018 -->
SELECT `name` , `lastname` , `price` , `prenotazioni`.`created_at`
FROM `paganti`

JOIN `pagamenti`
ON `paganti`.`id` = `pagante_id`

JOIN `prenotazioni`
ON `pagamenti`.`prenotazione_id` = `prenotazioni`.`id`

WHERE YEAR(`prenotazioni`.`created_at`) = 2018
    AND MONTH(`prenotazioni`.`created_at`) = 5

# <!-- 4.Fai la somma di tutti i prezzi delle prenotazioni per le stanze del primo piano -->
SELECT
FROM

LEFT JOIN `prenotazioni`
ON `prenotazioni`.`id` = `pagamenti`.`prenotazione_id`

LEFT JOIN `stanze`
ON `prenotazioni`.`stanza_id` = `stanze`.`id`

WHERE `stanze` . `floor` = 1


# <!-- 5.Prendi i dati di fatturazione per la prenotazionecon id=7 -->
SELECT *
FROM `pagamenti`

LEFT JOIN `paganti`
ON `pagamenti`.`pagante_id` = `paganti`.`id`

WHERE `pagamenti`.`prenotazione_id` = 7

# <!-- 6.Le stanze sono state tutte prenotate almeno una volta? (Visualizzare le stanze non ancora prenotate)
SELECT *
FROM `prenotazioni`

RIGHT JOIN `stanze`
ON `stanze`.`id` = `prenotazioni`.`stanza_id`

WHERE `prenotazione`.`id` IS NULL










# ------------------------------ QUERY CON "GROUP BY ------------------------------"

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

# <!-- 5.Quante prenotazioni ha fatto l’ospite che ha fattopiùprenotazioni? (quante, non chi!) -->
SELECT `ospite_id` , COUNT(*) AS `prenotazioni`
FROM `prenotazioni_has_ospiti`

GROUP BY `ospite_id`
GROUP BY `prenotazioni` DESC

LIMIT 1

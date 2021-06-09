# 1. Seleziona tutti gli ospiti che sono stati identificati con la carta di identità
SELECT `document_type` FROM `ospiti` WHERE `document_type` = 'CI'

# 2. Seleziona tutti gli ospiti che sono nati dopo il 1988
SELECT `date_of_birth` FROM `ospiti` WHERE `date_of_birth` > "1988"

# 3. Seleziona tutti gli ospiti che hanno più di 20anni (al momento dell’esecuzione della query)
SELECT `date_of_birth` FROM `ospiti` WHERE `date_of_birth` > "2001"
# Non so se questo punto l'ho svolto bene... "Al momento dell'esecuzione, mi mette il dubbio! Rivedere!




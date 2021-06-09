# 1. Seleziona tutti gli ospiti che sono stati identificati con la carta di identità
SELECT `document_type` FROM `ospiti` WHERE `document_type` = 'CI'

# 2. Seleziona tutti gli ospiti che sono nati dopo il 1988

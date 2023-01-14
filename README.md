SELECT W.ID,P.AGE,W.coins_needed,W.POWER
FROM Wands AS W 
JOIN Wands_Property AS P
ON W.CODE=P.CODE
WHERE P.is_evil =0 AND W.coins_needed=(SELECT MIN(coins_needed)
                                      FROM Wands AS X
                                       JOIN Wands_Property AS Y
                                      ON X.CODE=Y.CODE
                                      WHERE X.POWER=W.POWER AND Y.AGE=P.AGE
                                     )
ORDER BY W.POWER DESC,P.AGE DESC;                                     

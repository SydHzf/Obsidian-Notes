___
- Derivative metrics
- DoD/ WoW / MoM / YoY
 - friend with rolling and average
 - Keyword here is rolling
- Mostly solved using window functions
     FUNCTION OVER (PARTITION BY keys ORDER BY sort ROWS BETWEEN n PRECEDING
     AND CURRENT ROW)

 
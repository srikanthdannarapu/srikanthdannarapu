SELECT 
  100 * COUNT(CASE 
                 WHEN REGEXP_LIKE(BANKNET_REF_NUM, '^[A-Z]{3}[0-9A-Z]{6}$') THEN 1 
                 ELSE NULL 
               END) / COUNT(*) AS "Pattern1Percentage",
  100 * COUNT(CASE 
                 WHEN REGEXP_LIKE(BANKNET_REF_NUM, '^[A-Z]{3}[0-9A-Z]{6}[0-9]{4}$') THEN 1 
                 ELSE NULL 
               END) / COUNT(*) AS "Pattern2Percentage"
FROM your_table;



SELECT BANKNET_REF_NUM
FROM your_table
WHERE NOT REGEXP_LIKE(BANKNET_REF_NUM, '^[A-Z]{3}[0-9A-Z]{6}$') AND NOT REGEXP_LIKE(BANKNET_REF_NUM, '^[A-Z]{3}[0-9A-Z]{6}[0-9]{4}$');

SELECT
  100 * SUM(CASE WHEN REGEXP_LIKE(SUBSTR(BANKNET_REF_NUM, 1, 3), '^[A-Z]{3}$')
                AND REGEXP_LIKE(SUBSTR(BANKNET_REF_NUM, 4), '^[A-Z0-9]{6}$')
             THEN 1 ELSE 0 END) / COUNT(*) AS "Percentage"
FROM your_table;


### MDM REPORT QUERY


#### Meter row and column name profile type wise
```sql
SELECT
meter_number,
COUNT(DISTINCT CASE WHEN `type` = 'BILLING' THEN slot_time END) AS BILLING,
COUNT(DISTINCT CASE WHEN `type` = 'EVENT_CTRL' THEN slot_time END) AS EVENT_CTRL,
COUNT(DISTINCT CASE WHEN `type` = 'EVENT_CURRENT' THEN slot_time END) AS EVENT_CURRENT,
COUNT(DISTINCT CASE WHEN `type` = 'EVENT_OTHER' THEN slot_time END) AS EVENT_OTHER,
COUNT(DISTINCT CASE WHEN `type` = 'EVENT_POWER' THEN slot_time END) AS EVENT_POWER,
COUNT(DISTINCT CASE WHEN `type` = 'EVENT_TRANSACTION' THEN slot_time END) AS EVENT_TRANSACTION,
COUNT(DISTINCT CASE WHEN `type` = 'EVENT_VOLTAGE' THEN slot_time END) AS EVENT_VOLTAGE,
COUNT(DISTINCT CASE WHEN `type` = 'INSTANT' THEN slot_time END) AS INSTANT,
COUNT(DISTINCT CASE WHEN `type` = 'LOAD' THEN slot_time END) AS `LOAD`,
COUNT(DISTINCT CASE WHEN `type` = 'MIDNIGHT' THEN slot_time END) AS MIDNIGHT
FROM sense_hes_intelli_smart_prod.mdm_profile_data_audit
WHERE slot_time >= '2026-05-04 00:00:00'
AND slot_time < '2026-05-05 00:00:00'

AND status = 'SUCCESS'

GROUP BY

meter_number

ORDER BY

meter_number;
```


#### Group by meter_number and type

```sql
SELECT

meter_number,

`type`,

COUNT(*) AS data_count

FROM sense_hes_intelli_smart_prod.mdm_profile_data_audit

WHERE slot_time >= '2026-05-04 00:00:00'

AND slot_time < '2026-05-05 00:00:00'

AND status = 'SUCCESS'

GROUP BY

meter_number,

`type`

ORDER BY

meter_number,

`type`;
```
<!--stackedit_data:
eyJoaXN0b3J5IjpbMTg4MDU0NjU0M119
-->
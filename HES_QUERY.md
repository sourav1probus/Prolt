---


---

<h3 id="mdm-report-query">MDM REPORT QUERY</h3>
<h4 id="meter-row-and-column-name-profile-type-wise">Meter row and column name profile type wise</h4>
<pre class=" language-sql"><code class="prism  language-sql"><span class="token keyword">SELECT</span>
meter_number<span class="token punctuation">,</span>
<span class="token function">COUNT</span><span class="token punctuation">(</span><span class="token keyword">DISTINCT</span> <span class="token keyword">CASE</span> <span class="token keyword">WHEN</span> <span class="token punctuation">`</span><span class="token keyword">type</span><span class="token punctuation">`</span> <span class="token operator">=</span> <span class="token string">'BILLING'</span> <span class="token keyword">THEN</span> slot_time <span class="token keyword">END</span><span class="token punctuation">)</span> <span class="token keyword">AS</span> BILLING<span class="token punctuation">,</span>
<span class="token function">COUNT</span><span class="token punctuation">(</span><span class="token keyword">DISTINCT</span> <span class="token keyword">CASE</span> <span class="token keyword">WHEN</span> <span class="token punctuation">`</span><span class="token keyword">type</span><span class="token punctuation">`</span> <span class="token operator">=</span> <span class="token string">'EVENT_CTRL'</span> <span class="token keyword">THEN</span> slot_time <span class="token keyword">END</span><span class="token punctuation">)</span> <span class="token keyword">AS</span> EVENT_CTRL<span class="token punctuation">,</span>
<span class="token function">COUNT</span><span class="token punctuation">(</span><span class="token keyword">DISTINCT</span> <span class="token keyword">CASE</span> <span class="token keyword">WHEN</span> <span class="token punctuation">`</span><span class="token keyword">type</span><span class="token punctuation">`</span> <span class="token operator">=</span> <span class="token string">'EVENT_CURRENT'</span> <span class="token keyword">THEN</span> slot_time <span class="token keyword">END</span><span class="token punctuation">)</span> <span class="token keyword">AS</span> EVENT_CURRENT<span class="token punctuation">,</span>
<span class="token function">COUNT</span><span class="token punctuation">(</span><span class="token keyword">DISTINCT</span> <span class="token keyword">CASE</span> <span class="token keyword">WHEN</span> <span class="token punctuation">`</span><span class="token keyword">type</span><span class="token punctuation">`</span> <span class="token operator">=</span> <span class="token string">'EVENT_OTHER'</span> <span class="token keyword">THEN</span> slot_time <span class="token keyword">END</span><span class="token punctuation">)</span> <span class="token keyword">AS</span> EVENT_OTHER<span class="token punctuation">,</span>
<span class="token function">COUNT</span><span class="token punctuation">(</span><span class="token keyword">DISTINCT</span> <span class="token keyword">CASE</span> <span class="token keyword">WHEN</span> <span class="token punctuation">`</span><span class="token keyword">type</span><span class="token punctuation">`</span> <span class="token operator">=</span> <span class="token string">'EVENT_POWER'</span> <span class="token keyword">THEN</span> slot_time <span class="token keyword">END</span><span class="token punctuation">)</span> <span class="token keyword">AS</span> EVENT_POWER<span class="token punctuation">,</span>
<span class="token function">COUNT</span><span class="token punctuation">(</span><span class="token keyword">DISTINCT</span> <span class="token keyword">CASE</span> <span class="token keyword">WHEN</span> <span class="token punctuation">`</span><span class="token keyword">type</span><span class="token punctuation">`</span> <span class="token operator">=</span> <span class="token string">'EVENT_TRANSACTION'</span> <span class="token keyword">THEN</span> slot_time <span class="token keyword">END</span><span class="token punctuation">)</span> <span class="token keyword">AS</span> EVENT_TRANSACTION<span class="token punctuation">,</span>
<span class="token function">COUNT</span><span class="token punctuation">(</span><span class="token keyword">DISTINCT</span> <span class="token keyword">CASE</span> <span class="token keyword">WHEN</span> <span class="token punctuation">`</span><span class="token keyword">type</span><span class="token punctuation">`</span> <span class="token operator">=</span> <span class="token string">'EVENT_VOLTAGE'</span> <span class="token keyword">THEN</span> slot_time <span class="token keyword">END</span><span class="token punctuation">)</span> <span class="token keyword">AS</span> EVENT_VOLTAGE<span class="token punctuation">,</span>
<span class="token function">COUNT</span><span class="token punctuation">(</span><span class="token keyword">DISTINCT</span> <span class="token keyword">CASE</span> <span class="token keyword">WHEN</span> <span class="token punctuation">`</span><span class="token keyword">type</span><span class="token punctuation">`</span> <span class="token operator">=</span> <span class="token string">'INSTANT'</span> <span class="token keyword">THEN</span> slot_time <span class="token keyword">END</span><span class="token punctuation">)</span> <span class="token keyword">AS</span> INSTANT<span class="token punctuation">,</span>
<span class="token function">COUNT</span><span class="token punctuation">(</span><span class="token keyword">DISTINCT</span> <span class="token keyword">CASE</span> <span class="token keyword">WHEN</span> <span class="token punctuation">`</span><span class="token keyword">type</span><span class="token punctuation">`</span> <span class="token operator">=</span> <span class="token string">'LOAD'</span> <span class="token keyword">THEN</span> slot_time <span class="token keyword">END</span><span class="token punctuation">)</span> <span class="token keyword">AS</span> <span class="token punctuation">`</span><span class="token keyword">LOAD</span><span class="token punctuation">`</span><span class="token punctuation">,</span>
<span class="token function">COUNT</span><span class="token punctuation">(</span><span class="token keyword">DISTINCT</span> <span class="token keyword">CASE</span> <span class="token keyword">WHEN</span> <span class="token punctuation">`</span><span class="token keyword">type</span><span class="token punctuation">`</span> <span class="token operator">=</span> <span class="token string">'MIDNIGHT'</span> <span class="token keyword">THEN</span> slot_time <span class="token keyword">END</span><span class="token punctuation">)</span> <span class="token keyword">AS</span> MIDNIGHT
<span class="token keyword">FROM</span> sense_hes_intelli_smart_prod<span class="token punctuation">.</span>mdm_profile_data_audit
<span class="token keyword">WHERE</span> slot_time <span class="token operator">&gt;=</span> <span class="token string">'2026-05-04 00:00:00'</span>
<span class="token operator">AND</span> slot_time <span class="token operator">&lt;</span> <span class="token string">'2026-05-05 00:00:00'</span>
<span class="token operator">AND</span> <span class="token keyword">status</span> <span class="token operator">=</span> <span class="token string">'SUCCESS'</span>
<span class="token keyword">GROUP</span> <span class="token keyword">BY</span>
meter_number
<span class="token keyword">ORDER</span> <span class="token keyword">BY</span>
meter_number<span class="token punctuation">;</span>
</code></pre>
<h4 id="group-by-meter_number-and-type">Group by meter_number and type</h4>
<pre class=" language-sql"><code class="prism  language-sql"><span class="token keyword">SELECT</span>
meter_number<span class="token punctuation">,</span>
<span class="token punctuation">`</span><span class="token keyword">type</span><span class="token punctuation">`</span><span class="token punctuation">,</span>
<span class="token function">COUNT</span><span class="token punctuation">(</span><span class="token operator">*</span><span class="token punctuation">)</span> <span class="token keyword">AS</span> data_count
<span class="token keyword">FROM</span> sense_hes_intelli_smart_prod<span class="token punctuation">.</span>mdm_profile_data_audit
<span class="token keyword">WHERE</span> slot_time <span class="token operator">&gt;=</span> <span class="token string">'2026-05-04 00:00:00'</span>
<span class="token operator">AND</span> slot_time <span class="token operator">&lt;</span> <span class="token string">'2026-05-05 00:00:00'</span>
<span class="token operator">AND</span> <span class="token keyword">status</span> <span class="token operator">=</span> <span class="token string">'SUCCESS'</span>
<span class="token keyword">GROUP</span> <span class="token keyword">BY</span>
meter_number<span class="token punctuation">,</span>
<span class="token punctuation">`</span><span class="token keyword">type</span><span class="token punctuation">`</span>
<span class="token keyword">ORDER</span> <span class="token keyword">BY</span>
meter_number<span class="token punctuation">,</span>
<span class="token punctuation">`</span><span class="token keyword">type</span><span class="token punctuation">`</span><span class="token punctuation">;</span>
</code></pre>
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
eyJoaXN0b3J5IjpbLTE3NzEwOTI3MzNdfQ==
-->
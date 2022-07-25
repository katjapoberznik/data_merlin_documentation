---
layout: default
title: Load and sample
nav_order: 4
parent: Catalog
grand_parent: Admin
---

## Load and sample

Load & Sample enables that we can filer data from source table.
In EXTRACT SQL, we can define NEW query to read from source table. We can select just some columns, or we can rename some…
In Number of load partitions window, we can set number of partitions, which will define numbers of paroral loading. To use partition loading, define DST fields In Columns roles tab is mandatory. 

![](../../../snapshots/load_and_sample_1.PNG)

![](../../../snapshots/load_and_sample_2.PNG)

![](../../../snapshots/load_and_sample_3.PNG)


## Incremental load EX and ST

### 1. V_EX WHERE expression and PPN_GID is determined

<img src="../../../snapshots/load_sample_1.PNG" width="800">

**PPN_GID**

<img src="../../../snapshots/load_sample_2.PNG" width="600">

**EX**

TRUNCATE TABLE EX.EX_ORA_INS2_PSK_OSN_ENOTE_SKLEPDOK; <br>
"INSERT INTO FROM EX.EX_ORA_INS2_MET_NASLOV" <br>
SELECT * , NVL(CAST(ID AS VARCHAR(50)), 'XX') as PPN_GID <br>
FROM INSURANCE2."PSK_OSN_ENOTE_SKLEPDOK" <br>
WHERE trunc(sysdate - DATUM_VREDNOTENJA) < 70; <br>


**ST**

DELETE FROM ST.ST_ORA_INS2_PSK_OSN_ENOTE_SKLEPDOK <br>
WHERE PPN_GID IN (SELECT PPN_GID FROM VS_ORA_INS2_PSK_OSN_ENOTE_SKLEPDOK);<br>
INSERT INTO ST.ST_ORA_INS2_PSK_OSN_ENOTE_SKLEPDOK <br>
SELECT * FROM ST.VS_ORA_INS2_PSK_OSN_ENOTE_SKLEPDOK;





SD data format
==============

When using the **SD firmware** on the SCK, data is stored as **CSV** (comma separated) file on the SD card.

This is an example of the output file once opened on a spreadsheet application:

| ID | Temp    | ID| Hum     | ID| Light   | ID| Bat   | ID| Panel| ID| CO     | ID| NO2  | ID| Noise| Date       | Time    | 
|----|---------|---|---------|---|---------|---|-------|---|------|---|--------|---|------|---|------|------------|---------|
| 0  | 2821.20 | 1 | 4072.00 | 2 | 4413.10 | 3 | 96.40 | 4 | 0.00 | 5 | 94.67  | 6 | 0.65 | 7 | 5.23 | 2000-01-01 | 00:00:02 |
| 0  | 2784.40 | 1 | 4236.80 | 2 | 5936.70 | 3 | 96.10 | 4 | 0.00 | 5 | 278.27 | 6 | 1.05 | 7 | 2.39 | 2000-01-01 | 00:00:02 |


The data stored requires some conversions as specified on the table:

| ID  | Sensor       | Units | Conversion Formula                                 
|-----|--------------|-------|---------------------------------------------|
| 0   | Temperature  | ºC    |  T = -53 + 175.72 / 65536.0 * ( Traw * 10 ) |
| 1   | Humidity     | %Rel  |  H =   7 + 125.0  / 65536.0 * ( Hraw * 10 ) |
| 2   | Light        | Lux   |  L = Lraw / 10                              |
| 3   | Battery      | %     |  Not required                               |
| 4   | Panel        | mV    |  Not required                               |                                             
| 5   | CO      	  | kOhm  |  Not required                               |                                            
| 6   | NO2          | kOhm  |  Not required                               |                               
| 7   | Noise        | dB    |  Apply the conversion table from mV to dB: [CSV](https://gist.github.com/pral2a/d767cc45874361fd38bf) 
| 8   | Date         | DD:MM:YY |  Not required                            |                             
| 9   | Time         | hh:mm:ss |  Not required                            |                            







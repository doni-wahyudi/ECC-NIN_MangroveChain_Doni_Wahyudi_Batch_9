# Studi Kasus 5

## Analisis Jaringan Blockchain dalam Konservasi
### Task
CTO perlu memahami pola berbagi data blockchain untuk mengoptimalkan arsitektur sistem:
- Distribusi tipe data (Geografis/Personal/Transaksi) per wilayah
- Korelasi antara level akses dengan volume transaksi karbon
- Pola temporal penerbitan izin vs aktivitas blockchain
Analisis awal menunjukkan proyek dengan data geografis terbuka memiliki volume transaksi 2.5x lebih tinggi.
Aspek teknis yang dibutuhkan yaitu:
- Analisis jaringan hubungan antara node data
- Pola aliran informasi antar stakeholder
- Optimasi desain smart contract

### Dataset
Untuk menjawab permasalahan tersebut, diperlukan beberapa dataset sebagai berikut:
1. Data 002Mangrove_Conservation_Records.csv  

<div><style scoped>    .dataframe tbody tr th:only-of-type {        vertical-align: middle;    }    .dataframe tbody tr th {        vertical-align: top;    }    .dataframe thead th {        text-align: right;    }</style><table border="1" class="dataframe">  <thead>    <tr style="text-align: right;">      <th></th>      <th>Transaction_ID</th>      <th>Conservation_ID</th>      <th>Block_Hash</th>      <th>Carbon_Credits_Transferred</th>      <th>Transaction_Date</th>    </tr>  </thead>  <tbody>    <tr>      <th>0</th>      <td>T001</td>      <td>C001</td>      <td>0x1a2b3c4d</td>      <td>250</td>      <td>2024-01-16</td>    </tr>    <tr>      <th>1</th>      <td>T002</td>      <td>C002</td>      <td>0x2b3c4d5e</td>      <td>370</td>      <td>2024-02-11</td>    </tr>    <tr>      <th>2</th>      <td>T003</td>      <td>C003</td>      <td>0x3c4d5e6f</td>      <td>150</td>      <td>2024-03-06</td>    </tr>    <tr>      <th>3</th>      <td>T004</td>      <td>C004</td>      <td>0x4d5e6f7g</td>      <td>300</td>      <td>2024-04-21</td>    </tr>    <tr>      <th>4</th>      <td>T005</td>      <td>C005</td>      <td>0x5e6f7g8h</td>      <td>220</td>      <td>2024-05-13</td>    </tr>  </tbody></table></div>

2. Data 010Regulatory_Permits.csv

<div><style scoped>    .dataframe tbody tr th:only-of-type {        vertical-align: middle;    }    .dataframe tbody tr th {        vertical-align: top;    }    .dataframe thead th {        text-align: right;    }</style><table border="1" class="dataframe">  <thead>    <tr style="text-align: right;">      <th></th>      <th>Permit_ID</th>      <th>Conservation_ID</th>      <th>Permit_Type</th>      <th>Authority</th>      <th>Approval_Date</th>      <th>Permit_Status</th>    </tr>  </thead>  <tbody>    <tr>      <th>0</th>      <td>P101</td>      <td>C001</td>      <td>Environmental Permit</td>      <td>KLHK</td>      <td>2024-01-10</td>      <td>Approved</td>    </tr>    <tr>      <th>1</th>      <td>P102</td>      <td>C002</td>      <td>Environmental Permit</td>      <td>KLHK</td>      <td>2024-02-05</td>      <td>Approved</td>    </tr>    <tr>      <th>2</th>      <td>P103</td>      <td>C003</td>      <td>UKL-UPL</td>      <td>Dinas Lingkungan</td>      <td>2024-03-01</td>      <td>Pending</td>    </tr>    <tr>      <th>3</th>      <td>P104</td>      <td>C004</td>      <td>Environmental Permit</td>      <td>KLHK</td>      <td>2024-04-15</td>      <td>Approved</td>    </tr>    <tr>      <th>4</th>      <td>P105</td>      <td>C005</td>      <td>UKL-UPL</td>      <td>Dinas Lingkungan</td>      <td>2024-05-10</td>      <td>Approved</td>    </tr>  </tbody></table></div>

3. Data 013Blockchain_Data_Compliance.csv

<div><style scoped>    .dataframe tbody tr th:only-of-type {        vertical-align: middle;    }    .dataframe tbody tr th {        vertical-align: top;    }    .dataframe thead th {        text-align: right;    }</style><table border="1" class="dataframe">  <thead>    <tr style="text-align: right;">      <th></th>      <th>Data_ID</th>      <th>Conservation_ID</th>      <th>Data_Type</th>      <th>Consent_Obtained</th>      <th>Encryption_Level</th>      <th>Access_Level</th>    </tr>  </thead>  <tbody>    <tr>      <th>0</th>      <td>D101</td>      <td>C001</td>      <td>Geographic</td>      <td>Yes</td>      <td>High</td>      <td>Public</td>    </tr>    <tr>      <th>1</th>      <td>D102</td>      <td>C002</td>      <td>Personal</td>      <td>Yes</td>      <td>Medium</td>      <td>Restricted</td>    </tr>    <tr>      <th>2</th>      <td>D103</td>      <td>C003</td>      <td>Transaction</td>      <td>Yes</td>      <td>High</td>      <td>Auditor</td>    </tr>    <tr>      <th>3</th>      <td>D104</td>      <td>C004</td>      <td>Geographic</td>      <td>Yes</td>      <td>High</td>      <td>Public</td>    </tr>    <tr>      <th>4</th>      <td>D105</td>      <td>C005</td>      <td>Personal</td>      <td>Yes</td>      <td>Medium</td>      <td>Restricted</td>    </tr>  </tbody></table></div>

### Hasil dan Analisa
#### Distribusi Tipe Data per Wilayah  

langkah-langkah analisa:
1. tabel yang digunakan yaitu tabel mangrove_conservation_records kolom Location dan tabel blockchain_data_compliance kolom Data_Type
2. agregasi menggunakan count untuk melihat jumlah data
3. serta agregasi total data per lokasi dibagi dengan jumlah data keseluruhan dikali dengan 100 untuk mendapatkan persentase nya

Query:
```
SELECT
  c.Location,
  bdc.Data_Type,
  COUNT(*) AS jumlah_data,
  ROUND(COUNT(*) * 100.0 / SUM(COUNT(*)) OVER (PARTITION BY c.Location), 1) AS persentase
FROM
  mangrove_conservation_records c
JOIN
  blockchain_data_compliance bdc ON c.Conservation_ID = bdc.Conservation_ID
GROUP BY
  c.Location, bdc.Data_Type
ORDER BY
  c.Location, jumlah_data DESC;
```
Output:  
<div><style scoped>    .dataframe tbody tr th:only-of-type {        vertical-align: middle;    }    .dataframe tbody tr th {        vertical-align: top;    }    .dataframe thead th {        text-align: right;    }</style><table border="1" class="dataframe">  <thead>    <tr style="text-align: right;">      <th></th>      <th>location</th>      <th>data_type</th>      <th>jumlah_data</th>      <th>persentase</th>    </tr>  </thead>  <tbody>    <tr>      <th>0</th>      <td>Aceh Jaya</td>      <td>Geographic</td>      <td>1</td>      <td>100.0</td>    </tr>    <tr>      <th>1</th>      <td>Banyuwangi</td>      <td>Geographic</td>      <td>1</td>      <td>100.0</td>    </tr>    <tr>      <th>2</th>      <td>Bengkulu Utara</td>      <td>Personal</td>      <td>1</td>      <td>100.0</td>    </tr>    <tr>      <th>3</th>      <td>Blitar</td>      <td>Personal</td>      <td>1</td>      <td>100.0</td>    </tr>    <tr>      <th>4</th>      <td>Jember</td>      <td>Geographic</td>      <td>1</td>      <td>100.0</td>    </tr>  </tbody></table></div>


#### Korelasi Level Akses dengan Volume Transaksi

langkah-langkah analisa:
1. tabel yang digunakan yaitu tabel blockchain_data_compliance kolom Access_Level dan Data_Type, serta tabel blockchain_transactions kolom Transaction_ID dan Carbon_Credits_Transferred
2. untuk total_karbon didapat dari sum Carbon_Credits_Transferred
3. untuk rata-rata karbon didapat dari avg Carbon_Credits_Transferred
4. di group by berdasarkan Access_Level dan Data_Type

Query:  
```
SELECT
  bdc.Access_Level,
  bdc.Data_Type,
  COUNT(bt.Transaction_ID) AS jumlah_transaksi,
  SUM(bt.Carbon_Credits_Transferred) AS total_karbon,
  AVG(bt.Carbon_Credits_Transferred) AS rata_karbon
FROM
  blockchain_data_compliance bdc
LEFT JOIN
  blockchain_transactions bt ON bdc.Conservation_ID = bt.Conservation_ID
GROUP BY
  bdc.Access_Level, bdc.Data_Type
ORDER BY
  total_karbon DESC;
```

Output:
<div><style scoped>    .dataframe tbody tr th:only-of-type {        vertical-align: middle;    }    .dataframe tbody tr th {        vertical-align: top;    }    .dataframe thead th {        text-align: right;    }</style><table border="1" class="dataframe">  <thead>    <tr style="text-align: right;">      <th></th>      <th>access_level</th>      <th>data_type</th>      <th>jumlah_transaksi</th>      <th>total_karbon</th>      <th>rata_karbon</th>    </tr>  </thead>  <tbody>    <tr>      <th>0</th>      <td>Public</td>      <td>Geographic</td>      <td>9</td>      <td>2360</td>      <td>262.222222</td>    </tr>    <tr>      <th>1</th>      <td>Restricted</td>      <td>Personal</td>      <td>8</td>      <td>2055</td>      <td>256.875000</td>    </tr>    <tr>      <th>2</th>      <td>Auditor</td>      <td>Transaction</td>      <td>7</td>      <td>1860</td>      <td>265.714286</td>    </tr>  </tbody></table></div>

#### Pola Temporal Penerbitan Izin vs Aktivitas

langkah-langkah analisa:
1. membuat CTE bulan_izin yang berisi pengelompokkan data status izin tabel regulatory_permits per bulan
2. membuat CTE bulan_transaksi yang berisi pengelompokkan data transaksi tabel blockchain_transactions per bulan
3. melakukan join dari CTE bulan_izin dan CTE bulan_transaksi berdasarkan bulan yang sama

Query:
```
WITH bulan_izin AS (
  SELECT
    DATE_TRUNC('month', rp.Approval_Date) AS bulan,
    COUNT(*) AS jumlah_izin
  FROM
    regulatory_permits rp
  WHERE
    rp.Permit_Status = 'Approved'
  GROUP BY
    DATE_TRUNC('month', rp.Approval_Date)
),
bulan_transaksi AS (
  SELECT
    DATE_TRUNC('month', bt.Transaction_Date) AS bulan,
    COUNT(*) AS jumlah_transaksi,
    SUM(bt.Carbon_Credits_Transferred) AS total_karbon
  FROM
    blockchain_transactions bt
  GROUP BY
    DATE_TRUNC('month', bt.Transaction_Date)
)
SELECT
  i.bulan,
  i.jumlah_izin,
  t.jumlah_transaksi,
  t.total_karbon
FROM
  bulan_izin i
INNER JOIN
  bulan_transaksi t ON i.bulan = t.bulan
ORDER BY
  i.bulan;
```

Output:
<div><style scoped>    .dataframe tbody tr th:only-of-type {        vertical-align: middle;    }    .dataframe tbody tr th {        vertical-align: top;    }    .dataframe thead th {        text-align: right;    }</style><table border="1" class="dataframe">  <thead>    <tr style="text-align: right;">      <th></th>      <th>bulan</th>      <th>jumlah_izin</th>      <th>jumlah_transaksi</th>      <th>total_karbon</th>    </tr>  </thead>  <tbody>    <tr>      <th>0</th>      <td>2024-01-01 00:00:00.000 +0700</td>      <td>1</td>      <td>1</td>      <td>250</td>    </tr>    <tr>      <th>1</th>      <td>2024-02-01 00:00:00.000 +0700</td>      <td>1</td>      <td>1</td>      <td>370</td>    </tr>    <tr>      <th>2</th>      <td>2024-04-01 00:00:00.000 +0700</td>      <td>1</td>      <td>1</td>      <td>300</td>    </tr>    <tr>      <th>3</th>      <td>2024-05-01 00:00:00.000 +0700</td>      <td>1</td>      <td>1</td>      <td>220</td>    </tr>    <tr>      <th>4</th>      <td>2024-07-01 00:00:00.000 +0700</td>      <td>1</td>      <td>1</td>      <td>170</td>    </tr>  </tbody></table></div>

#### Visualisasi Jaringan dengan Python
1. Prepare Data
- Query data node:
```
SELECT c.Conservation_ID, c.Location, bdc.Data_Type, bdc.Access_Level,
COUNT(bt.Transaction_ID) AS transaction_count
FROM mangrove_conservation_records c
JOIN blockchain_data_compliance bdc ON c.Conservation_ID = bdc.Conservation_ID
LEFT JOIN blockchain_transactions bt ON c.Conservation_ID = bt.Conservation_ID
GROUP BY c.Conservation_ID, c.Location, bdc.Data_Type, bdc.Access_Level
```

- simpan ke dalam data_nodes.csv  
<div><style scoped>    .dataframe tbody tr th:only-of-type {        vertical-align: middle;    }    .dataframe tbody tr th {        vertical-align: top;    }    .dataframe thead th {        text-align: right;    }</style><table border="1" class="dataframe">  <thead>    <tr style="text-align: right;">      <th></th>      <th>conservation_id</th>      <th>location</th>      <th>data_type</th>      <th>access_level</th>      <th>transaction_count</th>    </tr>  </thead>  <tbody>    <tr>      <th>0</th>      <td>C017</td>      <td>Serang</td>      <td>Personal</td>      <td>Restricted</td>      <td>1</td>    </tr>    <tr>      <th>1</th>      <td>C001</td>      <td>Aceh Jaya</td>      <td>Geographic</td>      <td>Public</td>      <td>2</td>    </tr>    <tr>      <th>2</th>      <td>C011</td>      <td>Pontianak</td>      <td>Personal</td>      <td>Restricted</td>      <td>1</td>    </tr>    <tr>      <th>3</th>      <td>C007</td>      <td>Minahasa Selatan</td>      <td>Geographic</td>      <td>Public</td>      <td>1</td>    </tr>    <tr>      <th>4</th>      <td>C002</td>      <td>Takalar</td>      <td>Personal</td>      <td>Restricted</td>      <td>1</td>    </tr>  </tbody></table></div>


- Query data edge:
```
WITH transactions AS (
SELECT Conservation_ID, Block_Hash, COUNT(*) AS weight
FROM blockchain_transactions
GROUP BY Conservation_ID, Block_Hash
)
SELECT t1.Conservation_ID AS source, t2.Conservation_ID AS target, t1.weight
FROM transactions t1
JOIN transactions t2 ON t1.Block_Hash = t2.Block_Hash
WHERE t1.Conservation_ID != t2.Conservation_ID
```

- simpan ke dalam data_edges.csv
<div><style scoped>    .dataframe tbody tr th:only-of-type {        vertical-align: middle;    }    .dataframe tbody tr th {        vertical-align: top;    }    .dataframe thead th {        text-align: right;    }</style><table border="1" class="dataframe">  <thead>    <tr style="text-align: right;">      <th></th>      <th>source</th>      <th>target</th>      <th>weight</th>    </tr>  </thead>  <tbody>    <tr>      <th>0</th>      <td>C014</td>      <td>C003</td>      <td>1</td>    </tr>    <tr>      <th>1</th>      <td>C001</td>      <td>C005</td>      <td>1</td>    </tr>    <tr>      <th>2</th>      <td>C005</td>      <td>C001</td>      <td>1</td>    </tr>    <tr>      <th>3</th>      <td>C004</td>      <td>C015</td>      <td>1</td>    </tr>    <tr>      <th>4</th>      <td>C015</td>      <td>C004</td>      <td>1</td>    </tr>  </tbody></table></div>

Script Python:
```
import pandas as pd
from pyvis.network import Network
import networkx as nx
from datetime import datetime

nodes_df = pd.read_csv('C:\data\data_nodes.csv')
edges_df = pd.read_csv('C:\data\data_edges.csv')

# Inisialisasi jaringan
net = Network(height="750px", width="100%", bgcolor="#222222", font_color="white", notebook=True)

# Konfigurasi global
net.barnes_hut(gravity=-80000, central_gravity=0.3, spring_length=250, spring_strength=0.001, damping=0.09, overlap=0)

# Tambahkan node
for idx, row in nodes_df.iterrows():
  node_size = 10 + row['transaction_count'] * 2
  node_title = f"ID: {row['conservation_id']}<br>Lokasi: {row['location']}<br>Tipe: {row['data_type']}<br>Akses: {row['access_level']}<br>Transaksi: {row['transaction_count']}"
  
  # Tentukan warna berdasarkan tipe data
  if row['data_type'] == 'Geographic':
    color = '#4CAF50' # Hijau
  elif row['data_type'] == 'Personal':
    color = '#2196F3' # Biru
  else:
    color = '#FF5722' # Oranye
  
  # Tentukan bentuk berdasarkan level akses
  shape = 'dot' if row['access_level'] == 'Public' else 'diamond' if row['access_level'] == 'Restricted' else 'star'
  
  net.add_node(
    n_id=row['conservation_id'],
    label=row['conservation_id'],
    title=node_title,
    size=node_size,
    color=color,
    shape=shape,
    borderWidth=2
  )

# Tambahkan edge
for idx, row in edges_df.iterrows():
  net.add_edge(
    row['source'],
    row['target'],
    value=row['weight'],
    title=f"{row['weight']} transaksi",
    color='#757575'
  )

# Konfigurasi tampilan
net.set_options("""
{
"nodes": {
"font": {
"size": 12,
"face": "arial"
}
},
"edges": {
"smooth": {
"type": "continuous"
}
},
"physics": {
"forceAtlas2Based": {
"gravitationalConstant": -50,
"centralGravity": 0.01,
"springLength": 100,
"springConstant": 0.08
},
"minVelocity": 0.75,
"solver": "forceAtlas2Based"
}
}
""")

# Simpan dan tampilkan
net.show("blockchain_network.html")
```

Hasilnya akan seperti berikut:  
![pyvis image](img\pyvis.png)



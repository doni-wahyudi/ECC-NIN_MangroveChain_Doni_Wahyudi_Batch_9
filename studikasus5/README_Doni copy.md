# Studi Kasus 5

## Analisis Jaringan Blockchain dalam Konservasi

CTO perlu memahami pola berbagi data blockchain untuk mengoptimalkan arsitektur sistem:
- Distribusi tipe data (Geografis/Personal/Transaksi) per wilayah
- Korelasi antara level akses dengan volume transaksi karbon
- Pola temporal penerbitan izin vs aktivitas blockchain
Analisis awal menunjukkan proyek dengan data geografis terbuka memiliki volume transaksi 2.5x lebih tinggi.
Aspek teknis yang dibutuhkan yaitu:
- Analisis jaringan hubungan antara node data
- Pola aliran informasi antar stakeholder
- Optimasi desain smart contract

Untuk menjawab permasalahan tersebut, diperlukan beberapa dataset sebagai berikut:
1. Data 001Mangrove_Conservation_Records.csv  

<div><style scoped>    .dataframe tbody tr th:only-of-type {        vertical-align: middle;    }    .dataframe tbody tr th {        vertical-align: top;    }    .dataframe thead th {        text-align: right;    }</style><table border="1" class="dataframe">  <thead>    <tr style="text-align: right;">      <th></th>      <th>Conservation_ID</th>      <th>Location</th>      <th>Area_Ha</th>      <th>Carbon_Credits</th>      <th>Date_Recorded</th>    </tr>  </thead>  <tbody>    <tr>      <th>0</th>      <td>C001</td>      <td>Aceh Jaya</td>      <td>50</td>      <td>250</td>      <td>2024-01-15</td>    </tr>    <tr>      <th>1</th>      <td>C002</td>      <td>Takalar</td>      <td>75</td>      <td>370</td>      <td>2024-02-10</td>    </tr>    <tr>      <th>2</th>      <td>C003</td>      <td>Tanah Laut</td>      <td>30</td>      <td>150</td>      <td>2024-03-05</td>    </tr>    <tr>      <th>3</th>      <td>C004</td>      <td>Lampung Barat</td>      <td>60</td>      <td>300</td>      <td>2024-04-20</td>    </tr>    <tr>      <th>4</th>      <td>C005</td>      <td>Bengkulu Utara</td>      <td>45</td>      <td>220</td>      <td>2024-05-12</td>    </tr>  </tbody></table></div>

2. Data 006Conservation_Activities.csv  
<div><style scoped>    .dataframe tbody tr th:only-of-type {        vertical-align: middle;    }    .dataframe tbody tr th {        vertical-align: top;    }    .dataframe thead th {        text-align: right;    }</style><table border="1" class="dataframe">  <thead>    <tr style="text-align: right;">      <th></th>      <th>Activity_ID</th>      <th>Conservation_ID</th>      <th>Activity_Type</th>      <th>Date_Performed</th>      <th>Participants</th>    </tr>  </thead>  <tbody>    <tr>      <th>0</th>      <td>A001</td>      <td>C001</td>      <td>Planting</td>      <td>2024-01-20</td>      <td>5</td>    </tr>    <tr>      <th>1</th>      <td>A002</td>      <td>C002</td>      <td>Monitoring</td>      <td>2024-02-15</td>      <td>3</td>    </tr>    <tr>      <th>2</th>      <td>A003</td>      <td>C003</td>      <td>Restoration</td>      <td>2024-03-10</td>      <td>4</td>    </tr>    <tr>      <th>3</th>      <td>A004</td>      <td>C004</td>      <td>Planting</td>      <td>2024-04-25</td>      <td>6</td>    </tr>    <tr>      <th>4</th>      <td>A005</td>      <td>C005</td>      <td>Monitoring</td>      <td>2024-05-17</td>      <td>2</td>    </tr>  </tbody></table></div>

3. Data 010Regulatory_Permits.csv

<div><style scoped>    .dataframe tbody tr th:only-of-type {        vertical-align: middle;    }    .dataframe tbody tr th {        vertical-align: top;    }    .dataframe thead th {        text-align: right;    }</style><table border="1" class="dataframe">  <thead>    <tr style="text-align: right;">      <th></th>      <th>Permit_ID</th>      <th>Conservation_ID</th>      <th>Permit_Type</th>      <th>Authority</th>      <th>Approval_Date</th>      <th>Permit_Status</th>    </tr>  </thead>  <tbody>    <tr>      <th>0</th>      <td>P101</td>      <td>C001</td>      <td>Environmental Permit</td>      <td>KLHK</td>      <td>2024-01-10</td>      <td>Approved</td>    </tr>    <tr>      <th>1</th>      <td>P102</td>      <td>C002</td>      <td>Environmental Permit</td>      <td>KLHK</td>      <td>2024-02-05</td>      <td>Approved</td>    </tr>    <tr>      <th>2</th>      <td>P103</td>      <td>C003</td>      <td>UKL-UPL</td>      <td>Dinas Lingkungan</td>      <td>2024-03-01</td>      <td>Pending</td>    </tr>    <tr>      <th>3</th>      <td>P104</td>      <td>C004</td>      <td>Environmental Permit</td>      <td>KLHK</td>      <td>2024-04-15</td>      <td>Approved</td>    </tr>    <tr>      <th>4</th>      <td>P105</td>      <td>C005</td>      <td>UKL-UPL</td>      <td>Dinas Lingkungan</td>      <td>2024-05-10</td>      <td>Approved</td>    </tr>  </tbody></table></div>

4. 
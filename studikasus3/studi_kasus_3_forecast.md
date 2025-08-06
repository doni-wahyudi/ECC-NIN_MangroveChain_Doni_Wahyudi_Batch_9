# Prediksi Kinerja Proyek Berbasis Keterlibatan Masyarakat

## Studi Kasus #3 - Latar Belakang

CEO ingin mengembangkan **model prediktif** untuk mengalokasikan sumber daya secara optimal pada proyek konservasi mangrove. Data historis menunjukkan bahwa proyek dengan **partisipasi masyarakat di atas 30%** memiliki tingkat **keberlanjutan 75% lebih tinggi** setelah 3 tahun.

## Faktor yang Dianalisis

1. **Frekuensi Kegiatan Masyarakat** (Lokakarya / Konsultasi / Pelatihan)
2. **Distribusi Manfaat Ekonomi** kepada masyarakat lokal
3. **Tingkat Partisipasi Relatif** terhadap ukuran komunitas
4. **Korelasi Temporal** antara kegiatan dengan peningkatan biodiversitas

## Dataset yang Digunakan

- **014Community_Engagement**
- **004Community_Members**
- **001Mangrove_Conservation_Records**

## Query Normalisasi Partisipasi dan Biodiversitas

```sql
WITH partisipasi_normal AS (
    SELECT 
        ce.Conservation_ID, 
        ce.Participants::INTEGER / NULLIF((SELECT AVG(Participants::INTEGER) FROM "014Community_Engagement"), 0) AS partisipasi_relatif, 
        COUNT(*) OVER (PARTITION BY ce.Conservation_ID) AS frekuensi_kegiatan, 
        SUM(Benefit_Distributed::INTEGER) OVER (PARTITION BY ce.Conservation_ID) AS total_manfaat,
        ce.Engagement_Date
    FROM "014Community_Engagement" ce
),
biodiversitas_summary AS (
    SELECT
        mc.Conservation_ID,
        mc.Area_Ha,
        mc.Carbon_Credits,
        mc.Date_Recorded
    FROM "001Mangrove_Conservation_Records" mc
)
SELECT 
    pn.Conservation_ID,
    pn.partisipasi_relatif,
    pn.frekuensi_kegiatan,
    pn.total_manfaat,
    pn.Engagement_Date,
    bs.Area_Ha,
    bs.Carbon_Credits,
    bs.Date_Recorded AS biodiversity_record_date
FROM partisipasi_normal pn
LEFT JOIN biodiversitas_summary bs ON pn.Conservation_ID = bs.Conservation_ID
ORDER BY pn.Engagement_Date;
```

## Python Script: Time Series Forecasting dengan ARIMA

```python
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
from statsmodels.tsa.arima.model import ARIMA
from pandas.plotting import register_matplotlib_converters

register_matplotlib_converters()

# Simulasi Data Engagement (Date & Partisipasi Relatif)
dates = pd.date_range(start='2024-01-01', periods=20, freq='MS')
partisipasi_relatif = np.random.uniform(0.7, 1.4, 20)

# Membuat DataFrame
df_time_series = pd.DataFrame({
    'engagement_date': dates,
    'partisipasi_relatif': partisipasi_relatif
})
df_time_series.set_index('engagement_date', inplace=True)
df_time_series = df_time_series.asfreq('MS')  # Menetapkan frekuensi eksplisit

# Fit Model ARIMA (order p,d,q = 1,1,1)
model = ARIMA(df_time_series['partisipasi_relatif'], order=(1,1,1))
model_fit = model.fit()

# Forecast 6 Bulan Kedepan
forecast = model_fit.forecast(steps=6)
forecast_dates = pd.date_range(start=dates[-1] + pd.DateOffset(months=1), periods=6, freq='MS')

# Visualisasi Hasil Forecast
plt.figure(figsize=(12,6))
plt.plot(df_time_series.index, df_time_series['partisipasi_relatif'], label='Actual Partisipasi')
plt.plot(forecast_dates, forecast, label='Forecasted Partisipasi', linestyle='--', color='red')
plt.title('ARIMA Time Series Forecasting: Partisipasi Relatif')
plt.xlabel('Date')
plt.ylabel('Partisipasi Relatif')
plt.legend()
plt.grid(True)
plt.show()

# Output Forecast
forecast_df = pd.DataFrame({
    'Forecast_Date': forecast_dates,
    'Forecasted_Partisipasi': forecast.values
})
print(forecast_df)
```

## Output yang Dihasilkan

1. **Grafik Time Series**:
   - Menampilkan tren aktual dan prediksi Partisipasi Relatif 6 bulan ke depan.
2. **Tabel Forecast**:
   - Daftar nilai forecasted_partisipasi dari hasil ARIMA.

## Manfaat Analisis Ini

- Membantu manajemen dalam mengalokasikan sumber daya secara lebih akurat.
- Mengidentifikasi pola keterlibatan masyarakat yang menjadi indikator keberlanjutan proyek.
- Memantau efektivitas program community engagement selama fase awal proyek.

---

**Catatan:** Dataset produksi akan diambil dari integrasi tabel **014Community_Engagement**, **004Community_Members**, dan **001Mangrove_Conservation_Records** sesuai skenario aktual.


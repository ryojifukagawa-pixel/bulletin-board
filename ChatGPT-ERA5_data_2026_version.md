# ERA5データ取得方法

**User:** RFA  
**Created:** 6/8/2026 23:01:48  
**Updated:** 6/8/2026 23:03:59  
**Exported:** 6/8/2026 23:51:14  
**Link:** [https://chatgpt.com/c/6a26c9c3-05a0-8324-97f6-8a2458d8ca21](https://chatgpt.com/c/6a26c9c3-05a0-8324-97f6-8a2458d8ca21)  

## Prompt:
2026/6/8 23:03:39

Show me the current CDS screen layout (2026 version) with detailed button press instructions

## Response:
2026/6/8 23:03:39

以下は、2026年6月現在のCDS（Climate Data Store）の画面構成に合わせた「我孫子市のERA5時系列データ取得」の実践手順です。CDSの新画面では、昔の「cdsapp」画面とはかなり構成が変わっています。([cds.climate.copernicus.eu](https://cds.climate.copernicus.eu/datasets/reanalysis-era5-single-levels?tab=overview&utm_source=chatgpt.com))

まずデータセット画面を開きます。

[ERA5 hourly data on single levels from 1940 to present](https://cds.climate.copernicus.eu/datasets/reanalysis-era5-single-levels?utm_source=chatgpt.com)

---

# ① CDSへログイン

右上の

```text
Login
```

をクリックします。

未登録なら

```text
Register
```

から無料登録します。([cds.climate.copernicus.eu](https://cds.climate.copernicus.eu/datasets/reanalysis-era5-single-levels?tab=overview&utm_source=chatgpt.com))

---

# ② Download タブへ移動

画面上部に

```text
Overview
Download
Quality
Documentation
```

が並んでいます。

ここで

```text
Download
```

をクリックします。([cds.climate.copernicus.eu](https://cds.climate.copernicus.eu/datasets/reanalysis-era5-single-levels?Cg9GJMKvW2=063ZkCVMvb6&tab=download&utm_source=chatgpt.com))

---

# ③ Product Type

最初に現れるのが

```text
Product type
```

です。

通常は

```text
Reanalysis
```

だけにチェックします。

下記は使いません。

```text
Ensemble members
Ensemble mean
Ensemble spread
```

特殊な不確実性解析以外は不要です。([cds.climate.copernicus.eu](https://cds.climate.copernicus.eu/datasets/reanalysis-era5-single-levels?Cg9GJMKvW2=063ZkCVMvb6&tab=download&utm_source=chatgpt.com))

---

# ④ Variables

次に

```text
Variable
```

欄です。

建築環境解析ならまず次を選択します。

```text
2m temperature

2m dewpoint temperature

10m u-component of wind

10m v-component of wind

total cloud cover

surface solar radiation downwards

surface thermal radiation downwards
```

([cds.climate.copernicus.eu](https://cds.climate.copernicus.eu/datasets/reanalysis-era5-single-levels?Cg9GJMKvW2=063ZkCVMvb6&tab=download&utm_source=chatgpt.com))

---

# ⑤ Year

次に

```text
Year
```

です。

例として

```text
2024
```

にチェックします。

複数年選択も可能です。([cds.climate.copernicus.eu](https://cds.climate.copernicus.eu/datasets/reanalysis-era5-single-levels?Cg9GJMKvW2=063ZkCVMvb6&tab=download&utm_source=chatgpt.com))

---

# ⑥ Month

例えば7月なら

```text
July
```

を選択します。([cds.climate.copernicus.eu](https://cds.climate.copernicus.eu/datasets/reanalysis-era5-single-levels?Cg9GJMKvW2=063ZkCVMvb6&tab=download&utm_source=chatgpt.com))

---

# ⑦ Day

1か月全体なら

```text
Select all
```

を押します。

あるいは

```text
01 ～ 31
```

を選択します。([cds.climate.copernicus.eu](https://cds.climate.copernicus.eu/datasets/reanalysis-era5-single-levels?Cg9GJMKvW2=063ZkCVMvb6&tab=download&utm_source=chatgpt.com))

---

# ⑧ Time

ここが重要です。

1時間ごとの時系列を得る場合、

```text
Select all
```

を押します。

すると

```text
00:00
01:00
02:00
...
23:00
```

の24時間すべてが選択されます。([cds.climate.copernicus.eu](https://cds.climate.copernicus.eu/datasets/reanalysis-era5-single-levels?Cg9GJMKvW2=063ZkCVMvb6&tab=download&utm_source=chatgpt.com))

---

# ⑨ Geographic Area（見落としやすい）

下へスクロールすると

```text
Geographical area
```

があります。([cds.climate.copernicus.eu](https://cds.climate.copernicus.eu/datasets/reanalysis-era5-single-levels?Cg9GJMKvW2=063ZkCVMvb6&tab=download&utm_source=chatgpt.com))

ここで

```text
Sub-region extraction
```

を選択します。

---

# ⑩ 我孫子市の範囲入力

我孫子市中心

```text
Lat = 35.87
Lon = 140.02
```

ですが、

ERA5は

```text
0.25°格子
```

です。([cds.climate.copernicus.eu](https://cds.climate.copernicus.eu/datasets/reanalysis-era5-single-levels?tab=overview&utm_source=chatgpt.com))

そのため実務上は次を入力します。

```text
North = 36.00
West  = 140.00

South = 35.75
East  = 140.25
```

図にすると

```text
36.00 N
 ┌────────────┐
 │ 我孫子市    │
 └────────────┘
35.75 N

140.00E    140.25E
```

です。

これで我孫子周辺のERA5格子が取得できます。

---

# ⑪ Data Format

さらに下に

```text
Data format
```

があります。

ここは

```text
NetCDF
```

を推奨します。

後でColabやPythonで扱いやすいためです。([cds.climate.copernicus.eu](https://cds.climate.copernicus.eu/datasets/reanalysis-era5-single-levels?tab=overview&utm_source=chatgpt.com))

---

# ⑫ Download Format

通常は

```text
Unarchived
```

で問題ありません。

大量データならZIP形式も選べます。

---

# ⑬ Request Validation

画面最下部に

```text
Request validation
```

が表示されます。([cds.climate.copernicus.eu](https://cds.climate.copernicus.eu/datasets/reanalysis-era5-single-levels?Cg9GJMKvW2=063ZkCVMvb6&tab=download&utm_source=chatgpt.com))

ここで

```text
Product type
Variable
Year
Month
Day
Time
Geographical area
Data format
```

にエラーがないか確認します。

---

# ⑭ Submit

ログイン済みなら最下部に

```text
Submit
```

ボタンが現れます。

クリックします。

---

# ⑮ ジョブ完了待ち

数十秒～数分待つと

```text
Completed
```

になります。

その後

```text
Download
```

ボタンが現れます。

---

# ⑯ ファイル取得

例えば

```text
download.nc
```

あるいは

```text
reanalysis-era5-single-levels.nc
```

のようなNetCDFファイルがダウンロードされます。

---

# ⑰ Colabで我孫子1点を抽出

アップロード後、

```python
import xarray as xr

ds = xr.open_dataset("download.nc")

abiko = ds.sel(
    latitude=35.87,
    longitude=140.02,
    method="nearest"
)

print(abiko)
```

で我孫子市に最も近いERA5格子が取得できます。

---

なお、2025年末以降のCDSでは、ECMWFが「時系列専用のARCO（Zarr）版ERA5」を推奨し始めています。長期間（例えば1990～2025年の35年分）の単一点データ取得では、従来のNetCDFより高速になる場合があります。まずは従来どおりの **ERA5 hourly data on single levels → NetCDF取得** を確実に使いこなし、その後ARCO版へ進むのがおすすめです。([cds.climate.copernicus.eu](https://cds.climate.copernicus.eu/datasets/reanalysis-era5-single-levels?tab=overview&utm_source=chatgpt.com))

---

**Sources:**

- [ERA5 hourly data on single levels from 1940 to present](https://cds.climate.copernicus.eu/datasets/reanalysis-era5-single-levels?tab=overview&utm_source=chatgpt.com)



---
Powered by [ChatGPT Exporter](https://www.chatgptexporter.com)
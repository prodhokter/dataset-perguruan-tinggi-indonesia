# Dataset Perguruan Tinggi Indonesia

Data seluruh perguruan tinggi negeri, swasta, dan kedinasan di Indonesia.

## Data

**File:** `perguruan-tinggi-indonesia.csv`  
**Records:** 143 perguruan tinggi  
**Size:** ~17 KB  
**Delimiter:** titik koma (`;`)

## Kolom

| Kolom | Deskripsi | Contoh |
|-------|-----------|--------|
| `id` | UUID | `006077d9-df05-486d-a020-3192db4967f9` |
| `name` | Nama perguruan tinggi | `Universitas Indonesia` |
| `code` | Kode singkat | `UI` |
| `city` | Kota | `Kota Depok` |
| `region` | Provinsi | `Jawa Barat` |
| `type` | Tipe | `Negeri`, `Swasta`, `Kedinasan` |
| `logo_url` | URL logo | |
| `total_majors` | Jumlah program studi | `79` |
| `total_quota` | Total daya tampung | `3247` |
| `total_applicants` | Total peminat | `102197` |

## Contoh

```csv
id;name;code;city;region;type;logo_url;total_majors;total_quota;total_applicants
006077d9-df05-486d-a020-3192db4967f9;Universitas Indonesia;UI;Kota Depok;Jawa Barat;Negeri;;79;3247;102197
```

## API

Gunakan [api-datasets-indonesia](https://github.com/prodhokter/api-datasets-indonesia) untuk akses via REST API:

```
GET /api/universities?search=universitas&region=jawa+barat&type=negeri
GET /api/universities/:id
```

## Sumber

SNPMB / LTMPT — data resmi seleksi nasional perguruan tinggi.

## Lisensi

Data bersumber dari institusi pemerintah Indonesia. Gunakan sesuai ketentuan yang berlaku.

# Dataset Perguruan Tinggi Indonesia

[![License: MIT](https://img.shields.io/badge/license-MIT-blue.svg)](LICENSE)
[![API Status](https://img.shields.io/badge/api-live-green)](https://api.ibnuhabib.web.id/api/universities)
[![Records](https://img.shields.io/badge/records-143-orange)](perguruan-tinggi-indonesia.csv)

Data seluruh perguruan tinggi negeri, swasta, dan kedinasan di Indonesia beserta statistik kuota dan peminat.

## Data

| File | Records | Size | Delimiter |
|------|---------|------|-----------|
| `perguruan-tinggi-indonesia.csv` | 143 | ~17 KB | `;` (titik koma) |

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

## Contoh Data

```csv
id;name;code;city;region;type;logo_url;total_majors;total_quota;total_applicants
006077d9-df05-486d-a020-3192db4967f9;Universitas Indonesia;UI;Kota Depok;Jawa Barat;Negeri;;79;3247;102197
```

## API

Gunakan [api-datasets-indonesia](https://github.com/prodhokter/api-datasets-indonesia) untuk akses REST API.

**Base URL:** `https://api.ibnuhabib.web.id`

```bash
# Semua perguruan tinggi
curl "https://api.ibnuhabib.web.id/api/universities"

# Cari berdasarkan nama atau kode
curl "https://api.ibnuhabib.web.id/api/universities?search=institut"

# Filter PTN di Jawa Timur
curl "https://api.ibnuhabib.web.id/api/universities?region=jawa+timur&type=negeri"

# Detail + daftar program studi
curl "https://api.ibnuhabib.web.id/api/universities/006077d9-df05-486d-a020-3192db4967f9"

# Download CSV
curl -O "https://api.ibnuhabib.web.id/download/universities.csv"
```

**Parameter search:**

| Param | Deskripsi |
|-------|-----------|
| `search` | Nama atau kode PT |
| `region` | Provinsi (exact) |
| `type` | `Negeri`, `Swasta`, `Kedinasan` |

## Dataset Terkait

- [api-datasets-indonesia](https://github.com/prodhokter/api-datasets-indonesia) — REST API
- [dataset-program-studi-indonesia](https://github.com/prodhokter/dataset-program-studi-indonesia)
- [dataset-sekolah-indonesia](https://github.com/prodhokter/dataset-sekolah-indonesia)
- [dataset-kbbi-indonesia](https://github.com/prodhokter/dataset-kbbi-indonesia)
- [dataset-wilayah-indonesia](https://github.com/prodhokter/dataset-wilayah-indonesia)

## Sumber

SNPMB / LTMPT — data resmi seleksi nasional perguruan tinggi.

## Lisensi

MIT — © 2025 [Ibnul Habib](https://github.com/prodhokter). Data bersumber dari institusi pemerintah Indonesia.

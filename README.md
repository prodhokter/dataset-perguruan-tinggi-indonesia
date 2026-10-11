# Dataset Perguruan Tinggi Indonesia

[![License: MIT](https://img.shields.io/badge/license-MIT-blue.svg)](LICENSE)
[![Records](https://img.shields.io/badge/records-143-orange)](perguruan-tinggi-indonesia.csv)

Data 143 perguruan tinggi **negeri peserta SNPMB 2024** beserta statistik jumlah program studi, daya tampung, dan peminat.

Catatan cakupan (koreksi dari dokumentasi versi lama): berkas ini **bukan** daftar seluruh PTN, swasta, dan kedinasan di Indonesia. Semua 143 baris berasal dari daftar peserta SNPMB dan kolom `type` bernilai `Negeri` untuk seluruh baris. Kolom `logo_url` kosong di semua baris (tidak ada logo di sumber).

## Data

| File | Baris | Ukuran | Delimiter |
|------|-------|--------|-----------|
| `perguruan-tinggi-indonesia.csv` | 143 | ~17 KB | `;` (titik koma) |

| Kolom | Deskripsi | Contoh |
|-------|-----------|--------|
| `id` | UUID perguruan tinggi (dipakai sebagai kunci relasi ke dataset prodi) | `006077d9-df05-486d-a020-3192db4967f9` |
| `name` | Nama resmi | `Universitas Indonesia` |
| `code` | Kode singkat | `UI` |
| `city` | Kota/kabupaten | `Kota Depok` |
| `region` | Provinsi | `Jawa Barat` |
| `type` | Tipe PT, seluruh baris `Negeri` | `Negeri` |
| `logo_url` | URL logo, kosong di semua baris | (kosong) |
| `total_majors` | Jumlah program studi | `79` |
| `total_quota` | Total daya tampung | `3247` |
| `total_applicants` | Total peminat | `102197` |

## Contoh data

```csv
id;name;code;city;region;type;logo_url;total_majors;total_quota;total_applicants
006077d9-df05-486d-a020-3192db4967f9;Universitas Indonesia;UI;Kota Depok;Jawa Barat;Negeri;;79;3247;102197
```

## Cara pakai

### 1. Unduh langsung

```bash
curl -O https://raw.githubusercontent.com/prodhokter/dataset-perguruan-tinggi-indonesia/master/perguruan-tinggi-indonesia.csv
```

### 2. Lewat API publik

Base URL: `https://datasets.snbtku.com` (hostname kedua: `https://api.ibnuhabib.web.id`)

```bash
# Cari PT (nama atau kode)
curl "https://datasets.snbtku.com/api/v1/universities?q=universitas%20indonesia&limit=5"

# Program studi milik satu PT (pakai id PT di atas)
curl "https://datasets.snbtku.com/api/v1/majors?university_id=006077d9-df05-486d-a020-3192db4967f9&limit=10"
```

Contoh respons nyata:

```json
// GET /api/v1/universities?q=universitas indonesia&limit=1
{
  "items": [
    {
      "id": "006077d9-df05-486d-a020-3192db4967f9",
      "code": "UI",
      "name": "Universitas Indonesia",
      "city": "Kota Depok",
      "region": "Jawa Barat",
      "type": "Negeri",
      "logo_url": "",
      "total_majors": 79,
      "total_quota": 3247,
      "total_applicants": 102197
    }
  ],
  "limit": 1,
  "offset": 0,
  "total": 1
}
```

Rate limit 120 permintaan per menit per IP, CORS terbuka, respons di-cache 5 menit.

## Aturan pembersihan (dipakai platform SNBTKU)

1. UUID divalidasi saat impor; baris dengan UUID tidak sah dilewati.
2. Relasi ke dataset prodi diperiksa (semua `university_id` di dataset prodi harus ada di sini).
3. Angka kosong menjadi `NULL`.

## Sumber & lisensi

- Sumber: daftar peserta dan statistik SNPMB 2024.
- Repo ini (kompilasi dan pembersihan): MIT, Copyright (c) 2025 Ibnul Habib.

## Changelog

Lihat [CHANGELOG.md](CHANGELOG.md).

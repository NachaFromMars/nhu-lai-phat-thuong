---
name: nhu-lai-phat-thuong
description: >
  Thư viện Phật giáo đa truyền thống (Theravāda + Mahāyāna) với kinh điển gốc sẵn sàng tra cứu.
  Bao gồm: Pali Canon đầy đủ (4 Nikāya EPUB/PDF bản PTS + 10 bộ SuttaCentral Sujato EPUB + Vinaya 
  Brahmali + bilara-data JSON root Pali + dịch Anh + dịch Việt), Mahāyāna (8 kinh từ 84000.co + 
  3 kinh từ BuddhaNet). Tổng 194MB, 30+ bộ kinh.
  Use when: AI cần tra cứu kinh Phật, trích dẫn Pali Canon, tham chiếu Nikāya, tìm kinh Mahāyāna,
  viết về Phật giáo, soạn bài giảng, nghiên cứu Dharma, so sánh Theravāda-Mahāyāna, dịch thuật ngữ
  Pali/Sanskrit, hoặc bất kỳ task nào liên quan đến kinh điển Phật giáo.
  Triggers: kinh phật, pali canon, nikāya, sutta, dharma, phật giáo, theravada, mahayana, 
  tứ thánh đế, bát chánh đạo, duyên khởi, bát nhã, pháp hoa, địa tạng, dược sư, duy ma cật,
  buddhism, buddhist texts, sutra, tipitaka, tam tạng kinh, kinh tạng, luật tạng.
---

# Như Lai Phật Thưởng V1.0 — Thư Viện Kinh Điển Phật Giáo

## Tổng Quan

Skill chứa kinh điển Phật giáo đa truyền thống, sẵn sàng tra cứu và trích dẫn.

**Bao phủ:**
- Theravāda: Toàn bộ Pali Canon (5 bộ Nikāya + Khuddaka + Vinaya)
- Mahāyāna: 11 bộ kinh quan trọng (Bát Nhã, Duy Ma Cật, Kim Quang Minh, Địa Tạng, Dược Sư, v.v.)

**Format:** EPUB, PDF, JSON (bilara-data)

## Cấu Trúc Thư Viện

```
assets/
├── Theravada/
│   ├── PTS-Nikaya-EPUB/        — 4 Nikāya bản PTS unabridged (American Monk v2.0)
│   ├── PTS-Nikaya-PDF/         — 4 Nikāya PDF (cùng nguồn)
│   ├── SuttaCentral-Sujato-EPUB/ — 10 bộ EPUB (Bhikkhu Sujato, Aug 2025)
│   ├── SuttaCentral-Vinaya-EPUB/ — Luật Tạng (Bhikkhu Brahmali)
│   └── Bilara-Data-JSON/       — Root Pali + EN + VI translations (JSON segments)
│       ├── root/pli/           — Nguyên bản Pali
│       ├── translation-en/     — Dịch Anh (Sujato + others)
│       └── translation-vi/     — Dịch Việt (nếu có)
└── Mahayana/
    ├── 84000-Kangyur-PDF/      — 8 kinh dịch từ Tạng ngữ (84000.co)
    └── BuddhaNet-PDF/          — 3 kinh PDF (BuddhaNet.net)
```

## Danh Mục Chi Tiết

Xem `references/catalog.md` để biết đầy đủ danh sách kinh, mã Toh, nguồn gốc, và cách dùng.

## Cách Tra Cứu

### 1. Tra kinh Theravāda cụ thể (bilara-data JSON)

Bilara-data dùng segment ID: `{collection}{number}:{vagga}.{segment}`

```bash
# Tìm kinh theo keyword
grep -r "dependent origination" assets/Theravada/Bilara-Data-JSON/translation-en/ | head -20

# Đọc một sutta cụ thể (VD: MN 1 — Mūlapariyāya)
cat assets/Theravada/Bilara-Data-JSON/translation-en/en/sujato/sutta/mn/mn1_translation-en-sujato.json

# Root Pali tương ứng
cat assets/Theravada/Bilara-Data-JSON/root/pli/ms/sutta/mn/mn1_root-pli-ms.json

# Tìm thuật ngữ Pali
grep -r "paṭiccasamuppāda" assets/Theravada/Bilara-Data-JSON/root/ | head -10
```

### 2. Đọc EPUB (Nikāya đầy đủ)

EPUB files có thể đọc trực tiếp bằng epub-reader skill hoặc unzip:

```bash
# Unzip EPUB để đọc HTML
unzip -o assets/Theravada/PTS-Nikaya-EPUB/DN-pts-v2.0.epub -d /tmp/dn-pts/
# Đọc chapter
cat /tmp/dn-pts/OEBPS/*.xhtml | head -200
```

### 3. Tra Mahāyāna (PDF)

PDF files từ 84000.co và BuddhaNet — dùng pdftotext hoặc summarize skill.

## Nguồn Gốc & License

| Nguồn | License | Link |
|-------|---------|------|
| American Monk PTS v2.0 | Non-commercial (PTS) | americanmonk.org |
| SuttaCentral (Sujato/Brahmali) | CC0 | suttacentral.net |
| bilara-data | CC0 | github.com/suttacentral/bilara-data |
| 84000.co | CC BY-NC-ND 3.0 | 84000.co |
| BuddhaNet | Free distribution | buddhanet.net |

## Lưu Ý

- **3 kinh Mahāyāna chưa có bản dịch Anh hoàn chỉnh trên 84000:** Laṅkāvatāra (Lăng Già), Mahāparinirvāṇa (Đại Bát Niết Bàn), Saddharmapuṇḍarīka (Pháp Hoa)
- Bilara-data bản Việt có thể chưa đầy đủ — dùng bản Anh (Sujato) làm primary
- PTS EPUB là bản unabridged (đã roll out "..." repetitions) — dày hơn bản thường

# mijia-product-icons · Xiaomi Mi Home Product Sample Image Library

[简体中文](README.md) | **English**

> A snapshot library of sample images for products listed in the Xiaomi Mi Home (米家) product encyclopedia. Images and companion catalogs are organized by category, for personal study, research, and software testing.

Companion viewer app: **[mijia-product-gallery](https://github.com/iop666/mijia-product-gallery)** — a WinUI 3 desktop app that turns this library's 10,000+ product sample images into an offline-browsable gallery with search, filtering, favorites, and export. This repository is its data source.

- Data source: Mi Home public product encyclopedia <https://home.mi.com/webapp/content/baike/index.html#/>
- Snapshot date: **2026-11-24** (collected from the online product library API on that day; a point-in-time snapshot of the "currently listed" library. Previous snapshot: 2026-11-15, see [更新清单/更新清单_2026-11-24.md](更新清单/更新清单_2026-11-24.md) — change logs are written in Chinese)
- Coverage: **17 categories / 10,991 currently listed product models / 10,990 currently listed sample images** (1 model has no image, in "Environmental Appliances"); additionally, **26 models removed from the official website** are retained with their info and images for reference
- Image format: saved in the original format, with extensions `.png` / `.jpg` / `.gif` / `.webp`
- File naming: sample image file name = product model, e.g. `zhimi.heater.za1.png`
- Category rule: "New Arrivals" (新上线) is a rolling shelf on the Mi Home encyclopedia. Models on that shelf are always assigned to their real category; only models that do not yet appear in any real category stay under "New Arrivals" (currently 1). Every model is counted exactly once across the whole library.
- Retention policy: models removed from the official website are **never deleted locally** — their catalog rows are kept in place in every CSV with the note 「官网已移除该型号」 (removed from the official website), and their images stay in the image directories
- Windows checkout note: 2 images have file names starting with the Windows reserved device name `aux.` (`aux.aircondition.hc1.png`, `aux.aircondition.v1.png`, in "Environmental Appliances"). Windows cannot check out/extract such file names, so they are excluded from the repository tree; all 11,016 images are available in the Release archives

## Repository Layout

```
├─ README.md                     Project overview (Chinese)
├─ README.en.md                  This file (English)
├─ THIRD-PARTY-NOTICES.md        Third-party content notice (English)
├─ 更新清单/                      Change logs, one file per snapshot period (in Chinese)
│   ├─ 更新清单_2026-09-28.md     2026-09-03 → 2026-09-28 changes
│   ├─ 更新清单_2026-10-09.md     2026-09-28 → 2026-10-09 changes
│   ├─ 更新清单_2026-10-19.md     2026-10-09 → 2026-10-19 changes
│   ├─ 更新清单_2026-10-25.md     2026-10-19 → 2026-10-25 changes
│   ├─ 更新清单_2026-11-03.md     2026-10-25 → 2026-11-03 changes
│   ├─ 更新清单_2026-11-08.md     2026-11-03 → 2026-11-08 changes
│   ├─ 更新清单_2026-11-15.md     2026-11-08 → 2026-11-15 changes
│   └─ 更新清单_2026-11-24.md     2026-11-15 → 2026-11-24 changes
├─ 全部示例样图/                   11,014 sample images (flat, named by model)
├─ 分类示例样图/                   Sample images grouped by category
│   ├─ 插座开关/                   (Sockets & Switches)
│   ├─ 照明/                       (Lighting)
│   ├─ 环境电器/                   (Environmental Appliances)
│   ├─ … (17 categories in total, directory names in Chinese)
└─ 清单/                          Product ↔ image catalogs
    ├─ 00_总清单.csv                Master catalog
    ├─ 下架清单.csv                 Cumulative log of models removed from the official site
    ├─ _说明.txt                    Catalog generation notes (Chinese)
    └─ 按大类/<大类>.csv             Per-category catalogs
```

## Sample Image Counts by Category

| Category | Sample images |
|---|---:|
| Sockets & Switches (插座开关) | 3145 |
| Lighting (照明) | 2338 |
| Personal Care & Living (个护与起居) | 1180 |
| Environmental Appliances (环境电器) | 1139 (1,140 models, 1 without image) |
| Kitchen Appliances (厨房电器) | 662 |
| Bathroom (卫浴) | 499 |
| Cleaning Appliances (清洁电器) | 478 |
| Security (安防) | 461 |
| Sports & Health (运动健康) | 410 |
| Audio & Video (影音娱乐) | 206 |
| Sensors (传感器) | 202 |
| Routers & Gateways (路由网关) | 93 |
| Pets & Plants (宠物与植物) | 55 |
| Office & Learning (办公学习) | 43 |
| Others (其他) | 40 |
| Travel & In-Car (出行车载) | 38 |
| New Arrivals (新上线) | 1 |
| **Total** | **10990** |

> Note: the table above counts **currently listed** assets only; each row is the count of listed sample images in that period's catalog (CSV) and matches the total. The 26 sample images of officially removed models are still kept in the directory tree (each directory holds additional retained images beyond the numbers above); the 2 `aux.*` images in "Environmental Appliances" cannot be checked out on Windows due to reserved device names, so the repository's `全部示例样图/` and `分类示例样图/` trees each contain 11,014 images (10,988 listed + 26 retained); all 11,016 images are available in the Release archives.
>
> Data-quality note: in the 2026-10-25 snapshot, 6 rows of this table were mistakenly computed from directory-tree file counts (including retained images of removed models), which did not match the total. That period has been corrected back to the listed basis, including its change log and Release notes. The 2026-09-28 / 2026-10-09 / 2026-10-19 periods were already on the listed basis and were correct.

## Catalog Fields

`清单/00_总清单.csv` (UTF-8 with BOM, opens directly in Excel) has one row per product model, with fields: `大类` (category), `品牌` (brand), `产品名称` (product name), `型号` (model), `图片文件名` (image file name), `备注` (remarks). Models removed from the official website are still kept in their original category and sort position in every CSV, with the `备注` column set to 「官网已移除该型号」; all other rows have an empty `备注`, so you can filter on that column. `清单/下架清单.csv` separately accumulates every model removed from the official website across periods, with fields 「上期快照」 (previous snapshot) and 「本期快照」 (current snapshot); new rows are appended over time. `清单/按大类/` holds the per-category catalogs; `清单/_说明.txt` describes how the catalogs are generated (in Chinese).

> About removal dates: the Mi Home API does not provide the actual removal date of a product. 「上期快照」/「本期快照」 are merely the two snapshot dates against which a removal was observed (the model was still listed in the former and already missing in the latter). **All we can say is that the model disappeared within the interval between those two snapshots — this is not an official delisting date.** Do not infer a specific removal day from them.

## Related Apps

- This image library is the data source of **[mijia-product-gallery](https://github.com/iop666/mijia-product-gallery)**: a WinUI 3 desktop app for offline browsing, searching, filtering, favoriting, and exporting all Mi Home / ecosystem product sample images in this library;
- It also serves **MiHome-Windows (custom edition)** (<https://github.com/iop666/MiHome-Windows>): used as offline product image assets for its virtual test home (mock);
- The scraping and catalog scripts are one-off tools and are not distributed with this repository;
- Each snapshot is published with a date tag (e.g. `2026-09-28`); the full source archive of each period can be downloaded from the Releases page. The `aux.*` reserved-name images are provided as a supplementary attachment: <https://github.com/iop666/mijia-product-icons/releases>

## Copyright & Terms of Use

This repository mainly collects product sample images from the Mi Home public product encyclopedia, for personal study, research, software testing, and product reference organization.

Third-party product images in this repository are not original content of this project; their copyright belongs to the respective rights holders. This repository does not claim any intellectual property rights over such third-party content, including product images, product names, trademarks, or brand logos.

This project is provided for study, research, and software testing purposes only. **Commercial use and redistribution for profit are prohibited.** Unless explicitly authorized by the respective rights holders, this repository grants no third party any right to commercially use, sublicense, or redistribute the above third-party content.

This notice does not constitute a license for any third-party content. This snapshot reflects the state of the product library at the time of collection; it does not imply that any product is currently on sale or discontinued. Refer to official information for authoritative model and naming details.

If you believe any content in this repository infringes your legitimate rights, please contact the repository maintainer. See [THIRD-PARTY-NOTICES.md](THIRD-PARTY-NOTICES.md) for the English notice.

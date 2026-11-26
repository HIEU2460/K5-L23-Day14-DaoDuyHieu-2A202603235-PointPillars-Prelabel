# Báo cáo Day 14 — Đào Duy Hiếu — 2A202603235

- Mã học viên dùng với `--student`: `235`
- `seed_tag` trong `frames_A.txt`: `393590736f`

## 1. Dự đoán trước sweep (bước 5b)
- Tham số tôi nghĩ giảm công sửa nhiều nhất: **[TỰ ĐIỀN TRƯỚC SWEEP]**
- Vì sao (dựa trên ảnh BEV tập A và quan sát box thừa/box sót): **[TỰ ĐIỀN TRƯỚC SWEEP]**

## 2. Tập A: sửa tay và tune

Kết quả cấu hình gốc trên ba frame `s01f08`, `s02f52` và `s05f18`:

| Cấu hình | Xóa | Thêm | Sửa | Chi phí |
|---|---:|---:|---:|---:|
| Gốc | 78 | 4 | 0 | 27.4 |
| `best_config.json` | **[SAU SWEEP]** | **[SAU SWEEP]** | **[SAU SWEEP]** | **[SAU SWEEP]** |

- Tham số đã đổi trong `best_config.json`: **[ĐIỀN SAU SWEEP]**
- Kết quả leave-one-out (dán nguyên các dòng `scripts/pp_sweep.py` in ra): **[ĐIỀN SAU SWEEP]**
- Cấu hình có ổn định trên từng frame không? Vì sao tôi vẫn chọn (hoặc không chọn) nó: **[HỌC VIÊN TỰ NHẬN XÉT SAU KHI ĐỌC LEAVE-ONE-OUT]**

## 3. Trước/sau (bước 8)

> Chạy `scripts/pp_compare.py`, chọn một ảnh thực tế trong `d14_235/compare/`, rồi thay `<frame>` bên dưới.

![so sánh](../../d14_235/compare/<frame>.jpg)

- `scripts/pp_compare.py` báo giảm (hoặc tăng) **[ĐIỀN SAU BƯỚC 8]**% công sửa trên tập A.
- Dự đoán ở mục 1 đúng hay sai? Giải thích bằng số box xóa/thêm/sửa: **[HỌC VIÊN TỰ ĐỐI CHIẾU; AI KHÔNG VIẾT THAY]**

## 4. Tập B

Số đo từ lệnh:

```powershell
python scripts/pp_prelabel.py --data "$DataVF" --frames "d14_235/frames_B.txt" --config "d14_235/best_config.json" --gt "d14_235/ref_B.json"
```

| Xóa | Thêm | Sửa | Chi phí |
|---:|---:|---:|---:|
| **[SAU KHI SỬA ĐỦ 12 FRAME]** | **[SAU KHI SỬA ĐỦ 12 FRAME]** | **[SAU KHI SỬA ĐỦ 12 FRAME]** | **[SAU KHI SỬA ĐỦ 12 FRAME]** |

- Loại box tốn công sửa nhất ở tập B: **[ĐIỀN SAU KHI REVIEW TẬP B]**

## 5. Giới hạn

- Việc tune chỉ dựa trên ba frame tập A nên cấu hình được chọn có nguy cơ overfit và không chắc khái quát tốt sang 12 frame tập B.
- PointPillars được huấn luyện trên KITTI, trong khi dữ liệu VF khác về cảm biến, góc nhìn và phân bố dữ liệu; KITTI cũng không có lớp Truck và Bus như bộ nhãn của bài.
- Chi phí `0.3·xóa + 1.0·thêm + 0.5·sửa` là thước đo quy ước, không phải thời gian sửa nhãn thực tế.

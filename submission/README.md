# Lô nộp — Ngày 11 · Road Elements & SVM

Học viên: Đặng Minh Huy · `<tên>` = **DangMinhHuy** · Guideline: Road v1.0 · `revision` 1

Cấu trúc theo [`docs/delivery_road_v1.0.md`](../docs/delivery_road_v1.0.md) (đúng 5 file bắt buộc):

| File | Nội dung | Trạng thái |
| --- | --- | --- |
| `DangMinhHuy-front.zip` | CVAT for images 1.1, không kèm ảnh; A01–A16 (16 ảnh) | `lint` mở lại được ✓ |
| `DangMinhHuy-fisheye.zip` | CVAT for images 1.1, không kèm ảnh; B01–B12 (12 ảnh) | `lint` mở lại được ✓ |
| `DangMinhHuy-manifest.json` | Manifest do `road_check lint --manifest` tạo, `contains_images: false` ✓ | ✓ |
| `DangMinhHuy-qc1-for-ban-duoc-kiem.md` | Phiếu QC 1 — **đổi tên** thành `...-for-<tên bạn>.md` và điền sau khi nhận lô của bạn được ghép | chờ |
| `DangMinhHuy-report.md` | Báo cáo cá nhân (mục 3, 7a viết từ lỗi thật của `lint`) | ✓ |
| `images/` | 4 ảnh chụp cho mục 6 của báo cáo | ✓ |

## Kiểm lại trước khi nộp

```bash
cd submission
PYTHONPATH=../src python -m road_lab.road_check lint DangMinhHuy-front.zip DangMinhHuy-fisheye.zip \
    --manifest DangMinhHuy-manifest.json --name DangMinhHuy --revision 1
```

Còn **14 cảnh báo**, trong đó 8 dòng QC1-02 mức **nặng** (A05, A06, A07, A08, A09, A12, A14 thiếu L1/R1).
Theo đặc tả, ngoại lệ duy nhất là ảnh mà coach xác nhận không thấy vạch → phải ghi mã ảnh vào phiếu QC 1.
Danh sách chi tiết + việc cần làm ở phụ lục cuối [`DangMinhHuy-report.md`](DangMinhHuy-report.md).

Hai file zip bị `.gitignore` (`*.zip`) nên được thêm vào git bằng `git add -f`; đây là file nhãn, không chứa ảnh.

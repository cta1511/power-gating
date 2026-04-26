# Power Gating

Project thiết kế và mô phỏng các mạch logic có áp dụng kỹ thuật power gating trên môi trường Cadence/OpenAccess.

Repository này lưu các cell schematic, symbol, testbench và tài liệu liên quan đến việc khảo sát power gating cho một số mạch logic cơ bản như NAND, XOR, BUFFER, DFF và FULL ADDER.

## Nội Dung Chính

- Thiết kế các cổng logic cơ bản.
- So sánh các phiên bản mạch thường, mạch có power gating và các biến thể dual/diode.
- Lưu cell schematic, symbol và testbench dưới dạng OpenAccess database.
- Kèm tài liệu ghi chú kết quả/nhận xét trong file Word.

## Cấu Trúc Thư Mục

| Thư mục / File | Mô tả |
| --- | --- |
| `LogicGates/` | Các cổng logic cơ bản: AND, OR, NOT, XOR, BUFFER. |
| `Power_gating/` | Thiết kế power gating ban đầu. |
| `Power_gating_ver2/` | Phiên bản power gating thứ hai và cell `Ver2`. |
| `Power_gating_ver3/` | Phiên bản power gating thứ ba, gồm schematic và symbol. |
| `Tatcamach_1/` | Các mạch NAND, FULL ADDER, DFF và các biến thể 1MOS/3MOS. |
| `Tatcamach_2/` | Bộ thiết kế mở rộng với BUFFER, NAND, XOR, DFF, FULL ADDER và các biến thể power gating. |
| `CUOI_KY_SYMBOL/` | Các cell top, symbol và testbench dùng cho phần tổng hợp/báo cáo cuối kỳ. |
| `TEST/` | Các cell test và testbench cho NAND/XOR. |
| `Đường xanh lá đầu tiên là Vhold.docx` | Tài liệu ghi chú liên quan đến đường tín hiệu Vhold. |

## Định Dạng Dữ Liệu

Project sử dụng cấu trúc thư mục của Cadence/OpenAccess. Các file quan trọng gồm:

- `sch.oa`: dữ liệu schematic.
- `symbol.oa`: dữ liệu symbol.
- `master.tag`: thông tin view của cell.
- `data.dm`, `.oalib`, `cdsinfo.tag`: metadata của thư viện/cell.
- `thumbnail_128x128.png`: ảnh xem trước của schematic/symbol.

## Cách Sử Dụng

1. Clone repository:

   ```bash
   git clone https://github.com/cta1511/power-gating.git
   ```

2. Mở project trong môi trường Cadence Virtuoso/OpenAccess.

3. Nạp các thư viện cần dùng từ các thư mục như `LogicGates`, `Power_gating_ver3`, `Tatcamach_2`, `CUOI_KY_SYMBOL`.

4. Mở các cell schematic hoặc testbench từ Library Manager để xem, chỉnh sửa và chạy mô phỏng.

## Lưu Ý Khi Cập Nhật Project

Repository đã bỏ qua các file tạm và file lock của hệ thống/Cadence, bao gồm:

- `.DS_Store`
- `*.cdslck*`
- `sch.oa.cadence.*.tmp.*`
- thư mục kết quả tạm `.tmpADEDir`

Khi commit thay đổi mới, chỉ nên đưa lên các file thiết kế, symbol, schematic, testbench và tài liệu cần lưu trữ.

## Tác Giả

Project được thực hiện phục vụ việc thiết kế và khảo sát mạch power gating.

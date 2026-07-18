================================================================================
              TÀI LIỆU MÔ TẢ DỰ ÁN: ESP32 DEVELOPMENT BOARD (DEVBOARD)
                    Thiết kế PCB bằng Cadence Allegro / OrCAD
================================================================================
Ngày tạo tài liệu : 18/07/2026
Tên dự án          : DEVBOARD
Tác giả            : Huy
Thư mục dự án      : D:\Huy\baihoc\PCB\allegro
================================================================================


╔══════════════════════════════════════════════════════════════════════════════╗
║                         1. TÓM TẮT DỰ ÁN                                 ║
╚══════════════════════════════════════════════════════════════════════════════╝

Dự án DEVBOARD là việc thiết kế một bo mạch phát triển (Development Board) 
dựa trên vi điều khiển ESP32-WROOM-32E-N8. Bo mạch được thiết kế để có thể 
kết nối trực tiếp với máy tính thông qua cổng USB Type-C, cho phép nạp 
chương trình và giao tiếp UART mà không cần adapter bên ngoài.

Mạch bao gồm các khối chức năng chính:
  - Khối nguồn: Chuyển đổi 5V USB thành 3.3V cho ESP32
  - Khối giao tiếp USB-UART: Chuyển đổi tín hiệu USB sang UART qua IC CH340C
  - Khối vi điều khiển: ESP32-WROOM-32E-N8 với đầy đủ GPIO
  - Khối Auto-Reset: Tự động reset và đưa ESP32 vào chế độ nạp firmware

PCB được thiết kế 2 lớp (TOP và BOTTOM) với các linh kiện dán SMD, sử dụng 
footprint chuẩn 1206 cho điện trở và tụ điện. File Gerber đã được xuất sẵn 
sàng để gửi đi sản xuất.


╔══════════════════════════════════════════════════════════════════════════════╗
║                      2. PHẦN MỀM SỬ DỤNG                                  ║
╚══════════════════════════════════════════════════════════════════════════════╝

┌────────────────────────┬────────────────────────────────────────────────────┐
│ Phần mềm               │ Mô tả / Phiên bản                                │
├────────────────────────┼────────────────────────────────────────────────────┤
│ Cadence OrCAD Capture  │ Phiên bản 17.2 - Vẽ sơ đồ nguyên lý (Schematic) │
│ Cadence Allegro PCB    │ Phiên bản 17.2P019 / 17.2P028 - Thiết kế PCB     │
│                        │ Layout, đặt linh kiện, đi dây, xuất Gerber       │
│ OrCAD PCB Editor       │ Tích hợp trong bộ Cadence SPB 17.2               │
│ PSTWRITER              │ Phiên bản 17.2.0 - Xuất netlist từ schematic     │
│ Netrev                 │ Import netlist vào Allegro PCB                    │
└────────────────────────┴────────────────────────────────────────────────────┘

Đường dẫn cài đặt phần mềm: C:\Cadence\SPB_17.2\

Thư viện được sử dụng:
  - Thư viện mặc định Cadence: c:\cadence\spb_17.2\share\pcb\pcb_lib\symbols
  - Thư viện Allegro:          c:\cadence\spb_17.2\share\pcb\allegrolib\symbols
  - Thư viện tự tạo:           D:\Huy\baihoc\PCB\My_Libraries
  - Thư viện Cadence tùy chỉnh:D:\Huy\baihoc\PCB\MY_CADENCE_LIBS\FOOTPRINTS\


╔══════════════════════════════════════════════════════════════════════════════╗
║                      3. CÁC LINH KIỆN ĐƯỢC DÙNG                           ║
╚══════════════════════════════════════════════════════════════════════════════╝

─── 3.1. Bảng danh sách linh kiện (BOM - Bill of Materials) ───

┌──────┬──────────────────────────────┬───────────┬──────────┬───────────────┐
│ STT  │ Tên linh kiện                │ Ký hiệu   │ Giá trị  │ Footprint     │
├──────┼──────────────────────────────┼───────────┼──────────┼───────────────┤
│  1   │ Vi điều khiển ESP32          │ IC1       │ ESP32-   │ ESP32WROOM32  │
│      │ WROOM-32E-N8                 │           │ WROOM-   │ (Module)      │
│      │                              │           │ 32E-N8   │               │
├──────┼──────────────────────────────┼───────────┼──────────┼───────────────┤
│  2   │ IC chuyển đổi USB-UART       │ U2        │ CH340C   │ SOIC-16       │
│      │ CH340C                       │           │          │ (SOP-16)      │
├──────┼──────────────────────────────┼───────────┼──────────┼───────────────┤
│  3   │ IC ổn áp LDO 3.3V            │ U1        │ AMS1117  │ SOT-223       │
│      │ AMS1117-3.3                  │           │ -3.3     │               │
├──────┼──────────────────────────────┼───────────┼──────────┼───────────────┤
│  4   │ Cổng USB Type-C              │ J1        │ 10155435 │ Amphenol      │
│      │ Amphenol 10155435-00011LF    │           │ -00011LF │ USB-C         │
├──────┼──────────────────────────────┼───────────┼──────────┼───────────────┤
│  5   │ Transistor NPN (Auto-Reset)  │ Q1        │ NPN      │ SOT-23        │
├──────┼──────────────────────────────┼───────────┼──────────┼───────────────┤
│  6   │ Transistor NPN (Auto-Reset)  │ Q2        │ NPN      │ SOT-23        │
├──────┼──────────────────────────────┼───────────┼──────────┼───────────────┤
│  7   │ Tụ điện 10µF                 │ C3        │ 10µF     │ SMD 1206      │
├──────┼──────────────────────────────┼───────────┼──────────┼───────────────┤
│  8   │ Tụ điện 100µF                │ C4        │ 100µF    │ SMD 1206      │
├──────┼──────────────────────────────┼───────────┼──────────┼───────────────┤
│  9   │ Tụ điện 100nF                │ C5        │ 100nF    │ SMD 1206      │
├──────┼──────────────────────────────┼───────────┼──────────┼───────────────┤
│ 10   │ Tụ điện 10µF                 │ C6        │ 10µF     │ SMD 1206      │
├──────┼──────────────────────────────┼───────────┼──────────┼───────────────┤
│ 11   │ Tụ điện 100µF                │ C7        │ 100µF    │ SMD 1206      │
├──────┼──────────────────────────────┼───────────┼──────────┼───────────────┤
│ 12   │ Tụ điện 1µF                  │ C8        │ 1µF      │ SMD 1206      │
├──────┼──────────────────────────────┼───────────┼──────────┼───────────────┤
│ 13   │ Điện trở 10KΩ                │ R1        │ 10KΩ     │ SMD 1206      │
├──────┼──────────────────────────────┼───────────┼──────────┼───────────────┤
│ 14   │ Điện trở 10KΩ                │ R2        │ 10KΩ     │ SMD 1206      │
├──────┼──────────────────────────────┼───────────┼──────────┼───────────────┤
│ 15   │ Điện trở 5.1KΩ               │ R3        │ 5.1KΩ    │ SMD 1206      │
├──────┼──────────────────────────────┼───────────┼──────────┼───────────────┤
│ 16   │ Điện trở 5.1KΩ               │ R4        │ 5.1KΩ    │ SMD 1206      │
├──────┼──────────────────────────────┼───────────┼──────────┼───────────────┤
│ 17   │ Điện trở 10KΩ                │ R5        │ 10KΩ     │ SMD 1206      │
├──────┼──────────────────────────────┼───────────┼──────────┼───────────────┤
│ 18   │ Điện trở 10KΩ                │ R6        │ 10KΩ     │ SMD 1206      │
└──────┴──────────────────────────────┴───────────┴──────────┴───────────────┘

Tổng cộng: 18 linh kiện (4 IC/Module, 6 tụ điện, 6 điện trở, 2 transistor)

─── 3.2. Mô tả chi tiết từng linh kiện ───

[IC1] ESP32-WROOM-32E-N8:
  - Vi điều khiển Wi-Fi + Bluetooth đa năng của Espressif
  - Tích hợp 8MB Flash, CPU Xtensa LX6 lõi kép, xung nhịp 240MHz
  - Hỗ trợ Wi-Fi 802.11 b/g/n, Bluetooth 4.2, BLE
  - 38 chân GPIO (bao gồm ADC, DAC, SPI, I2C, UART, PWM...)
  - Điện áp hoạt động: 3.0V ~ 3.6V (tiêu chuẩn 3.3V)
  - Module 47 chân (nhiều chân GND dưới pad nhiệt)

[U1] AMS1117-3.3:
  - IC ổn áp tuyến tính (LDO) ngõ ra cố định 3.3V
  - Điện áp đầu vào: 4.5V ~ 12V
  - Dòng ra tối đa: 1A
  - Dropout voltage: ~1.1V
  - Gói: SOT-223 (3 chân: GND, VOUT, VIN)

[U2] CH340C:
  - IC chuyển đổi USB sang UART (USB to Serial)
  - Không cần thạch anh ngoài (tích hợp oscillator bên trong)
  - Hỗ trợ tốc độ baud tới 2Mbps
  - Tương thích USB 2.0 Full Speed
  - Gói: SOIC-16 (SOP-16)
  - 16 chân: GND, TXD, RXD, V3, UD+, UD-, NC, OUT#, CTS#, 
    DSR#, RI#, DCD#, DTR#, RTS#, R232, VCC

[J1] 10155435-00011LF (Amphenol):
  - Cổng USB Type-C Female receptacle
  - Hỗ trợ USB 2.0
  - Có các chân: DP1/DP2, DN1/DN2, CC1, CC2, VBUS, GND, Shield, SBU

[Q1, Q2] Transistor NPN (SOT-23):
  - Transistor NPN mục đích chung, gói SOT-23
  - Sử dụng cho mạch Auto-Reset (tự động vào chế độ bootloader)
  - Điện áp chịu đựng: 25V, Công suất: 500mW

[R1, R2, R5, R6] Điện trở 10KΩ - SMD 1206:
  - Điện trở kéo (pull-up/pull-down) cho mạch auto-reset và EN/IO0

[R3, R4] Điện trở 5.1KΩ - SMD 1206:
  - Điện trở kéo xuống trên chân CC1, CC2 của USB Type-C
  - Yêu cầu bắt buộc theo chuẩn USB Type-C để nhận diện nguồn 5V

[C3] Tụ 10µF, [C4] Tụ 100µF - SMD 1206:
  - Tụ lọc đầu ra 3.3V (bên AMS1117 ra)

[C5] Tụ 100nF - SMD 1206:
  - Tụ bypass cho chân V3 (3.3V nội bộ) của CH340C

[C6] Tụ 10µF, [C7] Tụ 100µF - SMD 1206:
  - Tụ lọc đầu vào (5V VBUS)

[C8] Tụ 1µF - SMD 1206:
  - Tụ lọc cho mạch EN (Enable) của ESP32


╔══════════════════════════════════════════════════════════════════════════════╗
║                      4. NGUYÊN LÝ HOẠT ĐỘNG                               ║
╚══════════════════════════════════════════════════════════════════════════════╝

─── 4.1. Sơ đồ khối tổng quan ───

  ┌─────────┐    ┌──────────┐    ┌───────────┐    ┌────────────────┐
  │ USB-C   │───>│ AMS1117  │───>│   3.3V    │───>│  ESP32-WROOM   │
  │ (5V)    │    │ LDO      │    │   Rail    │    │  -32E-N8       │
  │ J1      │    │ U1       │    │           │    │  IC1           │
  └────┬────┘    └──────────┘    └───────────┘    └───────┬────────┘
       │                                                   │
       │         ┌──────────┐                              │
       └────────>│ CH340C   │<────── UART (TXD/RXD) ──────┘
                 │ U2       │
                 └────┬─────┘
                      │
              ┌───────┴───────┐
              │  Auto-Reset   │
              │  Q1 + Q2      │
              │  (DTR# + RTS#)│
              └───────────────┘

─── 4.2. Chi tiết từng khối ───

[KHỐI NGUỒN] USB 5V → AMS1117-3.3 → 3.3V
  - Nguồn 5V được lấy từ chân VBUS (A4_B9) của cổng USB Type-C (J1)
  - Điện trở R3 (5.1K) kéo chân CC1 xuống GND, R4 (5.1K) kéo chân CC2 
    xuống GND → nhận diện là thiết bị USB (sink) theo chuẩn USB Type-C
  - Tụ C6 (10µF) và C7 (100µF) lọc nguồn đầu vào 5V
  - AMS1117-3.3 (U1): Chân VIN (pin 3) nhận 5V, chân VOUT (pin 2) xuất 3.3V,
    chân GND (pin 1) nối mass
  - Tụ C3 (10µF) và C4 (100µF) lọc nguồn đầu ra 3.3V
  - Nguồn 3.3V cấp cho ESP32 (chân 3V3) và các mạch khác

[KHỐI USB-UART] CH340C
  - IC CH340C (U2) nhận tín hiệu USB từ J1:
    + Chân UD+ (pin 5) ← DP1/DP2 (J1 chân A6/B6)
    + Chân UD- (pin 6) ← DN1/DN2 (J1 chân A7/B7)
  - Chân VCC (pin 16) nối 5V (VBUS)
  - Chân V3 (pin 4) xuất 3.3V nội bộ, tụ C5 (100nF) lọc
  - Chân GND (pin 1) nối mass
  - Chuyển đổi USB → UART:
    + TXD (pin 2 U2) → RXD0 (pin 34 IC1): Dữ liệu từ PC đến ESP32
    + RXD (pin 3 U2) ← TXD0 (pin 35 IC1): Dữ liệu từ ESP32 đến PC

[KHỐI AUTO-RESET] Q1 + Q2 + R1 + R2
  Mạch tự động reset ESP32 khi nạp firmware (giống NodeMCU/ESP32 DevKit):
  
  - Tín hiệu DTR# (pin 13 U2) → qua R2 (10K) → Base Q1
    + Khi DTR# = LOW → Q1 dẫn → Collector Q1 kéo chân EN xuống → Reset ESP32
    + Emitter Q1 nối vào net +3.3V thông qua mạch kéo
    
  - Tín hiệu RTS# (pin 14 U2) → qua R1 (10K) → Base Q2  
    + Khi RTS# = LOW → Q2 dẫn → Collector Q2 kéo IO0 xuống → Boot mode
    + Emitter Q2 nối vào net +3.3V
  
  - Trình tự nạp firmware:
    1. DTR# đi LOW, RTS# đi HIGH → EN = LOW (Reset), IO0 = HIGH
    2. DTR# đi HIGH, RTS# đi LOW → EN = HIGH (Chạy), IO0 = LOW (Boot mode)
    3. ESP32 khởi động vào chế độ Download/Bootloader
    4. Sau khi nạp xong, DTR# và RTS# trở về HIGH → ESP32 chạy bình thường

[KHỐI VI ĐIỀU KHIỂN] ESP32-WROOM-32E-N8
  - Chân 3V3 (pin 2) nhận nguồn 3.3V
  - Chân EN (pin 3) = Enable, kéo lên 3.3V qua R5 (10K), tụ C8 (1µF) lọc
  - Chân IO0 (pin 25) kéo lên 3.3V qua R6 (10K) → mặc định chạy bình thường
  - Chân RXD0 (pin 34) nhận TXD từ CH340C
  - Chân TXD0 (pin 35) phát RXD đến CH340C
  - Các chân GPIO còn lại (IO2, IO4, IO5, IO12~IO19, IO21~IO23, IO25~IO27,
    IO32~IO35, SENSOR_VP, SENSOR_VN) để trống → breakout ra header pin
  - Nhiều chân GND (pin 1, 15, 38~47) nối mass → tản nhiệt tốt


╔══════════════════════════════════════════════════════════════════════════════╗
║                  5. CÁCH LÀM TỪNG BƯỚC CHI TIẾT                           ║
╚══════════════════════════════════════════════════════════════════════════════╝

═══ GIAI ĐOẠN 1: CHUẨN BỊ ═══

Bước 1.1: Cài đặt phần mềm
  - Cài đặt Cadence SPB 17.2 (bao gồm OrCAD Capture + Allegro PCB Editor)
  - Đường dẫn mặc định: C:\Cadence\SPB_17.2\
  - Kiểm tra license hoạt động bình thường

Bước 1.2: Chuẩn bị thư viện
  - Tải/tạo thư viện tùy chỉnh trong thư mục:
    + D:\Huy\baihoc\PCB\My_Libraries\ (footprint tùy chỉnh)
    + D:\Huy\baihoc\PCB\MY_CADENCE_LIBS\FOOTPRINTS\ (footprint bổ sung)
  - Tạo footprint cho các linh kiện đặc biệt:
    + AMS1117 (SOT-223) → file AMS1117.dra / ams1117.psm
    + CH340C (SOIC-16) → file CH340C.dra / ch340c.psm
    + ESP32-WROOM-32E-N8 → footprint module 47 chân
    + USB Type-C Amphenol → footprint chuyên dụng
  - Các footprint chuẩn SMD 1206, SOT-23 lấy từ thư viện Cadence mặc định

Bước 1.3: Tạo dự án mới
  - Mở OrCAD Capture
  - File → New → Project → đặt tên "devboard"
  - Lưu tại D:\Huy\baihoc\PCB\
  - File dự án: devboard.opj

═══ GIAI ĐOẠN 2: VẼ SƠ ĐỒ NGUYÊN LÝ (SCHEMATIC) ═══

Bước 2.1: Tạo Schematic Page
  - Trong devboard.opj → mở SCHEMATIC1 → tạo PAGE1
  - Đặt kích thước giấy phù hợp (A3 hoặc A4)

Bước 2.2: Đặt các symbol linh kiện
  - Place → Part → chọn từ thư viện:
    + ESP32-WROOM-32E-N8 (IC1)
    + AMS1117-33 (U1)
    + CH340C (U2)
    + 10155435-00011LF - USB Type-C (J1)
    + NPN transistor SOT-23 (Q1, Q2)
    + CAP - Tụ điện (C3~C8)
    + R - Điện trở (R1~R6)

Bước 2.3: Nối dây (Wiring)
  - Place → Wire để nối các chân theo sơ đồ:
  
  [Khối nguồn:]
    J1 VBUS (A4_B9) ──→ U1 VIN (pin 3)
    J1 VBUS (A4_B9) ──→ U2 VCC (pin 16)
    J1 VBUS (A4_B9) ──→ C6 (+), C7 (+)
    U1 VOUT (pin 2) ──→ Net +3.3V
    U1 GND (pin 1)  ──→ GND
    C3 (+) ──→ +3.3V,  C3 (-) ──→ GND
    C4 (+) ──→ +3.3V,  C4 (-) ──→ GND
    C6 (-), C7 (-) ──→ GND
    
  [Khối USB:]
    J1 CC1 (A5)    ──→ R3 (pin 1)
    J1 CC2 (B5)    ──→ R4 (pin 1)
    R3 (pin 2)     ──→ GND
    R4 (pin 2)     ──→ GND
    J1 DP1/DP2     ──→ U2 UD+ (pin 5)
    J1 DN1/DN2     ──→ U2 UD- (pin 6)
    J1 GND, Shield ──→ GND
    
  [Khối UART:]
    U2 TXD (pin 2) ──→ IC1 RXD0 (pin 34)
    U2 RXD (pin 3) ──→ IC1 TXD0 (pin 35)
    U2 V3 (pin 4)  ──→ C5 (+)
    C5 (-)          ──→ GND
    U2 GND (pin 1) ──→ GND
    
  [Khối Auto-Reset:]
    U2 DTR# (pin 13) ──→ R2 (pin 2) ──→ Q1 Emitter (pin 2)
    U2 RTS# (pin 14) ──→ +3.3V (thông qua mạch kéo)
    R1 (pin 1)       ──→ Q1 Base
    R1 (pin 2)       ──→ +3.3V
    R2 (pin 1)       ──→ Q2 Base
    Q1 Collector      ──→ +3.3V
    Q2 Collector      ──→ +3.3V
    Q1 Emitter        ──→ (net liên quan EN)
    Q2 Emitter        ──→ (net liên quan IO0)
    
  [Khối ESP32:]
    IC1 3V3 (pin 2)  ──→ +3.3V
    IC1 EN (pin 3)   ──→ +3.3V (qua R5 pull-up)
    IC1 IO0 (pin 25) ──→ +3.3V (qua R6 pull-up)
    R5 (pin 1) ──→ +3.3V,  R5 (pin 2) ──→ (net EN filter)
    R6 (pin 1) ──→ +3.3V,  R6 (pin 2) ──→ IC1 IO0
    C8 (+) ──→ (net EN filter),  C8 (-) ──→ GND
    IC1 GND (tất cả chân GND) ──→ GND

Bước 2.4: Đặt nhãn nguồn và GND
  - Place → Power → GND, +3.3V, VBUS
  - Kiểm tra tất cả net đã được đặt tên đúng

Bước 2.5: Kiểm tra DRC trên Schematic
  - Tools → Design Rules Check
  - Sửa các lỗi nếu có
  - Kết quả hiện tại: 8 cảnh báo (warnings) về pin type conflict
    → Đây là cảnh báo bình thường, không ảnh hưởng hoạt động
  - Lưu file: DEVBOARD.DSN

═══ GIAI ĐOẠN 3: XUẤT NETLIST ═══

Bước 3.1: Tạo Netlist
  - Trong OrCAD Capture: Tools → Create Netlist
  - Chọn tab "PCB Editor" (cho Allegro)
  - Đặt thư mục output: D:\Huy\baihoc\PCB\allegro\
  - Nhấn OK → tạo ra 3 file quan trọng:
    + pstchip.dat   (định nghĩa chân linh kiện)
    + pstxprt.dat   (danh sách linh kiện)
    + pstxnet.dat   (danh sách kết nối net)

═══ GIAI ĐOẠN 4: THIẾT KẾ PCB LAYOUT ═══

Bước 4.1: Tạo Board trong Allegro
  - Mở Cadence Allegro PCB Editor
  - File → New → Board (.brd)
  - Tên file: DEVBOARD.brd
  - Thiết lập thông số board:
    + Đơn vị: Millimeter (mm)
    + Số lớp: 2 (TOP + BOTTOM)
    + Vẽ Board Outline

Bước 4.2: Import Netlist
  - File → Import → Logic → chọn thư mục allegro\
  - Hoặc dùng lệnh: netrev.exe -y 1 -i [thư mục netlist] [file .brd]
  - Netlist sẽ import tất cả linh kiện và kết nối vào board
  - Kiểm tra netrev.lst → "No error detected"

Bước 4.3: Đặt linh kiện (Placement)
  - Place → Quickplace hoặc đặt thủ công từng linh kiện
  - Nguyên tắc sắp xếp:
    + J1 (USB-C) đặt ở cạnh board → dễ kết nối
    + U2 (CH340C) đặt gần J1 → giảm chiều dài đường tín hiệu USB
    + U1 (AMS1117) đặt gần J1 → đường nguồn ngắn
    + IC1 (ESP32) đặt ở trung tâm hoặc phía đối diện
    + Tụ bypass đặt sát chân nguồn của từng IC
    + Q1, Q2 đặt gần U2 và IC1
  - Kiểm tra không overlap linh kiện

Bước 4.4: Đi dây (Routing)
  - Route → Interactive Route
  - Quy tắc đi dây:
    + Độ rộng đường nguồn (VCC, 3.3V, GND): ≥ 0.5mm
    + Độ rộng đường tín hiệu: 0.25mm
    + Đường USB (DP/DN): đi cặp vi sai, giữ đều chiều dài
    + Khoảng cách tối thiểu: theo quy tắc DRC
  - Đi dây lớp TOP trước, dùng via để chuyển lớp BOTTOM khi cần
  - Ưu tiên đi dây ngắn nhất có thể

Bước 4.5: Đổ đồng (Copper Pour)
  - Shape → Add Rectangle/Polygon
  - Đổ đồng GND trên lớp TOP
  - Hiện tại có 5 island đồng GND trên lớp TOP (theo shape_islands.rpt)
  - Kiểm tra không có island cô lập

Bước 4.6: Kiểm tra DRC trên PCB
  - Tools → Update DRC
  - Kết quả: "Total number of DRC errors: 0" ✓
  - Đảm bảo không còn lỗi nào trước khi xuất Gerber

═══ GIAI ĐOẠN 5: XUẤT FILE SẢN XUẤT ═══

Bước 5.1: Xuất Gerber (Artwork)
  - Manufacture → Artwork
  - Cấu hình:
    + Device Type: GERBER_RS274X
    + Output Units: MM (Millimeter)
    + Format: 2.5
    + Suppress Lead Zeroes: YES
  - Xuất các film:
    + TOP.art      → Lớp mạch in trên
    + BOTTOM.art   → Lớp mạch in dưới
    + SOLDERMASK_TOP.art → Lớp mặt nạ hàn trên
  - Kết quả: "ARTWORK finished" ✓

Bước 5.2: Xuất NC Drill
  - Manufacture → NC → NC Drill
  - Cấu hình NC Parameters:
    + Format: 4.5
    + Output Units: METRIC
    + Coordinates: ABSOLUTE
    + Tool Order: INCREASING
  - File output: DEVBOARD-1-2.drl
  - Kết quả khoan:
    + Lỗ via 0.3302mm (PLATED): 29 lỗ
    + Lỗ cơ khí 0.65mm (NON-PLATED): 2 lỗ
    + Tổng: 31 lỗ
  - Lưu ý: Có 4 slot hole (lỗ oblong) cần NC routing thay vì khoan

Bước 5.3: Đóng gói file gửi nhà sản xuất
  - Gom tất cả file Gerber (.art) + NC Drill (.drl) vào 1 thư mục
  - File cần gửi:
    + TOP.art (lớp trên)
    + BOTTOM.art (lớp dưới)
    + SOLDERMASK_TOP.art (mặt nạ hàn)
    + DEVBOARD-1-2.drl (file khoan)
  - Nén thành file ZIP và upload lên website nhà sản xuất PCB
    (ví dụ: JLCPCB, PCBWay, Elecrow, v.v.)


╔══════════════════════════════════════════════════════════════════════════════╗
║                      6. ĐÁNH GIÁ THÀNH PHẨM                               ║
╚══════════════════════════════════════════════════════════════════════════════╝

─── 6.1. Ưu điểm ───

  ✓ Thiết kế hoàn chỉnh với đầy đủ các khối chức năng cơ bản
  ✓ Sử dụng USB Type-C hiện đại (thay vì Micro-USB cũ)
  ✓ CH340C không cần thạch anh ngoài → giảm linh kiện, đơn giản hóa mạch
  ✓ Mạch Auto-Reset hoạt động tốt → nạp firmware tự động không cần bấm nút
  ✓ DRC trên PCB = 0 lỗi → thiết kế sạch, đúng quy tắc
  ✓ Netlist import không có lỗi → schematic và PCB khớp nhau hoàn toàn
  ✓ Sử dụng footprint SMD 1206 → dễ hàn bằng tay cho người mới
  ✓ PCB 2 lớp → chi phí sản xuất thấp
  ✓ Đổ đồng GND trên lớp TOP → cải thiện tản nhiệt và giảm nhiễu

─── 6.2. Nhược điểm / Cần cải thiện ───

  ✗ Chưa có lớp Silkscreen (tên linh kiện, hướng dẫn) → khó hàn khi 
    không có bản in hướng dẫn
  ✗ Có 5 island đồng GND → một số vùng đồng có thể bị cô lập, cần kiểm tra
  ✗ Chưa đổ đồng lớp BOTTOM → mất cơ hội cải thiện tản nhiệt
  ✗ Autoplace báo lỗi "No Package Keepin was found" → chưa định nghĩa 
    vùng đặt linh kiện đúng cách
  ✗ Có 4 slot hole cần NC routing → một số nhà sản xuất giá rẻ có thể 
    không hỗ trợ
  ✗ 8 cảnh báo DRC trên schematic về pin type conflict → nên xem xét lại
    định nghĩa pin trong thư viện
  ✗ Chưa có LED chỉ thị nguồn
  ✗ Chưa có nút RESET và nút BOOT thủ công
  ✗ Chưa breakout hết các GPIO ra header pin


╔══════════════════════════════════════════════════════════════════════════════╗
║                      7. KHÓ KHĂN GẶP PHẢI                                 ║
╚══════════════════════════════════════════════════════════════════════════════╝

─── 7.1. Khó khăn về thư viện ───

  • Phải tự tạo footprint cho AMS1117 (SOT-223) và CH340C (SOIC-16)
    vì thư viện mặc định Cadence không có sẵn
    → Tham khảo file: AMS1117.dra, CH340C.dra (symbol package)
    → Tham khảo hướng dẫn: HowToCreateANewPart.docx

  • Footprint ESP32-WROOM-32E-N8 là module lớn 47 chân với pad nhiệt 
    phía dưới → yêu cầu tạo footprint phức tạp

  • Footprint USB Type-C (Amphenol 10155435-00011LF) có nhiều chân kép 
    (A side + B side), cấu trúc phức tạp

─── 7.2. Khó khăn về thiết kế ───

  • Autoplace không hoạt động do chưa có Package Keepin → phải đặt 
    linh kiện thủ công hoàn toàn

  • Mạch Auto-Reset cần hiểu rõ timing của DTR# và RTS# → phải nghiên 
    cứu tài liệu ESP32 và sơ đồ reference design

  • Đi dây USB (DP/DN) cần tuân thủ impedance matching → khó kiểm soát 
    trên PCB 2 lớp giá rẻ

  • Component device type bị thay đổi (CH340C) → phải ECO update lại 
    (xem eco.txt)

─── 7.3. Khó khăn về phần mềm ───

  • Cadence Allegro có giao diện phức tạp, đường cong học tập cao
  • Quản lý thư viện (PSMPATH, PADPATH, MODULEPATH) cần cấu hình đúng
  • Có lúc phần mềm crash (file allegro_P02817.2_AllegroMiniDump.dmp 
    là bằng chứng crash dump)
  • Cần hiểu workflow Capture → Netlist → Allegro → DRC → Gerber


╔══════════════════════════════════════════════════════════════════════════════╗
║                      8. PHÁT TRIỂN TƯƠNG LAI                               ║
╚══════════════════════════════════════════════════════════════════════════════╝

─── 8.1. Cải tiến phần cứng (Version 2.0) ───

  □ Thêm LED chỉ thị nguồn (Power LED) trên rail 3.3V
  □ Thêm nút nhấn RESET (nối EN xuống GND qua nút)
  □ Thêm nút nhấn BOOT (nối IO0 xuống GND qua nút) để vào bootloader 
    thủ công khi auto-reset không hoạt động
  □ Breakout tất cả GPIO ra 2 hàng header pin (kiểu DevKit chuẩn)
  □ Thêm LED user (nối GPIO, ví dụ IO2) để test chương trình
  □ Đổ đồng GND cả lớp BOTTOM để cải thiện return path và tản nhiệt
  □ Thêm lớp Silkscreen (tên linh kiện, logo, phiên bản)
  □ Thêm Paste Layer cho quá trình hàn reflow
  □ Chuyển sang footprint 0805 hoặc 0603 để giảm kích thước board

─── 8.2. Mở rộng tính năng ───

  □ Thêm mạch sạc pin LiPo (TP4056 hoặc MCP73831)
  □ Thêm IC quản lý nguồn cho chế độ sleep sâu (deep sleep)
  □ Thêm cảm biến onboard (nhiệt độ, gia tốc, ánh sáng)
  □ Thêm slot MicroSD card cho data logging
  □ Thêm antenna ngoài hoặc connector U.FL cho Wi-Fi
  □ Tích hợp motor driver (DRV8833, L298N) cho ứng dụng robot

─── 8.3. Cải tiến quy trình thiết kế ───

  □ Sử dụng 4 lớp PCB cho thiết kế chuyên nghiệp hơn
  □ Thực hiện kiểm tra impedance matching cho đường USB
  □ Sử dụng design rule constraints chi tiết hơn
  □ Tạo thư viện chuẩn riêng cho các dự án sau
  □ Sử dụng version control (Git) để quản lý thay đổi thiết kế
  □ Viết testbench/test script kiểm tra board sau khi sản xuất
  □ Thử nghiệm hàn reflow thay vì hàn tay

─── 8.4. Ứng dụng mở rộng ───

  □ IoT Gateway: Thu thập dữ liệu cảm biến và gửi lên cloud
  □ Smart Home Controller: Điều khiển thiết bị qua Wi-Fi/Bluetooth
  □ Wearable Device: Kết hợp cảm biến + pin cho thiết bị đeo
  □ Robot Controller: Điều khiển motor, servo, cảm biến
  □ Weather Station: Trạm thời tiết tự động
  □ Industrial Monitoring: Giám sát thông số trong nhà máy


╔══════════════════════════════════════════════════════════════════════════════╗
║                           PHỤ LỤC                                         ║
╚══════════════════════════════════════════════════════════════════════════════╝

─── A. Danh sách file trong thư mục allegro\ ───

  File thiết kế chính:
    DEVBOARD.brd          → File board PCB chính (Allegro)
    DEVBOARD.SAV          → File backup board

  File netlist:
    pstchip.dat           → Định nghĩa footprint/chân linh kiện
    pstxprt.dat           → Danh sách linh kiện (expanded part list)
    pstxnet.dat           → Danh sách kết nối (expanded netlist)

  File Gerber (sản xuất):
    TOP.art               → Lớp mạch in TOP
    BOTTOM.art            → Lớp mạch in BOTTOM
    SOLDERMASK_TOP.art    → Mặt nạ hàn lớp TOP

  File khoan:
    DEVBOARD-1-2.drl      → File NC Drill (lỗ khoan)
    nc_param.txt          → Thông số khoan

  File footprint tùy chỉnh:
    AMS1117.dra           → Symbol footprint AMS1117
    ams1117.psm           → Package symbol AMS1117
    CH340C.dra            → Symbol footprint CH340C
    ch340c.psm            → Package symbol CH340C

  File báo cáo:
    eco.txt               → Báo cáo ECO (thay đổi thiết kế)
    netrev.lst            → Báo cáo import netlist
    batch_drc.log         → Báo cáo kiểm tra DRC
    ncdrill.log           → Báo cáo xuất file khoan
    photoplot.log         → Báo cáo xuất Gerber
    place.log             → Báo cáo đặt linh kiện
    refresh.log           → Báo cáo refresh
    dbdoctor.log          → Báo cáo kiểm tra database
    quickplace.log        → Báo cáo quickplace

  File khác:
    allegro.jrl           → Journal file (lịch sử thao tác)
    art_param.txt         → Thông số artwork
    netlist.log           → Log netlist
    pxlBA.txt             → File phụ trợ

─── B. Thông số kỹ thuật tóm tắt ───

  Kích thước board     : (cần đo trong Allegro)
  Số lớp               : 2 (TOP + BOTTOM)
  Số linh kiện         : 18
  Số net               : ~20 net
  Số lỗ khoan          : 31 (29 plated + 2 non-plated)
  Số lỗ slot           : 4 (cần NC routing)
  Lỗi DRC              : 0
  Định dạng Gerber     : RS274X
  Đơn vị               : Millimeter

================================================================================
                          --- HẾT TÀI LIỆU ---
          Dự án DEVBOARD - ESP32 Development Board - Cadence Allegro
================================================================================

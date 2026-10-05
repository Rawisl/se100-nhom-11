# Sơ đồ lớp chi tiết

```mermaid
classDiagram
    direction TB

    class DoiTuyen {
        +String maDoi
        +String tenDoi
        +String boMon
        +bool choPhepHoa
        +thongKeCaNhan(tv: ThanhVien, tuNgay: Date, denNgay: Date) ThongKeCaNhan
    }

    class ThanhVien {
        +String maTV
        +String hoTen
        +String sdt
        +String email
        +List~VaiTro~ cacVaiTro
        +TrangThaiTV trangThai
        +Map~String,String~ thuocTinhThem
        +Date ngayVaoDoi
        +capNhatLienLac(sdt: String, email: String) void
        +chuyenTrangThai(moi: TrangThaiTV) void
        +capTaiKhoan(tenDangNhap: String) TaiKhoan
        +xemLichBieu() List~LichBieu~
    }

    class TaiKhoan {
        +String maTK
        +String tenDangNhap
        +String matKhauBam
        +TrangThaiTaiKhoan trangThai
        +DateTime lanDangNhapCuoi
        +kichHoat(matKhauMoi: String) void
        +dangNhap(matKhau: String) bool
        +doiMatKhau(matKhauCu: String, matKhauMoi: String) void
        +khoa() void
        +moKhoa() void
    }

    class TinTuyenDung {
        +String maTin
        +String tieuDe
        +String yeuCau
        +int soLuongCan
        +Date hanNop
        +bool dangMo
        +dangTin() void
        +dongTin() void
    }

    class HoSoUngTuyen {
        +String maHoSo
        +String hoTen
        +String sdt
        +String email
        +String hoSoUrl
        +DateTime ngayNop
        +TrangThaiHoSo trangThai
        +String nhanXet
        +moiThu(hlv: ThanhVien) ThanhVien
        +tuChoi(lyDo: String) void
        +rutHoSo() void
    }

    class DanhGiaThuViec {
        +String maDG
        +Date ngayDanhGia
        +float diemChuyenMon
        +String nhanXet
        +KetQuaThuViec ketQua
        +chotKetQua() void
    }

    class QuyTacLap {
        +String maQuyTac
        +String tieuDe
        +LoaiLich loai
        +String diaDiem
        +List~int~ cacThu
        +Time gioBatDau
        +Time gioKetThuc
        +Date ngayBatDau
        +Date ngayKetThuc
        +taoCacBuoi() List~LichBieu~
        +giaHan(ngayKetThucMoi: Date) List~LichBieu~
        +suaTuBuoiNay(tu: LichBieu, gioBatDauMoi: Time, gioKetThucMoi: Time, diaDiemMoi: String) void
        +huyTuBuoiNay(tu: LichBieu, lyDo: String) void
    }

    class LichBieu {
        +String maLich
        +String tieuDe
        +LoaiLich loai
        +TrangThaiLich trangThai
        +DateTime batDau
        +DateTime ketThuc
        +String diaDiem
        +bool daSuaRieng
        +String lyDoHuy
        +sinhDiemDanh() List~DiemDanh~
        +kiemTraTrung() bool
        +doiLich(batDau: DateTime, ketThuc: DateTime) void
        +huyLich(lyDo: String) void
        +danhDauHoanThanh() void
        +guiThongBao(loai: LoaiThongBao) void
    }

    class DiemDanh {
        +PhanHoiThamGia phanHoi
        +String lyDoXinNghi
        +TrangThaiDiemDanh trangThai
        +DateTime thoiGianGhiNhan
        +guiPhanHoi(ph: PhanHoiThamGia, lyDo: String) void
        +ghiNhan(tt: TrangThaiDiemDanh, nguoi: ThanhVien) void
    }

    class TranDau {
        +String maTran
        +String tenGiai
        +String doiThu
        +int diemDoiMinh
        +int diemDoiThu
        +String chiTietKetQua
        +KetQuaTran ketQua
        +chotDoiHinh(ds: List~ThanhVien~) void
        +ghiKetQua(diemMinh: int, diemDoiThu: int, chiTiet: String) void
    }

    class ThamGiaTranDau {
        +String vaiTroTrongTran
        +bool laDuBi
        +Map~String,String~ soLieuThiDau
        +float diemDanhGia
        +String nhanXet
    }

    class ThongKeCaNhan {
        <<computed>>
        +Date tuNgay
        +Date denNgay
        +float tyLeChuyenCan
        +int soTranThamGia
        +float tyLeThang
        +float diemDanhGiaTB
    }

    class Quy {
        +String maQuy
        +String nganHang
        +String taiKhoanNhan
        +tinhSoDu() Decimal
        +kiemTraKhaNangChi(soTien: Decimal) bool
        +taoGiaoDichChi(hangMuc: String, soTien: Decimal, doiTac: String, nguoiThucHien: ThanhVien) GiaoDich
        +taoGiaoDichThuNgoai(hangMuc: String, soTien: Decimal, doiTac: String, nguoiThucHien: ThanhVien) GiaoDich
        +taoKhoanDongThang(ky: String, soTien: Decimal, hanDong: Date) List~KhoanDongQuy~
        +nhacThanhVienChuaDong(ky: String) int
    }

    class KhoanDongQuy {
        +String maKhoan
        +String ky
        +Decimal soTien
        +Date hanDong
        +TrangThaiKhoan trangThai
        +String lyDoHuy
        +taoMaQR() String
        +guiYeuCauDuyet(nguoiGui: ThanhVien) GiaoDich
        +danhDauDaDong() void
        +hoanVeChuaDong() void
        +huyKhoan(lyDo: String) void
        +kiemTraQuaHan() bool
    }

    class GiaoDich {
        +String maGD
        +LoaiGD loai
        +String hangMuc
        +Decimal soTien
        +String doiTac
        +DateTime thoiGian
        +TrangThaiGD trangThai
        +String ghiChu
        +PhuongThucXacNhan phuongThucXacNhan
        +String maThamChieu
        +String lyDoTuChoi
        +DateTime thoiGianXuLy
        +duyet(nguoiDuyet: ThanhVien) void
        +tuChoi(nguoiDuyet: ThanhVien, lyDo: String) void
    }

    class NhatKyHoatDong {
        +String maLog
        +DateTime thoiGian
        +LoaiHanhDong hanhDong
        +String loaiDoiTuong
        +String maDoiTuong
        +String giaTriCu
        +String giaTriMoi
        +String lyDo
        +ghi(hanhDong: LoaiHanhDong, nguoi: ThanhVien, loaiDoiTuong: String, maDoiTuong: String, giaTriCu: String, giaTriMoi: String, lyDo: String) NhatKyHoatDong
    }

    class ThongBao {
        +String maTB
        +LoaiThongBao loai
        +String noiDung
        +DateTime thoiGian
        +bool daDoc
    }

    class VaiTro {
        <<enumeration>>
        TUYEN_THU
        HUAN_LUYEN_VIEN
        THU_QUY
    }

    class TrangThaiTV {
        <<enumeration>>
        THU
        CHINH_THUC
        DA_LOAI
        ROI_DOI
    }

    class TrangThaiTaiKhoan {
        <<enumeration>>
        CHO_KICH_HOAT
        HOAT_DONG
        BI_KHOA
    }

    class TrangThaiHoSo {
        <<enumeration>>
        DA_NOP
        DANG_XET
        MOI_THU
        TU_CHOI
        DA_RUT
    }

    class KetQuaThuViec {
        <<enumeration>>
        DAT
        KHONG_DAT
    }

    class LoaiLich {
        <<enumeration>>
        TAP
        HOP
        THI_DAU
    }

    class TrangThaiLich {
        <<enumeration>>
        DU_KIEN
        DA_DOI
        DA_HUY
        HOAN_THANH
    }

    class PhanHoiThamGia {
        <<enumeration>>
        CHUA_PHAN_HOI
        SE_THAM_GIA
        XIN_NGHI
    }

    class TrangThaiDiemDanh {
        <<enumeration>>
        CHUA_GHI_NHAN
        CO_MAT
        DI_MUON
        VANG_CO_PHEP
        VANG_KHONG_PHEP
    }

    class KetQuaTran {
        <<enumeration>>
        THANG
        HOA
        THUA
    }

    class LoaiGD {
        <<enumeration>>
        THU
        CHI
    }

    class TrangThaiGD {
        <<enumeration>>
        CHO_XU_LY
        THANH_CONG
        THAT_BAI
    }

    class TrangThaiKhoan {
        <<enumeration>>
        CHUA_DONG
        CHO_XU_LY
        DA_DONG
        DA_HUY
    }

    class PhuongThucXacNhan {
        <<enumeration>>
        THU_QUY
        NGAN_HANG_API
    }

    class LoaiHanhDong {
        <<enumeration>>
        DOI_LICH
        HUY_LICH
        DOI_QUY_TAC
        HUY_QUY_TAC
        SUA_DIEM_DANH
        CHOT_DOI_HINH
        GHI_KET_QUA
        DUYET_GIAO_DICH
        TU_CHOI_GIAO_DICH
        TAO_GIAO_DICH
        HUY_KHOAN
        DOI_TRANG_THAI_TV
        DOI_VAI_TRO
        KHOA_TAI_KHOAN
    }

    class LoaiThongBao {
        <<enumeration>>
        NHAC_QUY
        YEU_CAU_DUYET
        KET_QUA_DUYET
        LICH_MOI
        LICH_DOI
        LICH_HUY
        KET_QUA_HO_SO
    }

    %% The team is the ownership root for members, fund, sessions, recurrence rules and the audit trail
    DoiTuyen "1" *-- "0..*" ThanhVien : gom
    DoiTuyen "1" *-- "1" Quy : coQuy
    DoiTuyen "1" *-- "0..*" TinTuyenDung : dang
    DoiTuyen "1" *-- "0..*" LichBieu : lap
    DoiTuyen "1" *-- "0..*" QuyTacLap : datQuyTac
    DoiTuyen "1" *-- "0..*" NhatKyHoatDong : ghiVet
    DoiTuyen ..> ThongKeCaNhan : tinh

    %% Identity: a member may have no account yet, an account always belongs to one member
    ThanhVien "1" *-- "0..1" TaiKhoan : coTaiKhoan

    %% Audit entries record who acted, the target object is referenced by type and id (no per-type links)
    NhatKyHoatDong "0..*" --> "0..1" ThanhVien : nguoiThucHien

    %% The computed statistics read from attendance and match records of one member
    ThongKeCaNhan ..> ThanhVien : cua
    ThongKeCaNhan ..> DiemDanh : tongHopTu
    ThongKeCaNhan ..> ThamGiaTranDau : tongHopTu

    %% A member reads the sessions they are expected at (through attendance records)
    ThanhVien ..> LichBieu : xem

    %% Recruitment flow (still undecided): application -> trial -> official member
    TinTuyenDung "1" *-- "0..*" HoSoUngTuyen : nhan
    HoSoUngTuyen "1" --> "0..1" ThanhVien : moiThuThanh
    ThanhVien "1" *-- "0..*" DanhGiaThuViec : duocDanhGia
    DanhGiaThuViec "0..*" --> "1" ThanhVien : nguoiDanhGia

    %% Schedule: a rule generates many sessions, a one-off session has no rule
    QuyTacLap "0..1" o-- "0..*" LichBieu : sinhRa

    %% Attendance is recorded per session and per member
    LichBieu "1" *-- "0..*" DiemDanh : ghiNhan
    DiemDanh "0..*" --> "1" ThanhVien : cua
    DiemDanh "0..*" --> "0..1" ThanhVien : nguoiGhiNhan

    %% A match is the detail record of exactly one session of type THI_DAU
    LichBieu "1" *-- "0..1" TranDau : chiTietTran
    TranDau "1" *-- "0..*" ThamGiaTranDau : doiHinh
    ThamGiaTranDau "0..*" --> "1" ThanhVien : cua

    %% Fund: transactions form the ledger of the fund, dues are generated per member and period
    Quy "1" *-- "0..*" GiaoDich : ghiNhan
    Quy "1" *-- "0..*" KhoanDongQuy : phatSinh
    KhoanDongQuy "0..*" --> "1" ThanhVien : phaiDong

    %% One due can have several payment attempts (failed ones plus at most one successful)
    GiaoDich "0..*" --> "0..1" KhoanDongQuy : thanhToanCho
    GiaoDich "0..*" --> "1" ThanhVien : nguoiThucHien
    GiaoDich "0..*" --> "0..1" ThanhVien : nguoiDuyet

    %% Notifications: each one targets a member and points to at most one related object
    ThongBao "0..*" --> "1" ThanhVien : nguoiNhan
    ThongBao "0..*" --> "0..1" LichBieu : veBuoi
    ThongBao "0..*" --> "0..1" KhoanDongQuy : veKhoan

    %% Business rules
    note for DoiTuyen "PHAN QUYEN (cong don theo cacVaiTro cua thanh vien, xac thuc qua TaiKhoan):<br/>HUAN_LUYEN_VIEN: tao/doi/huy lich va quy tac lap, diem danh, chot doi hinh, ghi ket qua tran, chuyen trang thai thanh vien, cap tai khoan, gan vai tro (chua chot ai quan tri thanh vien).<br/>THU_QUY: tao khoan dong quy, duyet/tu choi giao dich, tao giao dich chi va thu ngoai khoan, huy khoan.<br/>TUYEN_THU: khong them quyen nao, chi quyet dinh tu cach vao doi hinh thi dau.<br/>Moi thanh vien: gui phan hoi tham gia, gui yeu cau duyet khoan cua minh, xem lich, thong bao va thong ke cua chinh minh, doi mat khau.<br/>NhatKyHoatDong: HLV va THU_QUY xem duoc, khong ai sua hay xoa.<br/>choPhepHoa: bo mon co cho phep ket qua hoa hay khong, quyet dinh cach TranDau.ghiKetQua xu ly ti so bang nhau."

    note for ThanhVien "Flow: HoSoUngTuyen (tuyen) -> THU -> CHINH_THUC -> ThamGiaTranDau (thi dau)<br/>DA_LOAI: khong dat thu. ROI_DOI: roi doi.<br/>cacVaiTro: it nhat 1 vai tro, duoc giu nhieu vai tro cung luc (vi du TUYEN_THU + THU_QUY).<br/>thuocTinhThem: thong tin rieng cua bo mon do CLB tu quy dinh (vi du vi tri mac dinh, so ao, hang can), he thong khong rang buoc y nghia.<br/>Doi can co it nhat 1 thanh vien THU_QUY dang CHINH_THUC de duyet quy.<br/>Chi thanh vien CHINH_THUC moi phai dong quy.<br/>Khong xoa cung: ROI_DOI / DA_LOAI van giu lich su diem danh, giao dich, thi dau."

    note for TaiKhoan "Moi ThanhVien co toi da 1 TaiKhoan. Thanh vien chua co tai khoan van ton tai trong doi (HLV nhap thay phan hoi tham gia va diem danh).<br/>TaiKhoan chi xac thuc. Phan quyen lay tu ThanhVien.cacVaiTro.<br/>tenDangNhap UNIQUE. matKhauBam la ket qua bam mot chieu, khong luu mat khau goc.<br/>Vong doi: CHO_KICH_HOAT -> HOAT_DONG. HOAT_DONG va BI_KHOA chuyen qua lai bang khoa() / moKhoa().<br/>ThanhVien chuyen sang ROI_DOI / DA_LOAI thi TaiKhoan tu dong BI_KHOA.<br/>Thoi diem cap tai khoan (chi CHINH_THUC hay ca THU): chua chot."

    note for QuyTacLap "Chi lap theo tuan, chi cho loai TAP va HOP. cacThu theo ISO: 1 = Thu hai, 7 = Chu nhat.<br/>Moi lan sinh (taoCacBuoi / giaHan) toi da 50 buoi. Neu vuot thi ngayKetThuc bi cat ve ngay cua buoi thu 50.<br/>ngayKetThuc la moc neo luu tren quy tac: ngay cuoi cung da sinh toi. Chi tang len (taoCacBuoi, giaHan), khong bao gio giam, bat ke huy hay xoa buoi.<br/>giaHan(ngayKetThucMoi) sinh tiep tu ngay ke tiep ngayKetThuc den ngayKetThucMoi, nen khong phu thuoc cac buoi con ton tai va khong sinh lai ngay da huy hoac da xoa. ngayKetThucMoi phai sau ngayKetThuc.<br/>Gui 1 thong bao LICH_MOI tong hop cho ca chuoi, khong gui tung buoi.<br/>LichBieu sinh ra phai cung DoiTuyen voi quy tac.<br/>Sua/huy chi co 2 pham vi: chi buoi nay (LichBieu.doiLich / huyLich), hoac tu buoi nay tro di (suaTuBuoiNay / huyTuBuoiNay).<br/>suaTuBuoiNay chi doi gio trong ngay va dia diem, khong doi ngay. Buoi duoc chon luon duoc ap dung, ke ca khi daSuaRieng == true. No cap nhat luon gioBatDau, gioKetThuc, diaDiem cua quy tac de cac buoi sinh sau theo lich moi. Muon doi cacThu: huy tu buoi nay tro di roi tao quy tac moi.<br/>Hang loat chi tac dong buoi DU_KIEN hoac DA_DOI, bo qua HOAN_THANH va DA_HUY.<br/>Sua hang loat bo qua buoi daSuaRieng == true va khong dat daSuaRieng. Huy hang loat ap dung ca buoi daSuaRieng."

    note for LichBieu "RULE: TranDau chi gan duoc voi LichBieu loai THI_DAU. Buoi THI_DAU phai co TranDau truoc khi danhDauHoanThanh().<br/>Trang thai: DU_KIEN -> DA_DOI (doi duoc nhieu lan). DU_KIEN / DA_DOI -> HOAN_THANH hoac DA_HUY. HOAN_THANH va DA_HUY la trang thai cuoi.<br/>danhDauHoanThanh(): do HLV thao tac, chi khi da qua ketThuc, khong con DiemDanh CHUA_GHI_NHAN, va (voi buoi THI_DAU) moi ThamGiaTranDau ung voi DiemDanh CO_MAT hoac DI_MUON, neu khong HLV phai go thanh vien do khoi doi hinh.<br/>Moi thay doi gio hoac dia diem (ke ca sua hang loat) gui LICH_DOI va dat lai phanHoi ve CHUA_PHAN_HOI (mac dinh, chua chot). doiLich() them daSuaRieng = true neu buoi thuoc QuyTacLap.<br/>huyLich(): gui LICH_HUY, luu lyDoHuy.<br/>Buoi chua co phan hoi, diem danh hay doi hinh nao thi duoc xoa (kem cac DiemDanh mac dinh). Nguoc lai chi duoc huy.<br/>kiemTraTrung(): canh bao (khong chan) khi khoang gio giao nhau voi buoi chua huy khac cua doi."

    note for DiemDanh "UNIQUE (LichBieu, ThanhVien).<br/>Sinh san khi tao buoi (LichBieu.sinhDiemDanh): phanHoi = CHUA_PHAN_HOI, trangThai = CHUA_GHI_NHAN.<br/>Doi tuong mac dinh: thanh vien THU va CHINH_THUC (chua chot).<br/>Thanh vien vao doi sau: tao DiemDanh cho cac buoi DU_KIEN / DA_DOI sap toi. Thanh vien ROI_DOI / DA_LOAI: xoa DiemDanh CHUA_GHI_NHAN cua buoi sap toi, giu cac ban ghi da ghi nhan.<br/>guiPhanHoi: thanh vien tu thao tac, chi khi buoi DU_KIEN hoac DA_DOI va chua bat dau. Thanh vien chua co tai khoan thi HLV nhap thay.<br/>ghiNhan: HLV thao tac, chi khi buoi chua DA_HUY va da qua batDau. Sua mot DiemDanh da ghi nhan phai ghi NhatKyHoatDong (SUA_DIEM_DANH)."

    note for TranDau "ketQua suy ra tu diem so: THANG neu diemDoiMinh lon hon diemDoiThu, THUA neu nho hon, HOA neu bang nhau. Khong nhap tay. Neu DoiTuyen.choPhepHoa == false thi ghiKetQua tu choi ti so bang nhau (nhap diem sau cung, ke ca luot phu).<br/>diemDoiMinh, diemDoiThu la diem tong ket cua tran (vi du so set thang). chiTietKetQua la mo ta tuy chon (vi du 21-15, 18-21, 21-17).<br/>diemDoiMinh, diemDoiThu, ketQua de rong cho den khi ghiKetQua().<br/>ghiKetQua() chi thuc thi khi LichBieu cua tran la HOAN_THANH.<br/>chotDoiHinh(): chi khi buoi DU_KIEN hoac DA_DOI. Chi chon thanh vien CHINH_THUC co vai tro TUYEN_THU va phanHoi khac XIN_NGHI.<br/>ThamGiaTranDau UNIQUE (TranDau, ThanhVien). laDuBi == true la nguoi du bi. vaiTroTrongTran la chuoi tu do (vi tri, noi dung thi, so ghe...), soLieuThiDau la so lieu tuy bo mon (phut thi dau, ban thang...), he thong khong rang buoc."

    note for ThongKeCaNhan "Tinh trong khoang tuNgay - denNgay (vi du mot mua giai).<br/>tyLeChuyenCan = (CO_MAT + DI_MUON) / (CO_MAT + DI_MUON + VANG_KHONG_PHEP), chi tinh buoi HOAN_THANH. VANG_CO_PHEP khong tinh vao ca tu so lan mau so. Mau so bang 0 thi de rong.<br/>soTranThamGia: so ThamGiaTranDau cua tran thuoc buoi HOAN_THANH.<br/>tyLeThang: chi tinh tran da co ketQua. diemDanhGiaTB: trung binh diemDanhGia, bo qua gia tri rong."

    note for Quy "soDu khong luu. tinhSoDu() = tong soTien cac GiaoDich THU THANH_CONG tru tong soTien cac GiaoDich CHI THANH_CONG. Cac giao dich la so cai.<br/>INVARIANT: tinhSoDu() >= 0<br/>taoGiaoDichChi: chay trong 1 transaction co khoa ghi tren Quy, de kiemTraKhaNangChi() va ghi giao dich khong bi giao dich khac chen vao giua. Nem loi neu khong du so du. Ghi thang THANH_CONG.<br/>taoGiaoDichThuNgoai: THU khong gan khoan (tai tro, ung ho), ghi thang THANH_CONG.<br/>taoKhoanDongThang: ky co dang YYYY-MM. Goi lai cung ky khong sinh trung (xem UNIQUE o KhoanDongQuy).<br/>nhacThanhVienChuaDong(ky): chi nhac khoan CHUA_DONG, bo qua CHO_XU_LY va DA_HUY."

    note for KhoanDongQuy "UNIQUE (ThanhVien, ky). Chi sinh cho thanh vien CHINH_THUC.<br/>Trang thai: CHUA_DONG -> CHO_XU_LY -> DA_DONG. Bi tu choi: CHO_XU_LY -> CHUA_DONG. Thu quy huy: CHUA_DONG -> DA_HUY (luu lyDoHuy). DA_DONG va DA_HUY la trang thai cuoi.<br/>guiYeuCauDuyet() chi chay khi CHUA_DONG, tao GiaoDich CHO_XU_LY va chuyen khoan sang CHO_XU_LY.<br/>danhDauDaDong() / hoanVeChuaDong(): chi chay tu CHO_XU_LY, chi GiaoDich.duyet() / tuChoi() duoc goi.<br/>Qua han khong luu: kiemTraQuaHan() dung khi hanDong da qua va trangThai == CHUA_DONG. Khoan CHO_XU_LY khong tinh qua han.<br/>Thanh vien ROI_DOI khong tu dong huy khoan dang no, thu quy tu quyet dinh huyKhoan().<br/>Ma QR chua: soTien, nganHang va taiKhoanNhan cua Quy, noi dung chuyen khoan = maKhoan."

    note for GiaoDich "Giao dich THU gan voi KhoanDongQuy: tao khi thanh vien bam Yeu cau duyet. soTien bang soTien cua khoan (khong ho tro tra gop), nguoiThucHien la nguoi phai dong.<br/>Chi giao dich THU gan khoan moi co the CHO_XU_LY. THU khong gan khoan (Quy.taoGiaoDichThuNgoai) va CHI (Quy.taoGiaoDichChi) do thu quy tao, ghi thang THANH_CONG, khong qua buoc duyet.<br/>doiTac: nguoi nhan tien (giao dich CHI) hoac nguoi, don vi gui tien (THU khong gan khoan). Bat buoc voi giao dich khong gan khoan, de rong voi giao dich gan khoan.<br/>Giao dich THANH_CONG la so cai: khong sua, khong xoa. Cach sua giao dich da duyet nham: chua thiet ke.<br/>Trang thai: CHO_XU_LY -> THANH_CONG hoac THAT_BAI. Trang thai cuoi khong doi.<br/>duyet(): trong 1 transaction: GD -> THANH_CONG, khoan.danhDauDaDong(). Khong cap nhat so du, vi so du tinh tu cac giao dich THANH_CONG.<br/>tuChoi(): GD -> THAT_BAI, khoan.hoanVeChuaDong(), luu lyDoTuChoi. Thanh vien tao GD moi de thu lai.<br/>duyet() / tuChoi() chuyen trang thai bang cap nhat co dieu kien (chi khi dang CHO_XU_LY), de hai nguoi thao tac cung luc khong ap dung hai lan.<br/>Mot khoan co toi da 1 GD CHO_XU_LY va toi da 1 GD THANH_CONG.<br/>Chi thanh vien co THU_QUY moi duyet hoac tu choi. Thu quy tu duyet khoan cua chinh minh: chua chot.<br/>maThamChieu: ma giao dich ngan hang, UNIQUE neu co, chong ghi nhan 2 lan.<br/>Ve sau NGAN_HANG_API goi lai duyet() / tuChoi() giong thu quy, khi do nguoiDuyet de trong. Luong tu doi chieu khong qua nut Yeu cau duyet chua thiet ke."

    note for NhatKyHoatDong "Chi ghi thao tac co tac dong lon, theo LoaiHanhDong: doi/huy lich, doi/huy quy tac lap (1 dong cho ca chuoi, khong ghi tung buoi), sua DiemDanh da ghi nhan, chot doi hinh, ghi ket qua, duyet/tu choi/tao giao dich, huy khoan, doi trang thai hoac vai tro thanh vien, khoa tai khoan.<br/>Append-only: khong sua, khong xoa.<br/>Ghi trong cung transaction voi thao tac, khong co thao tac nao thanh cong ma thieu nhat ky.<br/>nguoiThucHien rong khi he thong tu thuc hien (vi du ngan hang API).<br/>loaiDoiTuong + maDoiTuong tro toi doi tuong bi tac dong. giaTriCu / giaTriMoi la anh chup truoc va sau thao tac dang van ban."

    note for ThongBao "Gan voi LichBieu (cac loai LICH_*) hoac KhoanDongQuy (NHAC_QUY, YEU_CAU_DUYET, KET_QUA_DUYET), moi thong bao chi gan 1 trong 2. KET_QUA_HO_SO khong gan doi tuong (phan tuyen dung chua chot).<br/>YEU_CAU_DUYET gui cho thanh vien THU_QUY, KET_QUA_DUYET gui cho nguoi dong."
```
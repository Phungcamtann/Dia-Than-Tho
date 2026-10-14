# 💿 Đĩa Than Thở

Website thương mại điện tử mua bán đĩa nhạc và merchandise âm nhạc đã qua sử dụng, theo mô hình **B2C kết hợp kênh thu mua sản phẩm từ người dùng**.

👥 Thực hiện bởi nhóm 8:

- Dương Hoàng Sâm (Leader - PM)
- Phạm Thiên Long (UI/UX Designer)
- Phùng Cẩm Tân (Backend Lead)
- Nguyễn Duy Thành Tài (Business analyst)
- Tiêu Lâm Định Quốc (Tester & Reporter)
- Trần Yến Phượng (Frontend Lead)

🧭 Project Coordinator(PC): Định Thị Anh Thư

## 1. 📖 Tổng quan

Đĩa Than Thở dự kiến cung cấp một nơi tập trung để người yêu âm nhạc tìm kiếm đĩa vinyl, CD, album, photocard, poster và merchandise đã qua sử dụng do cửa hàng đăng bán.

Người sở hữu sản phẩm không còn nhu cầu sử dụng có thể gửi yêu cầu bán lại cho cửa hàng. Administrator tiếp nhận thông tin, xét duyệt sơ bộ và phản hồi trên website. Người dùng không tự mở gian hàng hoặc đăng sản phẩm để bán trực tiếp cho nhau.

Các nhận định về nhu cầu, hành vi và khó khăn của người dùng là **giả định ban đầu cần xác minh** bằng phỏng vấn hoặc nguồn dữ liệu phù hợp.

## 2. 🎯 Mục tiêu đồ án

- Xây dựng website responsive với ba phân hệ: Customer, Trade-in/Buyback và Administrator.
- Trình diễn luồng mua hàng B2C và luồng gửi, xét duyệt, theo dõi phiếu thu mua.
- Áp dụng lập trình hướng đối tượng (OOP) trong backend C# để phân chia trách nhiệm và quản lý quy tắc nghiệp vụ.
- Xây dựng dữ liệu mô phỏng phục vụ demo và kiểm thử.
- Thực hiện dự án trong 8 tuần với nhóm 6 thành viên theo tài liệu Overview.

## 3. 👤 Người dùng

| Người dùng | Vai trò |
|---|---|
| **Customer** | Xem, tìm kiếm sản phẩm, thêm vào giỏ hàng và tạo đơn hàng mô phỏng. |
| **Người gửi yêu cầu thu mua** | Dùng tài khoản khách hàng để gửi phiếu bán lại sản phẩm, xem trạng thái, phản hồi và ngày lấy hàng dự kiến. |
| **Administrator** | Quản lý sản phẩm, tồn kho, đơn hàng; xét duyệt phiếu thu mua và tạo sản phẩm bán công khai thủ công. |

Việc lấy hàng, kiểm tra sản phẩm thực tế và thanh toán thu mua do cửa hàng xử lý ngoài hệ thống. Thông tin nguồn gốc và tình trạng không đồng nghĩa với chứng nhận chất lượng hoặc tính chính hãng.

## 4. 📦 Phạm vi MVP

### 4.1. 🛒 Customer Module

- Đăng ký, đăng nhập tài khoản.
- Xem danh mục và chi tiết sản phẩm, gồm thông tin nguồn gốc và tình trạng.
- Tìm kiếm, lọc theo danh mục, mức giá và tình trạng sản phẩm.
- Thêm sản phẩm vào giỏ hàng.
- Tạo và xem đơn hàng mô phỏng thuộc tài khoản của mình.

### 4.2. 🔄 Trade-in/Buyback Module

- Gửi phiếu yêu cầu bán lại sản phẩm, gồm thông tin chi tiết, tình trạng, hình ảnh, giá đề xuất, thông tin liên hệ và địa chỉ lấy hàng.
- Xem danh sách phiếu đã gửi, mã phiếu, chi tiết, trạng thái và phản hồi.
- Xem ngày lấy hàng dự kiến và địa chỉ đã cung cấp khi phiếu được duyệt.
- Xem lý do khi phiếu bị từ chối.

Phiếu thu mua có ba trạng thái:

| Trạng thái | Ý nghĩa |
|---|---|
| ⏳ **Chờ duyệt** | Trạng thái mặc định của phiếu mới gửi. |
| ✅ **Đã duyệt** | Chấp thuận sơ bộ dựa trên thông tin khai báo để tiếp nhận sản phẩm; chưa phải quyết định thu mua cuối cùng. |
| ❌ **Bị từ chối** | Không chấp thuận yêu cầu; hiển thị lý do từ chối. |

Giá đề xuất là mức người gửi mong muốn, chưa phải giá cửa hàng chấp nhận thanh toán. Trong demo, ngày lấy hàng dự kiến bằng ngày duyệt phiếu cộng 2 ngày; đây là giả định minh họa, không phải lịch được đơn vị vận chuyển xác nhận hoặc cam kết thu mua.

### 4.3. ⚙️ Administrator Module

- Quản lý sản phẩm và tồn kho.
- Quản lý, cập nhật trạng thái đơn hàng của khách mua.
- Tiếp nhận và kiểm tra thông tin khai báo trong phiếu thu mua.
- Duyệt sơ bộ hoặc từ chối phiếu; ghi phản hồi và lý do từ chối.
- Tạo sản phẩm B2C thủ công, kèm thông tin nguồn gốc và tình trạng để đăng bán.

Phiếu được duyệt **không tự động tạo sản phẩm bán công khai**. Website không ghi nhận xác nhận kiểm tra thực tế hoặc thanh toán thu mua.

### 4.4. 🔐 Quyền truy cập

- Người dùng phải đăng nhập để gửi phiếu thu mua.
- Customer chỉ được truy cập đơn hàng và phiếu thuộc tài khoản của mình.
- Chỉ Administrator được xét duyệt phiếu và quản lý sản phẩm bán công khai.
- Backend kiểm tra quyền và quyền sở hữu dữ liệu cho từng yêu cầu; việc ẩn nút trên giao diện không thay thế kiểm tra quyền.

## 5. 🛠️ Công nghệ và công cụ

### 5.1. Công nghệ đã chốt

| Thành phần | Lựa chọn |
|---|---|
| Ngôn ngữ backend | C# |
| Ngôn ngữ frontend | HTML, CSS, JavaScript |
| Framework giao diện | Bootstrap |
| Database | SQL Server Express |
| Truy cập dữ liệu | Entity Framework Core |
| Môi trường demo | Local |

### 5.2. Định hướng bổ sung

| Thành phần | Đề xuất |
|---|---|
| Backend framework | ASP.NET Core Web API trên .NET 10 LTS |
| Phiên bản EF Core | EF Core 10 và provider SQL Server tương thích |
| Phiên bản Bootstrap | Bootstrap 5.3 |
| Tài khoản và phân quyền | ASP.NET Core Identity, vai trò Customer/Administrator |
| Xác thực | Cookie HttpOnly khi frontend và API được phục vụ cùng website, kèm bảo vệ chống giả mạo yêu cầu |
| Giao tiếp frontend/backend | HTTP API, dữ liệu JSON, JavaScript `fetch` |
| Tài liệu API | OpenAPI và Swagger UI |
| Ảnh sản phẩm | Thư mục lưu ảnh local; database lưu đường dẫn |
| Kiểm thử | xUnit, Postman và kiểm thử giao diện thủ công |
| Quản lý mã nguồn | Git và GitHub |
| Thiết kế UI/UX | Figma |

Các mục bổ sung là đề xuất triển khai, chưa phải xác nhận đã cài đặt hoặc sử dụng. Nhóm cần thống nhất phiên bản cụ thể khi khởi tạo mã nguồn.

## 6. 🧩 Định hướng kiến trúc và OOP

Backend dự kiến tổ chức theo luồng:

**Frontend → Controller → Service → EF Core/DbContext → SQL Server**

| Thành phần | Trách nhiệm |
|---|---|
| **Controller** | Nhận yêu cầu HTTP, tiếp nhận dữ liệu đầu vào, gọi service và trả kết quả. |
| **Service** | Điều phối nghiệp vụ, kiểm tra quyền sở hữu dữ liệu và áp dụng quy tắc xử lý sản phẩm, đơn hàng, phiếu thu mua. |
| **Entity** | Biểu diễn dữ liệu và hành vi nghiệp vụ của các đối tượng trong hệ thống. |
| **DTO** | Định nghĩa dữ liệu đầu vào/đầu ra của API, tránh để người dùng tự ghi các trường do hệ thống quản lý. |
| **DbContext và cấu hình EF Core** | Quản lý ánh xạ, quan hệ, ràng buộc và truy cập database. |

### Nguyên tắc OOP dự kiến áp dụng

- **Đóng gói:** Trạng thái phiếu được thay đổi qua hành vi nghiệp vụ có kiểm tra điều kiện, thay vì cho phép cập nhật tùy ý từ dữ liệu frontend. Tồn kho cũng được thay đổi qua các thao tác có kiểm tra hợp lệ.
- **Trừu tượng:** Những nghiệp vụ chính có hợp đồng rõ ràng, chẳng hạn `IOrderService` và `IBuybackService`, để Controller phụ thuộc vào chức năng cần dùng.
- **Đa hình:** Controller sử dụng service qua interface; khi kiểm thử có thể thay thế dependency bằng một triển khai phục vụ kiểm thử.
- **Kế thừa có chọn lọc:** Chỉ sử dụng khi có quan hệ phù hợp; không tạo hệ thống lớp cha/con chỉ để thể hiện OOP. Một tài khoản Customer có thể vừa mua hàng vừa gửi yêu cầu thu mua.
- **Trách nhiệm rõ ràng:** Tách xử lý đơn hàng, phiếu thu mua và sản phẩm thành các service phù hợp; không đặt toàn bộ nghiệp vụ trong Controller.
- **Dependency Injection:** Cung cấp các dependency qua constructor để giảm phụ thuộc trực tiếp và hỗ trợ kiểm thử.

Các đối tượng nghiệp vụ dự kiến gồm `ApplicationUser`, `Category`, `Product`, `ProductImage`, `Order`, `OrderItem`, `BuybackRequest` và `BuybackRequestImage`. Thiết kế database và lớp chi tiết cần được nhóm rà soát trước khi lập trình.

OOP cần thể hiện trong cách bảo vệ quy tắc và phối hợp giữa các đối tượng, không chỉ ở việc tạo lớp hoặc interface. Nội dung trên là định hướng thiết kế, chưa phải bằng chứng mã nguồn đã đáp ứng OOP.

## 7. 📂 Cấu trúc mã nguồn dự kiến

```text
DiaThanTho/
├── backend/
│   ├── Controllers/
│   ├── Services/
│   │   ├── Interfaces/
│   │   └── Implementations/
│   ├── Entities/
│   ├── DTOs/
│   ├── Data/
│   │   └── Configurations/
│   ├── Migrations/
│   └── Program.cs
├── frontend/
│   ├── pages/
│   │   ├── customer/
│   │   └── admin/
│   └── assets/
│       ├── css/
│       ├── js/
│       └── images/
├── tests/
├── docs/
└── README.md
```

Đây là cấu trúc đề xuất cho giai đoạn triển khai, chưa phản ánh các thư mục đã tồn tại. Frontend và backend có thể được phát triển trong thư mục riêng, sau đó phục vụ cùng một website local.

## 8. 📊 Dữ liệu và tiêu chí hoàn thành

Theo Overview, mục tiêu MVP gồm:

- Hoàn thành toàn bộ chức năng Must Have được nhóm phê duyệt.
- Có tối thiểu 30 sản phẩm mẫu thuộc 3 danh mục, gồm ít nhất 10 sản phẩm minh họa nguồn hàng có sẵn và 10 sản phẩm minh họa nguồn hàng thu mua.
- Đếm phiếu thu mua mẫu riêng; không dùng phiếu thay thế chỉ tiêu sản phẩm.
- Thực hiện tối thiểu 30 test case, tỷ lệ Pass từ 90% trở lên và không còn lỗi Critical chưa xử lý.
- Thực hiện UAT với tối thiểu 5 người tham gia, tỷ lệ hoàn thành tác vụ từ 80% trở lên.
- Bàn giao demo local, source code, tài liệu quản lý, báo cáo kiểm thử và 6 Mini-PM Reports trong 8 tuần.

Đây là **mục tiêu**, chưa phải kết quả đã đạt. Việc demo local là lựa chọn triển khai hiện tại của nhóm.

Sản phẩm, phiếu thu mua và đơn hàng được tạo để minh họa phải ghi rõ **“Dữ liệu mô phỏng (synthetic/simulated data)”**. Dữ liệu này không chứng minh giao dịch, khách hàng hoặc hoạt động thu mua thực tế. Kết quả phỏng vấn và UAT chỉ được báo cáo khi thực sự thực hiện và có minh chứng.

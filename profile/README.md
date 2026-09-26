# EDUMY — Nền tảng E-learning tích hợp quản lý khóa học và đánh giá trực tuyến

![.NET 8](https://img.shields.io/badge/.NET-8-512BD4?logo=dotnet) ![React 19](https://img.shields.io/badge/React-19-61DAFB?logo=react) ![Flutter](https://img.shields.io/badge/Flutter-Dart_3.10-02569B?logo=flutter) ![PostgreSQL 16](https://img.shields.io/badge/PostgreSQL-16-4169E1?logo=postgresql) ![Docker](https://img.shields.io/badge/Docker-24+-2496ED?logo=docker) ![Nginx 1.27](https://img.shields.io/badge/Nginx-1.27-009639?logo=nginx) ![JWT](https://img.shields.io/badge/Auth-JWT-black?logo=jsonwebtokens) ![License](https://img.shields.io/badge/license-GPL--3.0-green)

---

## Mục lục

- [Giới thiệu](#giới-thiệu)
- [Thông tin đề tài](#thông-tin-đề-tài)
- [Bối cảnh & Động lực](#bối-cảnh--động-lực)
- [Mục tiêu đề tài](#mục-tiêu-đề-tài)
- [Đối tượng & Phạm vi nghiên cứu](#đối-tượng--phạm-vi-nghiên-cứu)
- [Khảo sát hệ thống liên quan](#khảo-sát-hệ-thống-liên-quan)
- [Khoảng trống công nghệ & Điểm mới](#khoảng-trống-công-nghệ--điểm-mới)
- [Kiến trúc hệ thống](#kiến-trúc-hệ-thống)
- [Cấu trúc Repository](#cấu-trúc-repository)
- [Phân tích yêu cầu chức năng](#phân-tích-yêu-cầu-chức-năng)
- [Yêu cầu phi chức năng](#yêu-cầu-phi-chức-năng)
- [Thiết kế cơ sở dữ liệu](#thiết-kế-cơ-sở-dữ-liệu)
- [Ngăn xếp công nghệ (Tech Stack)](#ngăn-xếp-công-nghệ-tech-stack)
- [Cấu hình & Triển khai](#cấu-hình--triển-khai)
- [DevOps & CI/CD](#devops--cicd)
- [Tình trạng hiện tại dự án](#tình-trạng-hiện-tại-dự-án)
- [Kế hoạch thực hiện](#kế-hoạch-thực-hiện)
- [Liên hệ](#liên-hệ)

---

<a name="giới-thiệu"></a>

## Giới thiệu

Trong bối cảnh nền giáo dục toàn cầu đang trải qua giai đoạn chuyển đổi số mạnh mẽ, các hệ thống E-learning dần khẳng định vai trò là xương sống của hạ tầng công nghệ giáo dục. Tuy nhiên, các hệ thống hiện tại thường bị phân mảnh, tách biệt rõ ràng giữa hệ thống quản lý nội dung học tập và nền tảng tổ chức thi cử độc lập, gây ra sự đứt gãy trong quá trình luân chuyển dữ liệu.

EDUMY ra đời nhằm giải quyết bài toán đó bằng kiến trúc **Microservices** hiện đại, kết hợp trải nghiệm Front-end mượt mà với sự khắt khe trong đánh giá năng lực học thuật, mang lại một giải pháp toàn diện cho các cơ sở giáo dục quy mô vừa và nhỏ.

<a name="thông-tin-đề-tài"></a>

## Thông tin đề tài

| Mục                      | Nội dung                                                                      |
| ------------------------ | ----------------------------------------------------------------------------- |
| **Tên đề tài**           | Xây dựng nền tảng E-learning tích hợp quản lý khóa học và đánh giá trực tuyến |
| **Tên hệ thống**         | EDUMY                                                                         |
| **Loại hình**            | Khóa luận tốt nghiệp                                                          |
| **Sinh viên thực hiện**  | Quang Nhật Hưng (MSSV: 2001230328)                                            |
| **Cộng tác viên**        | Nguyễn Châu Kha (MSSV: 2001230359), Nguyễn Văn Anh Tuấn (MSSV: 2001230863)    |
| **Giảng viên hướng dẫn** | TS. Nguyễn Thị Bích Ngân                                                      |
| **Đơn vị**               | Khoa Công nghệ Thông tin — Trường Đại học Công Thương TP.HCM (HUIT)           |
| **Thời gian thực hiện**  | Tháng 07/2026 – Tháng 11/2026 (5 tháng)                                       |
| **Trang web giới thiệu** | [edumy.nhathungdev.site](https://edumy.nhathungdev.site)                      |
| **Production** | [production.nhathungdev.site](https://production.nhathungdev.site)                      |

<a name="bối-cảnh--động-lực"></a>

## Bối cảnh & Động lực

### Thực trạng

Việc dạy và học trực tuyến không còn là giải pháp tình thế mà đã trở thành phương pháp giáo dục tiêu chuẩn song hành cùng mô hình truyền thống. Tuy nhiên, khi đi sâu vào trải nghiệm thực tế, các hệ thống hiện tại đang bộc lộ nhiều vấn đề đáng lo ngại:

1. **Phân mảnh hệ thống**: Các phần mềm thường bị tách biệt rõ ràng giữa hệ thống quản lý nội dung học tập (LMS) và nền tảng tổ chức thi cử độc lập, gây đứt gãy luồng dữ liệu.

2. **Giao diện lạc hậu**: Nhiều hệ thống mã nguồn mở hiện hành sở hữu giao diện Front-end khá cũ kỹ, không chú trọng đến trải nghiệm người dùng (UX/UI).

3. **Nút thắt cổ chai về hiệu năng**: Khi đối mặt với lượng truy cập đồng thời lớn trong các kỳ thi trực tuyến, kiến trúc Back-end của nhiều hệ thống thiếu tính linh hoạt, dẫn đến quá tải, giật lag hoặc mất đồng bộ dữ liệu.

4. **Chi phí vận hành cao**: Các giải pháp Cloud LMS thương mại đi kèm chi phí bản quyền lớn, không phù hợp với các cơ sở đào tạo quy mô vừa và nhỏ.

### Động lực

Việc lựa chọn đề tài xuất phát từ mong muốn vận dụng các kiến thức chuyên sâu về công nghệ phần mềm vào một bài toán thực tế đầy thách thức. Phát triển một sản phẩm công nghệ giáo dục hoàn chỉnh là cơ hội để rèn luyện:

- Tư duy thiết kế kiến trúc hệ thống (System Architecture Design)
- Kỹ năng lập trình Full-stack (Backend + Frontend Web + Mobile)
- Kỹ năng quản trị cơ sở dữ liệu và tối ưu hiệu năng
- Kỹ năng triển khai và vận hành hệ thống (DevOps)

<a name="mục-tiêu-đề-tài"></a>

## Mục tiêu đề tài

### Mục tiêu tổng quát

Nghiên cứu, phân tích, thiết kế và xây dựng thành công nền tảng E-learning **EDUMY** — một hệ thống phần mềm hoàn chỉnh tích hợp liền mạch giữa hai phân hệ cốt lõi là **quản lý khóa học** và **đánh giá trực tuyến**. Hệ thống đảm bảo vận hành ổn định với kiến trúc Back-end vững chắc, có khả năng mở rộng tốt và sở hữu giao diện Front-end hiện đại, thân thiện.

### Mục tiêu cụ thể

1. **Khảo sát và đặc tả yêu cầu**: Trích xuất chính xác các Use case nghiệp vụ của người dùng (Admin, Giảng viên, Học viên).

2. **Thiết kế cơ sở dữ liệu**: Xây dựng mô hình dữ liệu chuẩn hóa, giảm thiểu dư thừa, đảm bảo tính toàn vẹn tham chiếu.

3. **Xây dựng hệ thống API RESTful**: Thiết kế chuẩn giao tiếp giữa Client và Server, đảm bảo bảo mật và hiệu năng.

4. **Phát triển module chức năng**:
   - Module quản lý người dùng và xác thực (Authentication & Authorization)
   - Module quản trị hệ thống (Admin Dashboard)
   - Module quản lý khóa học (CRUD, cấu trúc bài giảng, tài nguyên đa phương tiện)
   - Module đánh giá trực tuyến (đa dạng định dạng câu hỏi, chấm điểm tự động)
   - Module thanh toán (tích hợp cổng thanh toán QR)
   - Module AI (Chatbot RAG, tự động sinh đề thi)

5. **Kiểm thử và triển khai**: Kiểm thử toàn diện các luồng chức năng, triển khai lên môi trường thực tế, đánh giá hiệu năng chịu tải.

<a name="đối-tượng--phạm-vi-nghiên-cứu"></a>

## Đối tượng & Phạm vi nghiên cứu

### Đối tượng nghiên cứu

Ba trụ cột chính của hệ thống giáo dục trực tuyến:

1. **Quy trình nghiệp vụ giáo dục hiện đại**: Quy trình tổ chức lớp học, phương pháp phân phối nội dung bài giảng, chuẩn mực trong kiểm tra đánh giá năng lực.

2. **Nhóm đối tượng người dùng**: Quản trị viên (Admin), Giảng viên (Instructor), Học viên (Student) — phân tích hành vi và kỳ vọng về UX/UI.

3. **Công nghệ nền tảng**: Framework lập trình Web (React), Mobile (Flutter), Backend (.NET 8), kỹ thuật xây dựng kiến trúc Microservices, quản trị cơ sở dữ liệu (PostgreSQL).

### Phạm vi nghiên cứu

**Phạm vi chức năng**:

- Quản lý tài khoản người dùng (đăng ký, đăng nhập, phân quyền)
- Quản trị vòng đời khóa học (tạo, sửa, xóa, xuất bản)
- Cung cấp không gian tương tác tài liệu học tập (video, PDF, Slide)
- Thiết lập và tổ chức bài thi đánh giá trực tuyến
- Quản lý giao dịch thanh toán và đối soát doanh thu
- Trợ lý ảo AI và tự động sinh đề thi

**Giới hạn** (không nằm trong phạm vi):

- Công cụ họp trực tuyến Video Call thời gian thực
- Thuật toán AI giám sát gian lận thi cử phức tạp

<a name="khảo-sát-hệ-thống-liên-quan"></a>

## Khảo sát hệ thống liên quan

Để định hình kiến trúc và tính năng cốt lõi cho EDUMY, nhóm thực hiện đã khảo sát ba nền tảng E-learning tiêu biểu, đại diện cho ba triết lý thiết kế khác nhau:

### 1. Moodle — LMS Open-source truyền thống

**Ưu điểm**:

- Hệ sinh thái Plugin khổng lồ, cho phép tùy biến sâu
- Phổ biến nhất trong môi trường học thuật
- Cộng đồng người dùng lớn, tài liệu phong phú

**Nhược điểm**:

- Kiến trúc Back-end **Monolithic** thế hệ cũ
- Cồng kềnh, tiêu tốn nhiều tài nguyên Server
- Nút thắt cổ chai (Bottleneck) khi scale đột ngột trong các kỳ thi tập trung
- Giao diện người dùng phức tạp, trải nghiệm rời rạc

### 2. Canvas — Cloud LMS hiện đại

**Ưu điểm**:

- Vận hành trên nền tảng điện toán đám mây
- Thiết kế lấy người dùng làm trung tâm (User-centric Design)
- Hệ thống API phong phú, UI/UX tốt cho giáo dục chính quy

**Nhược điểm**:

- Mô hình SaaS đi kèm **chi phí vận hành rất cao**
- Mã nguồn đóng, hạn chế khả năng can thiệp Database
- Không phù hợp với các tổ chức giáo dục vừa và nhỏ

### 3. Udemy — MOOC Marketplace thương mại

**Ưu điểm**:

- Kiến trúc **Microservices** chịu tải cực tốt
- Hàng triệu luồng Streaming video đồng thời
- Trải nghiệm người dùng (UX) cực kỳ mượt mà

**Nhược điểm**:

- Công cụ kiểm tra đánh giá rất sơ sài (chủ yếu trắc nghiệm đơn giản)
- Thiếu tính khắt khe, minh bạch trong đánh giá
- Không có cơ sở giám sát quá trình học tập theo chuẩn hàn lâm

<a name="khoảng-trống-công-nghệ--điểm-mới"></a>

## Khoảng trống công nghệ & Điểm mới

### Khoảng trống cần giải quyết

1. **Sự đánh đổi giữa trải nghiệm và tính chuyên sâu**: Hệ thống UX mượt (Udemy) thì đánh giá sơ sài; hệ thống đánh giá tốt (Moodle) thì UX phức tạp.

2. **Chi phí và rào cản vận hành**: Sự cồng kềnh trong quản trị hạ tầng (Moodle) hay rào cản chi phí bản quyền (Canvas) khiến các cơ sở đào tạo quy mô vừa và nhỏ khó tiếp cận chuyển đổi số toàn diện.

3. **Nút thắt cổ chai về dữ liệu thi cử**: Trong các bài thi đồng thời quy mô lớn, hệ thống chưa được tối ưu truy vấn thường xuyên gặp Deadlock hoặc Timeout.

### Điểm mới của EDUMY

1. **Thiết kế tinh gọn, lai tạo ưu điểm**: Kết hợp trải nghiệm Front-end mượt mà (như Udemy) với sự khắt khe trong đánh giá năng lực (như Moodle).

2. **Chuẩn hóa giao tiếp hệ thống**: Áp dụng chặt chẽ kiến trúc RESTful API, Front-end và Back-end hoạt động độc lập, dễ dàng đóng gói Docker và mở rộng theo lưu lượng thực tế.

3. **Luồng đánh giá tích hợp (Integrated Flow)**: Module kiểm tra đánh giá trực tuyến được liên kết trực tiếp vào tiến trình học, tự động hóa lưu trữ điểm số với độ toàn vẹn dữ liệu cao nhất.

4. **Chi phí tối ưu**: Tận dụng công nghệ mã nguồn mở và miễn phí, phù hợp với ngân sách của các cơ sở đào tạo vừa và nhỏ.

<a name="kiến-trúc-hệ-thống"></a>

## Kiến trúc hệ thống

EDUMY được thiết kế theo kiến trúc **Microservices**, chia nhỏ hệ thống thành các dịch vụ nghiệp vụ hoạt động hoàn toàn độc lập, giúp bảo trì và mở rộng thuận lợi hơn so với khối mã nguồn Monolithic truyền thống.

### Sơ đồ kiến trúc tổng thể

```
┌─────────────────────────────────────────────────────────────────┐
│                         CLIENT LAYER                             │
│                                                                  │
│  ┌──────────────────────┐    ┌──────────────────────────────────┐│
│  │   Web Browser         │    │        Mobile App (Flutter)      ││
│  │  (React 19 + Vite 8) │    │     iOS & Android (Dart 3.10)    ││
│  │  Feature-Sliced Design│    │          (Scaffold)              ││
│  └──────────┬────────────┘    └──────────────┬───────────────────┘│
└─────────────┼────────────────────────────────┼───────────────────┘
              │ HTTPS / RESTful API           │ HTTPS / RESTful API
┌─────────────▼────────────────────────────────▼───────────────────┐
│                      API GATEWAY LAYER                            │
│                                                                   │
│  ┌─────────────────────────────────────────────────────────────┐  │
│  │                     Nginx 1.27-alpine                       │  │
│  │  • TLS Termination (Cloudflare Full Strict)                 │  │
│  │  • Reverse Proxy        • Request Routing                   │  │
│  │  • Security Headers     • Static File Serving               │  │
│  │  • Rate Limiting (backend) • SPA Fallback                   │  │
│  └─────────────────────────────────────────────────────────────┘  │
└───────────────────────────────┬───────────────────────────────────┘
                                │
┌───────────────────────────────▼───────────────────────────────────┐
│                     MICROSERVICES LAYER (4 services)               │
│                                                                    │
│  ┌────────────────┐ ┌────────────────┐ ┌──────────────┐ ┌───────┐│
│  │ Authentication │ │     System     │ │   Payment    │ │Course ││
│  │   Module       │ │   Management   │ │   Module     │ │ Mgmt  ││
│  │   .NET 8       │ │   Module       │ │   .NET 8     │ │Module ││
│  │   JWT+RBAC     │ │   .NET 8       │ │  VietQR/SePay│ │.NET 8 ││
│  │   Port: 5083   │ │   Port: 5243   │ │  Port: 5299  │ │:5164  ││
│  └───────┬────────┘ └───────┬────────┘ └──────┬───────┘ └───┬───┘│
│          │                  │                  │             │    │
│          └──────────────────┼──────────────────┼─────────────┘    │
│                             │                  │                  │
│  ┌──────────────────────────┼──────────────────┼──────────────┐   │
│  │          Internal Communication: X-Internal-Token header    │   │
│  └────────────────────────────────────────────────────────────┘   │
│                                                                    │
│  ┌────────────────────────────────────────────────────────────┐   │
│  │              SignalR Notification Hub                       │   │
│  │     (Real-time notifications via WebSocket)                 │   │
│  └────────────────────────────────────────────────────────────┘   │
└───────────────────────────────┬───────────────────────────────────┘
                                │
┌───────────────────────────────▼───────────────────────────────────┐
│                         DATA LAYER                                 │
│                                                                    │
│  ┌──────────────────────────┐  ┌────────────────────────────────┐ │
│  │     PostgreSQL 16        │  │       Supabase Storage         │ │
│  │  (Relational Database)   │  │   (Object Storage - S3 API)    │ │
│  │                          │  │                                │ │
│  │  • Users & Profiles      │  │  • Video bài giảng (MP4)       │ │
│  │  • Courses & Lessons     │  │  • Tài liệu PDF, Slide         │ │
│  │  • Question Banks        │  │  • Hình ảnh, thumbnail         │ │
│  │  • Transactions          │  │  • Tài nguyên bài giảng        │ │
│  │  • Exam Results          │  │                                │ │
│  │  • Catalog Data (CAT_*)  │  │                                │ │
│  └──────────────────────────┘  └────────────────────────────────┘ │
└────────────────────────────────────────────────────────────────────┘
```

### Nguyên lý hoạt động

1. **API Gateway (Nginx 1.27)** là điểm tiếp nhận duy nhất, chịu trách nhiệm:
   - TLS Termination thông qua Cloudflare (Full Strict mode)
   - Định tuyến request đến đúng Microservice theo URL prefix
   - Bảo mật với Security Headers (HSTS, X-Frame-Options, X-Content-Type-Options)
   - SPA Fallback cho Frontend, Static File Serving

2. **Các Microservice** giao tiếp với nhau qua RESTful API nội bộ, sử dụng header `X-Internal-Token` để xác thực liên service, đảm bảo hệ thống vận hành trơn tru ngay cả khi một service gặp sự cố.

3. **SignalR Notification Hub** cung cấp khả năng thông báo real-time qua WebSocket cho người dùng.

4. **PostgreSQL 16** là cơ sở dữ liệu duy nhất (shared database), tất cả 4 service truy cập chung nhưng mỗi service có DbContext riêng.

<a name="cấu-trúc-repository"></a>

## Cấu trúc Repository

Dự án được tổ chức thành 4 thư mục chính, mỗi thư mục là một Git repository riêng biệt:

```
Edumy/
├── BE/                                 # Backend - 4 Microservices .NET 8
│   ├── AuthenticationModule/           # Xác thực & phân quyền (port 5083)
│   │   ├── Presentation.Authentication.API/    # Entry point, Controllers
│   │   ├── Presentation.Context/               # DbContext, DTOs, Migrations
│   │   ├── Presentation.Services/              # Business logic
│   │   ├── Presentation.Repository/            # Data access layer
│   │   ├── Presentation.Models/                # Entity models
│   │   ├── Presentation.Extensions/            # Autofac modules, Middlewares
│   │   ├── Presentation.Common/                # Shared utilities
│   │   ├── CommonLibrary/                      # Shared library
│   │   ├── Tests/                              # Test project (scaffolded)
│   │   ├── Dockerfile
│   │   ├── .env / .env.example
│   │   └── .github/workflows/                  # CI/CD pipelines
│   │
│   ├── CourseManagementModule/         # Quản lý khóa học (port 5164)
│   │   └── (cấu trúc tương tự)
│   │
│   ├── PaymentModule/                  # Thanh toán (port 5299)
│   │   └── (cấu trúc tương tự)
│   │
│   └── SystemManagementModule/         # Quản trị hệ thống (port 5243)
│       └── (cấu trúc tương tự)
│
├── FE/                                 # Frontend
│   ├── EWebsite/                       # React Web App (chính)
│   │   ├── src/
│   │   │   ├── app/                    # Entry point, routing, providers
│   │   │   ├── pages/                  # Route-level components
│   │   │   ├── widgets/                # Complex UI blocks
│   │   │   ├── features/               # User-facing functionality
│   │   │   ├── entities/               # Domain entities
│   │   │   └── shared/                 # Reusable utilities, API, UI
│   │   ├── Dockerfile
│   │   ├── nginx.conf
│   │   └── .github/workflows/
│   │
│   └── Emobile/                        # Flutter Mobile App (scaffold)
│       └── lib/
│           ├── main.dart
│           └── shared/libs/l10n/       # Localization (vi/en)
│
├── Design/                             # Wireframe & Design System
│   ├── index.html                      # Navigation hub
│   ├── shared/                         # Design tokens, components, icons
│   │   ├── buttons/                    # 4 button types (HTML)
│   │   ├── layout/                     # 4 layout templates (HTML)
│   │   ├── icons/                      # 442 SVG icons (14 categories)
│   │   ├── Constants/                  # Colors (xlsx), Typography (PDF)
│   │   └── references/entites/         # 32 C# entity model files
│   └── Web/                            # 31 HTML prototype screens
│       ├── Auth/       (6 screens)
│       ├── Home/       (1 screen)
│       ├── Course/     (5 screens)
│       ├── Exam/       (6 screens)
│       ├── Cart/       (2 screens)
│       ├── User/       (4 screens)
│       └── Instructor/ (7 screens)
│
└── Infra/                              # Infrastructure & Deployment
    ├── docker-compose.yml              # 7 services orchestration
    ├── nginx/
    │   ├── conf.d/default.conf         # Reverse proxy config
    │   └── ssl/                        # Cloudflare Origin Cert
    ├── .env / .env.example             # Environment variables
    ├── .github/workflows/cd.yml        # CD pipeline
    └── scripts/cleanup.sh              # Docker image cleanup
```

<a name="phân-tích-yêu-cầu-chức-năng"></a>

## Phân tích yêu cầu chức năng

Hệ thống EDUMY được chia thành 4 module Microservice hoạt động độc lập, mỗi module đảm nhận một nhóm nghiệp vụ riêng biệt.

<a name="1-authentication-module"></a>

### 1. Authentication Module (Port 5083)

**Vai trò**: Người gác cổng của hệ thống, chịu trách nhiệm định danh người dùng và cấp phát quyền truy cập trước khi request được chuyển tiếp đến các service nghiệp vụ khác.

**Cơ chế xác thực**: Token-based Authentication sử dụng **JSON Web Token (JWT)** với khóa HMAC-SHA256. Khi xác thực thành công, hệ thống trả về Access Token (15 phút) và Refresh Token (7 ngày), cho phép Client đính kèm vào Header của các lần gọi API tiếp theo.

**Phân quyền**: Mô hình **Role-Based Access Control (RBAC)** với 4 vai trò:

| Vai trò                        | Quyền hạn chính                                                                 |
| ------------------------------ | ------------------------------------------------------------------------------- |
| **Quản trị viên (Admin)**      | Quản lý người dùng, phê duyệt giảng viên, CRUD danh mục, thống kê toàn hệ thống |
| **Người bảo trì (Maintainer)** | Hỗ trợ quản trị, phân quyền hạn chế                                             |
| **Giảng viên (Instructor)**    | CRUD khóa học, quản lý ngân hàng câu hỏi, tạo đề thi, chấm điểm                 |
| **Học viên (Student)**         | Xem khóa học, làm bài kiểm tra, theo dõi tiến độ                                |

**API Endpoints**:

| Method | Endpoint                                        | Auth             | Mô tả                            |
| ------ | ----------------------------------------------- | ---------------- | -------------------------------- |
| POST   | `/authen-module/api/v2/Auth/Register`           | Anonymous        | Đăng ký tài khoản (rate: 3/phút) |
| POST   | `/authen-module/api/v2/Auth/Login`              | Anonymous        | Đăng nhập (rate: 5/phút)         |
| POST   | `/authen-module/api/v2/Auth/ForgotPassword`     | Anonymous        | Quên mật khẩu (rate: 3/2phút)    |
| POST   | `/authen-module/api/v2/Auth/ResetPassword`      | Anonymous        | Đặt lại mật khẩu                 |
| POST   | `/authen-module/api/v2/Auth/Active`             | Anonymous        | Kích hoạt tài khoản              |
| POST   | `/authen-module/api/v2/Auth/RefrestToken`       | Anonymous        | Làm mới Access Token             |
| POST   | `/authen-module/api/v2/Auth/Logout/{userId}`    | Anonymous        | Đăng xuất                        |
| POST   | `/authen-module/api/v2/Auth/ChangePassword`     | Authenticated    | Đổi mật khẩu                     |
| GET    | `/authen-module/api/v2/Auth/GetProfile`         | Authenticated    | Xem hồ sơ người dùng             |
| GET    | `/authen-module/api/v2/Google/GetGoogleAuthUrl` | Anonymous        | Lấy URL Google OAuth             |
| POST   | `/authen-module/api/v2/Google/Web/Login`        | Anonymous        | Đăng nhập/đăng ký qua Google     |
| POST   | `/authen-module/api/v2/User/Pagingnation`       | Admin/Maintainer | Danh sách người dùng phân trang  |
| GET    | `/health`                                       | Anonymous        | Health check                     |

**Luồng xác thực**:

```
Client                    Auth Service                    Database
  │                          │                              │
  │── POST /api/auth/login ──│                              │
  │   {email, password}      │── Verify credentials ────────│
  │                          │                              │
  │                          │◄── User found ───────────────│
  │                          │                              │
  │                          │── Generate JWT ──────────────│
  │                          │  (Access + Refresh Token)    │
  │                          │                              │
  │◄── 200 OK ──────────────│                              │
  │   {accessToken,          │                              │
  │    refreshToken,         │                              │
  │    user, role}           │                              │
```

**Cơ chế bảo mật**:

- ASP.NET Core Identity với lockout (5 lần thử sai → khóa 15 phút)
- Refresh Token lưu dưới dạng SHA-256 hash trong DB
- Security Stamp Validation cho password reset và account activation
- Token rotation: Refresh Token cũ bị vô hiệu hóa khi đăng nhập

<a name="2-system-management-module"></a>

### 2. System Management Module (Port 5243)

**Vai trò**: Trung tâm điều khiển dành riêng cho Admin, tập trung vào việc duy trì sự ổn định của hệ thống, quản lý thông tin định danh cấp cao và thiết lập tham số vận hành chung.

**API Endpoints chính**:

| Method | Endpoint                                        | Mô tả                    |
| ------ | ----------------------------------------------- | ------------------------ |
| PUT    | `/system-module/api/v2/Profile/{userId}`        | Cập nhật hồ sơ           |
| PUT    | `/system-module/api/v2/Profile/{userId}/avatar` | Upload avatar            |
| DELETE | `/system-module/api/v2/Profile/{id}`            | Soft-delete người dùng   |
| PUT    | `/system-module/api/v2/Profile/{id}/restore`    | Khôi phục người dùng     |
| GET    | `/system-module/hubs/notification`              | SignalR Notification Hub |
| GET    | `/health`                                       | Health check             |

**Controllers hiện có**: CatCourseCategory, CatCourseType, CatDocumentCategory, CatDocumentType, CatExamCategory, CatGradingRule, CatInstructorApplicationRequirement, CatNotificationType, CatProvince, CatSubjectCategory, CatTag, CatVoucherType, Course, Exam, InternalNotification.

**Real-time**: SignalR Notification Hub cho phép推送 thông báo tức thời đến người dùng qua WebSocket.

<a name="3-payment-module"></a>

### 3. Payment Module (Port 5299)

**Vai trò**: Dịch vụ tài chính độc lập, chịu trách nhiệm quản lý toàn bộ vòng đời giao dịch từ khởi tạo đơn hàng, kết nối cổng thanh toán bên thứ ba, đến đối soát doanh thu.

**API Endpoints**:

| Method | Endpoint                                     | Mô tả                   |
| ------ | -------------------------------------------- | ----------------------- |
| POST   | `/payment-module/api/v2/PaymentOrder/create` | Tạo đơn hàng với VietQR |
| GET    | `/health`                                    | Health check            |

**Cổng thanh toán**: **VietQR** thông qua **SePay** (chuyển khoản ngân hàng QR).

**Luồng thanh toán**:

```
Học viên              Payment Service             SePay              Course Service
  │                        │                       │                    │
  │── Mua khóa học ────────│                       │                    │
  │                        │── Tạo Order ──────────│                    │
  │                        │   (Pending)           │                    │
  │◄── Mã QR VietQR ──────│                       │                    │
  │                        │                       │                    │
  │── Quét QR thanh toán ──┼───────────────────────│                    │
  │                        │                       │                    │
  │                        │◄── Webhook: Success ──│                    │
  │                        │                       │                    │
  │                        │── Cập nhật Order ─────│                    │
  │                        │   (Completed)         │                    │
  │                        │                       │                    │
  │                        │── Gọi API Enroll ─────┼────────────────────│
  │                        │                       │                    │
  │◄── Thông báo thành công────────────────────────┼────────────────────│
```

**Entities liên quan**: PaymentOrder, PaymentTransaction, Voucher, UserVoucher, Enrollment, ExamEnrollment.

<a name="4-course-management-module"></a>

### 4. Course Management Module (Port 5164)

**Vai trò**: Trái tim của toàn bộ nền tảng, quản lý vòng đời trọn vẹn của khóa học — từ tải lên tài nguyên, cấu hình học liệu, đến tương tác bài giảng và thực hiện đánh giá năng lực.

#### Quản lý khóa học

**Vòng đời khóa học**:

```
Draft ──→ Active ──→ Published
  ↑          │            │
  └──────────┘            │
  (Chỉnh sửa)      Học viên truy cập
```

**Entities chính**: Course, CourseSection, Lesson, Resource, Video, Enrollment.

#### Ngân hàng câu hỏi

**4 định dạng câu hỏi**:

| Định dạng                | Chấm điểm | Ví dụ                          |
| ------------------------ | --------- | ------------------------------ |
| Trắc nghiệm 1 đáp án     | Tự động   | A, B, C, D chỉ 1 đáp án đúng   |
| Trắc nghiệm nhiều đáp án | Tự động   | Chọn tất cả đáp án đúng        |
| Đúng / Sai               | Tự động   | True/False                     |
| Tự luận (Essay)          | Thủ công  | Viết đoạn văn, giảng viên chấm |

**Entities liên quan**: Question, QuestionOption, Exam, ExamQuestion, ExamAttempt, AttemptQuestion, AttemptAnswer.

#### Bài kiểm tra & Chấm điểm

| Chức năng             | Mô tả                                             |
| --------------------- | ------------------------------------------------- |
| Tạo đề thi            | Chọn câu hỏi từ ngân hàng, cấu hình tham số       |
| Bộ đếm thời gian thực | Đếm ngược, tự động thu bài khi hết giờ            |
| Xáo trộn đề           | Random thứ tự câu hỏi và đáp án                   |
| Tự động lưu nháp      | Lưu bài làm theo từng phút                        |
| Chấm tự động          | Trắc nghiệm + Đúng/Sai: đối chiếu đáp án tức thời |
| Chấm thủ công         | Tự luận: giảng viên chấm kèm phản hồi             |
| Thống kê kết quả      | Báo cáo điểm số, biểu đồ phân tích                |

#### Upload tài nguyên

| Chức năng        | Mô tả                                         |
| ---------------- | --------------------------------------------- |
| Upload Video     | Video bài giảng (lưu tạm rồi encode)          |
| Upload Thumbnail | Hình ảnh thumbnail khóa học                   |
| Upload Document  | Tài liệu PDF/Slide cho bài giảng              |
| Cloud Storage    | Lưu trữ trên Supabase Storage (S3-compatible) |

<a name="yêu-cầu-phi-chức-năng"></a>

## Yêu cầu phi chức năng

### Hiệu năng (Performance)

| Tiêu chí                            | Mục tiêu  | Ghi chú                                   |
| ----------------------------------- | --------- | ----------------------------------------- |
| Thời gian phản hồi API thông thường | < 2 giây  | Áp dụng cho đa số API (CRUD, tìm kiếm)    |
| Thời gian phản hồi API nộp bài      | < 500ms   | Yêu cầu tốc độ cao, đặc biệt trong thi cử |
| Thời gian xử lý AI (tạo đề thi)     | < 30 giây | Tác vụ bất đồng bộ, không gián đoạn UI    |

### Khả năng chịu tải (Scalability)

| Tiêu chí             | Mục tiêu                                        |
| -------------------- | ----------------------------------------------- |
| Người dùng đồng thời | Tối thiểu 1.000 người dùng                      |
| Kiến trúc mở rộng    | Horizontal Scaling — từng service scale độc lập |
| Assessment Engine    | Ưu tiên scale trước trong các kỳ thi tập trung  |

### Bảo mật (Security)

| Biện pháp             | Mô tả                                                           |
| --------------------- | --------------------------------------------------------------- |
| HTTPS (TLS 1.2/1.3)   | Mã hóa toàn bộ giao tiếp qua Cloudflare Full Strict             |
| JWT Authentication    | HMAC-SHA256, Access Token 15 phút, Refresh Token 7 ngày         |
| ASP.NET Core Identity | Built-in password hashing, lockout, security stamp              |
| RBAC                  | Role-Based Access Control cho 4 vai trò                         |
| Rate Limiting         | Giới hạn request tại AuthenticationModule (fixed window)        |
| Input Validation      | Kiểm tra đầu vào ở cả Client và Server                          |
| Security Headers      | HSTS, X-Frame-Options, X-Content-Type-Options, X-XSS-Protection |
| Docker Non-root       | Container chạy với user không phải root (appuser:appgroup)      |
| Internal API Token    | X-Internal-Token header cho giao tiếp liên service              |

### Độ tin cậy (Reliability)

| Tiêu chí       | Mục tiêu                              |
| -------------- | ------------------------------------- |
| Uptime         | Hướng tới 99.9%                       |
| Tính nhất quán | ACID cho giao dịch thanh toán         |
| Health Check   | Endpoint /health trên mỗi service     |
| Auto Restart   | Docker restart policy: unless-stopped |

### Khả năng bảo trì (Maintainability)

| Tiêu chí          | Mô tả                                      |
| ----------------- | ------------------------------------------ |
| Containerization  | Docker multi-stage build, Alpine Linux     |
| CI/CD             | GitHub Actions + GitOps deployment         |
| API Documentation | Swagger/OpenAPI trên mỗi service           |
| Logging           | Structured logging (JSON), contextual info |
| Code Style        | EditorConfig đồng nhất Across modules      |

### Trải nghiệm người dùng (UX)

| Tiêu chí        | Mô tả                                        |
| --------------- | -------------------------------------------- |
| Responsive      | Tối ưu cho Desktop, Tablet, Mobile           |
| Cross-browser   | Hoạt động trên Chrome, Firefox, Safari, Edge |
| Dark/Light Mode | Hỗ trợ giao diện tối/sáng (Ant Design)       |
| Loading State   | Lazy loading routes, Suspense fallback       |
| i18n            | Hỗ trợ đa ngôn ngữ (Vietnamese, English)     |

<a name="thiết-kế-cơ-sở-dữ-liệu"></a>

## Thiết kế cơ sở dữ liệu

### Cơ sở dữ liệu: PostgreSQL 16

**Chiến lược**: Shared Database — tất cả 4 Microservice truy cập chung một database (`edumy-core-master`), mỗi service có ApplicationDbContext riêng với query filter隔离 dữ liệu.

**ORM**: Entity Framework Core 8 với Npgsql provider.

**Các nhóm thực thể chính**:

#### Thực thể lõi (Core Entities)

| Entity                   | Mô tả                                                                                 |
| ------------------------ | ------------------------------------------------------------------------------------- |
| ApplicationUser          | Mở rộng IdentityUser: FullName, AvatarUrl, DOB, Gender, Address, ProvinceId, GoogleId |
| Course                   | Title, Description, ThumbnailUrl, Price, PromotionPrice, CreatorId, CourseTypeId      |
| CourseSection            | CourseId, Title, Order                                                                |
| Lesson                   | SectionId, Title, Type, Order, BusinessStatus                                         |
| Exam                     | CourseId, LessonId, Title, ExamCategoryId                                             |
| Question                 | Title, SubjectCategoryId                                                              |
| QuestionOption           | QuestionId, Content, IsCorrect                                                        |
| Enrollment               | UserId, CourseId, PaymentOrderId, Status                                              |
| ExamEnrollment           | UserId, ExamId, PaymentOrderId, Status                                                |
| PaymentOrder             | UserId, Code, SubTotal, DiscountAmount, TotalAmount, VoucherId, OrderStatus, QrUrl    |
| PaymentTransaction       | PaymentOrderId, BankName, AccountNumber, Amount, TransactionDate                      |
| Voucher                  | Code, DiscountType, DiscountValue, StartDate, EndDate, MaxUsage                       |
| Resource                 | LessonId, Title, Url, DocumentTypeId                                                  |
| Video                    | LessonId, Title, OriginalFileName, VideoStatus                                        |
| Notification             | NotificationType, Content                                                             |
| UserNotification         | UserId, NotificationId, IsRead                                                        |
| UserActionToken          | UserId, TokenHash, Type, ExpiresAt                                                    |
| Article                  | Content management                                                                    |
| Conversation/ChatMessage | Messaging system                                                                      |

#### Danh mục (Catalog Entities - CAT\_\* prefix)

| Entity                               | Mô tả                  |
| ------------------------------------ | ---------------------- |
| CAT_Province                         | Tỉnh/Thành phố         |
| CAT_CourseCategory                   | Danh mục khóa học      |
| CAT_CourseType                       | Loại khóa học          |
| CAT_SubjectCategory                  | Danh mục môn học       |
| CAT_ExamCategory                     | Danh mục bài thi       |
| CAT_DocumentCategory                 | Danh mục tài liệu      |
| CAT_DocumentType                     | Loại tài liệu          |
| CAT_Tag                              | Thẻ gắn                |
| CAT_Level                            | Cấp độ                 |
| CAT_Occupation                       | Nghề nghiệp            |
| CAT_GradingRule                      | Quy tắc chấm điểm      |
| CAT_VoucherType                      | Loại voucher           |
| CAT_InstructorApplicationRequirement | Yêu cầu đơn giảng viên |
| CAT_NotificationType                 | Loại thông báo         |

#### Base Entity Pattern

Tất cả catalog entities kế thừa `BaseEntity`:

- `Id` (auto-increment int)
- `Code`, `Name`, `Description`
- `IsDefault`, `SortOrder`
- `CreatedAt`, `CreatedBy`, `UpdatedAt`
- `Status` (GeneralStatus enum: Deleted=-1, InActive=0, Active=1)

**Soft Delete**: Tất cả entities sử dụng `GeneralStatus` enum với query filter để soft delete thay vì hard delete.

**Auto Timestamp**: `ApplicationDbContext.SaveChangesAsync()` tự động cập nhật `CreatedAt` và `UpdatedAt`.

<a name="ngăn-xếp-công-nghệ-tech-stack"></a>

## Ngăn xếp công nghệ (Tech Stack)

### Tổng quan

| Thành phần         | Công nghệ                                 |
| ------------------ | ----------------------------------------- |
| Backend Framework  | .NET 8 (ASP.NET Core Web API)             |
| Ngôn ngữ Backend   | C# 12                                     |
| ORM                | Entity Framework Core 8 (Npgsql)          |
| DI Container       | Autofac                                   |
| Object Mapping     | AutoMapper                                |
| Database           | PostgreSQL 16                             |
| Frontend Web       | React 19 + Vite 8 + TypeScript 6          |
| UI Library         | Ant Design 6 + Tailwind CSS 4             |
| Mobile             | Flutter (Dart 3.10)                       |
| API Gateway        | Nginx 1.27-alpine                         |
| Containerization   | Docker (multi-stage, Alpine Linux)        |
| CDN / TLS          | Cloudflare (Full Strict SSL)              |
| Authentication     | JWT (HMAC-SHA256) + ASP.NET Core Identity |
| OAuth              | Google OAuth 2.0                          |
| Payment Gateway    | VietQR via SePay                          |
| Object Storage     | Supabase Storage (S3-compatible)          |
| Real-time          | SignalR (WebSocket)                       |
| Localization       | ASP.NET Core IStringLocalizer + i18next   |
| Email              | SMTP (Gmail, async via job queue)         |
| CI/CD              | GitHub Actions + GitOps                   |
| Container Registry | GitHub Container Registry (GHCR)          |
| License            | GNU GPLv3                                 |

### Backend (.NET 8)

| Công nghệ                       | Mục đích                          |
| ------------------------------- | --------------------------------- |
| .NET 8                          | Nền tảng Backend Microservices    |
| ASP.NET Core Web API            | Xây dựng RESTful API              |
| Entity Framework Core 8         | ORM, tự động ánh xạ Database      |
| Autofac                         | Dependency Injection Container    |
| AutoMapper                      | Object-to-Object Mapping          |
| ASP.NET Core Identity           | User management, password hashing |
| System.IdentityModel.Tokens.Jwt | Xử lý JWT Authentication          |
| Swashbuckle                     | Swagger/OpenAPI documentation     |
| Supabase.Storage                | File/Object Storage client        |
| FluentEmail (SMTP)              | Email sending                     |
| SignalR                         | Real-time communication           |

**Lý do chọn .NET 8**:

- Hiệu năng xử lý luồng dữ liệu vượt trội nhờ Garbage Collection tiên tiến
- Ngôn ngữ C# mang tính chặt chẽ về kiểu dữ liệu, mô hình OOP hoàn chỉnh
- Khả năng xử lý đa luồng (Concurrency) giúp tiếp nhận hàng ngàn lượt nộp bài cùng lúc
- Hệ sinh thái thư viện phong phú, hỗ trợ mạnh từ Microsoft

### Frontend Web (React 19 + Vite 8)

| Công nghệ             | Phiên bản | Mục đích                        |
| --------------------- | --------- | ------------------------------- |
| React                 | 19        | Thư viện xây dựng giao diện SPA |
| Vite                  | 8         | Công cụ biên dịch, HMR          |
| TypeScript            | 6         | Kiểu dữ liệu tĩnh               |
| React Router          | 7         | Điều hướng SPA                  |
| Ant Design            | 6         | UI Component Library            |
| Tailwind CSS          | 4         | Utility-first CSS               |
| Axios                 | 1.18      | HTTP Client                     |
| TanStack React Query  | 5         | Server state management         |
| Zustand               | 5         | Client state management         |
| React Hook Form + Zod | 7 + 4     | Form handling & validation      |
| i18next               | 26        | Internacionalização             |

**Architecture**: Feature-Sliced Design (FSD) với các tầng: `app` → `pages` → `widgets` → `features` → `entities` → `shared`.

**Lý do chọn React + Vite**:

- Kiến trúc SPA giúp giao diện phản hồi nhanh, không tải lại trang
- Vite 8 mang lại tốc độ biên dịch cực nhanh và Hot Module Replacement
- TypeScript giúp phát hiện lỗi sớm, codebase dễ bảo trì
- Feature-Sliced Design tạo cấu trúc code rõ ràng, scalable

### Mobile (Flutter)

| Công nghệ            | Phiên bản | Mục đích                     |
| -------------------- | --------- | ---------------------------- |
| Flutter              | 3.x       | Framework Mobile đa nền tảng |
| Dart                 | 3.10      | Ngôn ngữ lập trình           |
| Provider             | 6         | Quản lý trạng thái           |
| Hive                 | 2         | Local storage                |
| flutter_svg          | 2         | Hiển thị SVG                 |
| cached_network_image | 3         | Cache hình ảnh               |
| Lottie               | 3         | Hiệu ứng animation           |

**Lý do chọn Flutter**:

- Biên dịch trực tiếp thành ứng dụng Native cho cả iOS và Android
- Công cụ kết xuất đồ họa độc lập, hiển thị sắc nét trên mọi thiết bị
- Hot Reload giúp tăng tốc phát triển

<a name="cấu-hình--triển-khai"></a>

## Cấu hình & Triển khai

### Môi trường Production

| Thành phần | Giá trị                       |
| ---------- | ----------------------------- |
| Domain     | `production.nhathungdev.site` |
| VPS        | Debian (Google Cloud)         |
| IP         | 35.190.177.59                 |
| TLS        | Cloudflare Origin Certificate |
| SSL Mode   | Full (Strict)                 |

### Docker Compose Services (7 services)

| Service                 | Image                                              | Port     |
| ----------------------- | -------------------------------------------------- | -------- |
| `nginx-proxy`           | `nginx:1.27-alpine`                                | 80, 443  |
| `edumy-ui-web`          | `ghcr.io/edumyvietnam/edumy-frontend:v1.0.0`       | 80\*     |
| `authentication-module` | `ghcr.io/edumyvietnam/edumy-authentication:v4.1.2` | 5083\*   |
| `course-module`         | `ghcr.io/edumyvietnam/edumy-course:v4.1.0`         | 5164\*   |
| `payment-module`        | `ghcr.io/edumyvietnam/edumy-payment:v3.0.1`        | 5299\*   |
| `system-module`         | `ghcr.io/edumyvietnam/edumy-system:v3.2.0`         | 5243\*   |
| `postgresdb`            | `postgres:16`                                      | 5432\*\* |

\* Port nội bộ, không publicly exposed
\*\* Bound to `127.0.0.1:5432` only

### Traffic Flow

```
Client → Cloudflare (Full Strict TLS) → Nginx (:443 HTTPS)
                                            │
                                    ┌───────┴───────┐
                                    │               │
                             Backend Modules    Frontend (:80)
                                    │
                             PostgreSQL (internal, localhost:5432)
```

### Nginx Configuration

- **TLS**: TLS 1.2/1.3 only, ECDHE ciphers
- **Security Headers**: HSTS (`max-age=31536000; includeSubDomains; preload`), X-Frame-Options SAMEORIGIN, X-Content-Type-Options nosniff, X-XSS-Protection
- **Upload Limit**: `client_max_body_size 100M`
- **Cloudflare Real IP**: `set_real_ip_from` cho tất cả Cloudflare IP ranges
- **SPA Fallback**: `try_files $uri $uri/ /index.html`
- **Static Asset Caching**: 1 year cho assets có hash

### Environment Variables (`.env`)

| Variable                            | Mô tả                        |
| ----------------------------------- | ---------------------------- |
| `POSTGRES_PASSWORD`                 | Mật khẩu PostgreSQL          |
| `ConnectionStrings__DbConnection`   | Connection string database   |
| `Jwt__SecretKey`                    | Khóa bí mật JWT              |
| `Jwt__Issuer` / `Jwt__Audience`     | JWT issuer/audience          |
| `GoogleOAuth__Web__ClientId`        | Google OAuth Client ID       |
| `GoogleOAuth__Web__ClientSecret`    | Google OAuth Client Secret   |
| `Smtp__Username` / `Smtp__Password` | SMTP credentials (Gmail)     |
| `Supabase__Key`                     | Supabase API Key             |
| `InternalApi__Token`                | Token giao tiếp liên service |

<a name="devops--cicd"></a>

## DevOps & CI/CD

### Cấu trúc CI/CD

Mỗi Microservice và Frontend đều có CI/CD pipeline riêng thông qua GitHub Actions:

```
┌──────────────────────────────────────────────────────────────┐
│                    CI/CD Pipeline Flow                        │
│                                                               │
│  Code Push → CI Build → Release → Docker Build → GitOps      │
│                                      │                        │
│                                      ▼                        │
│                              Push to GHCR                     │
│                                      │                        │
│                                      ▼                        │
│                        Repository Dispatch to Infra           │
│                                      │                        │
│                                      ▼                        │
│                          SSH → VPS → Docker Compose Up        │
│                                      │                        │
│                                      ▼                        │
│                          Telegram Notification                │
└──────────────────────────────────────────────────────────────┘
```

### CI Pipeline (`ci.yaml`)

**Trigger**: Push/PR to `main`

**Steps**:

1. Checkout code
2. Setup .NET 8.0
3. Restore NuGet packages (with caching)
4. Build (Release configuration)
5. Format check (`dotnet format --verify-no-changes`)
6. Publish & upload artifacts

### Docker Build Pipeline (`docker-build.yml`)

**Trigger**: On release

**Steps**:

1. Multi-platform Docker build (amd64 + arm64)
2. Push to GitHub Container Registry (GHCR)
3. GitOps: Update image tag in `Infra-cicd` repository
4. Trigger deployment via `repository_dispatch`

### CD Pipeline (`cd.yml`) — Infra Repository

**Trigger**: Push to `main`

**Steps**:

1. Detect changed service (via git diff + commit message regex)
2. SSH into VPS
3. `git fetch && git reset --hard origin/main`
4. Sync image tags from `.env.example` to `.env`
5. `docker compose pull --ignore-pull-failures`
6. `docker compose up -d --remove-orphans`
7. `docker image prune -f --filter "until=48h"`
8. Send Telegram notification on success

### Notification

- **Telegram Bot**: Thông báo deploy thành công qua HTML-formatted message
- **Release-Please**: Automated versioning và release notes

<a name="tình-trạng-hiện-tại-dự-án"></a>

## Tình trạng hiện tại dự án

> Cập nhật: Tháng 09/2026

### Tổng quan tiến độ

| Layer               | Trạng thái               | Ghi chú                                      |
| ------------------- | ------------------------ | -------------------------------------------- |
| **Backend**         | **Hoạt động**            | 4 microservices đã deploy production         |
| **Frontend Web**    | **Scaffold**             | Kiến trúc FSD hoàn thiện, UI chưa implement  |
| **Frontend Mobile** | **Scaffold**             | Chỉ có localization scaffolding              |
| **Design**          | **Hoàn thiện 31 screen** | Wireframe HTML cho tất cả chức năng chính    |
| **Infra**           | **Hoạt động**            | Docker Compose trên VPS, CD pipeline tự động |

### Backend — Chi tiết

| Module                 | Version | Trạng thái | Ghi chú                                  |
| ---------------------- | ------- | ---------- | ---------------------------------------- |
| AuthenticationModule   | v4.1.2  | Production | JWT, RBAC, Google OAuth, Rate Limiting   |
| CourseManagementModule | v4.1.0  | Production | CRUD khóa học, Section/Lesson, Upload    |
| PaymentModule          | v3.0.1  | Production | VietQR/SePay, PaymentOrder               |
| SystemManagementModule | v3.2.0  | Production | Profile, Catalogs, SignalR Notifications |

**Điểm mạnh**:

- Kiến trúc layered rõ ràng (API → Service → Repository → DbContext)
- Generic Repository + Generic Service pattern
- Autofac DI container
- Auto timestamp (CreatedAt/UpdatedAt) trong SaveChangesAsync
- Soft delete với GeneralStatus enum
- XML documentation trên tất cả controller actions
- EditorConfig đồng nhất code style
- Swagger/OpenAPI documentation
- Structured logging
- Health check endpoints

**Vấn đề cần xử lý**:

- Không có unit test hoặc integration test
- CORS开放 (`AllowAnyOrigin`) — cần restrict cho production domains
- `NotFoundException` handler chưa implement (throw `NotImplementedException`)
- Some blocking calls (`.Result`) trong async methods — có thể gây thread pool starvation
- Trivy vulnerability scanner bị tắt trong CI/CD
- Duplicate code giữa các module (entities giống nhau)
- Tên method có typo (`RefrestToken`, `Pagingnation`)

### Frontend Web — Chi tiết

**EWebsite (React 19)**:

| Thành phần       | Trạng thái | Ghi chú                                    |
| ---------------- | ---------- | ------------------------------------------ |
| Kiến trúc FSD    | Hoàn thiện | app/pages/widgets/features/entities/shared |
| Routing          | Hoàn thiện | Lazy loading, Suspense fallback            |
| Providers        | Hoàn thiện | QueryProvider + ThemeProvider              |
| Axios Client     | Hoàn thiện | baseURL, timeout, headers configured       |
| Pages            | Scaffold   | HomePage ("Application Initialized"), 404  |
| Widgets          | Scaffold   | Header, Sidebar, PageHeader — placeholder  |
| Features         | Scaffold   | Auth, Courses, Theme — placeholder         |
| Entities         | Scaffold   | Branch, Category, Course, Department, User |
| Shared UI        | Scaffold   | Button, Input, Spinner, ErrorFallback      |
| State Management | Scaffold   | Zustand installed, no stores implemented   |
| i18n             | Scaffold   | i18next installed, no config/translations  |
| Forms            | Scaffold   | react-hook-form + zod installed, no usage  |
| Tests            | Không có   | Không test framework, không test files     |

**Emobile (Flutter)**:

| Thành phần   | Trạng thái | Ghi chú                        |
| ------------ | ---------- | ------------------------------ |
| Localization | Hoàn thiện | Vietnamese + English ARB files |
| Main App     | Scaffold   | MaterialApp + "Hello World!"   |
| Screens      | Không có   | Chưa implement screen nào      |
| Tests        | Không có   | Không test files               |

### Design — Chi tiết

| Khu vực      | Số screen | Trạng thái    |
| ------------ | --------- | ------------- |
| Home         | 1         | Hoàn thiện    |
| Auth         | 6         | Hoàn thiện    |
| User Profile | 4         | Hoàn thiện    |
| Course       | 5         | Hoàn thiện    |
| Cart         | 2         | Hoàn thiện    |
| Exam         | 6         | Hoàn thiện    |
| Instructor   | 7         | Hoàn thiện    |
| Admin        | 0         | Chưa thiết kế |
| **Tổng**     | **31**    |               |

**Design System**:

- **Colors**: Primary (#2558E5), Secondary (#FF6B4A), Neutral, Success, Warning, Error, Info
- **Typography**: Inter font, weights 400-800, scale H1=56px → H6=20px
- **Components**: 4 button types (Primary, Secondary, Outline, Icon) × 4 states
- **Layouts**: Navbar, Footer, Admin Layout, Instructor Layout
- **Icons**: 442 SVG icons trong 14 categories

### Infrastructure — Chi tiết

| Thành phần          | Trạng thái     | Ghi chú                               |
| ------------------- | -------------- | ------------------------------------- |
| Docker Compose      | Hoạt động      | 7 services, single VPS                |
| Nginx               | Hoạt động      | TLS, Security Headers, SPA Fallback   |
| PostgreSQL          | Hoạt động      | Port 5432 (internal only)             |
| Cloudflare          | Hoạt động      | Full Strict TLS, CDN, DDoS protection |
| CI/CD               | Hoạt động      | GitHub Actions + GitOps               |
| Telegram Notify     | Hoạt động      | Deploy success notifications          |
| Monitoring          | Không có       | Không có monitoring/logging stack     |
| Database Backup     | Manual         | Chưa có automated backup              |
| Container Resources | Không có limit | Không set mem_limit/cpus              |



<a name="liên-hệ"></a>
## Liên hệ

Mọi thắc mắc, góp ý về đề tài EDUMY, xin vui lòng liên hệ:

| Kênh             | Thông tin                                                |
| ---------------- | -------------------------------------------------------- |
| **Email**        | quangnhathung2005@gmail.com                              |
| **Điện thoại**   | 0838557433                                               |
| **Địa chỉ**      | 77 Bùi Xuân Phái, Phường Phú Mỹ Hưng, Quận 7, TP.HCM     |
| **Website**      | [edumy.nhathungdev.site](https://edumy.nhathungdev.site) |
| **GitHub**       | [EdumyVietNam](https://github.com/EdumyVietNam)          |
| **Giờ làm việc** | Thứ 2 – Thứ 6: 8:00 – 18:00, Thứ 7: 8:00 – 12:00         |

---

## Bản quyền

© 2026 EdumyVietNam. All rights reserved.

_Made by Quang Nhat Hung_

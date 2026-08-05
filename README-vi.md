<p align="center">
    <img src="doc/demo/logo.png" width="80px" />
    <h1 align="center">Cloud Mail</h1>
    <p align="center">Dịch vụ email đơn giản, đáp ứng, được thiết kế để chạy trên Cloudflare Workers 🎉</p> 
    <p align="center">
       <a href="/README.md" style="margin-left: 5px">简体中文</a> | English 
    </p>
    <p align="center">
        <a href="https://github.com/maillab/cloud-mail/tree/main?tab=MIT-1-ov-file" target="_blank" >
            <img src="https://img.shields.io/badge/license-MIT-green" />
        </a>    
        <a href="https://github.com/maillab/cloud-mail/releases" target="_blank" >
            <img src="https://img.shields.io/github/v/release/maillab/cloud-mail" alt="releases" />
        </a>  
        <a href="https://github.com/maillab/cloud-mail/issues" >
            <img src="https://img.shields.io/github/issues/maillab/cloud-mail" alt="issues" />
        </a>  
        <a href="https://github.com/maillab/cloud-mail/stargazers" target="_blank">
            <img src="https://img.shields.io/github/stars/maillab/cloud-mail" alt="stargazers" />
        </a>  
        <a href="https://github.com/maillab/cloud-mail/forks" target="_blank" >
            <img src="https://img.shields.io/github/forks/maillab/cloud-mail" alt="forks" />
        </a>
    </p>
    <p align="center">
        <a href="https://trendshift.io/repositories/20459" target="_blank" >
            <img src="https://trendshift.io/api/badge/repositories/20459" alt="trendshift" >
        </a>
    </p>
</p>

## Mô tả
Chỉ với một tên miền, bạn có thể tạo nhiều địa chỉ email khác nhau, tương tự như các nền tảng email lớn. Dự án này có thể được triển khai trên Cloudflare Workers để giảm chi phí máy chủ và tự xây dựng dịch vụ email của riêng bạn.

## Trưng bày dự án

- [Demo trực tiếp](https://skymail.ink)<br>
- [Hướng dẫn triển khai](https://doc.skymail.ink/en/)<br>


| ![](/doc/demo/demo1.png) | ![](/doc/demo/demo2.png) |
|--------------------------|--------------------------|
| ![](/doc/demo/demo3.png) | ![](/doc/demo/demo4.png) |

## Tính năng

- **💰 Chi phí thấp**: Không cần máy chủ — triển khai trên Cloudflare Workers giúp giảm chi phí.

- **💻 Giao diện đáp ứng**: Tự động thích ứng với cả máy tính để bàn và hầu hết trình duyệt di động.

- **📧 Gửi email**: Tích hợp với Resend, hỗ trợ gửi email hàng loạt và file đính kèm.

- **🛡️ Tính năng quản trị**: Quản trị người dùng và email với kiểm soát truy cập theo RBAC.

- **📦 Hỗ trợ file đính kèm**: Gửi và nhận file đính kèm, lưu trữ và tải xuống qua Cloudflare R2.

- **🔔 Đẩy email**: Chuyển tiếp email nhận tới bot Telegram hoặc các nhà cung cấp email khác.

- **📡 API mở**: Hỗ trợ tạo người dùng hàng loạt qua API và truy vấn email theo nhiều điều kiện.

- **🔢 Nhận diện mã xác thực**: Tự động nhận diện mã xác thực bằng Workers AI.

- **📈 Trực quan hóa dữ liệu**: Sử dụng ECharts để hiển thị dữ liệu hệ thống, bao gồm tăng trưởng email người dùng.

- **🎨 Cá nhân hóa**: Tùy chỉnh tiêu đề trang web, nền đăng nhập và độ trong suốt.

- **🤖 CAPTCHA**: Tích hợp Turnstile CAPTCHA để ngăn đăng ký tự động.

- **📜 Thêm tính năng**: Đang phát triển...

## Công nghệ

- **Nền tảng**: [Cloudflare Workers](https://developers.cloudflare.com/workers/)

- **Web Framework**: [Hono](https://hono.dev/)

- **ORM**: [Drizzle](https://orm.drizzle.team/)

- **Frontend**: [Vue3](https://vuejs.org/)

- **UI**: [Element Plus](https://element-plus.org/)

- **Dịch vụ email**: [Resend](https://resend.com/)

- **Cache**: [Cloudflare KV](https://developers.cloudflare.com/kv/)

- **Cơ sở dữ liệu**: [Cloudflare D1](https://developers.cloudflare.com/d1/)

- **Lưu trữ file**: [Cloudflare R2](https://developers.cloudflare.com/r2/)

## Cấu trúc dự án

```
cloud-mail
├── mail-worker				    # Dự án backend worker
│   ├── src                  
│   │   ├── api				    # Lớp API
│   │   ├── const  			    # Hằng số dự án
│   │   ├── dao                 # Lớp truy cập dữ liệu
│   │   ├── email			    # Xử lý và xử lý email
│   │   ├── entity			    # Thực thể cơ sở dữ liệu
│   │   ├── error			    # Ngoại lệ tùy chỉnh
│   │   ├── hono			    # Web framework, middleware, xử lý lỗi
│   │   ├── i18n			    # Quốc tế hóa
│   │   ├── init			    # Khởi tạo DB và cache
│   │   ├── model			    # Mô hình dữ liệu phản hồi
│   │   ├── security		# Xác thực và phân quyền
│   │   ├── service		    # Lớp logic nghiệp vụ
│   │   ├── template		# Mẫu thông điệp
│   │   ├── utils			    # Hàm tiện ích
│   │   └── index.js			# Điểm vào
│   ├── package.json		# Phụ thuộc dự án
│   └── wrangler.toml		# Cấu hình dự án
│
├─ mail-vue			        # Dự án frontend Vue
│   ├── src
│   │   ├── axios 			    # Cấu hình Axios
│   │   ├── components		# Component tùy chỉnh
│   │   ├── echarts		    # Tích hợp ECharts
│   │   ├── i18n			    # Quốc tế hóa
│   │   ├── init			    # Khởi tạo khi startup
│   │   ├── layout		    # Component layout chính
│   │   ├── perm			    # Quyền và phân quyền
│   │   ├── request		    # Lớp request API
│   │   ├── router		    # Cấu hình router
│   │   ├── store			    # Quản lý state toàn cục
│   │   ├── utils			    # Hàm tiện ích
│   │   ├── views			    # Page components
│   │   ├── app.vue		    # Component gốc
│   │   ├── main.js		    # Entry JS file
│   │   └── style.css		# Styles toàn cục
│   ├── package.json		# Phụ thuộc dự án
└── └── env.release			# Cấu hình môi trường (release)
```

## Nhà tài trợ

<a href="https://doc.skymail.ink/support.html">
<img width="170px" src="./doc/images/support.png" alt="">
</a>

## Giấy phép

Dự án này được cấp phép theo giấy phép [MIT](LICENSE).

## Liên hệ

[Telegram](https://t.me/cloud_mail_tg)

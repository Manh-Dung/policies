# Hướng dẫn tạo trang Privacy Policy cho Ứng dụng Google Play

Tài liệu này là hướng dẫn để tạo các trang Chính sách Bảo mật (Privacy Policy) chuẩn chỉnh cho các ứng dụng tải lên Google Play, giúp tránh bị từ chối do vi phạm "Data Safety" và "Privacy Policy" (đặc biệt là lỗi thiếu thông tin về Xóa Dữ Liệu).

## 1. Yêu cầu Bắt buộc từ Google Play
Một trang Privacy Policy chuẩn của Google Play **PHẢI** có các thông tin sau:
1. **Thông tin về thu thập dữ liệu**: Thu thập những gì, dùng để làm gì (kể cả offline hay online).
2. **Dịch vụ bên thứ ba (Third-party Services)**: Nếu dùng Firebase, AdMob, Crashlytics, phải có link đến policy của họ.
3. **Thời gian lưu trữ dữ liệu (Data Retention)**: Lưu trữ trong bao lâu.
4. **Quyền Xóa Dữ Liệu (Data Deletion)**: Hướng dẫn người dùng cách xóa dữ liệu của họ (ví dụ: gỡ cài đặt, gửi email yêu cầu).
5. **Quyền riêng tư của trẻ em (Children's Privacy)**: Thông tin về việc không thu thập dữ liệu của trẻ dưới 13 tuổi (hoặc theo quy định).
6. **Thông tin liên hệ (Contact Us)**: Email hỗ trợ rõ ràng.

## 2. Template HTML chuẩn (Sections Quan trọng)

Khi tạo trang HTML mới, hãy đảm bảo copy các phần sau và điều chỉnh cho phù hợp với từng app:

### 2.1. Dịch vụ bên thứ ba (Third-Party Services)
Nếu app có dùng Firebase hoặc quảng cáo, cần liệt kê rõ:

```html
<section>
    <h2>Third-Party Services</h2>
    <p>We use a limited number of third-party services for app stability, analytics, and advertisements. We do not sell your personal data.</p>
    <ul>
        <li><strong>Firebase Analytics & Crashlytics:</strong> To understand usage trends and fix crashes. <a href="https://firebase.google.com/policies/analytics" target="_blank">Privacy Policy</a>.</li>
        <li><strong>Google AdMob:</strong> To serve advertisements. <a href="https://policies.google.com/privacy" target="_blank">Privacy Policy</a>.</li>
        <li><strong>Google Play Services:</strong> Required for core Android OS functionalities.</li>
    </ul>
</section>
```

### 2.2. Thời gian Lưu trữ và Xóa dữ liệu (Data Retention & Deletion) - RẤT QUAN TRỌNG

**Mẫu cho app OFFLINE (chỉ lưu trên máy, không có server riêng):**
```html
<section>
    <h2>Data Retention and Deletion</h2>
    <p>Your core app data is stored locally on your device and is not sent to any external servers. You can permanently delete all your data at any time by uninstalling the application from your device or clearing the app's data in your device's settings.</p>
    <p>For automatically collected information via third-party services (like Firebase Analytics), data is largely aggregated and pseudonymous. We retain such information for up to 14 months. You can stop all collection of information by uninstalling the Application.</p>
    <p>If you have provided us with any direct personal information (like an email address for support) and wish to have it deleted, please contact us at <strong>manhdung5a@gmail.com</strong>. We will process your request and delete your data within a reasonable timeframe.</p>
</section>
```

**Mẫu cho app ONLINE (có Database, lưu trên Firebase/Server):**
```html
<section>
    <h2>Data Retention and Deletion</h2>
    <p>We retain your personal data as long as your account is active. If you wish to delete your account and all associated data, please use the "Delete Account" feature within the app's settings or contact us at <strong>manhdung5a@gmail.com</strong>.</p>
    <p>Upon receiving your request, we will permanently delete your account and personal data from our active databases within a reasonable timeframe, unless retention is required by law.</p>
</section>
```

### 2.3. Quyền của Trẻ em
```html
<section>
    <h2>Children’s Privacy</h2>
    <p>Our service does not address anyone under the age of 13. We do not knowingly collect personal information from children.</p>
</section>
```

### 2.4. Thông tin liên hệ
```html
<section class="contact-info">
    <h2>Contact Us</h2>
    <p>If you have any questions about this Privacy Policy or your data, please contact us at:</p>
    <p><strong>Name:</strong> Nguyễn Mạnh Dũng</p>
    <p><strong>Email:</strong> manhdung5a@gmail.com</p>
</section>
```

## 3. Checklist khi Publish App (Data Safety Form)
Khi điền form **Data safety** trên Google Play Console:
1. **Thu thập dữ liệu:** Có (nếu có dùng Firebase/Crashlytics).
2. **Loại dữ liệu:** Crash logs, App performance, Device IDs, v.v. (tùy thuộc Firebase thu thập gì).
3. **Mục đích:** Analytics, Developer communications.
4. **Xóa dữ liệu (QUAN TRỌNG):** Phải chọn **"Có cơ chế để người dùng yêu cầu xóa dữ liệu"** (Users can request that their data is deleted).
5. **Link yêu cầu xóa dữ liệu:** Dán URL trang Privacy Policy của app vào đó (ví dụ: `https://manh-dung.github.io/policies/period_tracker/`).

Làm đúng các bước này sẽ đảm bảo app luôn tuân thủ chuẩn Policy mới nhất của Google Play!

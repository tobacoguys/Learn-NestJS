<h1>Giới thiệu về NestJS</h1>
Trong bộ bài viết này, chúng ta sẽ tìm hiểu những cơ bản của Nest. Để làm quen với Nest, chúng ta sẽ xây dựng CRUD cơ bản với các tính năng cơ bản.

<h2>Ngôn ngữ</h2>
Nest tương thức với cả TypeScript và JavaScript. Để sử dụng JavaScript thì phải cần biên dịch Babel. <br>
Nest chủ yếu sử dụng TypeScript, nhưng có thể chuyển các đoạn mã sang JavaScript gốc.

<h2>Cài đặt</h2>
Thiết lập dự án với Nest CLI. Với npm được cài đặt, bạn có thể tạo 1 dự án NestJS theo lệnh sau:
$ npm i -g @nestjs/cli
$ nest new project-name

Thư mục project-name sẽ được tạo, các module và 1 số tệp mẫu khác sẽ được cài đặt và thư mục src/ sẽ được tạo và chứa 1 số tệp cốt lõi. <br>

<img src="https://images.viblo.asia/full/c9b434cd-bb2b-4c88-b8a9-27cd3bc70949.png">

Giải thích:
app.controller.ts: Chứa các router để xử lý các request và trả về response cho client.
app.controller.spec.ts: Có nhiệm vụ viết unit-test cho các controller. Như kiểu kiểm tra các logic của app.controller để đảm bảo rằng các phương thức và endpoint hoạt động chính xác
app.module.ts: Module gốc của ứng dụng. Nó được đóng vai trò là "trung tâm" của ứng dụng trong việc cấu hình và kết nối các thành phần khác của ứng dụng, chẳng hạn như controllers, services, modules con và các providers.
app.service.ts: Service chứa các logic mà controller sẽ dùng đến.
main.ts: Sử dụng nestFactory để tạo ứng dụng

Về cơ bản thì main.ts sẽ sử dụng static method create() của NestFactory để tạo server app như sau:

import { NestFactory } from '@nestjs/core';
import { AppModule } from './app.module';

async function bootstrap() {
    const app = await NestFactory.create(AppModule);
    await app.listen(3000);
}
boostrap();

static method create() là 1 phương thức tĩnh của lớp NestFactory, được sử dụng để khởi tạo và cấu hình ứng dụng, từ đó bắt đầu chạy ứng dụng trên 1 server HTTP.
Ngoài ra NestJS khuyến khích chúng ta nên tuân thủ theo cấu trúc project như sau để luôn giữ cho mã sạch, tái sử dụng, độc lập và khả năng mở rộng cao.

https://images.viblo.asia/full/55e76541-b477-4b79-abef-6961e7599c5c.png
<img src="https://images.viblo.asia/full/55e76541-b477-4b79-abef-6961e7599c5c.png">

<h2>Chạy ứng dụng</h2>
Sau khi quá trình cài đặt hoàn tất, chạy lệnh sau để được nhận đường dẫn HTTP được gửi đến:
$ npm run start

Lệnh này khởi động ứng dụng với máy chủ HTTP được xác định trong tệp src/main.ts. Khi ứng dụng đang chạy, hãy mở trình duyệt của bạn và điều hướng đến http://localhost:3000/. Bạn sẽ thấy thông báo Hello World!

Ngoài ra để theo dõi những thay đổi trong tệp, chạy lệnh:
$ npm run start:dev
Lệnh này sẽ theo dõi các tệp của bạn, tự động biên dịch lại và tải lại máy chủ.
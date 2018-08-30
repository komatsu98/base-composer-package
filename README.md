# Bài tập Trainee Colombo 2018

## Base composer package

Thực hiện bởi [Hồ Anh Tiến](https://github.com/komatsu98)

## Liên kết

- [Hướng dẫn](http://www.darwinbiler.com/creating-composer-package-library/)
- [demo](https://packagist.org/packages/komatsu98/random-string)

## Các bước thực hiện

### Tạo cấu trúc thư mục project

Chạy dòng lệnh sau trong console (sau khi đã cài đặt composer). Thay đổi **mylibrary** trong lệnh sau thành tên thư viện của bạn.
   
    
    composer create-project buonzz/composer-library-template mylibrary


Lệnh trên chỉ tạo ra một thư viện mới dưới thư mục mylibrary. Hãy xem các file được tạo ra:

* **src** đây là nơi đặt code của bạn, mỗi class sẽ cần cư trú tại file riêng của nó trong thư mục này.
* **tests** mỗi class trong thư mục src cần được test trước khi được "include" ở nơi khác. Vì vậy cơ bản ta chỉ tạo các class test để test các class khác.
* **.gitignore** ignore file, không publish lên Git.
* **LICENSE** các điều khoản về giấy phép, bản quyền.
* **README.md** tài liệu mini về thư viện, hiển thị ở homepage khi push lên github và packagist.
* **composer.json** lưu giữ thông tin về thư viện, như là tên package, tác giả và các dependency.
* **phpunit.xml** là file cấu hình của PHPUnit.

Đây là cấu trúc cơ bản nhất để bắt đầu.

### Tối ưu hóa các file đã được tạo

Đổi tên file **src/YourClass.php** thành tên class của bạn.Nhớ rằng không nên đặt nhiều class vào trong cùng 1 file PHP. Như vậy thì tên class khi chọn sẽ khớp với tên file. Nếu cần viết class khác, hãy tạo 1 file mới.

#### Namespacing

Namespace cho các class để chúng không bị xung đột khi dùng trong ứng dụng. Thông thường, namespace tốt là Github username củ bạn.

Trên thực tế, mỗi class bạn tạo nên được đặt dưới cú pháp **VendorNamePackageName**. Đây nên là dòng đầu tiên trong mỗi class trong thư viện của bạn.


### Publish những thứ bạn đã làm

> Trước khi publish package, hãy chắc rằng bạn đã thay đổi trường "type" trong file composer.json thành "library". Điều này giúp cho package.org có thể nhìn nhận package của bạn như một thư viện.

Giờ bạn cần có tài khoản ở các trang sau để publish công việc của mình:

Nếu chưa có tài khoản hãy đăng ký trước. Sau khi tạo repo mới trên tài khoản github của mình, repo nên được đặt tên giống với tên thư viện. Sau đó push thư viện lên repo đó bằng cách:
    
    
    git init
    git remote add origin [[email protected]][2]:yourusername/yourlibraryname.git
    git add --all
    git commit -m "initial files"
    git tag -a v1.0.0 -m "initial release"
    git push -u origin master

Sau đó, click vào tab **Settings** trên repo. Ở cột bên trái, click **Webhooks & Services**. Ở tab **Services**, click **Add Service** chọn **Packagist**

Nhập username và token packagist của bạn.

Để lấy token, vào [trang profile][3] và click nút **Show Token** để copy token. Paste token này vào GitHub.

Paste url của Github repo trên packagist. Có thể mất một lúc để packagist validate tên package và thư viện. Khi hoàn tất, package của bạn giờ đã lên packagist!

Để dùng thư viện của bạn, đơn giản chỉ cần
    
    
    composer init
    composer require yourusername/yourpackagename

Sau đó tạo file index.php sẽ load autoloader
    
    
    require 'vendor/autoload.php';

Tất cả class trong thư viện của bạn đã sẵn sàng để sử dụng!

* * *


[1]: http://www.darwinbiler.com/designing-and-making-the-readme-file-for-your-github-repository/
[2]: http://www.darwinbiler.com/cdn-cgi/l/email-protection
[3]: https://packagist.org/profile/


## Kiến thức nắm được

- Biết tạo 1 package cơ bản
- Biết viết Test cơ bản cho chương trình PHP của mình

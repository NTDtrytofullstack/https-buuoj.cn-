# https-buuoj.cn-
- Cùng đến với 1 bài tập cơ bản nhưng mình thấy khó VKl nào :)).
![image](https://user-images.githubusercontent.com/130078745/232853635-768fd672-ee9b-43bf-8c13-89145e92b66e.png)
- Nhìn lướt qua ta có thể thấy để lấy đc flag thì v2 phải = 11.28125.
- Cùng vào terminal để xem chi tiết và debug.
![image](https://user-images.githubusercontent.com/130078745/232861621-40dae26c-391f-473c-88fe-1edcdde59476.png)
- Ta sử dụng Tel để xem địa chỉ 1 cách chi tiết.
![image](https://user-images.githubusercontent.com/130078745/232865975-5071c435-b07e-485d-9a3c-2eb46d6adb6d.png)
- với biến v1 có 44 byte , ta sẽ sử dụng buffer overflow nhập vào đủ 44 byte dữ liệu ở v1 nhập tiếp 4 byte dữ liệu để cho 4 byte đó tràn sang v2 và đạt đc những gì chúng ta muốn làm.
- Để tràn dữ liệu sang cho v2 = 11.28125 chúng ta cần chuyển sang kiểu dữ liệu HEX mới có thể nhập đc, để làm dc điều đó ta cần vào https://www.h-schmidt.net/FloatConverter/IEEE754.html để thực hiện việc chuyển đổi:
![image](https://user-images.githubusercontent.com/130078745/232864549-12397262-6118-4ec0-b67f-cb64ae305bec.png)
- để nhập biến ta sử dụng framesswork của python viết tools để thực hiện đc việc nhập dữ liệu vào v2.
![image](https://user-images.githubusercontent.com/130078745/232868952-f3af919d-bd97-44c0-b1c0-f1220e1315e9.png)
- sau khi viết tools ta cùng chạy thử: ![image](https://user-images.githubusercontent.com/130078745/232871261-ebbbc340-0ea9-45c5-96d8-7ddf5281ccc4.png)
- Nhưng tại sao ta vẫn ko thu đc flag ?
- Đó là vì file flag mà t cần ko có sẵn trong máy mà nằm trong sever của trang web gốc , thế nên ta cần lấy id sever và cùng truy cập vào sever để lấy flag:
- Đây là host port của sever: ![image](https://user-images.githubusercontent.com/130078745/232872970-95059415-bbb7-4fe3-aede-cc78b8123c2a.png)
- sau đấy ta cần thực hiện câu lệnh truy cập vào sever : ![image](https://user-images.githubusercontent.com/130078745/232873202-a6bceabc-fee0-479e-8b87-696a8cc8e7a3.png)
- Nhưng ta cần có 1 lưu ý , chương trình ko thể chạy đồng thời 2 đối tượng và các câu lệnh trước đã trèn đc dữ liệu vào v2 và thứ chúng ta cần bây giờ chỉ là truy cập vào sever lấy flag cho nên ta chỉ cần câu lệnh truy cập vào sever thôi.
- Ta cùng chạy lại chương trình để xem flag của chúng ta: ![image](https://user-images.githubusercontent.com/130078745/232873784-f7f2fe5c-8902-4b15-bc7b-670549d5f5f2.png)
- Sau khi đã truy cập sever thành công , ta thu đc Flag như sau : **flag{7dd651f3-23c7-4383-bb86-6981bc3e539e}**.
- Cùng nhập flag vào trang web để xem có đúng ko nhé : ![image](https://user-images.githubusercontent.com/130078745/232874315-6510133a-a673-4557-afa1-60bbbc0e888a.png)
- Flag đã đúng : ![image](https://user-images.githubusercontent.com/130078745/232874462-af6767c0-4d2e-46c0-bc38-276195a75348.png)
---
# 1 Số câu lệnh cơ bản trong pwntool:
  ## Lệnh nhận giá trị:
  - recv() 
  - recvuntil(). vd: **recvuntil(b'hello ')** thì câu lệnh này sẽ lưu giữ liệu cho đến khi gạp chuỗi kí tự hello.
  ## lệnh đọc file
  - process(). vd: process(./ten_file)
  ## lệnh gửi dữ liệu.
  - send().
  - sendline(). là kiểu sau khi trả kiểu dữ liệu sẽ xuống dòng hay enter.
  - sendafter().vd: **sendafter(b'Hello ', biến). thì nó sẽ gửi dữ liệu sau chuỗi kí tự hello.
  - sendlineafter(). vd: **sendlineafter(b'Hello ', biến). thì nó sẽ gửi dữ liệu sau chuỗi kí tự hello sau đấy xuống dòng hay enter.
  ## kiểu trả về hay **return 0; bên C**:
  - interactive(). công dụng trả về dữ liệu hay dừng lại trong chương trình.
  ## lệnh chỉ k/l bit.
  - p64() = 64bit = 8byte.
  - p32()= 32bit = 4byte.
  - p16() = 16bit = 2byte.
  ## lẹnh truy cập sever.
  - remote('port',host).
  ## lệnh thực hiện trong môi trường.
  - process() là chạy trên chương trình.
  - remote() là lệnh chạy trên sever.
  ## *Lưu ý**
  - cũng phải đặt tên 1 biến tạo thành 1 đối tượng để chúng ta thực hiện: ![image](https://user-images.githubusercontent.com/130078745/232883578-8a34bb93-e394-435d-8e9f-3e2ee5f2b968.png)

- cùng xem 1 vài ví dụ: ![image](https://user-images.githubusercontent.com/130078745/232883706-b1a35bd1-2ac8-4633-a3a8-f4b5202fad49.png)

- như hình khi đã đặt tên 1 đối tượng để thực hiện ta cần phải gọi tên đối tương và **.** sau đấy là câu lệnh để có thể chạy chương trình như : **p.cau_lenh()**.

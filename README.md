## Đây là 1 wallet cá nhân với 1 số chức năng cơ bản đủ để mô tả quá trình hoạt động của solidity
Trước khi chạy phầm mềm này ta cân clone về 1 thư mục tùy ý
ta bật command prompt tại cửa sổ của ide, ở đây mình dùng ide là webstorm để minh họa 
#### xong đó dùng câu lệnh git clone https://github.com/doducDAD/wallet để có thể download về máy.
#### cài đặt ganache và metamask.
Vì solidity là một ngôn ngữ dùng để viết các contract mà các contract lại hoạt động trên các mạng, trên môi trường EVM của ETH, Em có làm một bài reseach nho nhỏ 
nói chi tiết về phần này của solidity tại : https://github.com/doducDAD/se2022-14.2/tree/main/ReseachW1 ở đây em đã nói chi tiết về EVM của ETH, và một số chức năng chính của solidity.
Ở đây công cụ để tạo một môi trưởng mạng ảo Local đó chính là Ganache đây là công cụ có thể nói tốt nhất hiện nay cho các blockchain dev. Có 2 công cụ buil phổ biến
hiện nay là hardhat và truffle thì ở ví dụ này em quyết định chọn truffle, ý tưởng đề tài khá đơn giản để có thể giải thích cơ bản về cách hoạt động của một contract


Trước tiên là với Ganache ta khởi động app lên sẽ có giao diện như sau :

![image](https://user-images.githubusercontent.com/74479681/206176944-d35eadc0-ecde-4c8a-b95f-6854e0f6d491.png)

Lúc này ta cần setup new workspace

![image](https://user-images.githubusercontent.com/74479681/206177160-2b9a8290-52d2-4248-a04e-b102702bb2d7.png)

Ta cần điền tên workspace(tùy ý) và sau đó tại phần add project ta cần trỏ đến file truffle-config tại chính thư mục ta vừa clone trên git

![image](https://user-images.githubusercontent.com/74479681/206177349-2998eb1f-52ce-4132-8a12-1825d7e6bdfa.png)

App lúc này hiện lên với 10 địa chỉ ví testnet cho chúng ta 

![image](https://user-images.githubusercontent.com/74479681/206177545-3249c4c4-7604-4453-9b94-7ecb2a4b0691.png)

### Tới bước setup cho metamask : 



Tại phần tạo tài khoản ta chọn nhập tài khoản:

  ![image](https://user-images.githubusercontent.com/74479681/206177883-da52c198-71b2-4c74-9964-8791ea31b818.png)

Lúc này tại app ganache ta chọn 1 ví để import bằng cách ấn show keys ở ngay bên cạnh 

![image](https://user-images.githubusercontent.com/74479681/206178051-c5fc35c5-773a-401c-bfd6-c2eb567c1a15.png)

Việc ta cần làm là copy dòng privatekey đó vào phần nhập tài khoản của metamask

####  Thêm mạng Ganache testnet local  :

Từ ví metamask ta ấn vô 

![image](https://user-images.githubusercontent.com/74479681/206178447-eb58a51d-2bb4-4677-b5e0-faadf32cc564.png)

sau đó ấn thêm mạng và chọn thêm mạng theo cách thủ công.

Với RPC lấy tại phần RPC Sever của ganache ta có thể setup như sau :

![image](https://user-images.githubusercontent.com/74479681/206178830-9779c764-889f-46c8-ad47-5a9ceae1d70d.png)

lúc này tài khoản đã nhận 100ETH là chúng ta đã kết nối với mạng thành công : 

![image](https://user-images.githubusercontent.com/74479681/206178877-e27a366f-746a-4696-980d-73cdb3f707e6.png)















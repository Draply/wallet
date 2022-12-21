## Đây là 1 wallet cá nhân với 1 số chức năng cơ bản đủ để mô tả quá trình hoạt động của solidity
Trước khi chạy phầm mềm này ta cân clone về 1 thư mục tùy ý
ta bật command prompt tại cửa sổ của ide, ở đây em dùng ide là webstorm để minh họa 
#### xong đó dùng câu lệnh git clone https://github.com/doducDAD/wallet để có thể download về máy.
#### cài đặt ganache và metamask.
Vì solidity là một ngôn ngữ dùng để viết các contract mà các contract lại hoạt động trên các mạng, trên môi trường EVM của ETH, em có làm một bài reseach nho nhỏ 
nói chi tiết về phần này của solidity tại : https://github.com/doducDAD/se2022-14.2/tree/main/ReseachW1 ở đây em đã nói chi tiết về EVM của ETH, và một số chức năng chính của solidity.
## EVM là gì ?
EVM nói một cách đơn giản là một phần trong mạng Ethereum có nhiệm vụ xử lý việc triển khai và thực thi trên smart contract. Một giao dịch chuyển ETH từ tài khoản EOA này qua tài khoản EOA khác sẽ không cần EVM xử lý. EVM có trên tất cả các client (node) của mạng Ethereum, hướng đến mục tiêu như là một máy tính phi tập trung toàn cầu.

EVM là một máy trạng thái Turing hoàn chỉnh, bởi vì tất cả các bước thực thi được giới hạn trong một lượng hữu hạn các bước tính toán. Đây là điều khác biệt so với Bitcoin khi trên bitcoin thì Stack Machine chỉ là máy Turing không hoàn chỉnh.

EVM được thiết kế theo kiến trúc stack-based, tất cả đều được lưu trong stack, word size là 256-bit. Các thành phần lưu trữ thông tin trên EVM được chia ra thành 3 phần

Một mã ROM cố định, không thể thay đổi. Được load cùng byte code của smart contract khi xử lý contract.
Một bộ nhớ ngắn hạn. . Khi muốn lưu trên Solidity thì dùng từ khóa memory
Một bộ nhớ dài hạn. Khi muốn lưu trên Solidity thì dùng từ khóa storage

![image](https://user-images.githubusercontent.com/74479681/208826525-8ad5f538-b0c5-4e60-b147-6063b4334e90.png)


### Ở đây công cụ để tạo một môi trưởng mạng ảo Local đó chính là Ganache đây là công cụ có thể nói tốt nhất hiện nay cho các blockchain dev. Có 2 công cụ buil phổ biến
hiện nay là hardhat và truffle thì ở ví dụ này em quyết định chọn truffle, ý tưởng đề tài khá đơn giản để có thể giải thích cơ bản về cách hoạt động của một contract



## Trước tiên là với Ganache ta khởi động app lên sẽ có giao diện như sau :

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

## Sơ qua về một số chức năng có trong contract mà chúng ta tạo 
file solidity nằm tại contracts/Faucet.sol
Ở đây ta có các funtion tương ứng với các chức năng : 
- addFunds : Thêm 1 lượng ETH vào ví của bản thân.
- getFundersIndex : trả về thông tin của ví vừa gửi ETH đến.
- getAllFunders   : trả về 1 list các ví đã gửi ETH đến ví.
- withdraw        : rút 1 lượng ETH từ ví của bản thân

Khi contract hoạt động, nó sẽ trả về 1 file Json và việc khai thác thông tin hay làm việc với 1 contract thực tế là chúng ta sẽ làm việc với chính file json này.
Ở đây vì em có chạy trước phần mềm 1 vài lần do đó đã có file json sẵn ở trong sản phẩm và được lưu tại public/Faucet.json

Nguyên lý hoạt động ở đây là khi ta deployed 1 contract nó sẽ được "Di cư " lên các node mạng blockchain và chạy trên đó, việc này được thực hiện qua file migrations(Tiếng Anh cũng có nghĩa là di cư). Ở đây cần được đặt tên theo định dạng sẵn ví dụ với tên 1_faucet_migration.js , thì 1 là thứ tự chạy, ví dụ dự án của chúng ta có nhiều contract và cùng deploy 1 thì thứ tự chạy của chúng sẽ do ta đặt tên và quyết định. Để có thể kiểm tra việc deploy có thành công hay không, ta có thể 
sử dụng câu lệnh : truffle migration tại termimnal. Ta có thể nhận được kết quả trả về dạng như sau :

Truffle v5.6.0 (core: 5.6.0)
Node v16.15.1
PS U:\NFT-Mar\faucet> truffle migration

Compiling your contracts...
===========================
> Compiling .\contracts\Faucet.sol
> Compiling .\contracts\Faucet.sol
> Artifacts written to U:\NFT-Mar\faucet\public\contracts
> Compiled successfully using:
   - solc: 0.8.9+commit.e5eed63a.Emscripten.clang


Starting migrations...
======================
> Network name:    'development'
> Network id:      5777
> Block gas limit: 6721975 (0x6691b7)


1_faucet_migration.js
=====================

   Replacing 'Faucet'
   ------------------
   > transaction hash:    0xab6fc670b480b35c1339d71fb60e1d3f3245f1318ea4f8a8905b088485dc3eff
   > Blocks: 0            Seconds: 0                                                                                                                                                                                                    
   > contract address:    0x989a89e10385e956Dd59a8B6Be3e9dbe1153c863
   > block number:        1
   > block timestamp:     1670417661
   > account:             0x68BFC772b95DAD13c23A32Eb91f9C8C96d5dF6Cb
   > balance:             99.98997682
   > gas used:            501159 (0x7a5a7)
   > gas price:           20 gwei
   > value sent:          0 ETH
   > total cost:          0.01002318 ETH

   > Saving artifacts
   -------------------------------------
   > Total cost:          0.01002318 ETH

Summary
   - solc: 0.8.9+commit.e5eed63a.Emscripten.clang

ở đây ta đang mint ra một địa chỉ ví cá nhân, ta có thể thấy được một cách trực quan qua ganache tại cửa sổ Block, Transaction và Contract tại Ganache.

![image](https://user-images.githubusercontent.com/74479681/206185211-7fa127ca-0fc4-4b6d-bf52-b9e6df1fc86d.png)

Với Created Contract Address là địa chỉ ví được tạo cho ví cá nhân mà phần mềm chúng ta sẽ sử dụng. Ở ví dụ hiện tại trên máy em là  : 
0x4d0492DF51198d9fF814881dCa9AB9d87AA482e4


Tiếp đó để khởi động phần mềm tại termimnal ta thực hiện lệnh npm start.
Tại đây ta cần connect metamask với trang web sao cho địa chỉ ví hiện ra giống như địa chỉ ví đã import vào metamask trước đó  :


![image](https://user-images.githubusercontent.com/74479681/206186317-6b8afdd5-e7ea-42d7-867f-a3cc8ce0cd13.png)

khi ta thực hiện add 1 ETH 

![image](https://user-images.githubusercontent.com/74479681/206187217-e464ba65-8f40-49da-9139-e99ed604e234.png)

cửa sổ metamask yêu cầu xác nhận với đầy đủ số lượng ETH cần chuyển cũng như chi phí chuyển (ở đây được tính bằng gas, 1ETH = 1000gas và ta có thể tăng gas với 1 số giao dịch nhằm được phân quyền uy tiên trong một số trường hợp như có nhiều người cùng mua 1 token thì ai gas nhiều hơn sẽ được ưu tiên giao dịch trước )

![image](https://user-images.githubusercontent.com/74479681/206187705-ff1bf10e-3b83-4851-8931-2c1c7bb3ade3.png)

Ở đây tài khoản của chúng ta vừa tạo đã nhận được 1 ETH :

Kiểm tra contract tại công cụ ganache phần transaction  ta cũng có thể thấy 

![image](https://user-images.githubusercontent.com/74479681/206188993-b61c8622-01ce-4f2d-8f18-366583cb5e9f.png)

phần to contract Addresss : 0x4d0492DF51198d9fF814881dCa9AB9d87AA482e4  là địa chỉ nhận cũng chính là địa chỉ ví ta vừa tạo. giá trị là 1ETH với số gas là 85075. Được thực hiện bởi hàm addFund của contract.














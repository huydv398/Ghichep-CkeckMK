# Tìm hiểu giao thức SNMP

Giới thiệu giao thức SNMP

>**SNMP** (Simple Network Management Protocol)-Giao thức quản lý mạng đơn giản. Là một tập hợp các giao thức không chỉ cho phép kiểm tra nhằm đảm bảo các thiết bị mạng như Route, Switch hay Server đang vận hành mà vận hành một cách tối ưu, ngoài ra SNMP còn cho phép quản lý các thiết bị từ xa.

Ví dụ: Dùng SNMP để tắt một Interface nào đó trên Route, theo dõi hoạt động của Card Internet hoặc kiểm soát nhiệt độ trên Switch.

Tất cả các thiết bị có thể chạy các phần mềm cho phép lấy được thông tin SNMP đều có thể quản lý được. Không chỉ các thiết bị vật lý mà cả những phần mềm như Web server, database.

![Imgur](https://i.imgur.com/36YHIhj.png)

* Network management station: Thường là một máy tính chạy phần mềm quản lý SNMP dùng để giám sát và điều khiển tập chung các Network element
* Network element (Device, host, Application): là các thiết bị, máy tính hoặc phần mềm tương thích SNMP và được quản lý bởi Network Management 
* Một Management station có thể quản lý nhiều element và một element cũng có thể được quản lý bởi nhiều Management

Giao thức là một tập hợp các thủ tục mà các bên tham gia cần tuân theo để có thể giao tiếp được với nhau. Trong lĩnh vực thông tin, một giao thưc quy định, định dạng(format) của dòng dữ liệu trao đổi với nhau và quy định trình tự, thủ tục để trao đổi dòng dữ liệu đó. Nếu một bên tham gia gửi dữ liệu không đúng định dạng hoặc không theo trình tự thì bên khác sẽ không hiểu hoặc từ chối trao đổi thông tin. SNMP là một giao thức, do đó nó có những quy định riêng mà các thành phần trong mạng phải tuân theo.

Một thiết bị hiểu được và hoạt động tuân theo giao thức SNMP được gọi là "có hỗ trợ SNMP" (SNMP Supported) hoặc "tương thích SNMP" (SNMP compartible) 

SNMP dùng để quản lý, nghĩa là có thể theo dõi, có thể lấy thông tin, có thể được thông báo, và có thể tác động để hệ thống hoạt động như ý muốn. VD một số khả năng của phần mềm  SNMP:

* Theo dõi tốc độ đường truyền của một Route, biết được tổng số byte đã truyền và nhận
* Lấy thông tin máy chủ đang có bao nhiêu ổ cứng, mỗi ổ cứng còn trống bao nhiêu.
* Tự động nhận cảnh báo khi switch có một port bị down
* Điều khiển tắt (shutdown) các port trên Switch.

SNMP dùng để quản lý mạng, nghĩa là nó có thể chạy trên nền TCP/IP và quản lý các thiết bị mạng TCP/IP. Các thiết bị mạng không nhất thiết phải là máy tính mà có thể là switch, route, Firewall, ADSL Gateway, và cả một số phần mềm cho phép quản trị bằng SNMP. Giả sử bạn có một thiết bị được gắn địa chỉ IP có thể kết nối mạng và nó hỗ trợ SNMP thì có thể quản lý nó từ xa bằng SNMP.

Nó được thiết kế đơn giản trong cấu trúc bản tin và thủ tục hoạt động, và còn đơn giản trong bảo mật. Sử dụng phần mềm SNMP, người quản trị mạng có thể quản lý, giám sát tập chung từ xa toàn mạng của mình.

## Ưu điểm trong thiết kế của SNMP

SNMP được thiết kế đơn giản hóa quá trình quản lý các thành phần trong mạng. Nhờ đó các thành phần SNMP có thể được phát triển nhanh và tốn ít chi phí

SNMP được thiết kế để có thể mở rộng các chức năng quản lý, giám sát. Không có giới hạn rằng SNMP có thể quản lý được cái gì. khi có một thiết bị mới với các thuộc tính, tính năng mới thì người ta có thể thiết kế "custom" SNMP để phục vụ riêng cho riêng mình

SNMP được thiết kế để có thể hoạt động độc lập với các kiến trúc và cơ chế của các thiết bị hỗ trợ SNMP. Các thiết bị khác nhau có hoạt động khác nhau nhưng đáp ứng SNMP là giống nhau. 

### Các phiên bản của SNMP
SNMP có 4 phiên bản : SNMPv1, SNMPv2c, SNMPv2u và SNMPv3

## Các khái niệm nền tảng SNMP

### Các thành phần trong SNMP

Kiến trúc của SNMP 
![Imgur](https://i.imgur.com/36YHIhj.png)

* Network management station: Thường là một máy tính chạy phần mềm quản lý SNMP dùng để giám sát và điều khiển tập chung các Network element
* Network element (Device, host, Application): là các thiết bị, máy tính hoặc phần mềm tương thích SNMP và được quản lý bởi Network Management 
* Một Management station có thể quản lý nhiều element và một element cũng có thể được quản lý bởi nhiều Management


1 element có thể được quản lý bởi 2 station. Nếu station lấy thông tin từ element thì cả 2 station sẽ có thông tin giống nhau. Nếu cả 2 tác động đến cùng 1 element thì element sẽ đáp ứng cả 2 theo thứ tự cái nào đến trước.

Ngoài ra còn có khái niệm SNMP agent. SNMP agent là một tiến trình (process) chạy trên Network Element, có nhiệm vụ cung cấp thông tin của Element cho Station, nhờ đó station có thể quản lý được element. Chính xác hơn là Application chạy trên station và Agent chạy trên element. 2 tiến trình này giao tiếp với nhau

![Imgur](https://i.imgur.com/SIJl7q5.png)

### Object ID

Mỗi thiết bị hỗ trợ SNMP có thể cung cấp nhiều thông tin khác nhau, mỗi thông tin đó được gọi là Object. ví dụ:

* Máy tính có thể được cung cấp thông tin: Tổng số ổ cứng, tổng số port nối mạng, tổng byte đã truyền - nhận, tên máy, tên các process đang chạy,...
* Route có thể cung cấp các thông tin: tổng số card, tổng số port, tình trạng của các Port trên route,...

Mỗi Object có một tên gọi và một mã để nhận dạng Object đó, mã số được gọi là Object ID.

Ở hầu hết các thiết bị, các Object có nhiều giá trị thì thường được viết dưới dạng sub-id. sub-id không nhất thiết phải liên tục hay bắt đầu từ 0.

OID của các Object phổ biến có thể được chuẩn hóa, OID của các Object do bạn tạo ra tì bạn phải tự mô tả chúng. Để lấy một thông tin có OID đã chuẩn hóa thì Application phải gửi một bản tin SNMP có chứa OID của Object đó cho SNMP Agent, SNMP Agent khi nhận được thì nó phải trả lời bằng thông tin ứng với OID đó.

VD: Muốn lấy tên của một PC chạy WINDOW hay Linux hoặc tên của một Route thì SNMP Application chỉ cần gửi bản tin có chứa OID là 1.3.6.1.2.1.1.5.0 . Khi SNMP Agent trên HĐH hay Route nhận được bản tin có chưa OID 1.3.6.1.2.1.1.5.0, Agent lập tức hiểu rằng đây là bản tin hỏi sysName.0 và Agent sẽ trả lời bằng tên của hệ thống. Nếu SNMP Agent nhận được một OID mà nó không hiểu(không hỗ trợ) thì nó sẽ không trả lời.


![Imgur](https://i.imgur.com/W0IS9Ul.png)

Một ưu điểm của SNMP là nó được thiết kế để chạy độc lập với các thiết bị khác nhau. Chính là nhờ việc chuẩn hóa OID mà ta có thể dùng một SNMP Application để lấy thông tin các loại Device của hãng khác nhau.


### Object access 
Mỗi Object có quyền truy cập là READ_ONLY HOẶC READ_WRITE. Mọi Object đều có thể đọc được nhưng chỉ những Object có quyền READ_WRITE mới có thể thay đổi được giá trị

### Management Information Base 
MIB (cơ sở thông tin quản lý) là một cấu trúc dữ liệu gồm các đối tượng được quản lý(managed Object), được dùng để quản lý các thiết bị chạy trên TCP/IP. MIB là kiến trúc chung mà các giao thức quản lý trên TCP/IP nên tuân theo, trong đó có SNMP. MIB được thể hiện thành 1 File (MIB file), và có thể biểu diễn bằng một case(MIB tree). MIB có thể được chuẩn hóa và tự tạo.

## Các phương thức của SNMP

Giao thức SNMPv1 có 5 phương thức hoạt động, tương ứng 5 loại bản tin: **GetRequest**, **GetNextRequest**, **SetRequest**, **GetReponse**, **Trap**.

Mỗi bản tin đều chứa OID để biết Object mang trong đó là gì. 
* OID trong GetRequest cho biết nó muốn lấy thông tin của Object nào.
* OID trong GetReponse cho biết nó mang giá trị của Object nào.
* OID trong SetRequest chỉ ra nó muốn thiết lập giá trị cho Object nào.
* OID trong Trap chỉ ra nó thông báo sự kiện xảy ra đối với Object nào.


### GetRequest
Bản tin GetRequest được Manager gửi đến Agent để lấy một thông báo nào đó. Trong GetRequest có chứa OID của Object muốn lấy.

VD: Muốn lấy thông tin tên của Device 1 thì Manager gửi bản tin GetRequest OID=1.3.6.1.2.1.1.5 đến Device 1, Tiến trình SNMP Agent trên Device 1 sẽ nhận được một bản tin và tạo bản tin trả lời.

Trong một bản tin GetRequest có thể chưa nhiều OID, nghĩa là dùng một GetRequest có thể lấy về nhiều thông tin cùng lúc.

### GetNextRequest 
Bản tin GetNextRequest cũng dùng để lấy thông tin và cũng có chứa OID, tuy nhiên nó dùng để lấy thông tin của Object nằm kế tiếp Object được chỉ ra trong bản tin

Tại sao phải có phương thức GetNextRequest? Một MIB bao gồm nhiều OID được sắp xếp thứ tự nhưng không liên tục, nếu biết một OID thì không xác định được OID kế tiếp. Do đó ta cần GetNextRequest liên tục thì ta sẽ lấy được toàn bộ thông tin của Agent.

### SetRequest 
Bản tin SetRequest được Manager gửi cho Agent để thiết lập một giá trị nào đó. Ví dụ:

* Có thể đặt lại tên của một máy tính hay Route bằng phần mềm SNMP Manager, bằng cách gửi bản tin SetRequest có OID là 1.3.6.1.2.1.1.5.0(sysName.0) và có giá trị là tên mới cần đặt.

* Có thể Shutdown một port trên Switch bằng phần mềm SNMP Manager

Chỉ những Object có quyền READ_WRITE mới có thể thay đổi được giá trị.

### GetReponse

Mỗi khi SNMP Agent nhận được các bản tin GetRequest, GetNextRequest hay SetRequest thì nó sẽ gửi lại một bản tin GetReponse để trả lời. Trong bản tin GetReponse có chứa OID của Object được request và giá trị của Object đó.

### Trap
Bản tin Trap được Agent tự động gửi cho Manager mỗi khi có sự kiện xảy ra bên trong Agent, các sự kiện này không phải các hoạt động thường xuyên của Agent mà là các sự kiện mang tính biến cố. Ví dụ: Khi có một port down, khi có một người dùng login không thành công, hoặc khi thiết bị khởi động lại, Agent sẽ gửi trap cho Manager.

Tuy nhiên không phải mọi biến cố đều được Agent gửi trap, cũng không phải mọi Agent đều gửi trap khi xảy ra biến cố. Việc Agent đều gửi trap khi xảy ra cùng một biến cố. Việc Agent gửi hay không gửi trap cho biến cố nào là do hãng sản xuất Device/Agent quy định.

Phương thức Trap là độc lập với các phương thức request/response. SNMP request/response dùng để quản lý còn SNMP trap là dùng để cảnh báo. Nguồn gửi trap là Trap Sender và nơi nhận trap là Trap Receiver. Một Trap Sender có thể được cấu hình để gửi trap đến đến nhiều Trap Receiver cùng lúc.

Có 2 loại Trap: Trap phổ biến (Generic Trap) và Trap đặc thù(Specific Trap).
* Generic Trap được quy định trong các chuẩn SNMP, còn Specific Trap do người dùng tự định nghĩa(người dùng ở đây là hãng sản xuất SNMP Device).

* Loại Trap là một số nguyên chứa trong bản tin Trap, dựa vào đó mà phía nhận Trap biết bản tin Trap có ý nghĩa gì.

Theo SNMPv1, Generic Trap có 7 loại như sau: coldStart(0), warmStart(1),linkDown(2), LinkUp(3), authenticationFalure(4), egpNeighborlosss(5), enterpriseSpecific(6). Giá trị trong ngoặc là mã số của các loại trap. Ý nghĩa của của các bản tin Generic Trap như sau:

* coldStart: Thông báo rằng thiết bị gửi bản tin này đang khởi động lại (reinitialize) và cấu hình của nó có thể bị thay đổi sau khi khởi động lại.
* warmStart: Thông báo rằng thiết bị gửi bản tin này đang khởi động lại và giữ nguyên cấu hình cũ.
* linkDown: thông báo rằng thiết bị gửi bản tin này phát hiện được một trong những kết nối truyền thông(communication link) của nó gặp lỗi.
* LinkUp: Thông báo rằng thiết bị gửi bản tin này phát hiện được một trong những kết nối truyền thông của nó đã khôi phục trở lại. Trong bản tin Trap có tham số chỉ ra ifIndex của kết nối được khôi phục.
* authenticationFalure: Thông báo rằng thiết bị gửi bản tin này đã nhận được một bản tin không được chứng thực thành công(Bản tin bị chứng thực không thành công có thể thuộc nhiều giao thức khác nhau như telnet, ssh, snmp, ftp,...). Thông thường Trap loại này xảy ra là do user đăng nhập không thành công vào thiết bị.
* egpNeighborlosss: Thông báo rằng một trong số những "EGPnieghbor" của hai thiết bị gửi Trap đã bị coi là down và quan hệ đối tác(peer relationship) giữa 2 bên không còn được duy trì.
* enterpriseSpecific: Thông báo rằng bản tin Trap này không thuộc các kiểu Generic như trên mà nó là một loại bản tin do người dùng tự định nghĩa.


# Mini guideline — bài làm cá nhân

> Điền nội dung này trước khi bắt đầu gán nhãn. Giữ lại các quyết định sau khi self-QC.

## Định nghĩa lớp

| Lớp | Định nghĩa của bạn | Ví dụ/điểm phân biệt |
| --- | --- | --- |
| `car` | Ô tô con chở người, kích thước nhỏ và thấp: sedan, hatchback, SUV, crossover, taxi, bán tải cỡ nhỏ. | Quan sát được ba phần riêng: capo phía trước, khoang kính/mui, cốp hoặc đuôi ngắn. Chiều cao mui thấp, chiều dài chỉ khoảng 1–1.3 lần các xe con quanh nó. SUV tuy cao hơn sedan nhưng capo vẫn rõ nên vẫn là `car`. Xe taxi hay xe đang đỗ sát lề cũng là `car`. |
| `truck` | Xe vận tải hàng, cabin và thùng hàng là hai phần tách nhau: tải thùng kín, tải thùng hở, xe ben, xe bồn, đầu kéo (kể cả khi có sơ-mi rơ-moóc). | Giữa cabin và thùng có đường ngăn hoặc khe hở rõ; thùng hàng dạng hộp vuông, cao, thân không có hàng cửa sổ cho khách. Khác với `bus` ở chỗ bus là một thân liền từ đầu tới đuôi với nhiều cửa sổ chạy dọc hông. Bán tải nhỏ thùng hở xếp vào `car`, không xếp vào `truck`. |
| `bus` | Xe chở nhiều hành khách cỡ lớn hoặc vừa: buýt nội đô, xe khách đường dài, minibus (tầm 16 chỗ trở lên). | Thân dài, nguyên khối dạng hộp, hông xe có hàng cửa sổ liên tục, nóc phẳng và dài; thường dài từ 2 lần xe con trở lên. Khác với `van` ở chiều dài vượt trội và có cửa lên xuống ở đầu hoặc giữa thân; van thì ngắn, kích thước gần xe con. |
| `van` | Xe dạng hộp cỡ nhỏ, dùng chở hàng hoặc chở khách (khoảng 7–16 chỗ), gồm minivan. | Phần đầu rất ngắn (capo ngắn hoặc gần như liền với kính), thân vuông vức, nóc cao rõ rệt so với xe con kế bên; chiều dài chỉ hơn xe con một chút. Khác với `car`: SUV có capo dài và nóc thấp hơn, còn van trông như một khối hộp. Khác với `truck`: van không có ranh giới giữa cabin và thùng. |

## Quy tắc chung

- Box bám sát vật thể nghĩa là: các cạnh của box tiếp xúc với điểm ngoài cùng của phần xe nhìn thấy (gồm cả gương chiếu hậu nếu rõ), không để dư khoảng trống, không ôm cả bóng xe trên mặt đường, quầng sáng đèn pha ban đêm hay xe bên cạnh. Vẽ xong thì phóng to kiểm tra từng cạnh, sai lệch không quá 2–3 px.
- Vật thể bị che khuất: nếu phần còn thấy đủ để biết lớp (ví dụ thấy mui và kính, hoặc đầu/đuôi xe) thì vẽ box bao quanh phần nhìn thấy, không suy đoán phần bị khuất. Hai xe chồng lên nhau thì vẽ hai box độc lập, mỗi box chỉ gồm phần của xe tương ứng. Nếu xe bị cột điện hay biển báo che một dải hẹp ở giữa thì vẫn vẽ một box liền cho cả xe.
- Vật thể bị cắt bởi rìa ảnh: vẫn gán nhãn khi phần còn lại đủ để nhận ra lớp trong schema; cạnh box nằm đúng mép ảnh (tọa độ 0 hoặc 1), không kéo box ra ngoài khung và không ước lượng kích thước phần bị cắt.
- Vật thể rất nhỏ/mơ hồ: xe ở xa vẫn gán nếu nhận ra là xe (nhãn eval có box chỉ khoảng 13×23 px). Chỉ bỏ qua khi xe quá nhỏ hoặc quá mờ đến mức không chắc là xe. Nếu chắc là xe nhưng phân vân giữa hai lớp (van/bus, van/car) thì ghi vào bảng ca mơ hồ và hỏi giảng viên, không tự phỏng đoán.
- Ngoài phạm vi: không gán xe máy, xe đạp, người đi bộ, xe ba gác, xe in trên biển quảng cáo, xe phản chiếu trong kính.

## Ghi lại quyết định cho ít nhất ba ca mơ hồ

| Ảnh | Tình huống | Quyết định cuối | Lý do theo schema |
| --- | --- | --- | --- |
| `drive_001` (xe trắng nhỏ đỗ bên trái vỉa hè) | Thân hình hộp, dễ nhầm với `van` | `car` | Kích thước nhỏ hơn sedan bên cạnh, đây là xe con cỡ mini; `van` phải có thân dài và mui cao hơn xe con |
| `drive_019` (xe trắng hình hộp đỗ cạnh sedan xám) | Xe cỡ nhỏ, dễ nhầm với `car` như ca `drive_001` | `van` | Dài gần bằng sedan bên cạnh nhưng mui cao, phẳng kéo dài tới đuôi, capo rất ngắn, cửa hông lớn → minivan theo schema; khác `drive_001` vì xe mini ở đó ngắn hơn sedan |
| `drive_028` (xe trắng thân dài đỗ sau SUV trắng, mép trái ảnh) | Bị SUV phía trước và ô che màu cam che phần đầu xe; không rõ là xe tải nhỏ hay van | `van` | Phần nhìn thấy là một khối thân liền, mui phẳng kéo dài, không thấy khe tách cabin – thùng hàng nên không đủ căn cứ gán `truck`; kích thước dưới 2 lần xe con nên không phải `bus` → theo schema là van chở hàng |

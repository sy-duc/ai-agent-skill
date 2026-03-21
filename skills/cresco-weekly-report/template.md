<!--
  HƯỚNG DẪN CHO AGENT:
  - Các dòng trong khối <!-- --> là mô tả/ghi chú, KHÔNG xuất ra báo cáo
  - Mỗi mục có thể kèm ghi chú để agent hiểu ngữ cảnh và chỉnh sửa phù hợp
  - Khi xuất báo cáo, chỉ giữ lại nội dung, bỏ toàn bộ comment
-->

<!--
  Mục này liệt kê các task đã thực hiện trong tuần trước.
  Mỗi task đánh số ①②③...
  Nội dung ngắn gọn, rõ ràng, dùng thể khẳng định.

  SUBTASK: Nếu task có nhiều subtask, đánh số 1,2,3... cho mỗi subtask.

  TRẠNG THÁI HOÀN THÀNH (áp dụng cho mỗi task/subtask):
  - Đã xong → ghi "完了" ở cuối dòng
  - Có ngày dự kiến hoàn thành → ghi "（dự kiến hoàn thành vào dd/mm）" ở cuối dòng
  - Chưa biết / bỏ qua → không ghi gì thêm
-->
Ⅰ．対応済みタスク

① {task_1} （完了）
・{mô tả bổ sung task nếu có}
② {task_2}（dự kiến hoàn thành vào dd/mm）
③ {task_3}
・{mô tả bổ sung task}
  1. {subtask_1}（完了）
  ・{mô tả bổ sung subtask nếu có}
  2. {subtask_2}（dự kiến hoàn thành vào dd/mm）

<!--
  Mục này liệt kê kế hoạch tuần tới.
  Mỗi task đánh số ①②③...

  SUBTASK: Nếu task có nhiều subtask, đánh số 1,2,3... cho mỗi subtask.

  THỜI GIAN DỰ KIẾN (áp dụng cho mỗi task/subtask):
  - Có ngày dự kiến → ghi "（dự kiến hoàn thành vào dd/mm）" ở cuối dòng
  - Chưa biết / bỏ qua → không ghi gì thêm
-->
Ⅱ．来週の予定

① {plan_1}（dự kiến hoàn thành vào dd/mm）
・{mô tả bổ sung task nếu có}
② {plan_2}
・{mô tả bổ sung task nếu có}
  1. {subtask_1}（dự kiến hoàn thành vào dd/mm）
  ・{mô tả bổ sung subtask nếu có}
  2. {subtask_2}

<!--
  Mục này ghi các vấn đề khác: blocker, rủi ro, đề xuất, thông báo...
  Nếu không có gì thì ghi: ・特に問題ありません。
-->
Ⅲ．その他

・{issue_1}

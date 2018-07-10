## Questions

Bạn hiểu gì về kiểu dữ liệu Atom, bạn thường sử dụng atom trong những trường hợp nào và tại sao?

## Curated answers

Participants: `@u`, `@vietthang`, `@toanha`, `@mquy`, `IATAI`, `@HQC`.

* kiểu dữ liệu mà  giá trị là tên của nó. Giới hạn là 1tr.
* không được garbage collected. => đừng generate dynamically, xài atom chỉ xài cho literal.
* sử dụng atom là thao tác so sánh nhanh hơn: O(1) (atom là reference tới atom table).
* giống symbols của Ruby 🤷‍♂️.

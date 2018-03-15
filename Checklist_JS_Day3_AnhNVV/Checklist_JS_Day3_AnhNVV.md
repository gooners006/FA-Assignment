1 this & Object prototype
1.1 this
this là một trong những cơ chế gây rối nhất trong JS, theo em this là gì ?
  Khi một hàm được gọi, sẽ có một bản ghi được tạo ra. Bản ghi này có chứa những thông tin về hàm nói được gọi ra từ đâu(call-stack), 
  gọi như thế nào, tham số nào được truyền vào,... trong đó có "this" là tham chiếu tới đối tượng. Nó không liên quan tới việc hàm được 
  gọi ở đâu, mà liên quan tới cách gọi nó như thế nào
Cách hiểu 1: this trỏ tới function f, đúng hay sai?
  Sai.

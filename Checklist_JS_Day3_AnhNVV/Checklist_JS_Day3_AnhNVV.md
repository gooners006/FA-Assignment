1 this & Object prototype
1.1 this
this là một trong những cơ chế gây rối nhất trong JS, theo em this là gì ?
  this là một con trỏ chỉ vào hàm nó nằm trong
Cách hiểu 1: this trỏ tới function f, đúng hay sai?
  Sai. this này đang trỏ tới một biến count global, không phải trong f()
Cách hiểu 2: this trỏ tới scope của function, đúng hay sai?
  Sai. this trong trường hợp này không trỏ đến được scope của hàm f()

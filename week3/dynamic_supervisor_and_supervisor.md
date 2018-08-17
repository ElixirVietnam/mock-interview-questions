# Question

> DynamicSupervisor với Supervisor giống nhau và khác nhau về cách sử dụng như thế nào?

# Discussion

-vietthang

> Supervisor thì sẽ start children theo order. Còn Dynamic Supervisor sẽ start with no children. Children đc start với `start_child`
> Về cách sử dụng thì cả 2 đều supervise child-processes. Trong khi Superviser là static with order còn Dynamic Superviser để supervise child-process dynamically. Như cái tên của nó.

-hqc

> Nếu e biết trước child-process của e là gì thì dùng Supervisor. còn nếu ko biết hoặc runtime mới biết thì DynamicSupervisor.

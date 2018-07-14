# Question

Process và Port giống và khác thế nào?

# Discussion

- from @vietthang

> Vừa đọc lại basic types của elixir. Thì pid là reference đến local hoặc remote process. Còn port reference đến external resource. Theo em hiểu thì là port sẽ cung cấp 1 byted-oriented interface để giao tiếp với các external program bằng cách gửi dữ liệu dạng byte/binaries. Processes và ports đều sinh ra để giao tiếp với các process khác. Nhưng với proccess thì là internally (Erlang VM) còn port là externally (OS process).

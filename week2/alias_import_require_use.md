# Question
Phân biệt các keywords: `alias`, `import`, `require` và `use`

# Discussion

- from @toanha

`import`: Hiểu đơn giản nó sẽ bê toàn bộ functions và macros của module B vô module A để sử dung. Mình có thể gọi tắt 1 function trong B mà không cần bắt đầu bằng tên module. Có thể sử dụng thêm 2 từ khóa `only` nếu chỉ muốn lấy 1 số hàm, marco hoặc từ khóa `except` nếu muốn loại từ hàm hay macro nào đó

```elixir
defmodule A do
  def say_world() do
    IO.puts("world")
  end

  defmacro if_unless(expr, opts) do
    quote do
      if !unquote(expr), unquote(opts)
    end
  end
end

defmodule B do
  import A

  def say_hello do
    IO.puts("Hello ")

    if_unless false do
      say_world()
    end
  end
end

defmodule Main do
  def run() do
    B.say_hello()
  end
end

Main.run()
```

`required`: Khi muốn sử dụng marco của 1 module nào đó, bắt buộc phải require module đó trước khi gọi marco

```elixir
defmodule A do
  def say_world() do
    IO.puts("world")
  end

  defmacro if_unless(expr, opts) do
    quote do
      if !unquote(expr), unquote(opts)
    end
  end
end

defmodule B do
  require A

  def say_hello do
    IO.puts("Hello ")

    A.if_unless false do
      A.say_world()
    end
  end
end

defmodule Main do
  def run() do
    B.say_hello()
  end
end

Main.run()
```

`alias`: Dùng để setup 1 alias name cho 1 module.

```elixir
alias ModuleA, as: AAA

> AAA.abc <=> ModuleA.abc <=> Elixir.ModuleA.abc
```

`use`: thường xài kiểu như abstract, Khi module B use module A, nó sẽ invoke marco `__using__` trong module A

```elixir
defmodule A do
  defmacro __using__(opts) do
    quote do
      IO.puts("Hello ")
    end
  end
end

defmodule B do
  use A

  def say_hello do
    IO.puts("World")
  end
end

defmodule Main do
  def run() do
    B.say_hello()
  end
end

Main.run()
```

Chi tiết: [Xem tại kipalog](https://kipalog.com/posts/Phan-biet-cac-tu-khoa-use--alias--require-va-import)

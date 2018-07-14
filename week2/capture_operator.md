# Question

> Capture operator trong Elixir là gì? Nó được sử dụng khi nào? Cho ví dụ.

# Discussion

- from @LATAL
> Chỉ biết dùng không biết giải thích.
```elixir
Enum.filter([%{a: 1}, %{a: 2}, %{a: 3}], &(Map.get(&1,  :a) == 1))
# Shorthand
Enum.filter([%{a: 1}, %{a: 2}, %{a: 3}], &(&1.a == 1))
```

- from @vietthang

> Capture operator hay `&` theo em nghĩ là shorthand của khai báo anonymous function và capture named functions

```elixir
Enum.filter(1..100, &get_odd/1)`
Enum.map(1..10, &(& * 2))
```

- from @HQC

có một trò vui mà capture operator làm dc mà anonymous function ko làm dc là anonymous function ko thể escape dc ở compile time
vd như

```elixir
defmodule A do
    @fun fn a -> a + 1 end

    def a(a), do: @fun.(a)
end

defmodule B do
    @fun &B.fun/1

    def b(b), do: @fun.(b)

    def fun(b), do: b + 1
end
```

> A ko compile dc vì anonymous func ko escape dc để inject vào AST.

# Summary
- from @gopher (#algorithms)
> Về mặt lý thuyết thì bản chất của pattern matching là check xem 2 expression có equal hay ko. nếu equal thì bind variable cả 2 vế và execute 1 đoạn code nếu có. Ví dụ dễ hình dung là function ở Erlang chính là define qua pattern matching. Vì erlang là họ prolog. Haskell hạn chế hơn nhiều chỉ define dc nếu cái expression là constructor khi khai báo Algebraic data type. trong scala thì thoáng hơn 1 tí, tức là có thể custom qua hàm unapply cái đó gọi là extractor object. Ví dụ erlang {x, 1} = {2, 1} Sau khi match xong thì x = 2. bên clojure cũng có 1 dạng khác của pattern matching là destructing. Trong prolog thi pattern matching chinh la unification

- from @vietthang
> Việc expect 1 giá trị với 1 pattern là giống nhau về cấu trúc/giá trị.
> Ví dụ:
```
-------------
f(x) = 10 / x, if x != 0

def f(0), do: raise "Cannot devide by zero"
def f(x), do: 10 / x

-------------

case http_get(url) do
    {:ok, %Response{} = res} -> put_status(conn, 200)
    {:error, %Reason{} = rea} -> put_status(conn, 422)
end
```

- from @mquy
> pattern matching là dựa trên Algebraic data types (sum types).

- from @HQC
> mình nghĩ pattern matching erlang khác với pattern matching trong lý thuyết. cái pattern matching erlang so trùng là value chứ ko phải type. Value có thể là một struct. VD
```elixir
case user do
  %Facebook{} -> user.name
  %Peteboc{} -> user.username
end
```

- from @mqy
> nghĩ một cách tổng quan, value cũng là "type" đó.

- from @u
> pattern matching là binding + conditional

- from @mquy
> Tại sao lại là binding + conditional

- from @u
> Thì thay vì viết pattern match thì viết if rồi binding tay. Ví dụ {x,y} = a =>

```
if is_tuple(a) && len(a) == 2 {
  x =a.0
  y = a.1
}
```

- from @toanha
> theo mình hiểu đơn giản thế này. pattern matching gồm 2 vế, vế đầu là pattern, 1 pattern co the la 1 bien, 1 ham ... Matching tuc la extract gia tri cua cai pattern do ra. Ví dụ

```
Bien
x = 3 tuc la dang extract gia tri 3 vao x. 

Map
m = %{a: 1}
%{a: x} = m
x -> 1 minh dang extract gia tri voi key la :a tu map m

Ham
def(params = %User{}) do
end
Cho nay minh dang extract gia tri cua params 1 struct User

def(params = %{"id" => id}) do
end
Cho nay minh extract gia tri "id" tu 1 map. Va chi match khi tham so params la 1 map co chua key "id"

List
l = [1,2,3]
[h | t] = l
Minh extract gia tri dau tien cua list l, voi vi trong elixir 1 list co the bieu dien bang [1, 2, 3] = [1 | [2, 3]] = [1 | [2 | 3]]

Tuong tu Binary pattern thi coi them trong bai post cua a HQC
```

# Raw

vietthang [2:10 PM]
:smile: Bình thường dùng mà bảo nói định nghĩa cũng kb nói thế nào thật :neutral_face:

thien [2:11 PM]
thiệt, giải thích mấy khái niệm thì chịu thua :joy:

mquy [2:11 PM]
pattern matching là dựa trên Algebraic data types

nhducfp [2:12 PM]
chắc phải giải thích pattern trước rồi mới giải thích matching nhỉ

vietthang [2:12 PM]
Pattern match là việc expect 1 giá trị với 1 pattern là giống nhau về cấu trúc. vế còn lại em định nói giống anh @mquy là dựa trên algebra

mquy [2:14 PM]
khổ cái là không bao giờ nhớ algebraic viết sao :roflrofl:

viet [2:14 PM]
pattern matching là kỹ thuật match các pattern :smile:

nhducfp [2:15 PM]
algebraic data: dữ liệu đại số :crying:

harris [2:15 PM]
thua

triet [2:15 PM]
>If you can't explain it simply, you don't understand it well enough
>_- Albert Einstein_
(edited)

nhducfp [2:16 PM]
algebraic effects: hiệu ứng đại số =))

vietthang [2:17 PM]
Vậy thì a @viet best. So true
> pattern matching là kỹ thuật match các pattern
triet
>If you can't explain it simply, you don't understand it well enough
>_- Albert Einstein_
Posted in #elixirYesterday at 2:15 PM

mquy [2:18 PM]
đúng mà, pattern matching hoạt động là dựa trên nguyên lý của algebraic data types

nhducfp [2:19 PM]
bên reasonml/ocaml có vụ match `exception`, elixir với mấy language khác thì sao nhỉ
```
switch (List.find((i) => i === theItem, myItems)) {
| item => print_endline(item)
| exception Not_found => print_endline("No such item found!")
};
```
(edited)

triet [2:23 PM]
Nếu trong khuôn khổ interview thì trả lời thế này không ổn
viet
pattern matching là kỹ thuật match các pattern :smile:
Posted in #elixirYesterday at 2:14 PM

lATAl [2:24 PM]
thực sự cũng không biết trả lời thế nào :disappointed:

harris [2:24 PM]
rớt rồi :thinkcry:

mquy [2:24 PM]
nghĩ là `ocaml` nó xử lý vụ throw như kiểu return
nên dùng pattern matching ok

viet [2:27 PM]
là @triet thì sẽ trả lời như thế nào ?
triet
Nếu trong khuôn khổ interview thì trả lời thế này không ổn
https://vietnamrb.slack.com/archives/C0JD6N86S/p1530861268000287
Posted in #elixirYesterday at 2:23 PM

triet [2:27 PM]
Em không biết :troll:
mà không biết thật :okay:
cc @HQC

viet [2:28 PM]
hóng trùm cuối :okay:

HQC [2:28 PM]
_mình cũng ko biết_ :troll: (edited)
cơ mà trả lời bằng match operator là dc mà

triet [2:29 PM]
uploaded this image: desk_flip.jpg 


triet [2:29 PM]
^Add dùm e cái emoji với

HQC [2:29 PM]
đâu phải lý thuyết đại số hay functional programming con đường sáng gì đâu

h [2:29 PM]
triet tu add dc ma?

triet [2:29 PM]
bị disable rồi anh
https://jmp.sh/fdyh5yB
Jumpshare
Screen Shot 2018-07-06 at 2.29.23 PM.png
Shared with Jumpshare
https://storage.jumpshare.com/preview/xX4ZToX3WNJp5oyQHOZSX392XuSD2SriuXNlpgJmsM98hFOAV1d_Qeupg4MhmH7ILwG4mSxKV-07DWO8aQoe-w
không có chổ customize

HQC [2:37 PM]
:table-flip:

triet [2:38 PM]
ok, cool, continue nào anh

vietthang [2:38 PM]
Thế câu này trả lời thế nào thì nhà tuyển dụng có thể gật đầu đc hả a (edited)
keyword là gì ạ
:thinkhard:

triet [2:39 PM]
Tưởng tượng interviewer/newbie không biết gì về elixir, pattern matching và mục tiêu là giải thích sao cho người đó hiểu

HQC [2:40 PM]
giờ tưởng tượng @triet ko hiểu, giải thích sao cho triet hieu là dc rồi. triet CTO, gật đầu là chuẩn rồi (edited)

triet [2:40 PM]
:okay:
không phải tưởng tượng đâu anh

viet [2:41 PM]
ko hiểu thì sao lại đi hỏi :disappointed:
ít nhất cũng phải có base nào đó

triet [2:42 PM]
~không hiểu~ không biết
make sense?

vietthang [2:42 PM]
a @triet biết pattern matching rồi

triet [2:42 PM]
^chưa

nhducfp [2:42 PM]
vậy @triet biết pattern là gì chưa?

vietthang [2:42 PM]
Vậy thì em xin thử giải thích

triet [2:42 PM]
mời em thử :kappa:

vietthang [2:43 PM]
ví dụ từ toán học. f(x) = a / x, if x != 0
-> code
```elixir
def f(0), do: raise "Cannot devide by zero"
def f(x), do: 10 / x
```
Ở đây thì argument match với pattern nào thì được xử lý theo cách khác nhau

mquy [2:50 PM]
pattern matching là nó dựa trên sum types, vì có sum types nên mới chia ra loại matching được
mà sum types là gì, là sum của các types :kappa:

harris [2:51 PM]
sum types với union types khác nhau chỗ nào anh?

harris [2:51 PM]
:thinkcry:

triet [2:52 PM]
à ra là cái đó à, vậy thì mình biết rồi, cơ mà giải thích kiểu này newbie chắn chắn không hiểu :kappa:

harris [2:53 PM]
đang đọc -> https://waleedkhan.name/blog/union-vs-sum-types/

mquy [2:54 PM]
theo anh biết thì nó như nhau
ai biết nó khác nhau chỗ nào thì chia sẻ với :omg:

HQC [2:56 PM]
mình nghĩ pattern matching erlang khác với pattern matching trong lý thuyết :think:
cái pattern matching erlang so trùng là value chứ ko phải type (edited)

mquy [2:56 PM]
nghĩ một cách tổng quan, value cũng là "type" đó (edited)
@harris tl;dr nào

nhducfp [2:58 PM]
ủa vậy elixir có variant không @HQC

HQC [2:58 PM]
variant là gì :think:

mquy [3:00 PM]
@harris tóm lại union với sum khác nhau ở chỗ label :think:

nhducfp [3:00 PM]
```
type myResponseVariant =
  | Yes
  | No
  | PrettyMuch;
```
kiểu như vầy này, gọi là union type phải không nhỉ?
nếu dựa vào value thôi làm sao phân biệt được `Peteboc(name, age)` and `Facebook(name, age)`


HQC [22 hours ago]
value có thể có là một `struct` (có thể tạm hiểu như type) mà



HQC [22 hours ago]
vd `%Facebook{name: "a", age: 18}`


HQC [22 hours ago]
triển khai thành code nó sẽ là

```elixir
case user do
  %Facebook{} -> user.name
  %Peteboc{} -> user.username
end
```

nhducfp [22 hours ago]
ah, vậy em hiểu rồi, cám ơn anh

mquy [3:00 PM]
đngs rồi

harris [3:01 PM]
không có label
-> union ?
à không

HQC [3:02 PM]
vậy mà các bác cũng lái qua type theory dc, tại hạ xin bái phục :pray:

nhducfp [3:02 PM]
> cái pattern matching erlang so trùng là value chứ ko phải type
tại vì em thấy cái này hơi lạ (lạ so với em) (edited)

mquy [3:02 PM]
:haskell:  ftw :yaomin:

HQC [3:02 PM]
nó so trùng value thật mà

vietthang [3:03 PM]
=)))
đi hơi xa rùi

HQC [3:04 PM]
còn cái `myResponseVariant` thì :yaomin:

```elixir
defguard is_my_variant(var), do: is_yes(var) or is_no(var) or is_pretty_much(var)
```

nhducfp [3:05 PM]
vì em muốn làm thế này
```
let greeting =
  switch (myAccount) {
  | None => "Hi!"
  | Facebook(name, age) => "Hi " ++ name ++ ", you're " ++ string_of_int(age) ++ "-year-old."
  | Peteboc(name, age) => "Hi " ++ name ++ ", you're " ++ string_of_int(age) ++ "-year-old."
  | Facebook(_, _) => "Hello facebook user"
  | Peteboc(_, _) => "Hello Peteboc user"
  | Instagram(name) => "Hello " ++ name ++ "!"
  };
```

mquy [3:05 PM]
tại vì có thể coi value là type một giá trị
nên về lý thuyết pattern matching là dựa trên vậy :kappa:

vietthang [3:07 PM]
Thế tóm váy lại dựa trên 1 đống lý thuyết vậy thì pattern matching là gì ạ :thinkhard:

nhducfp [3:09 PM]
là một công cụ giúp ta detect pattern của 1 value

vietthang [3:10 PM]
Nếu chỉ giải thích theo nghĩa hẹp thì nếu ai hỏi em pattern matching là gì thì e chỉ trả lời là
> việc expect 1 giá trị với 1 pattern là giống nhau về cấu trúc
vd
```
case http_get(url) do
    {:ok, %Response{} = res} -> put_status(conn, 200)
    {:error, %Reason{} = rea} -> put_status(conn, 422)
end
```

HQC [3:13 PM]
cơ mà theo mình biết thì erlang dc thiết kế ko theo một cái lý thuyết nào cả
có cái conf nào mà ông Robert nói là họ design ra OTP, xong rồi đọc lại paper về actor model, mới biết cái mình vừa build có vẻ giống với actor model

mquy [3:15 PM]
> Great minds think alike

HQC [3:15 PM]
nên mình nghĩ lúc design pattern matching, họ cũng ko đọc type theory đâu :troll:

mquy [3:15 PM]
nên chung quy về một mối mà :yaomin:

HQC [3:15 PM]
họ có xạo ko thì mình ko biết :troll:
http://erlang.org/pipermail/erlang-questions/2014-June/079796.html
cơ mà túm lại hôm nay ai note lại discussion vậy :smile:

vietthang [3:18 PM]
Hôm qua e chưa note lại. Để em note lại cho :3

HQC [3:20 PM]
nghe đồn @mquy có write access vào Elixir-VN repo trên github

mquy [3:21 PM]
chắc phải nhờ anh @kiennt add @vietthang vào nhỉ :think:

HQC [3:21 PM]
mới tạo repo

harris [3:22 PM]
@mquy về js làm y format luôn anh
:omg:

HQC [3:22 PM]
github username của vietthang là gì nhỉ?
làm y format cho ruby luôn
chứ ko thành dead lang mất :neutral_face:

vietthang [3:23 PM]
`vthang95` anh ơi

kensupermen [3:24 PM]
@HQC cho e xin link repo vs a oi :smile:

HQC [3:24 PM]
sorry quên https://github.com/ElixirVietnam/mock-interview-questions
ElixirVietnam/mock-interview-questions
Last updated
4 minutes ago
ElixirVietnam/mock-interview-questionsYesterday at 3:21 PMAdded by GitHub

mquy [3:27 PM]
triệu hồi @kcjpop để làm tương tự cho js :think:

u [3:28 PM]
Pattern matching = switch case xịn hơn thôi chứ có gì đâu nhỉ

u [3:29 PM]
:think:

kcjpop [3:29 PM]
> This repository is empty. :areukiddingme:

u [3:30 PM]
Đâu cần phải là sum type mới match được @mquy

mquy [3:30 PM]
thì nói về định nghĩa mà :thinkhard:

u [3:33 PM]
Uhm chắc cái đó lý thuyết bên haskell nhỉ

u [3:34 PM]
Chứ em nghĩ pattern matching là binding + conditional

mquy [3:35 PM]
đâu về lý thuyết types chung luôn đó chớ :think:
mà sao lại là binding + conditional

vietthang [3:36 PM]
có cả variable binding nữa. Điều kiện là pattern match

u [3:38 PM]
Thì thay vì viết pattern match
Thì viết if
Rồi binding tay
{x,y} = a
=>
```
if is_tuple(a) && len(a) == 2 {
  x =a.0
  y = a.1
}
```
Kiểu vậy đó @mquy

mquy [3:42 PM]
nhưng với if là em đanh so sánh giá trị
còn pattern là so sánh pattern
về bản chất nó khác nhau
nhưng mà có vể dùng cách này viết cách kia dc

HQC [3:44 PM]
Cơ mà đó là cách pattern matching trong elixir hoạt động mà
Pattern matching trong erlang là so giá trị mà

mquy [3:46 PM]
quên gần hết elixir :yaomin:

HQC [3:46 PM]
Mình là ng interview mình sẽ đánh rớt @mquy
Cái tội pv elixir mà trả lời haskell

mquy [3:47 PM]
:omg:

toanha [3:58 PM]
theo mình hiểu đơn giản thế này. pattern matching gồm 2 vế, vế đầu là pattern, 1 pattern co the la 1 bien, 1 ham ... Matching tuc la extract gia tri cua cai pattern do ra. Ví dụ
```
Bien
x = 3 tuc la dang extract gia tri 3 vao x. 

Map
m = %{a: 1}
%{a: x} = m
x -> 1 minh dang extract gia tri voi key la :a tu map m

Ham
def(params = %User{}) do
end
Cho nay minh dang extract gia tri cua params 1 struct User

def(params = %{"id" => id}) do
end
Cho nay minh extract gia tri "id" tu 1 map. Va chi match khi tham so params la 1 map co chua key "id"

List
l = [1,2,3]
[h | t] = l
Minh extract gia tri dau tien cua list l, voi vi trong elixir 1 list co the bieu dien bang [1, 2, 3] = [1 | [2, 3]] = [1 | [2 | 3]]

Tuong tu Binary pattern thi coi them trong bai post cua a HQC
```
(edited)

toanha [4:02 PM]
còn chổ lúc này @vietthang nói là https://vietnamrb.slack.com/archives/C0JD6N86S/p1530863003000103. Thì bởi do thằng elixir nó coi mấy cái function mình define, cái nào match trước thì nó thực thi trước thoy
vietthang
-> code
```
def f(0), do: raise "Loi roi"
def f(x), do: 10 / x
```
Posted in #elixirYesterday at 2:43 PM
trường hợp đảo lại thứ tự 2 hàm trên là kết quả khác liền

vietthang [4:03 PM]
À cái này e quên nói về vị trí
E chỉ đang focus về pattern match

lATAl [4:03 PM]
ề em tưởng erlang cũng thế

vietthang [4:03 PM]
Erlang khác

toanha [4:03 PM]
tương tự với hàm `case`, `cond`, `with` ...

vietthang [4:03 PM]
Erlang variable chỉ đc bind 1 lần thôi

toanha [4:03 PM]
cái nào match trước thì chạy trước

lATAl [4:04 PM]
ý là thứ tự hàm ấy

toanha [4:05 PM]
erlang thì mình chưa tìm hiểu nên k biết :omg:

mquy [4:20 PM]
một điểm nữa quên nhắc đến là ở pattern matching nó ko phải equal mà equality :kappa:

toanha [4:21 PM]
hiểu như tương đương trong toán học phải k a @mquy

mquy [4:22 PM]
chắc vậy á, tại vì ngu toán :yaomin:

checkraiser [6:22 PM]
Pattern matching thì cũng quay về `case x of : isPattern1 x -> , isPattern2 x ->` 
Message Input

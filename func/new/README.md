# `new` 函数

`new(T)` 可以创建一个类型为 T 的无名变量，初始化为 T 的零值。返回值是变量的地址，类型是 `*T`。

```go
p := new(int)
fmt.Println(*p) // 0
*p = 2
fmt.Println(*p) // 2
```

通过 `new` 创建的变量，和通过普通方法创建的变量没什么区别。`new` 只是一种语法糖。

下面的两个 `newInt` 函数行为一致：

```go
func newInt() *int {
    return new(int)
}

func newInt() *int {
    var dummy int
    return &dummy
}
```

每次调用 new 产生的地址都是不同的：

```go
p := new(int)
q := new(int)
fmt.Println(p == q) // false
```
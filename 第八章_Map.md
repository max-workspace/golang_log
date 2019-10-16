###1.0 声明、初始化和 make
```golang
var map1 map[keytype]valuetype
```
>var map1 map[string]int
####1.1 map 是引用类型
####1.2 Map内的元素是无序的
####1.3 未初始化的 map 的值是 nil
>对于未初始化的变量无法对其进行一般的操作
####1.4 value 可以是任意类型的
####1.5 key 的类型可以是string、int、float
>数组、切片和结构体不能作为 key ，但是指针和接口类型可以
####1.6 map的初始化的两种方式
```golang
var map1 map[keytype]valuetype = map[keytype]valuetype{key1: val1, key2: val2}
简写 
map2 := map[keytype]valuetype{key1: val1, key2: val2}
****
var map3 = make(map[keytype]valuetype)
简写
map4 := make(map[keytype]valuetype)
```
####1.7 将一个map类型的变量赋值给相同类型的map类型的变量，新的变量修改也会影响到原本变量的值
####1.8 map 容量
>map不存在固定长度或者最大限制，但可以选择标明 map 的初始容量 capacity
```golang
map2 := make(map[string]float32, 100)
```
>当 map 增长到容量上限的时候，如果再增加新的 key-value 对，map 的大小会自动加 1。
####1.9 map的value可以使用切片以此实现一个key对应多个value
```golang
mp1 := make(map[int][]int)
mp2 := make(map[int]*[]int)
```
***
###2.0 测试键值对是否存在及删除元素
```golang
val1, isPresent = map1[key1]
```
####2.1 map通过返回多个值来判断对应key是否存在
>val1不存在时为对应类型的零值，无法用来判断对应key1是否存在  
>isPresent 为true表示存在，false表示不存在
```golang
delete(map1, key1) 
```
####2.2 delete用来删除指定key和对应value
>如果 key1 不存在，该操作不会产生错误
***
###3.0 for-range 的配套用法
```golang
for key, value := range map1 {
	...
}
```
>注意map本身是无序的，所以for-range遍历map也是无序的
###4.0 将 map 的键值对调
####4.1 为 map 进行键值对调
>4.1.1 创建一个keyType和valueType位置相反的map  \
>4.1.2 循环原本的map，分离出index和value  \
>4.1.3 将分离出的value当作新的index，分离出的index当作新的value，插入新的map
###5.0 map 的排序
####5.1 为 map 排序
>5.1.1 获取map的key或者value  \
>5.1.2 对获取到的key或者value进行排序  \
>5.1.3 对排序后的key或者value进行循环，打印出对应map的键值对

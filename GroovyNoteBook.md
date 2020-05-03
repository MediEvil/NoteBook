---
note:
    id: ""
    tags: []
    modifiedAt: 2020-05-03T01:34:38.507Z
    createdAt: 2020-05-03T01:34:09.259Z
---
## Groovy 笔记

### list常用操作

1. 集合遍历

```groovy
def list = [1,2,3]
list.each {
  println(it)
}
```

it是与当前元素对应的隐式函数

2. 取最大最小值
* 简单逻辑
```groovy
def list = [1,2,3]
def max = list.max()
def min = list.min()
assert 3 == max
assert 1 == min
```
* 复杂逻辑
```groovy
// fat and tall
def FAT = new Person(180, 180)
// short and thin
def SAT = new Person(160, 80)
// fat and short
def FAS = new Person(130,150)

def persons = [FAT, SAT, FAS]

// height of fattest person
def HOFP = persons.max { it.weight }.height
assert 180 == HOFP
// weight of shortest person
def WOSP = persons.min { it.height }.weight
assert 150 == WOSP
// height of tallest person
def HOTP = persons.max { it.height }.height
assert 180 == HOTP

class Person {
  Long height
  Long weight
  
  Person(Long height, Long weight) {
    this.height = height
    this.weight = weight
  }
}
```

3. 创建新列表

* 快捷创建新列表

```groovy
def list = [1,2,3]
def newList = list*.multiply(2)
println(newList)
```

创建了一个每个元素都乘以2的列表，新列表为[2,4,6]

* 复杂逻辑创建新列表

```groovy
def itemA = new Item(1, 'itemA')

def itemASku1 = new ItemSku(1000, 500)
def itemASku2 = new ItemSku(800, 600)

def itemASkus = [itemASku1, itemASku2]

def itemCompositeA = new ItemComposite(itemA, itemASkus)

def itemB = new Item(2, 'itemB')

def itemBSku = new ItemSku(900, 400)

def itemBSkus = [itemBSku]

def itemCompositeB = new ItemComposite(itemB, itemBSkus)

def list = [itemCompositeA, itemCompositeB]

def newList = list.collect {
  def newIt = [:]
  newIt.id = it.item.id
  if (it.item.title) {
    newIt.title = it.item.title
  }
  newIt.origPrice = it.itemSkus.max {it.origPrice}.origPrice
  newIt.price = it.itemSkus.min {it.price}.price
  newIt
}

println(newList)

class ItemComposite {
  Item item
  List<ItemSku> itemSkus
  
  ItemComposite(Item item, List<ItemSku> itemSkus) {
    this.item = item
    this.itemSkus = itemSkus
  }
}

class Item {
  Long id
  String title
  
  Item(Long id, String title) {
    this.id = id
    this.title = title
  }
}

class ItemSku {
  Long origPrice
  Long price
  
  ItemSku(Long origPrice, Long price) {
    this.origPrice = origPrice
    this.price = price
  }
}
```

对于新列表进行了许多逻辑判断，如判空，取最大值等，闭包中嵌套闭包

4. 计算sum值
groovy的inject方法以闭包作为参数处理一个数据结构并返回一个值，inject方法的第一个参数是第二个参数（闭包）的立即返回值
```groovy
def list = [1,2,3]
def sum = list.inject {s,it -> s + it}
assert sum == 6
```



### 树集
Treeset是一个有序集合，使用红黑树，以任意顺序将元素插入到集合中，遍历时，每个值按照排序后的顺序呈现。必须实现comparable接口。
将一个元素添加到树中比添加到散列表中慢，添加一个有1000个元素的树，大约需要比较10次

### 队列与双端队列
LinkedList和ArrayDeque

### 优先级队列
使用堆，并没有对元素进行排序，但每次调用remove，总会获得当前优先级队列中最小的元素，对树执行添加和删除操作，可以让最小的元素移动到跟，同样必须实现Comparable，或者构造器传入Comparator对象


## 映射
HashMap和TreeMap(键值排序)
### 更新映射项
正常情况下，可以得到一个与键关联的值，完成更新再放回更新后的值就可以，但是注意当第一次put是，get会返回一个null，会出现空指针异常，可以使用getOrDefault();
```
counts,put(word,counts.getOrDefault(word,0)+1)
```
merge方法处理可能更好，使用方法是
```
counts.merge(word,1,Integer:sum)//键不存在，将word与1关联，否则将原值和1求和
```
### 映射视图
3中视图，键集，值集，键/值对集,注意keySet不是HashSet或者TreeSet，只是实现了Collection接口而已

```
Set<K> keySet()
Collection<V> values()
Set<Map,Entry<K,V>> entrySet()
```

### 弱散列映射

### 链接散列集与映射

LinkedHashSet和LinkedHasMap类用来记住插入元素项的顺序，将使用访问顺序，而不是插入顺序对映射条目进行迭代
LinkedHashMap可以用来实现高速缓存，例如
```
Map<K,V> cache = newLinkedHadhMap<128,0.75,true>
{
    protected boolean removeEldestEntry(Map.Entry<K,V> eldest)
    {
        return size()>100;
    }
}
```
### 枚举集与映射

### 标识散列映射
视图与包装器

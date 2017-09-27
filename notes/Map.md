# Map  
> key 和 value构成的entry实例构成，常用hasgMap和二叉树treeMap ,不可以重复key

map => sortedMap => NavigableMap => TreeMap
map => abstractMap => (TreeMap,HashMap,weakHashMap)
- map的bucket，也就是一个键值对
- Capacity 容量 ，一共有多少个桶可以用，默认16个
- size map实例多少个键值对
- Load factor加载因子，默认0.75，也就是16*0.75=12，超出了就扩容和重新散列
- 每次扩容rehash都会影响性能，所以不如事先规定长度
### HashMap 非常重要
> HashMap put key和value时候，散列算法，对key算出hashCode值,如果key一样，value直接替换，如果key不一样，hashcode一样的，两个entry实例，变成一个链表 ,这样就影响性能
```
//空指针异常 int = null
int value = map.put("apple", 5000);

//这样就不会错
Integer value = map.put("apple", 5000);

map.put("apple", 5000);//返回为null
map.put("mi", 2000);
map.put("vivo", 3000);
map.put("vivo", 4000);//返回3000
System.out.println(map);

//集合的键值对的个数
System.out.println(map.size());

//获取value
System.out.println(map.get("heimei"));

//删除一组数据
map.remove("vivo");
System.out.println(map);
```
### map遍历 key 
> keySet() return set
```
Collection<String> set = map.keySet();
for(String key: set) {
	System.out.println("key="+key);
}
```
### map 遍历 key&value
> entrySet(); return set
```
import java.util.Map.Entry;
Set<Entry<String,Integer>> sets = map.entrySet();
for(Entry<String,Integer> e: sets) {
	String key = e.getKey();
	int value = e.getValue().intValue();
	System.out.println("key="+key+"&value="+value);
}
```
### map 遍历value
> values 返回collection不是list因为无序
```
Collection<Integer> values = map.values();
System.out.println(values);

```
### 类作为key
> 当一个类作为HashMap的key时，为了提高性能,equals方法和hashCode要重写
1. 修改equals，如果两个对象equals，那么应该让他们的hashCode相同
2. hashCode多次调用返回的数字应该相同，不应该变化，除非参与equals的属性值变化了

```






```
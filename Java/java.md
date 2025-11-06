# Java常用接口

java 接口的方法只能是抽象的或静态方法

java 接口内的属性都是public static final

java 接口不能继承其它的类，可以实现多个接口，而java类只能单继承

dwadwad

wdadwDwa

Java 中常用的接口包括但不限于以下几种：

1. **List 接口**：`java.util.List` 接口表示一个有序的集合，允许重复元素。常见的实现类有 `ArrayList`、`LinkedList` 和 `Vector`。
2. **Set 接口**：`java.util.Set` 接口表示一个不包含重复元素的集合。常见的实现类有 `HashSet`、`LinkedHashSet` 和 `TreeSet`。
3. **Map 接口**：`java.util.Map` 接口表示键值对的映射集合。常见的实现类有 `HashMap`、`LinkedHashMap`、`TreeMap` 和 `Hashtable`。
4. **Queue 接口**：`java.util.Queue` 接口表示一种先进先出 (FIFO) 的集合。常见的实现类有 `LinkedList`、`PriorityQueue` 和 `ArrayDeque`。
5. **Deque 接口**：`java.util.Deque` 接口表示一种双端队列，可以在两端添加或删除元素。常见的实现类有 `ArrayDeque` 和 `LinkedList`。
6. **Iterator 接口**：`java.util.Iterator` 接口用于迭代集合中的元素，提供了统一的迭代访问方式。常用于遍历集合类的元素。
7. **Comparable 接口**：`java.lang.Comparable` 接口定义了一个用于对象比较的方法 `compareTo`，使得对象可以进行自然排序。
8. **Comparator 接口**：`java.util.Comparator` 接口定义了用于对象比较的方法 `compare`，允许在不修改对象本身的情况下进行排序。
9. **Runnable 接口**：`java.lang.Runnable` 接口用于表示一个可运行的任务，通常与线程一起使用，用于多线程编程。
10. **Callable 接口**：`java.util.concurrent.Callable` 接口类似于 `Runnable` 接口，但是它可以返回一个结果并抛出一个异常。

这些接口是 Java 编程中常用的基础接口，它们提供了各种功能和特性，使得 Java 编程更加灵活和高效。





## Collections工具类









## 包装类













## 迭代器Iterator

Set

迭代：一个一个的往出拿



next()  下一个

hasNext()   是否存在下一个元素





```java
import java.util.*;

public class TestList {
    public static void main(String[] args) {
        List<String> list = new ArrayList<>();
        list.add("李易峰");
        list.add("蔡徐坤");
        list.add("吴亦凡");
        list.add("鹿晗");

        System.out.println(list);

        //创建迭代器
        Iterator<String> it  = list.listIterator();
        while(it.hasNext()){
            String s = it.next();
            System.out.println(s);
        }
    }
}

```











## Math类

Math中没有构造方法，类的成员都是静态成员，通过类名就可以直接调用

- 常用方法

![image-20240423210118518](../../typora文件/typora图片/image-20240423210118518.png)

```java
public class MathDemo {
    public static void main(String[] args) {
        //1、public static int abs(int a)	获取参数a的绝对值
        System.out.println(Math.abs(88)); //88
        System.out.println(Math.abs(-88)); //88

        //2、public static double ceil(double a)	向上取整
        System.out.println(Math.ceil(12.34)); //13.0
        System.out.println(Math.ceil(12.56)); //13.0

        //3、public static double floor(double a)	向下取整
        System.out.println(Math.floor(12.34)); //12.0
        System.out.println(Math.floor(12.56)); //12.0

        //4、public static long round(double a)	四舍五入取整
        System.out.println(Math.round(12.34)); //12
        System.out.println(Math.round(12.56)); //13

        //5、public static int max(int a,int b)	返回两个数中较大值
        System.out.println(Math.max(66,88)); //88

        //6、public static int min(int a,int b)	返回两个数中较小值
        System.out.println(Math.min(66,88)); //66

        //7、public static double pow(double a,double b)	获取a的b次幂
        System.out.println(Math.pow(2.0,3.0)); //8.0

        //8、public static double random()	返回值为double类型随机数 [0.0~1.0）
        System.out.println(Math.random()); //0.36896250602163483
        System.out.println(Math.random()); //0.3507783145075083
    }
}

```



## Arrays类（数组）操作

![image-20240423210413732](../../typora文件/typora图片/image-20240423210413732.png)

- toString(T[] array)

```java
Integer[] array={1,2,3,4,5}
String arrayAsString=Arrays.toString(array);
```

- sort(T[] array)

```java
Integer[] array={3,1,4,2,5};
Arrays.sort(array);
```

- binarySearch(T[] array, T key)   

  在  **排序** 数组中使用二份搜索算法查找指定元素

  ```java
  Integer[] array={1,2,3,4,5};
  int index=Arrays.binarySearch(array,3);
  ```

- equals(T[] array1, T[] array2)

  ```java
  boolean isEqual=Arrays.equals(array1,array2);
  ```

- fill(T[] array, T value)

  将数组所有元素替换为指定的值

  ```java
  Integer[] array=new Integer[5];
  Arrays.fill(array,7);
  ```

- copyOf(T[] original, int newLength)

  将指定数组的指定长度的部分复制到一个新数组中

  ```java
  Integer[] original={1,2,3,4,5,};
  Integer[] copy=Arrays.copyOf(original,3);
  ```

- copyOfRange(T[] original, int from, int to)

  不包括结束索引

  ```java
  Integer[] original={1,2,3,4,5};
  Integer[] copy=Arrays.copyOfRange(origianl,1,4);
  //copy的范围是[2,3,4]
  ```

- asList(T… a)

  ```java
  Integer[] array={1,2,3,4,5};
  List<Integer> list=Arrays.asList(array);
  ```



## List操作

list.add()  添加元素

list.remove()  删除元素

list.size()   列表大小

list.get(i)  从列表中获取当前索引的元素

list.contains(element)  判断容器中是否有该元素



遍历列表和数组一样





## ArrayList 动态数组

- `boolean add(E e)`: 在列表的末尾添加指定的元素。

  ```java
  ArrayList<String> list = new ArrayList<>();
  list.add("Apple");
  list.add("Banana");
  ```

- `void add(int index, E element)`: 在指定的位置插入指定的元素。

  ```java
  list.add(1, "Orange");
  ```

- `E get(int index)`: 返回列表中指定位置的元素。

  ```java
  String fruit = list.get(0);
  ```

- `E set(int index, E element)`: 将列表中指定位置的元素替换为指定的元素。

  ```java
  list.set(1, "Grapes");
  ```

- `boolean remove(Object o)`: 从列表中删除指定的元素。

  ```java
  list.remove("Apple");
  ```

- `E remove(int index)`: 删除列表中指定位置的元素。

  ```java
  String removedElement = list.remove(2);
  ```

- `int size()`: 返回列表中的元素数量。

  ```java
  int size = list.size();
  ```

- `boolean isEmpty()`: 如果列表不包含任何元素，则返回 true。

  ```java
  boolean isEmpty = list.isEmpty();
  ```

- `void clear()`: 从列表中移除所有元素。

  ```java
  list.clear();
  ```

- `boolean contains(Object o)`: 如果列表包含指定的元素，则返回 true。

  ```java
  boolean contains = list.contains("Banana");
  ```

- `int indexOf(Object o)`: 返回列表中指定元素的第一个匹配项的索引，如果列表中不包含该元素，则返回 -1。

  ```java
  int index = list.indexOf("Grapes");
  ```

- `int lastIndexOf(Object o)`: 返回列表中指定元素的最后一个匹配项的索引，如果列表中不包含该元素，则返回 -1。

  ```java
  int lastIndex = list.lastIndexOf("Banana");
  ```

- `void ensureCapacity(int minCapacity)`: 确保列表的容量至少是指定的最小值。

  ```java
  list.ensureCapacity(20);
  ```

- `void trimToSize()`: 将列表的容量调整为当前元素数量。

  ```java
  list.trimToSize();
  ```






## LinkedList

删除和插入操作效率优于ArrayList







## Set操作

Set是一个接口，中不允许重复

set.add()

set.remove(value)

set.size()

set.contains(value)







## HashSet

不允许重复元素存；

无序性；

允许存在null元素；

适合快速查找，去重；

- 创建HashSet对象

  ```java
  HashSet<String> hashSet = new HashSet<>();
  ```

- 添加元素

  ```java
  hashSet.add("Apple");
  ```

- 检查元素是否存在

  ```java
  String searchElement = "banana";
  hashSet.contains(searchElement);
  ```

- 移除元素

  ```java
  hashSet.remove("Apple");
  ```

- 获取集合大小

  ```java
  hashSet.size();
  ```

- 检查是否为空

  ```java
  hashSet.isEmpty();
  ```

- 清空hashSet

  ```java
  hashSet.clear();
  ```

  

## TreeSet

默认进行排序；并非输入的存储顺序







## Map操作

put(key,value)

remove(key)   

size()

containsKey()

containsValue()

**如果出现了相同的Key，原来的数据会被顶掉**

keySet()  把map中的所有Key打包成Set集合返回

get(Key)   获取key的value

entrySet（）  返回map中的所有键值对的Set视图



## HashMap

java中常用的基于哈希表实现的Map接口的一种。它以键—值对的形式储存数据，并根据键的哈希值存储和检索数据，具有一下特点：

1. **键唯一**：`HashMap` 中的键是唯一的，每个键最多只能映射到一个值。
2. **无序性**：`HashMap` 中的键-值对没有固定的顺序，不保证顺序和插入顺序相同。
3. **允许空键和空值**：`HashMap` 中可以使用 null 作为键，也可以使用 null 作为值。
4. **非线程安全**：`HashMap` 不是线程安全的，如果需要在多线程环境下使用，需要进行额外的同步措施。

- `V put(K key, V value)`: 将指定的值与指定的键关联，并将其存储在 `HashMap` 中。
- `V get(Object key)`: 返回指定键所映射的值，如果该键不存在，则返回 null。
- `boolean containsKey(Object key)`: 如果 `HashMap` 中包含指定的键，则返回 true。
- `boolean containsValue(Object value)`: 如果 `HashMap` 中包含一个或多个键映射到指定的值，则返回 true。
- `V remove(Object key)`: 如果存在键的映射关系，则将该键的映射关系从 `HashMap` 中移除，并返回之前与该键关联的值。
- `int size()`: 返回 `HashMap` 中键-值映射关系的数量。
- `boolean isEmpty()`: 如果 `HashMap` 中没有键-值映射关系，则返回 true。
- `void clear()`: 从 `HashMap` 中移除所有的键-值映射关系。





## TreeMap

可以根据键值进行排序









## String类

- 字符串拼接

  ```java
  String greeting = str1 + " " + str2;
  String message = str1.concat(" ").concat(str2);
  ```

- 字符串长度

  ```java
  int length = str1.length();
  ```

- 提取子串

  ```java
  //从索引为2的位置开始提取子串
  String sub = str1.substring(2);
  ```

- 检索子串

  ```java
  int index = str1.indexOf("lo");
  ```

- 比较字符串，使用equals( )或者 compareTo( ) 方法比较字符串是否相等

  ```java
  boolean isEqual = str1.equals(str2);
  int result = str1.compareTo(str2);
  ```

- 转换大小写

  ```java
  String upperCase = str1.toUpperCase();
  String lowerCase = str2.toLowerCase();
  ```

- 去除空白字符

  ```java
  String trimmedStr = str.trim();
  ```

  







## StringBuffer类

- StringBuffer是java中的一个类，用于处理可变字符串。

- StringBuffer的内容可有修改，而String的内容不可修改。



- 获取长度和容量

  ```java
  int length = sb.length();
  int capacity = sb.capacity();
  ```

- 反转字符串

  ```java
  sb.reverse();
  ```

- 获取指定位置的字符

  ```java
  char ch = sb.charAt(0);
  ```

- 获取子串

  ```java
  String subString = sb.substring(1,3);
  ```

- 转换为字符串数组或者不可变字符串

  ```java
  char[] charArray = sb.toString().toCharArray();
  String ans = sb.toString();
  ```

- 检索子串的位置，返回第一次出现的位置

  ```java
  int index = sb.indexOf("llo");
  ```

  




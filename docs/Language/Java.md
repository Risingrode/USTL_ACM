
# Java基础

> 代码由`lmh`同学提供，我只是复习总结而已。

代码下载链接：https://pan.baidu.com/s/1l4r0jbeZ-L-PNO98wOXAPw?pwd=1111 
提取码：1111

# 输入(Scanner)

```java
//创建键盘录入对象Scanner
Scanner sc = new Scanner(System.in);
//通过Scanner对象调用方法，赋值给变量
int year = sc.nextInt();
//判断输入的是不是int类型,返回值是bool
sc.hasNextInt();
// 释放资源
sc.close();
```
> scanner可以输入各种类型数据，看java的数据提示即可

## next()用法总结：
1. 一定要读取到有效字符后才可以结束输入。
2. 对输入的有效字符之前所遇到的空白，会自动将其去除。
3. 只有输入的有效字符后才将其后面输入的空白作为结束符。
4. next()不能得到带有空格的字符串。
5. 读取结束后，该方法会将我们的鼠标定位在我们输入数据的那一行。

## nextLine()用法总结：
1. 以回车符作为结束标识符，获取到的是回车符前输入的所有字符串（包括空格）。
2. 读取结束后，该方法会将我们的鼠标定位在我们输入数据的那一行的下一行。


## 先使用nextLine再使用next()、nextInt()等没问题，但是先使用next()和nextInt()等之后就不可以再紧跟nextLine使用。（这一点很重要！！！）
1. 这是因为next()等这些方法读取结束后会紧跟一个回车符，而nextLine会直接读取到这个回车符，这就导致出现我们还没有来得及输入我们想要输入的数据，nextLine就以为我们已经输入完了这样的情况！
2. 解决办法：我们直接在next()使用后加两个nextLine()就OK了，这样第一个nextLine()就会当一个‘替死鬼’，第二个nextLine()我们就可以输入自己想要输入的数据啦！

# 输出(System.out.println)

## println
> println()其实调用了print()再调用newLine()来实现换行。

## printf

> 相当于c语言的printf,可以指定格式进行输出。

## 静态方法的特点

1. **关联于类：** 静态方法属于整个类，而不是属于类的实例。因此，可以通过类名来调用静态方法，无需创建类的实例。

2. **无需实例化：** 由于静态方法不依赖于类的实例，所以在调用静态方法时，无需创建类的对象。这使得静态方法可以在没有实例的情况下使用。

3. **不访问实例变量：** 静态方法不能直接访问类的实例变量（非静态成员变量），因为它们没有与任何特定实例相关联。但是，它们可以访问静态成员变量，因为静态成员变量也与类相关联。

4. **常用于工具方法：** 静态方法通常用于定义工具方法，这些方法独立于类的实例，执行某些通用操作，例如数学计算、文件操作、字符串处理等。例如，`Math` 类中的所有方法都是静态方法，因为它们执行数学运算而无需创建 `Math` 的实例。

5. **静态块：** 静态方法可以包含静态块（static block），静态块在类被加载时执行，通常用于初始化静态成员变量或执行其他一次性的初始化工作。

```java
public class MyClass {
    static {
        // 静态块中的代码在类加载时执行
        // 用于初始化静态成员变量等
    }
}
```
6. **全局访问点：** 静态方法可以提供一个全局的访问点，使得其他类和代码可以轻松地调用这些方法，而不必关心类的实例化和细节。

需要注意的是，静态方法不能访问非静态方法和非静态变量，因为它们不依赖于类的实例。另外，静态方法不能被重写，因为它们是与类直接关联的，而不是与实例关联的。
总之，静态方法用就完了，无需创建实例。

## `String.valueOf(num)` 

用于将不同类型的数据转换为字符串类型。它的作用是将给定的数据转换为字符串，无论数据的原始类型是什么。

# 数组

## 复制
```java
int[] arr = { 11, 22, 33, 44, 55 };
int[] newArr = Arrays.copyOf(arr, 4);
System.out.println(Arrays.toString(newArr));
// 方法二
int[] a = new int [5];
// 原数组 起始位置 目标数组 起始位置 复制个数
System.arraycopy(arr, 1, a, 2, 3);
System.out.println(Arrays.toString(a));
```

## length与size的区别

1. `length()` 方法：

- `length()` 是用于获取数组的长度的方法。它只能用于数组，而不能用于集合（如`List`、`String`等）。
- 在数组中，`length` 是一个属性，而不是方法，所以没有括号。
- 用于获取数组的元素数量，返回的是一个整数。

2. `size()` 方法：

- `size()` 通常用于获取集合类对象的大小，如 `List`、`Set`、`Map` 等。它是集合框架中通用的方法。
- 在集合类中，`size()` 是一个方法，需要使用括号进行调用。
- 用于获取集合中元素的数量，返回的是一个整数。


## equalsIgnoreCase()
`equalsIgnoreCase()` 方法是 Java 中的字符串比较方法，用于比较两个字符串的内容是否相等，但不考虑它们的大小写。

## 重写与重载的区别

1. 重载是在同一个类中定义多个同名方法，方法名相同但参数不同。
2. 重写是子类覆盖父类中的同名方法，方法名和参数都必须相同。
3. 重载是编译时的多态性（静态绑定），而重写是运行时的多态性（动态绑定）。
4. 重载通常用于实现相似功能的方法，而重写用于实现父类方法的不同行为。

## 初始化数组的几种方式
在Java中，你可以使用多种方式来初始化数组，具体取决于你的需求和代码风格。以下是一些初始化数组的常见方式：

1. **使用大括号（Array Literal）初始化数组**：
    ```java
        int[] numbers = {1, 2, 3, 4, 5};
    ```
2. **使用`new`关键字初始化数组**：
    ```java
        int[] numbers = new int[5];
    ```
3. **动态初始化二维数组**：
    ```java
        int[][] matrix = new int[3][3];
    ```

4. **使用数组工具类初始化**：
   Java提供了`Arrays`类，可以使用`Arrays.fill()`方法为数组的所有元素分配相同的初始值。
    ```java
    import java.util.Arrays;
    int[] numbers = new int[5];
    Arrays.fill(numbers, 0); // 将所有元素初始化为0
    ```
5. **使用静态初始化块**：
   你可以在静态初始化块中初始化数组，这样可以在类加载时执行初始化。
   ```java
   public class MyClass {
       static int[] numbers;
       static {
           numbers = new int[] {1, 2, 3};
       }
   }
   ```

## 关于类中的super()方法

1. 调用父类的构造方法：通过`super()`语句，子类可以调用父类的构造方法，以确保在创建子类对象时，首先执行父类的初始化操作。
2. 如果子类的构造方法没有显式调用`super()`，Java会默认调用父类的无参构造方法。

## brak高级用法
```java
   outerLoop: for (int i = 1; i <= 3; i++) {
       for (int j = 1; j <= 3; j++) {
           System.out.println("i: " + i + ", j: " + j);
           if (i == 2 && j == 2) {
               break outerLoop; // 使用标签跳出外层循环
           }
       }
   }
```

## String的api

1. `charAt(index)`: 拿到下标`index`的字符

## `StringBuilder` 和 `StringBuffer`

1. 线程安全性：
   - `StringBuilder`：是非线程安全的，适合在单线程环境下使用。由于它不需要考虑线程同步，因此在单线程情况下性能更高。
   - `StringBuffer`：是线程安全的，适合在多线程环境下使用。它的方法都是同步的，可以确保多个线程同时操作时不会出现数据混乱的情况。

2. 性能：
   - `StringBuilder`：由于不需要线程同步，所以在单线程环境下通常比 `StringBuffer` 更快。
   - `StringBuffer`：由于需要线程同步，所以在多线程环境下能够保证数据的一致性，但性能通常比 `StringBuilder` 稍差。

在选择使用 `StringBuilder` 还是 `StringBuffer` 时，通常考虑以下因素：
- 如果在单线程环境下操作字符串，建议使用 `StringBuilder`，以获得更好的性能。
- 如果在多线程环境下操作字符串，需要确保线程安全性时，使用 `StringBuffer`。

# Exception

```java
    System.out.println(arr[index]);
            System.out.println("结果出来了");
        } catch (IndexOutOfBoundsException i) {
            i.printStackTrace();  // printStackTrace()打印异常信息
            System.out.println("i数组越界了");
        } catch (Exception e) {
            e.printStackTrace();  // printStackTrace()打印异常信息
            System.out.println("e数组越界了");
        } finally {
            sc.close();
            System.out.println("关闭资源");
        }
```

1. 首先，程序尝试执行 `System.out.println(arr[index]);` 
2. 这行代码，如果 `index` 超出了数组 `arr` 的索引范围，就会抛出 `IndexOutOfBoundsException` 异常。
3. 接下来，程序会捕获异常。它先检查是否是 `IndexOutOfBoundsException` 类型的异常，
4. 如果是，就执行 `catch (IndexOutOfBoundsException i)` 块中的代码，打印出异常信息，然后显示 "i数组越界了"。
5. 如果异常不是 `IndexOutOfBoundsException`，而是其他类型的异常，程序会进入 `catch (Exception e)` 块，同样打印出异常信息，然后显示 "e数组越界了"。
6. 无论是哪种情况，最终都会执行 `finally` 块中的代码。这个块中的代码用于关闭资源（这里是关闭 `Scanner` 对象），然后显示 "关闭资源"。


# ArrayList
1. `arr.addAll(arr1);`
   - 这行代码将集合 `arr1` 中的所有元素添加到集合 `arr` 中。
2. `arr.removeAll(arr1);`
   - 这行代码从集合 `arr` 中删除所有存在于集合 `arr1` 中的元素。
3. `arr.toArray();`
   - 这行代码将集合 `arr` 中的元素转换为一个数组

## 迭代器遍历
```java
    Iterator<Integer> it = list.iterator();
        while (it.hasNext()) {// 是否具有下一个元素
            Integer num = it.next();
            System.out.println(num);
        }
```

## 自定义排序
```java
    TreeSet<User> set = new TreeSet<>((o1, o2) -> {
            int i = o1.getName().length() - o2.getName().length();
            return  i== 0 ? o1.getAge() - o2.getAge() : i;
        });
```
1. **有序性**
2. **唯一性**
3. **基于红黑树实现**：`TreeSet` 的底层数据结构是一颗红黑树。这保证了元素的插入、删除和查找的时间复杂度都是 O(log n)。
4. **不允许 null 元素**：由于要保持有序性，`TreeSet` 不允许插入 null 元素。
5. **快速查找**：由于底层数据结构是一颗二叉搜索树，`TreeSet` 提供了快速的查找操作。
6. **不是线程安全的**：如果多个线程同时访问一个 `TreeSet` 实例，并且至少有一个线程在结构上修改了集合，那么它必须保持外部同步。


## `Arrays.asList(arr)`和`Collections`

1. `Arrays.asList(arr)` 将数组转换为一个固定大小的列表。这意味着你不能对这个列表进行增删操作。
2. `Arrays.asList("11", "22", "33", "44")` 将字符串数组转换为列表。
3. 使用 `Collections.addAll()` 将元素添加到列表中。
4. 使用 `Collections.sort()` 对列表进行排序。


# 线程并行

```java
public class Test {
    public static void main(String[] args) {
        MyThread myThread = new MyThread();
        Thread t1 = new Thread(myThread);
        Thread t2 = new Thread(myThread);
        Thread t3 = new Thread(myThread);
        t1.start(); // start函数会默认执行myThread重载的run方法
        t2.start();
        t3.start();
        for (int i = 1; i <= 10; i++) {
            System.out.println("Main抽到了" + i + "号");
        }
    }
}

public class MyThread implements Runnable {
    @Override
    public void run() {
        for (int i = 1; i <= 10; i++) {
            System.out.println(Thread.currentThread().getName() + "抽到了" + i + "号");
        }
    }
}
```

## 锁 
### 线程安全1

```java
public class Test {
    // 定义票的个数
    private static int num = 8;
    @Override
    public void run() {
        for (int i = 0; i < 3; i++) {
            synchronized (TicketDemo.class) {
                if (num > 0) {
                    try {
                        Thread.sleep(100);
                    } catch (InterruptedException e) {
                        e.printStackTrace();
                    }
                    num--;
                    System.out.println(super.getName() + "已经卖出一张票，还剩" + num + "张！");
                }
            }
        }
    }
}

```

> 解释： 定义一个类锁，锁住整个类，这样就可以保证每次只有一个线程进入代码块，从而保证了线程安全。
> 只有当A线程跑完后，B线程才能进入代码块，这样就保证了线程安全。

### 线程安全2
> Runnable接口实现方式
```java
public class TicketDemo implements Runnable {
    private int num = 5;
    @Override
    public void run() {
        for (int i = 0; i < 3; i++) {
            synchronized (this){
                if(num > 0 ){
                    try {
                        Thread.sleep(100);
                    } catch (InterruptedException e) {
                        e.printStackTrace();
                    }
                    num--;
                    System.out.println(Thread.currentThread().getName() + "已经卖出一张票，还剩" + num + "张！");
                }
            }
        }
    }
}
```

# 文件操作

## File

1. `FileOutputStream`：用于向文件中写入数据。
2. `FileInputStream`：用于从文件中读取数据。
3. `FileReader`：用于读取字符流。
4. `FileWriter`：用于写入字符流。

> `while ((len = in.read(ch)) != -1)`每次读取，最多读1024字节





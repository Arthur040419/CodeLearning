# Java面试题

此笔记用于记录我在准备面试时看到的题目及其解决思路和代码



## 写一个方法，输入一个文件名和一个字符串，统计这个字符串在这个文件中出现的次数。

### 1.思路

1.使用字符输入流来读取文件，可以用字符缓冲输入流来包装一下

2.用`readLine`方法每次读取一行

3.判断每一行中要找的字符串出现的次数

这里要注意，每行出现的次数可能有多次，所以在找到一次后要将后面的字符串分割出来，直到最后分隔出来的字符串长度小于要找的字符串长度或者再也找不到要找的字符串

4.最后返回出现的次数



### 2.学习到的新方法

String提供的`indexOf`方法，参数可以为一个字符串，返回结果为该字符串第一次出现的索引

```java
public int indexOf(String str);
```



### 3.实现代码

```java
import java.io.*;
public class CountString {
    public static void main(String[] args) {
        System.out.println(countString(new File("D:\\zzz\\countString.txt"), "明月"));
    }

    /**
     * 统计文件中某个字符串出现的次数
     *
     * @param file 要统计的文件
     * @param s    要找的字符串
     * @return 返回字符串出现的次数
     */
    public static int countString(File file, String s) {
        try (
                //1.创建字符输入流
                Reader reader = new FileReader(file);

        ) {
            try (
                    //2.将字符输入流包装成字符缓冲输入流
                    BufferedReader bufferedReader = new BufferedReader(reader);
            ) {
                //3.定义一个变量记住出现的次数
                int count = 0;
                //line用于记住每次读取的一行
                String line;
                while ((line = bufferedReader.readLine()) != null) {
                    //index用于记住每行找到的字符所在的索引
                    int index = -1;
                    //如果字符串长度大于目标字符串的长度或字符串中存在目标字符串才计数
                    while (line.length() >= s.length() && (index=line.indexOf(s)) != -1) {
                        count++;
                        //将目标字符串后续的字符串截取出来继续统计
                        line=line.substring(index+s.length());
                    }
                }
                return count;
            }
        } catch (Exception e) {
            throw new RuntimeException(e);
        }

    }
}
```



## 如何用Java代码列出一个目录下所有的文件？

### 1.思路

1.首先获取当前目录下的所有文件对象

2.然后遍历当前目录下的文件对象

如果是文件则打印文件名，如果是文件夹就打印出文件夹名并递归调用当前方法



### 2.实现代码

```java
import java.io.File;

public class ListFiles {
    public static void main(String[] args) {
        listFiles(new File("D:\\工作上的文件"),0);
    }

    /**
     * 列出当前目录下的所有文件
     * @param file      当前目录
     * @param level     目录的深度，用于格式化列出来的文件
     */
    public static void listFiles(File file,int level){
        //先进行非法判断
        if(!file.exists()){
            //如果文件目录不存在则返回
            return;
        }
        //打印当前目录名
        for (int i = 0; i < level-1; i++) {
            //进行格式化，开头缩进
            System.out.print("\t");
        }
        System.out.println(file.getName());
        //列出当前目录的所有文件对象
        File[] files = file.listFiles();
        //遍历files
        for (File f : files) {
            if(f.isFile()){
                //如果是文件，就直接打印出文件名
                for (int i = 0; i < level; i++) {
                    //进行格式化，开头缩进
                    System.out.print("\t");
                }
                System.out.println(f.getName());
            }else {
                //如果是目录,递归调用本方法
                listFiles(f,level+1);
            }
        }

    }
}
```



## Integer的值缓存机制

在创建Integer的对象时，由于Java值缓存机制的存在，在-128~127范围内的Integer对象将直接从缓存中取出，超出这个范围才会重新创建一个对象

```java
public class Test6 {
    public static void main(String[] args) {
        //Integer的值缓存机制
        Integer i1 = Integer.valueOf(127);
        Integer i2 = Integer.parseInt("127");
        //由于值缓存机制，127的Integer对象直接从缓存中获取，因此i1与i2地址一样
        System.out.println(i1 == i2);   //true


        Integer i3 = Integer.parseInt("128");
        Integer i4 = Integer.parseInt("128");
        //由于128超出了-128~127的范围，所以128的Integer对象需要单独创建，这会导致i3与i4的地址不一致
        System.out.println(i3 == i4);   //false

        Integer i5 = Integer.parseInt("-129");
        Integer i6 = Integer.parseInt("-129");
        //同理，-129也不在-128~127的范围内，因此i5与i6的地址也不一样
        System.out.println(i5 == i6);   //false

        Integer i7 = Integer.parseInt("190");
        Integer i8 = i7;
        //当然，直接传地址可能一样哈
        System.out.println(i7 == i8);   //true
    }
}
```

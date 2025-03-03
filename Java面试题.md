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




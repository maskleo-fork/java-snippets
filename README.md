# Java Snippets

[![Build status](https://travis-ci.org/iluwatar/java-snippets.svg?branch=master)](https://travis-ci.org/iluwatar/java-snippets)
 
受启发于 [30 seconds of code](https://github.com/Chalarangelo/30-seconds-of-code), 这是一个可重用的经过测试的Java代码片段的集合。

## How to contribute
用代码片段更新示例应用程序并为其添加测试。 在证明它工作之后，更新这个README.md。

## 目录

### 数组
* [拼接2个泛型的数组](#拼接2个泛型的数组)
* [拼接多个泛型的数组](#拼接多个泛型的数组)

### 文件
* [列出目录](#列出目录)
* [从文件按行读取到字符串](#从文件按行读取到字符串)

### 数学
* [阶乘](#阶乘)
* [斐波那契](#斐波那契)

### 多媒体
* [截屏](#截屏)

### 字符串
* [反向字符串](#反向字符串)
* [字符串转时间](#字符串转时间)

## 数组

### 拼接2个泛型的数组

```java
    public static <T> T[] arrayConcat(T[] first, T[] second) {
        T[] result = Arrays.copyOf(first, first.length + second.length);
        System.arraycopy(second, 0, result, first.length, second.length);
        return result;
    }
```

[⬆ 返回顶部](#目录)

### 拼接多个泛型的数组

```java
    public static <T> T[] nArrayConcat(T[] first, T[]... rest) {
        int totalLength = first.length;
        for (T[] array : rest) {
            totalLength += array.length;
        }
        T[] result = Arrays.copyOf(first, totalLength);
        int offset = first.length;
        for (T[] array : rest) {
            System.arraycopy(array, 0, result, offset, array.length);
            offset += array.length;
        }
        return result;
    }
```

[⬆ 返回顶部](#目录)

## 文件

### 列出目录

```java
    public static File[] listDirectories(String path) {
        return new File(path).listFiles(File::isDirectory);
    }
```

[⬆ 返回顶部](#目录)

### 从文件按行读取到字符串

```java
    public static List<String> readLines(String filename) throws IOException {
        return Files.readAllLines(new File(filename).toPath());
    }
```

[⬆ 返回顶部](#目录)

## 数学
 
### 阶乘

```java
    public static int fibonacci(int n) {
        if (n <= 1) return n;
        else return fibonacci(n-1) + fibonacci(n-2);
    }
```

[⬆ 返回顶部](#目录)

### 斐波那契

```java
    public static int factorial(int number) {
        int result = 1;
        for (int factor = 2; factor <= number; factor++) {
            result *= factor;
        }
        return result;
    }
```

[⬆ 返回顶部](#目录)

## 多媒体
 
### 截屏
 
```java
    public static void captureScreen(String filename) throws AWTException, IOException {
        Dimension screenSize = Toolkit.getDefaultToolkit().getScreenSize();
        Rectangle screenRectangle = new Rectangle(screenSize);
        Robot robot = new Robot();
        BufferedImage image = robot.createScreenCapture(screenRectangle);
        ImageIO.write(image, "png", new File(filename));
    }
```

[⬆ 返回顶部](#目录)

## 字符串
 
### 反向字符串
 
```java
    public static String reverseString(String s) {
        return new StringBuilder(s).reverse().toString();
    }
```

[⬆ 返回顶部](#目录)

### 字符串转时间

```java
    public static Date stringToDate(String date, String format) throws ParseException {
        SimpleDateFormat simpleDateFormat = new SimpleDateFormat(format);
        return simpleDateFormat.parse(date);
    }
```

[⬆ 返回顶部](#目录)

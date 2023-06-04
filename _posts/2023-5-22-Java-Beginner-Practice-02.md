---
layout:     post
title:     Java初学实践02
subtitle:  基础的学生信息管理系统
date:       2023-5-22
author:     Draper-crypto
header-img: img/blogimg/post-bg-e2e-ux.jpg
catalog: true
tags:
    - Java
    - 学习笔记
---

# 一、任务说明

1. 使用 Java 编写一个基础的学生信息管理系统
2. 可以连接到 MySQL 数据库，并支持以下功能:
   - 增加学生记录
   - 删除学生记录
   - 修改学生记录
   - 查询学生记录
   - 退出程序

# 二、代码实现

1. 源代码

```java
import java.sql.*;
import java.util.Scanner;

public class Student {
    private String name;
    private int age;
    private String gender;
    private String studentId;

    public Student(String name, int age, String gender, String studentId) {
        this.name = name;
        this.age = age;
        this.gender = gender;
        this.studentId = studentId;
    }

    // 返回姓名
    public String getName() {
        return name;
    }

    // 返回年龄
    public int getAge() {
        return age;
    }

    // 返回性别
    public String getGender() {
        return gender;
    }

    // 返回学生ID
    public String getStudentId() {
        return studentId;
    }
}

class StudentManager {
    private static final String DB_URL = "jdbc:mysql://localhost:3306/mydatabase"; // 数据库URL地址
    private static final String DB_USER = "root"; // 数据库用户名
    private static final String DB_PASSWORD = "#####"; // 数据库密码

    public static void main(String[] args) {
        Connection conn = null;
        Statement stmt = null;
        ResultSet rs = null;

        try {
            // 连接到数据库
            conn = DriverManager.getConnection(DB_URL, DB_USER, DB_PASSWORD);

            // 创建一个Statement对象
            stmt = conn.createStatement();

            Scanner scanner = new Scanner(System.in);

            while (true) {
                // 输出菜单选项
                System.out.println("请选择要执行的操作：");
                System.out.println("1. 增加学生记录");
                System.out.println("2. 删除学生记录");
                System.out.println("3. 修改学生记录");
                System.out.println("4. 查询学生记录");
                System.out.println("5. 退出程序");

                int choice = scanner.nextInt();

                if (choice == 1) {
                    // 插入一条新的学生记录
                    System.out.println("请输入学生姓名：");
                    String name = scanner.next();
                    if (!isValidName(name)) {
                        System.out.println("输入的姓名不合法，请重新输入！");
                        continue;
                    }
                    System.out.println("请输入学生年龄：");
                    int age = scanner.nextInt();
                    if (!isValidAge(age)) {
                        System.out.println("输入的年龄不合法，请重新输入！");
                        continue;
                    }
                    System.out.println("请输入学生性别（男/女）：");
                    String gender = scanner.next();
                    if (!isValidGender(gender)) {
                        System.out.println("输入的性别不合法，请重新输入！");
                        continue;
                    }
                    System.out.println("请输入学生学号：(学号应为10位纯数字)");
                    String studentId = scanner.next();
                    if (!isValidStudentId(studentId)) {
                        System.out.println("输入的学号不合法，请重新输入！");
                        continue;
                    }

                    // 创建一个Student对象并使用PreparedStatement插入到数据库中
                    Student student = new Student(name, age, gender, studentId);
                    String sql = "INSERT INTO students (name, age, gender, student_id) VALUES (?, ?, ?, ?)";
                    PreparedStatement pstmt = conn.prepareStatement(sql);
                    pstmt.setString(1, student.getName());
                    pstmt.setInt(2, student.getAge());
                    pstmt.setString(3, student.getGender());
                    pstmt.setString(4, student.getStudentId());
                    pstmt.executeUpdate();

                    System.out.println("学生记录已成功插入！");
                } else if (choice == 2) {
                    // 删除学生记录
                    System.out.println("请输入要删除的学生姓名：");
                            String name = scanner.next();

                    // 使用PreparedStatement删除数据库中的学生记录
                    String sql = "DELETE FROM students WHERE name = ?";
                    PreparedStatement pstmt = conn.prepareStatement(sql);
                    pstmt.setString(1, name);
                    int count = pstmt.executeUpdate();

                    if (count == 0) { // 如果删除的记录数为0，则说明数据库中不存在该学生记录
                        System.out.println("数据库中不存在该学生记录，请重新输入！");
                    } else {
                        System.out.println("学生记录已成功删除！");
                    }
                } else if (choice == 3) {
                    // 更新学生记录
                    System.out.println("请输入要修改的学生姓名：");
                    String name = scanner.next();

                    // 使用PreparedStatement查询要修改的学生记录
                    String sql = "SELECT * FROM students WHERE name = ?";
                    PreparedStatement pstmt = conn.prepareStatement(sql);
                    pstmt.setString(1, name);
                    rs = pstmt.executeQuery();

                    if (!rs.next()) { // 如果查询结果集为空，则说明数据库中不存在该学生记录
                        System.out.println("数据库中不存在该学生记录，请重新输入！");
                    } else {
                        int age = rs.getInt("age");

                        System.out.println("请输入学生新的年龄：");
                        age = scanner.nextInt();
                        if (!isValidAge(age)) {
                            System.out.println("输入的年龄不合法，请重新输入！");
                            continue;
                        }

                        // 使用PreparedStatement更新数据库中的学生记录
                        sql = "UPDATE students SET age = ? WHERE name = ?";
                        pstmt = conn.prepareStatement(sql);
                        pstmt.setInt(1, age);
                        pstmt.setString(2, name);
                        pstmt.executeUpdate();

                        System.out.println("学生记录已成功修改！");
                    }
                } else if (choice == 4) {
                    // 查询学生记录
                    String sql = "SELECT * FROM students";
                    rs = stmt.executeQuery(sql);

                    // 输出查询结果
                    while (rs.next()) {
                        String name = rs.getString("name");
                        int age = rs.getInt("age");
                        String gender = rs.getString("gender");
                        String studentId = rs.getString("student_id");

                        // 创建一个Student对象并输出学生信息
                        Student s = new Student(name, age, gender, studentId);
                        System.out.println("姓名：" + s.getName() + "，年龄：" + s.getAge() + "，性别：" + s.getGender() + "，学号：" + s.getStudentId());
                    }
                } else if (choice == 5) {
                    // 退出程序
                    break;
                } else {
                    System.out.println("无效的选择，请重新输入！");
                }
            }
        } catch (SQLException e) {
            e.printStackTrace();
        } finally {
            // 关闭连接
            try {
                if (rs != null) {
                    rs.close();
                }
                if (stmt != null) {
                    stmt.close();
                }
                if (conn != null) {
                    conn.close();
                }
            } catch (SQLException e) {
                e.printStackTrace();
            }
        }
    }

    // 判断姓名是否合法
    private static boolean isValidName(String name) {
        return name.matches("[\\u4E00-\\u9FA5]+");
    }

    // 判断年龄是否合法
    private static boolean isValidAge(int age) {
        return age >= 0 && age <= 150;
    }

    // 判断性别是否合法
    private static boolean isValidGender(String gender) {
        return gender.equals("男")
                || gender.equals("女");
    }

    // 判断学号是否合法
    private static boolean isValidStudentId(String studentId) {
        return studentId.matches("\\d{10}");
    }
}
```

2. 运行截图

（1）增加学生记录

![image-20230521230631089](https://typora-img-1301299232.cos.ap-shanghai.myqcloud.com/img/image-20230521230631089.png)

   ![image-20230521230758205](https://typora-img-1301299232.cos.ap-shanghai.myqcloud.com/img/image-20230521230758205.png)

（2）删除学生记录

![image-20230521231003255](https://typora-img-1301299232.cos.ap-shanghai.myqcloud.com/img/image-20230521231003255.png)

![image-20230521231104376](https://typora-img-1301299232.cos.ap-shanghai.myqcloud.com/img/image-20230521231104376.png)

（3）修改学生记录

![image-20230521231304699](https://typora-img-1301299232.cos.ap-shanghai.myqcloud.com/img/image-20230521231304699.png)

![image-20230521231236569](https://typora-img-1301299232.cos.ap-shanghai.myqcloud.com/img/image-20230521231236569.png)

![image-20230521231341929](https://typora-img-1301299232.cos.ap-shanghai.myqcloud.com/img/image-20230521231341929.png)

（4）查询学生记录

![image-20230521231518851](https://typora-img-1301299232.cos.ap-shanghai.myqcloud.com/img/image-20230521231518851.png)

（5）退出程序

![image-20230521231606919](https://typora-img-1301299232.cos.ap-shanghai.myqcloud.com/img/image-20230521231606919.png)

（6）校验功能

![image-20230521233319792](https://typora-img-1301299232.cos.ap-shanghai.myqcloud.com/img/image-20230521233319792.png)

![image-20230521233259094](https://typora-img-1301299232.cos.ap-shanghai.myqcloud.com/img/image-20230521233259094.png)

![image-20230521233352989](https://typora-img-1301299232.cos.ap-shanghai.myqcloud.com/img/image-20230521233352989.png)

![image-20230521233424718](https://typora-img-1301299232.cos.ap-shanghai.myqcloud.com/img/image-20230521233424718.png)

![image-20230521233444915](https://typora-img-1301299232.cos.ap-shanghai.myqcloud.com/img/image-20230521233444915.png)

# 三、代码解释

1.`Student` 类

（1）代码

```java
public class Student {
    private String name;
    private int age;
    private String gender;
    private String studentId;

    public Student(String name, int age, String gender, String studentId) {
        this.name = name;
        this.age = age;
        this.gender = gender;
        this.studentId = studentId;
    }

    // 返回姓名
    public String getName() {
        return name;
    }

    // 返回年龄
    public int getAge() {
        return age;
    }

    // 返回性别
    public String getGender() {
        return gender;
    }

    // 返回学生ID
    public String getStudentId() {
        return studentId;
    }
}
```

（2）解释

`Student` 类有以下实例变量：

- `name`：表示学生姓名。
- `age`：表示学生年龄。
- `gender`：表示学生性别。
- `studentId`：表示学生学号。

这些变量的类型分别是 `String`、`int` 和 `String`。这个类还有一个构造函数，用于初始化这些变量。此外，它还定义了以下公共方法：

- `getName()`：用于获取学生姓名。
- `getAge()`：用于获取学生年龄。
- `getGender()`：用于获取学生性别。
- `getStudentId()`：用于获取学生学号。

这些方法都返回了对应变量的值。

2.`StudentManager `类

（1）代码

```java
class StudentManager {
    private static final String DB_URL = "jdbc:mysql://localhost:3306/mydatabase"; // 数据库URL地址
    private static final String DB_USER = "root"; // 数据库用户名
    private static final String DB_PASSWORD = "151505"; // 数据库密码

    public static void main(String[] args) {
        Connection conn = null;
        Statement stmt = null;
        ResultSet rs = null;

        try {
            // 连接到数据库
            conn = DriverManager.getConnection(DB_URL, DB_USER, DB_PASSWORD);

            // 创建一个Statement对象
            stmt = conn.createStatement();

            Scanner scanner = new Scanner(System.in);

            while (true) {
                // 输出菜单选项
                System.out.println("请选择要执行的操作：");
                System.out.println("1. 增加学生记录");
                System.out.println("2. 删除学生记录");
                System.out.println("3. 修改学生记录");
                System.out.println("4. 查询学生记录");
                System.out.println("5. 退出程序");

                int choice = scanner.nextInt();

                if (choice == 1) {
                    // 插入一条新的学生记录
                    System.out.println("请输入学生姓名：");
                    String name = scanner.next();
                    if (!isValidName(name)) {
                        System.out.println("输入的姓名不合法，请重新输入！");
                        continue;
                    }
                    System.out.println("请输入学生年龄：");
                    int age = scanner.nextInt();
                    if (!isValidAge(age)) {
                        System.out.println("输入的年龄不合法，请重新输入！");
                        continue;
                    }
                    System.out.println("请输入学生性别（男/女）：");
                    String gender = scanner.next();
                    if (!isValidGender(gender)) {
                        System.out.println("输入的性别不合法，请重新输入！");
                        continue;
                    }
                    System.out.println("请输入学生学号：(学号应为10位纯数字)");
                    String studentId = scanner.next();
                    if (!isValidStudentId(studentId)) {
                        System.out.println("输入的学号不合法，请重新输入！");
                        continue;
                    }

                    // 创建一个Student对象并使用PreparedStatement插入到数据库中
                    Student student = new Student(name, age, gender, studentId);
                    String sql = "INSERT INTO students (name, age, gender, student_id) VALUES (?, ?, ?, ?)";
                    PreparedStatement pstmt = conn.prepareStatement(sql);
                    pstmt.setString(1, student.getName());
                    pstmt.setInt(2, student.getAge());
                    pstmt.setString(3, student.getGender());
                    pstmt.setString(4, student.getStudentId());
                    pstmt.executeUpdate();

                    System.out.println("学生记录已成功插入！");
                } else if (choice == 2) {
                    // 删除学生记录
                    System.out.println("请输入要删除的学生姓名：");
                            String name = scanner.next();

                    // 使用PreparedStatement删除数据库中的学生记录
                    String sql = "DELETE FROM students WHERE name = ?";
                    PreparedStatement pstmt = conn.prepareStatement(sql);
                    pstmt.setString(1, name);
                    int count = pstmt.executeUpdate();

                    if (count == 0) { // 如果删除的记录数为0，则说明数据库中不存在该学生记录
                        System.out.println("数据库中不存在该学生记录，请重新输入！");
                    } else {
                        System.out.println("学生记录已成功删除！");
                    }
                } else if (choice == 3) {
                    // 更新学生记录
                    System.out.println("请输入要修改的学生姓名：");
                    String name = scanner.next();

                    // 使用PreparedStatement查询要修改的学生记录
                    String sql = "SELECT * FROM students WHERE name = ?";
                    PreparedStatement pstmt = conn.prepareStatement(sql);
                    pstmt.setString(1, name);
                    rs = pstmt.executeQuery();

                    if (!rs.next()) { // 如果查询结果集为空，则说明数据库中不存在该学生记录
                        System.out.println("数据库中不存在该学生记录，请重新输入！");
                    } else {
                        int age = rs.getInt("age");

                        System.out.println("请输入学生新的年龄：");
                        age = scanner.nextInt();
                        if (!isValidAge(age)) {
                            System.out.println("输入的年龄不合法，请重新输入！");
                            continue;
                        }

                        // 使用PreparedStatement更新数据库中的学生记录
                        sql = "UPDATE students SET age = ? WHERE name = ?";
                        pstmt = conn.prepareStatement(sql);
                        pstmt.setInt(1, age);
                        pstmt.setString(2, name);
                        pstmt.executeUpdate();

                        System.out.println("学生记录已成功修改！");
                    }
                } else if (choice == 4) {
                    // 查询学生记录
                    String sql = "SELECT * FROM students";
                    rs = stmt.executeQuery(sql);

                    // 输出查询结果
                    while (rs.next()) {
                        String name = rs.getString("name");
                        int age = rs.getInt("age");
                        String gender = rs.getString("gender");
                        String studentId = rs.getString("student_id");

                        // 创建一个Student对象并输出学生信息
                        Student s = new Student(name, age, gender, studentId);
                        System.out.println("姓名：" + s.getName() + "，年龄：" + s.getAge() + "，性别：" + s.getGender() + "，学号：" + s.getStudentId());
                    }
                } else if (choice == 5) {
                    // 退出程序
                    break;
                } else {
                    System.out.println("无效的选择，请重新输入！");
                }
            }
        } catch (SQLException e) {
            e.printStackTrace();
        } finally {
            // 关闭连接
            try {
                if (rs != null) {
                    rs.close();
                }
                if (stmt != null) {
                    stmt.close();
                }
                if (conn != null) {
                    conn.close();
                }
            } catch (SQLException e) {
                e.printStackTrace();
            }
        }
    }

    // 判断姓名是否合法
    private static boolean isValidName(String name) {
        return name.matches("[\\u4E00-\\u9FA5]+");
    }

    // 判断年龄是否合法
    private static boolean isValidAge(int age) {
        return age >= 0 && age <= 150;
    }

    // 判断性别是否合法
    private static boolean isValidGender(String gender) {
        return gender.equals("男")
                || gender.equals("女");
    }

    // 判断学号是否合法
    private static boolean isValidStudentId(String studentId) {
        return studentId.matches("\\d{10}");
    }
}
```

（2）解释

`StudentManager` 类是一个包含 `main` 方法的类，它是学生信息管理系统的主要实现。该类首先定义了三个私有静态常量，这些常量分别表示数据库的 URL 地址、用户名和密码。这些常量在程序的其他位置都可以被访问。

在 `main` 方法中，它首先创建了一个 `Connection` 对象，该对象用于连接到 MySQL 数据库。然后，它创建了一个 `Statement` 对象，用于执行 SQL 语句。接下来，它使用一个 `while` 循环来显示菜单选项、读取用户输入并执行相应的操作。具体来说，它可以执行以下操作：

- 增加学生记录
- 删除学生记录
- 修改学生记录
- 查询学生记录
- 退出程序

对于每个操作，代码会提示用户输入相应的信息，并使用 `PreparedStatement` 将数据插入到数据库中。在查询学生记录时，代码会执行一个 `SELECT` 语句，并使用 `ResultSet` 对象来遍历结果集。最后，代码会关闭连接和资源。

此外，`StudentManager` 类还包含了四个私有静态方法，用于判断学生信息的合法性。这些方法分别是：

- `isValidName(String name)`：用于判断学生姓名是否合法。
- `isValidAge(int age)`：用于判断学生年龄是否合法。
- `isValidGender(String gender)`：用于判断学生性别是否合法。
- `isValidStudentId(String studentId)`：用于判断学生学号是否合法。

这些方法都返回一个布尔值，表示学生信息是否合法。这些方法的实现分别使用了正则表达式或简单的逻辑运算。

# 四、总结

本代码实现了基本的增加、删除、改正的功能；将学生信息的合法性判断封装成了四个静态方法，可以在不同的地方重复使用，提高代码的复用性；使用了 `Connection` 和 `Statement` 对象连接到了 MySQL 数据库，并使用了 `PreparedStatement` 执行 SQL 语句。

本代码的缺点也十分明显，虽然这段代码使用了 `PreparedStatement` 来避免 SQL 注入攻击，但是它没有对用户输入进行任何的校验。代码只实现了基本的增删改查功能，如果需要添加其他功能，如按照成绩排序等，代码结构可能需要进行较大的调整，可拓展性较差。

总体来说，这段代码仅实现了一个简单的学生信息管理系统，结构清晰，代码易于理解。但是，它还存在一些安全性和可扩展性问题，需要进一步优化。

# 国内平台创作链接

👉知乎：[点击转跳](https://zhuanlan.zhihu.com/p/631115016)

👉CSDN：[点击转跳](https://blog.csdn.net/Suprman88/article/details/130798706)


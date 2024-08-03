---
title: Lombok 笔记
date: 2023-12-29 15:49:43
categories: Java
tags:
- Lombok
---

```java
import lombok.*;
import lombok.extern.slf4j.Slf4j;

// 类的所有字段生成 get 和 set 方法
@Getter
@Setter
// 生成 toString 方法, 默认是 Student(name=小明, age=18)
@ToString
// 生成 equals 和 hashCode 方法
@EqualsAndHashCode
// 生成一个无参数的构造方法
@NoArgsConstructor
// 包括：@Log, @Log4j, @Log4j2, @Slf4j, @JBossLog 等
@Slf4j
public class Student {
    private String name;
    // 不会为 final 生成 set 方法
    private final int age = 18;

    public static void main(String[] args) {
        log.info("message");
    }
}

// includeFieldNames: 是否在输出中包含字段名
// exclude: 排除某些字段
// of: 要在输出中显示的字段
// callSuper：是否调用超类的 toString 方法
@ToString(includeFieldNames = false, exclude = "age", callSuper = true)
// doNotUseGetters: 是否直接使用字段值而非调用 get 方法
@EqualsAndHashCode(doNotUseGetters = true, exclude = "age")
// 生成一个构造方法, 标记为 final 和 @NonNull 的字段会被作为参数
@RequiredArgsConstructor
class Teacher {
    // 只为某个字段生成 get 和 set 方法
    @Getter
    @Setter
    private String name;
    @NonNull
    private int age;
}

// get 方法的访问级别是 protected
@Getter(AccessLevel.PROTECTED)
@Setter
// 生成一个包含所有字段的构造方法
@AllArgsConstructor
// age 不会被包含在 equals 和 hashCode 方法中
@EqualsAndHashCode(onlyExplicitlyIncluded = true)
class Book {
    @EqualsAndHashCode.Include
    private String name;
    private int age;
}

// 将未初始化的 final 字段初始化为其默认值（0、false、null等）
@NoArgsConstructor(force = true)
class Red {
    private final String name;
    private final int age = 18;
}

// 生成一个静态的工厂方法
@RequiredArgsConstructor(staticName = "of")
class Blue {
    @NonNull
    private int age;
}

// 改变生成的构造方法的访问级别
@AllArgsConstructor(access = AccessLevel.PROTECTED)
class Pink {

}

// 相当于同时使用了 @Getter 、@Setter 、@RequiredArgsConstructor、@ToString、@EqualsAndHashCode
@Data
class Yellow {
    private String name;
    private final int age;
}

// 生成了一个名为 create() 静态实体类生成方法，同时私有化了无参构造器
@Data(staticConstructor = "create")
class Purple {

    private String name;
}

// 某个字段不想生成 get/set 方法，或者是 toString() 、equals() 、hashCode() 方法
@Data
class Orange {
    @Getter(value = AccessLevel.NONE)
    private String name;

    @Setter(value = AccessLevel.NONE)
    private String title;

    @ToString.Exclude
    private int age;

    @EqualsAndHashCode.Exclude
    private String email;
}

// 生成全参构造器和 builder
@Data
@Builder
class White {
    private String name;
    private int age;

}

// 通过 Builder 模式创建 User 对象
@Builder
@ToString
class User {
    private String name;
    private int age;
    private String email;

    public static void main(String[] args) {
        User tom = User.builder()
                .name("TOM")
                .age(11)
                .email("tom@qq.com")
                .build();
        System.out.println(tom);
    }
}

@ToString
class Cat {
    private String name;
    private int age;
    private String email;

    // 控制哪些字段需要在 builder 中出现
    @Builder
    public Cat(String name) {
        this.name = name;
        // build 默认值
        this.email = "mimi@qq.com";
    }

    public static void main(String[] args) {
        Cat mimi = Cat.builder().name("mimi").build();
        System.out.println(mimi);

        // 未设值, 字段的值就会默认为 null
        Cat build = Cat.builder().build();

        test();
    }

    // 不用 try catch exception
    @SneakyThrows
    private static void test() {
        Class.forName("User");
    }
}

// 创建不可变类
// 为所有字段添加 private final 修饰符
// 生成所有字段的 Getter 方法, 因为字段是 final 的，所以没有 Setter 方法
// @Value 就是 @Getter @FieldDefaults(makeFinal = true, level = AccessLevel.PRIVATE) @AllArgsConstructor @EqualsAndHashCode @ToString
@Value
class Point {
    private int x;
}
```
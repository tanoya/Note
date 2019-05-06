# 关于持久化的Object增加字段进行序列化

我们会将一些数据对象持久化到数据库中，但是我们需要修改已经持久化到数据库中的对象数据结构，此时如果只是单纯的增加字段，是可以的。
*例如*
```
package com.toy;

import com.miui.global.kit.util.JSONUtils;

public class Application {
    public static void main(String[] args) {
        System.out.println("hello, world!");

//        Older older = new Older();
//        older.setAge(100);
//        older.setName("Hello");
//        try {
//            String str = JSONUtils.toJSONString(older);
//
//            Newer newer = JSONUtils.toInstance(str, Newer.class);
//            System.out.println("sout");
//
//        } catch (Exception e) {
//            System.out.println("error!");
//        }

        Newer newer = new Newer();
        newer.setAge(100);
        newer.setName("Hello");
        newer.setSchool("sanZhong");

        Meta son = new Meta();
        son.setSon("hello");
        newer.setSon(son);


        try {
            String str = JSONUtils.toJSONString(newer);

            Older older = JSONUtils.toInstance(str, Older.class);
            System.out.println("sout");

        } catch (Exception e) {
            System.out.println("error!");
        }

    }


    private static class Older{
        private int age;
        private String name;

        public int getAge() {
            return age;
        }

        public void setAge(int age) {
            this.age = age;
        }

        public String getName() {
            return name;
        }

        public void setName(String name) {
            this.name = name;
        }
    }

    private static class Newer{
        private int age;
        private String name;
        private String school;
        private Meta son;

        public int getAge() {
            return age;
        }

        public void setAge(int age) {
            this.age = age;
        }

        public String getName() {
            return name;
        }

        public void setName(String name) {
            this.name = name;
        }

        public String getSchool() {
            return school;
        }

        public void setSchool(String school) {
            this.school = school;
        }

        public Meta getSon() {
            return son;
        }

        public void setSon(Meta son) {
            this.son = son;
        }
    }

    private static class Meta{
        private String son;

        public String getSon() {
            return son;
        }

        public void setSon(String son) {
            this.son = son;
        }
    }
}

```
经实验，代码中的这两种转换都是可以的，不会有任何问题，这也是为我们增加字段增加了理论依据。
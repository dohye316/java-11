# java-11
零钱通 项目
项目-零钱通
项目需求说明
使用java开发零钱通项目，可以完成收益入账，消费，查看明细，推出系统等功能
先完成基本功能
再实现改进
1.用户输入4退出时，给出提示“你确定要退出吗？y/n",必须输入正确的y/n,否则循环输入指令，直到输入y或者n。
2.在收益入账和消费时，判断金额是否合理，并给出相应的提示。
3.将面向过程的代码修改成面向对象的方法，编写SmallChanageSysOOP.java类，并使用SmallChanageSysApp完成调试。

package com.hspedu.encapsulate;


//import java.util.Scanner;

//import com.sun.java_cup.internal.runtime.Scanner;


import java.text.SimpleDateFormat;
import java.util.Date;
import java.util.Scanner;

public class SmallChanageSys {
    //先过程编程再oop
    //1.0
    public static void main(String[] args) {
        //化繁为简
        //1.先完成显示菜单，并可以选择菜单，给出对应提示
        //设计定义相关的变量
        //2.完成零钱通明细
        //老韩的思路1.可以把收益入账和消费，保存到数组2.可以使用对象3.简单的话可以使用String拼接
        //完成收益入账，完成功能驱动程序员增加新的变化和代码
        String details = "--------------零钱通明细----------------";
        double money = 0;
        double balance = 0;
        double mo = 0;
        String note = "";
        Date date = null;//date java.util类型
        SimpleDateFormat sdf = new SimpleDateFormat("yyyy-MM-dd HH:mm");//可以用于日期格式化的
        boolean loop = true;
        Scanner scanner = new Scanner(System.in);
        //4.消费
        //5.退出
        int key ;
        do{
            System.out.println("===========零钱通菜单============");
            System.out.println("\t\t\t1.零钱通明细");
            System.out.println("\t\t\t2.收益入账");
            System.out.println("\t\t\t3.消费");
            System.out.println("\t\t\t4.退      出");
            System.out.println("请选择（1-4）：");
            key = scanner.nextInt();

            //使用switch 分支控制
            switch (key){
                case 1:
                    System.out.println(details);
                     break;
                case 2:
                    System.out.println("2收益入账");
                    money = scanner.nextDouble();
                    //money的值范围应该校验
                    balance += money;
                    //拼接收益入账信息到 detail
                    date = new Date();//获取当前日期
                    details +="\n收益入账\t+"+money +"\t"+ sdf.format(date) + "\t" + balance;

                    break;
                case 3:

                    System.out.println("3.消费金额");
                    money = scanner.nextDouble();
                    //money 的值范围应该校验
                    System.out.println("消费说明");
                    note = scanner.next();
                    balance -=money;
                    //拼接信息到details



                    //拼接收益入账信息到 detail

                    date = new Date();//获取当前日期
                    details +="\n" + note + "\t-"+money +"\t"+ sdf.format(date) + "\t" + balance;
                    break;
                case 4:
                    //用户输入4退出时，给出提示“你确定要退出吗？y/n”，“必须输入正确的y/n"
                    //否则循环输入指令，直到输入y或者n
                    //老韩思路分析
                    //1.定义一个变量choice,接收用户的输入
                    //2.使用while + break 来处理接收到的输入时 y 或者 n
                    //3.建议一段代码，完成一个小功能，尽量不要混在一起

                    String choice = " ";

//                    if ("y".equals(choice)) {
//                          loop = false;
//                          break;
//                    }else if ("n".equals(choice)) {
//                           break;
//                    }
                    while(true){
                        System.out.println("你确定要退出吗？");
                        choice = scanner.next();
                        if ("y".equals(choice)||"n".equals(choice));
                        break;
                    }
                    if (choice.equals("y")) {
                      loop = false;
                    }
                    break;


                default:
                    System.out.println("选择有误");
            }
        }while(loop);
        System.out.println("已退出了零钱通");








    }
}

========================
OOP版
package com.hspedu.encapsulate;

import java.text.SimpleDateFormat;
import java.util.Date;
import java.util.Scanner;

/**
 * 该类是完成零钱通的各个功能的类
 * 使用oop面向对象编程
 * 将各个功能对应一个方法，
 */
public class SmallChanageSysOOP {
    //化繁为简
    //1.先完成显示菜单，并可以选择菜单，给出对应提示
    //设计定义相关的变量
    //2.完成零钱通明细
    //老韩的思路1.可以把收益入账和消费，保存到数组2.可以使用对象3.简单的话可以使用String拼接
    //完成收益入账，完成功能驱动程序员增加新的变化和代码
    String details = "--------------零钱通明细----------------";
    double money = 0;
    double balance = 0;
    double mo = 0;
    String note = "";
    Date date = null;//date java.util类型
    SimpleDateFormat sdf = new SimpleDateFormat("yyyy-MM-dd HH:mm");//可以用于日期格式化的
    boolean loop = true;
    Scanner scanner = new Scanner(System.in);
    //4.消费
    //5.退出
    int key;



    public void mainMenu() {
        do{
            System.out.println("===========零钱通菜单============");
            System.out.println("\t\t\t1.零钱通明细");
            System.out.println("\t\t\t2.收益入账");
            System.out.println("\t\t\t3.消费");
            System.out.println("\t\t\t4.退      出");
            System.out.println("请选择（1-4）：");
            key = scanner.nextInt();

            //使用switch 分支控制
            switch (key){
                case 1:
                   this.detail();
                    break;
                case 2:
                   this.income();
                    break;
                case 3:

                   this.pay();
                   break;
                case 4:
                  this.exit();
                  break;
                default:
                    System.out.println("您输入有误");
            }
        }while(loop);
    }

    //完成零钱通明细
    public void detail() {
        System.out.println(details);
    }

    public void income() {
        System.out.println("2收益入账");
        money = scanner.nextDouble();
        //money的值范围应该校验
        if (money <= 0 ){
            System.out.println("收益入账金额需要大于 0");
            return;//退出方法不再执行
        }
        balance += money;
        //拼接收益入账信息到 detail
        date = new Date();//获取当前日期
        details += "\n收益入账\t+" + money + "\t" + sdf.format(date) + "\t" + balance;

    }

    public void pay() {
        System.out.println("3.消费金额");
        money = scanner.nextDouble();
        if (money <= 0|| money>balance) {
            System.out.println("你的消费金额应该在0" + balance);
            return;
        }
        //money 的值范围应该校验
        System.out.println("消费说明");
        note = scanner.next();
        balance -= money;
        //拼接信息到details


        //拼接收益入账信息到 detail

        date = new Date();//获取当前日期
        details += "\n" + note + "\t-" + money + "\t" + sdf.format(date) + "\t" + balance;
    }

    public void exit() {
        //用户输入4退出时，给出提示“你确定要退出吗？y/n”，“必须输入正确的y/n"
        //否则循环输入指令，直到输入y或者n
        //老韩思路分析
        //1.定义一个变量choice,接收用户的输入
        //2.使用while + break 来处理接收到的输入时 y 或者 n
        //3.建议一段代码，完成一个小功能，尽量不要混在一起

        String choice = " ";

//                    if ("y".equals(choice)) {
//                          loop = false;
//                          break;
//                    }else if ("n".equals(choice)) {
//                           break;
//                    }
        while (true) {
            System.out.println("你确定要退出吗？");
            choice = scanner.next();
            if ("y".equals(choice) || "n".equals(choice)) ;
            break;
        }
        if (choice.equals("y")) {
            loop = false;
        }

        return;




    }
}class start{
    public static void main(String[] args) {


        SmallChanageSysOOP smallChanageSysOOP = new SmallChanageSysOOP();
        smallChanageSysOOP.mainMenu();
    }
}


练习题：
1.定义一个Person类name age job 初始化PErson对象数组，有三个person对象
按照age从大到小进行排序
package com.hspedu.encapsulate.Homework_ofOOP;

public class Homework01 {
    public static void main(String[] args) {
       //初始化Person 对象数组，有三个person对象
        Person[] people = new Person[3];
        people[0] = new Person("jack",10,"java工程师");
        people[1] = new Person("tom",50,"大数据工程师");
        people[2] = new Person("mary",30,"php工程师");
        //输出当前对象数组
        for(int i = 0; i < people.length; i++){
            System.out.println(people[i] + "\t");
        }
       //使用冒泡排序
        Person temp = null;
        for (int i = 0; i < people.length-1; i++) {
            for (int j = 0; j < people.length-1-i; j++) {
                //如果前面的人的age<后面的人小就交换
                //要求按照名字的长度从小到大   加一个getName().length
                if (people[i].getAge()<people[i+1].getAge()) {
                    people[i] = people[i+1];
                     temp = people[i];
                     people[i+1] = temp;
                }
             }
        }
        System.out.println("效果");
        for(int i = 0; i < people.length; i++){
            System.out.println(people[i] + "\t");
        }
    }
}class Person{
    private String name;
    private int age;
    private String job;

    public Person(String name, int age, String job) {
        this.name = name;
        this.age = age;
        this.job = job;
    }


    @Override
    public String toString() {
        return "Person{" +
                "name='" + name + '\'' +
                ", age=" + age +
                ", job='" + job + '\'' +
                '}';
    }

    public String getName() {
        return name;
    }

    public void setName(String name) {
        this.name = name;
    }

    public int getAge() {
        return age;
    }

    public void setAge(int age) {
        this.age = age;
    }

    public String getJob() {
        return job;
    }

    public void setJob(String job) {
        this.job = job;
    }

    public Object[] arr( ){
             Object []ints = new Object[3];
            ints[0] =  name;
            ints[1] =  age;
            ints[2] =  job;



return ints;

    }
}

四种访问权限：
private              同类
public              同类同包    不同包不同子类
protected            同类同包    子类
无                     同类同包         


package com.hspedu.encapsulate.Homework_ofOOP;

public class Homework03 {
    public static void main(String[] args) {
        System.out.println("======manage======");
        manage manage = new manage("tom", 1500,22,1.2);
        //设置奖金
        manage.setBonus(3000);
        manage.printsalary();
         System.out.println("======nomaltmp=======");
        Nemp nemp  = new Nemp("jakc", 12000, 22, 1.0);

        nemp.printsalary();
    }
}class Emoloyee{
    private String name;
    private double salary;
    private int days;
    private double grade;

    public String getName() {
        return name;
    }

    public void setName(String name) {
        this.name = name;
    }

    public double getSalary() {
        return salary;
    }

    public void setSalary(double salary) {
        this.salary = salary;
    }

    public int getDays() {
        return days;
    }

    public void setDays(int days) {
        this.days = days;
    }

    public double getGrade() {
        return grade;
    }

    public void setGrade(double grade) {
        this.grade = grade;
    }

    public Emoloyee(String name, double salary, int days, double grade) {
        this.name = name;
        this.salary = salary;
        this.days = days;
        this.grade = grade;
    }

    public void printsalary(){
        System.out.println("员工"+getName() +"工资是=" +
                " "+ ( getDays()*getSalary()*getGrade()));
    }
}class  manage extends Emoloyee{
    private double bonus;
    //创建manager对象时，奖金是多少并不是确定的，因为老师在构造器中，不给bonus
    //可以通过setBonus

    public manage(String name, double salary, int days, double grade) {
        super(name, salary, days,grade);

    }

    public double getBonus() {
        return bonus;
    }

    public void setBonus(double bonus) {
        this.bonus = bonus;
    }

    // 方法：重写
    @Override   //因为经理的工资计算方法方式和Employee不一样，所以我们重写
    public void printsalary() {
        System.out.println(getName() +"工资是=" +
                " "+ ( getDays()*getSalary()*getGrade()));

    }
}class Nemp extends Emoloyee{
    //普通员工没有特有的属性


    @Override
    public void printsalary() {
System.out.print("员工");
       super.printsalary();
        //普通员工和Employee输出工资情况一样，所以直接调用父类的printSal()
    }

    public Nemp(String name, double salary, int days, double grade) {
        super(name, salary, days,grade);


    }
}
======manage======
经理tom工资是= 39600.0
======nomaltmp=======
员工jakc工资是= 264000.0


package com.hspedu.encapsulate.Homework_ofOOP;

public class Homewrok05 {
    String name = "Rose";
    Homewrok05(){
        System.out.println("test");//test1
    }
    Homewrok05(String name){
        this.name = name;//修改成john
    }

}class Demo extends Homewrok05{
    String name = "jack";
    Demo(){
        super();
        System.out.println("Demo");//2
    }
    Demo(String s){
        super(s);
    }public void test(){
        System.out.println(super.name);//3Rose 父 5 john
        System.out.println(this.name);//4jack 本 6 jack
    }
    public static  void main(String[]args){
        new Demo().test();//无参
        new Demo("john").test();//匿名

    }
}
test
Demo
Rose
jack
john
jack


package com.hspedu.encapsulate.Homework_ofOOP;

public class Homework06 {
    public static void main(String[] args) {
        CheckingAccount checkingAccount = new CheckingAccount(100000);
        checkingAccount.deposit(10);
        checkingAccount.withdraw(9);

    }
}class BankAccount{
    private double balance;
    public BankAccount(double initialBalance){
        this.balance = initialBalance;
    }
    public void deposit(double amount){
        balance += amount;


    }
    public void withdraw (double amount ){

        balance -= amount;

    }

    public double getBalance() {
        return balance;
    }

    public void setBalance(double balance) {
        this.balance = balance;
    }
//set 和getBalance方法
}class CheckingAccount extends BankAccount{
    public CheckingAccount(double initialBalance) {
        super(initialBalance);
    }

    @Override
    public void deposit(double amount) {
        super.deposit(amount-1);//巧妙的作用了父类的deposit
        //1块钱如银行的账号
    }

    @Override
    public void withdraw(double amount) {
        super.withdraw(amount+1);
    }

编写Doctor类name age job gender sal
相应的getter（）和setter（）方法，5个参数的构造器，重写父类（Object）的equals（）方法；public boolean equals(Object obj) 并判断测试类中创建的两个对象是否相等，相等就是判断属性是否相同
答案：
=========

class Doctor extends Object {
    private String name;
    private int age;
    private String job;
    private char gender;
    private double sal;

    public String getName() {
        return name;
    }

    public void setName(String name) {
        this.name = name;
    }

    public int getAge() {
        return age;
    }

    public void setAge(int age) {
        this.age = age;
    }

    public String getJob() {
        return job;
    }

    public void setJob(String job) {
        this.job = job;
    }

    public char getGender() {
        return gender;
    }

    public void setGender(char gender) {
        this.gender = gender;
    }

    public double getSal() {
        return sal;
    }

    public void setSal(double sal) {
        this.sal = sal;
    }

    public Doctor(String name, int age, String job, char gender, double sal) {
        this.name = name;
        this.age = age;
        this.job = job;
        this.gender = gender;
        this.sal = sal;

    }

    @Override
    public boolean equals(Object obj) {
        if (this == obj) return true;
        //判断obj是否是Doctor类型或子类
        if (!(obj instanceof Doctor)) {
             return false;
        }
        //向下转型，因为obj的运行类型是Doctor或者其子类型
        Doctor doctor =(Doctor)obj;
        return this.name.equals((doctor.name)) && this.age == doctor.age&&
                this.gender == doctor.gender&& this.job.equals(doctor.job)&&this.sal == doctor.sal;
    }

    @Override
    public int hashCode() {
        return Objects.hash(name, age, job, gender, sal);
    }
}
========


==         比较运算符，用于基本数据类型，可以判断值是否相等，用于引用类型，可以判断两个对象是否相等
equals    java类都可以使用equals属于Object   不可以用于基本数据类型，可以用于引用类型，默认是判断两个对象是否相等，但是子类往往重写该方法，比较对象的属性是否相等，比如String integer

================

package com.hspedu.encapsulate.Homework_ofOOP;

public class Homework10 {
    public static void main(String[] args) {

        Person000[] person = new Person000[4];
        person[0] = new Teache("张飞", '男', 30, 5);
//        Person000 p1= new Teache("张飞",'男',30,5);
        person[1] = new Teache("jack", '女', 22, 6);
//      Person000 p2=new Teache("jack",'女',22,6);
        person[2] = new Student("tom", '男', 10, 2155);
//      Person000 p3=new Student ("tom",'男',10,2155);
        person[3] = new Student("saim", '女', 5, 3655);
//      Person000 p4=new Student("saim",'女',5,3655);
        Homework10 homework10 = new Homework10();
        homework10.bubblesort(person);
        System.out.println("效果");
        for(int i = 0; i <  person.length; i++){
            homework10.test(person[i]);
        }

//                System.out.println("老师的信息");
//        System.out.println(person[0]  );
////        p1.play(); p1.teach();
//
//        System.out.println(person[1]);
////        p2.play();p2.teach();
//
//        System.out.println(person[2]);
////        p3.play();p3.study();
//
//        System.out.println(person[3]);
////        p4.play();p4.study();
    }
        public void test(Person000 p){
            if(p instanceof Teache){
                ((Teache)p).teach();
                ((Teache)p).play();
            }else if(p instanceof Student){
                ((Student)p).study();
                ((Student)p).play();
            } else{System.out.println("not");} }




public void bubblesort(Person000[]person){

        for(int i = 0; i < person.length; i++){
            System.out.println(person[i] + "\t");
        }
        //使用冒泡排序
        Person000 temp = null;
        for (int i = 0; i < person.length-1; i++) {
            for (int j = 0; j < person.length-1-i; j++) {
                //如果前面的人的age<后面的人小就交换
                //要求按照名字的长度从小到大   加一个getName().length
                if (person[i].getAge() <  person[i+1].getAge()) {
                    person[i] =  person[i+1];
                     temp = person[i];
                    person[i+1] = temp;
                }
            }
        }
        System.out.println("效果");
        for(int i = 0; i <  person.length; i++){
            System.out.println(  person[i].toString() + "\t");
        }
}

    }
class Student extends Person000{

    private  int stu_id;

    public Student(String name, char sex, int age, int stu_id) {
       super(name,sex, age);
        this.stu_id = stu_id;
    }

    @Override
    public String toString() {
        return "Student{" +
                "stu_id=" + stu_id +
                '}'+ super.toString();

    }

    public int getStu_id() {
        return stu_id;
    }

    public void setStu_id(int stu_id) {
        this.stu_id = stu_id;
    }

    public void study(){
        System.out.println("我承诺，我会好好学习");
    } public void play() {
        super.play();
        System.out.println("学号："+ stu_id);
        System.out.println("爱玩足球");
    }
}class Teache extends Person000{

    private int work_age;

    @Override
    public String toString() {
        return "Teache{" +
                "work_age=" + work_age +
                '}'+ super.toString();
    }

    public Teache (String name, char sex, int age, int work_age) {
       super(name, sex, age);
        this.work_age = work_age;
    }

    public void teach(){
        System.out.println("我承诺，我会认真教学");
    }

    @Override
    public void play() {
        super.play();
        System.out.println("工龄："+work_age);
        System.out.println( "爱玩象棋");
    }
}class Person000{
    private String name;
    private  char sex;
    private  int age;

    public Person000(String name, char sex, int age) {
        this.name = name;
        this.sex = sex;
        this.age = age;
    }public void play(){
        System.out.println("姓名："+name+"\n年龄："+age+"\n性别："+sex);
    }public void study(){

    }public void teach(){

    }

    public String getName() {
        return name;
    }

    public void setName(String name) {
        this.name = name;
    }

    public char getSex() {
        return sex;
    }

    public void setSex(char sex) {
        this.sex = sex;
    }

    public int getAge() {
        return age;
    }

    public void setAge(int age) {
        this.age = age;
    }

    @Override
    public String toString() {
        return "Person000{" +
                "name='" + name + '\'' +
                ", sex=" + sex +
                ", age=" + age +
                '}';
    }
}

多态：方法或对象，具有多种形态，是oop的第三大特征，是建立在封装和继承基础之上，
多态具体体现
1.方法的多态，方法重载，方法的重写
2.对象的多态，对象的编译类型和运行类型可以不一致，编译类型在定义时，就确定，不能变化
对象的运行类型是可以变化的，可以通过getClass()来查看运行类型。
编译类型看定义时=号的左边，运行类型看=号的右边。




java动态绑定机制：
1.当调用对象的方法时，该方法会和对象的内存地址/运行类型绑定
2.当调用对象的属性时，没有动态绑定机制，哪里声明，哪里使用




房屋出租设计
项目设计-程序框架图（分层模式=》当软件比较复杂，需要模式管理）

房屋出租程序框架图
1.系统有哪些类（文件）
2.明确类与类的调用关系

HouseView.java类    界面      //    编写listHouse（）界面
                                            //编写mainMenu方法主菜单
1.显示界面                          //编写addHouse方法接收用户输入
2.接收用户输入                       //编写delHouse方法           //编写findHouse 接收输入id
3.调用其他类完成对房屋的各种操作//updateHouse()接收输入id

HouseService.java类    业务层          //  编写一个方法list（）返回所有的房屋信息
定义一个House【】数组                  //编写方法add（House newHouse ）把新的house对象加入到house数组，返回bool                     //编写方法del（int delld）；完成真正删除任务，返回一个boolean                                                 //编写一个方法find（int findid）返回House对象，没有则返回null
1.相应HouseViewde 调用
2.完成对房屋信息的各种操作（增删改查crud）：create read update delete
House.java类      domain域
1.一个House对象表示一个房屋信息

HouseRentApp.java 
main(){
//创建HouseView对象
//调用该对象，显示主菜单

工具类 Utility
完成获取用户各种输入
准备工具Utility 提高开发效率
在实际开发中，公司都会提供相应的工具类和开发库，可以提高开发效率，程序员也需要能够看懂别人写的代码，并能够正确的调用
1.了解Utility类的使用
2.测试Utility

项目功能实现- 显示主菜单和完成退出软件功能
化繁为简（一个一个功能逐步实现）
说明：实现功能的三部曲 明确完成功能-》思路分析-》代码实现
功能说明
用户打开软件，可以看到主菜单，可以退出软件
思路分析
在HouseView.java中，编写一个方法MianMenu，显示菜单
代码实现：

编写一个mainMenu方法，可以显示主菜单

项目功能实现- 完成删除房屋信息的功能
功能说明： 
编写HouseView 和HouseService

房屋查找功能实现

package com.hspedu.houserent_;

import com.hspedu.houserent_.View.HouseView;

public class HouseRentApp {
    public static void main(String[] args) {
        //创建HouseView对象，并且显示主菜单，是整个程序入口
        new HouseView().mainMenu();

        System.out.println("========房屋出租系统菜单========");



    }
}



package com.hspedu.houserent_.View;

import com.hspedu.houserent_.Service.House;
import com.hspedu.houserent_.Service.HouseService;
import com.hspedu.houserent_.Utility.Utility;

import java.text.SimpleDateFormat;
import java.util.Date;


/**
 *1.显示界面
 * 2.接收用户输入
 * 3.调用HouseService完成对房屋信息的各种操作
 */
public class HouseView {
    //显示菜单
    Date date = null;
    SimpleDateFormat datef = new SimpleDateFormat("yyyy-mm-dd HH:mm");
    private  boolean loop = true;//控制显示菜单
    private char key=' ';//接收用户选择
    private HouseService houseservice = new HouseService(10);//设置数组的大小为10
   //delHouse() 接收输入的id，调用Service 的del方法
    public void delHouse(){
        System.out.println("===========添加房屋===========");
        System.out.println("请输入删除房屋的编号（-1退出）=======");
        int delId = Utility.readInt();
        if (delId == -1){
            System.out.println("===========放弃删除房屋系统=========");
            return;
        }
        System.out.println("请小心选择：");
       char choice = Utility.readConfirmSelection();

        if (choice == 'Y') {
            if (houseservice.del(delId)){
                System.out.println("============删除房屋信息成功==========");
            }else{
                System.out.println("=========房屋编号不全==========");
            }

        }else{
            System.out.println("===============放弃删除================");
        }
    }

    //编写addHouse（）接收输入，创建House对象，调用add方法
    public void addHosue(){
        System.out.println("==========添加房屋==========");
        System.out.println("姓名 ");
        String name = Utility.readString(8);
        System.out.println("电话");
        String phone = Utility.readString(11);
        System.out.println("地址");
        String address= Utility.readString(16);
        System.out.println("月租");
        int rent = Utility.readInt();
        System.out.println("状态");
        String state = Utility.readString(3);
           date = new Date();
        //创建一个新的House对象
        House house = new House(0, name, phone, address, rent, state,datef.format(date));
        if (houseservice.add(house)){
            System.out.println("========添加房屋成功==========");
        }else{
            System.out.println("=========添加错误========");
        }



    }

    //编写listHouse（）显示房屋列表
    public void listHouse(){
        System.out.println("===========房屋列表==========");
        System.out.println("编写\t\t房主\t\t电话\t\t地址\t\t月租\t\t状态");
        House[]house =houseservice.list();
        for (int i = 0; i < house.length; i++) {
            if (house[i]==null){
                break;
            }else{
            System.out.println(house[i]);}
        }
        System.out.println("房屋列表显示完毕");
    }
    public void exit(){
        char c =Utility.readConfirmSelection();
        if (c=='Y'){
            loop = false;
        }
    }
    //根据id修改房屋信息
    public void update(){
        System.out.println("============修改房屋信息============");
        System.out.println("============请选择待修改房屋编号==========");
        int i = Utility.readInt();
        if (i == -1){
            System.out.println("=============你放弃修改房屋信息=============");
            return;
        }
        House byId = houseservice.findById(i);
        if (byId == null){
            System.out.println("===========你要修改的房屋信息不存在===========");
            return;
        }
        System.out.println("姓名（"+byId.getName()+")");
        String name = Utility.readString(8,"请输入少于8的字符串");
        if (!"".equals(name)){
            byId.setName(name);
        }
        System.out.println("电话（"+byId.getPhone()+")");
        String phone = Utility.readString(12,"请输入12位的电话号码");
        if (!"".equals(phone)){
            byId.setName(phone);}

        System.out.println("地址（"+byId.getAddress()+")");
        String address = Utility.readString(12,"请输入12位的电话号码");
        if (!"".equals(address)){
            byId.setName(address);}
        System.out.println("租金（"+byId.getRent()+")");
        int zujin = Utility.readInt(8);
        if (!"".equals(zujin)){
            byId.setRent(zujin);}
        System.out.println("状态（"+byId.getState()+")");
        String state = Utility.readString(12,"请输入已租或未租");
        if (!"".equals(state)){
            byId.setState(state);}
    }
    public void findHouse(){
        System.out.println("=========查找房屋信息=========");
        System.out.println("请输入：");
        int findId = Utility.readInt();
        House byId = houseservice.findById(findId);
        if (byId != null){
            System.out.println(byId);
        }else{
            System.out.println("==========查找房屋信息id不存在==========");
        }

    }

    //显示主菜单
    public void mainMenu(){
        do {
            System.out.println("----------房屋出租系统------------");
            System.out.println("\t\t\t1.新增房源");
            System.out.println("\t\t\t2.查找房源");
            System.out.println("\t\t\t3.删除房屋");
            System.out.println("\t\t\t4.修改房屋信息");
            System.out.println("\t\t\t5.房屋列表");
            System.out.println("\t\t\t6.退     出");
            System.out.println("请输入1-6");
            key = Utility.readChar();
            switch (key) {
                case '1':
                    System.out.println("新增");
                    addHosue();
                    break;
                case '2':
                    System.out.println("查找");
                    findHouse();
                    break;
                case '3':
                    System.out.println("删除");
                    delHouse();
                    break;
                case '4':
                    System.out.println("修改");
                    update();
                    break;
                case '5':
                    System.out.println("房 屋 列 表");
                    listHouse();
                    break;
                case '6':


                    System.out.println("退出");
                    exit();
                    break;
            }

        } while (loop);


    }
}


package com.hspedu.houserent_.Service;
//HouseService.java类    业务层          //  编写一个方法list（）返回所有的房屋信息
//        定义一个House【】数组
//        1.相应HouseViewde 调用
//        2.完成对房屋信息的各种操作（增删改查crud）：create read update delete
//        House.java类      domain域
//        1.一个House对象表示一个房屋信息


public class HouseService {
    private House[]house;//保存House对象

    private  int houseNums;//记录当前有多少个房屋信息
    private  int idCounteer= 1; //记录当前的id增长
    //构造器

    public HouseService(int size) {
        house= new House[size];


    }
    //find方法，返回House对象或者null
    public House findById(int findId){
        //遍历数组
        for (int i = 0; i < houseNums; i++) {
            if (findId == house[i].getId()){
                return house[i];
            }
        }
            return null;
    }
    //del方法，删除一个房屋信息
    public boolean del(int delId) {
        //应当先找到要删除的房屋信息对应的下标
        //强调，一定要搞清楚 下标和房屋的编号不是一回事
        int index = -1;
        for (int i = 0; i < houseNums; i++) {
            if (delId == house[i].getId()) {//要删除的房屋对应的id，在数组下标为i的元素
                //id是数组下标为i的元素
                index = i;//就使用index记录i


            }
        }
        if (index == -1) {//说明delId 在数组中不存在
            return false;
        }
            //如果找到，这里
            for (int i = index; i < houseNums - 1; i++) {
                house[i] = house[i + 1];


            }
        house[--houseNums] = null;//把当前存在的房屋信息的最后一个设置null

        return true;


    }
public House[]list(){
    return house;
}public boolean add(House newHouse){
        //判断是否还可以继续添加(我们暂时不考虑)
        if (houseNums >= house.length){
            //不能在添加

            System.out.println("数组已满，已经添加数组。。。");
            return false;
        }
        house[houseNums]= newHouse;
        houseNums++;
        //我们程序员需要设计一个id自增长的机制，然后鞥新newHouse的id
        newHouse.setId(idCounteer++);
        return true;
    }

}


package com.hspedu.houserent_.Service;

/**
 * House 的对象表示一个房屋信息
 */
public class House {
    //
    private String days;
    private int id;
    private String name;
    private String phone;
    private  String address;
    private int rent;
    private String state;

    public House(int id, String name, String phone, String address, int rent, String state,String days) {
        this.id = id;
        this.name = name;
        this.phone = phone;
        this.address = address;
        this.rent = rent;
        this.state = state;
        this.days = days;
    }

    public String getDays() {
        return days;
    }

    public void setDays(String days) {
        this.days = days;
    }

    public int getId() {
        return id;
    }

    public void setId(int id) {
        this.id = id;
    }

    public String getName() {
        return name;
    }

    public void setName(String name) {
        this.name = name;
    }

    public String getPhone() {
        return phone;
    }

    public void setPhone(String phone) {
        this.phone = phone;
    }

    public String getAddress() {
        return address;
    }

    public void setAddress(String address) {
        this.address = address;
    }

    public int getRent() {
        return rent;
    }

    public void setRent(int rent) {
        this.rent = rent;
    }

    public String getState() {
        return state;
    }

    public void setState(String state) {
        this.state = state;
    }//为了方便的输出对象信息，我们实现toString方法

    @Override
    public String toString() {
        return
                 id +
                "\t\t" + name +
                "\t\t" + phone +
                "\t\t" + address +
                "\t\t" + rent +
                "\t\t" + state +
                "\t\t" + days;
    }
}






package com.hspedu.houserent_.Utility;


/**
	工具类的作用:
	处理各种情况的用户输入，并且能够按照程序员的需求，得到用户的控制台输入。
*/

import java.util.*;
/**

	
*/
public class Utility {
	//静态属性。。。
    private static Scanner scanner = new Scanner(System.in);

    
    /**
     * 功能：读取键盘输入的一个菜单选项，值：1——5的范围
     * @return 1——5
     */
	public static char readMenuSelection() {
        char c;
        for (; ; ) {
            String str = readKeyBoard(1, false);//包含一个字符的字符串
            c = str.charAt(0);//将字符串转换成字符char类型
            if (c != '1' && c != '2' && 
                c != '3' && c != '4' && c != '5') {
                System.out.print("选择错误，请重新输入：");
            } else break;
        }
        return c;
    }

	/**
	 * 功能：读取键盘输入的一个字符
	 * @return 一个字符
	 */
    public static char readChar() {
        String str = readKeyBoard(1, false);//就是一个字符
        return str.charAt(0);
    }
    /**
     * 功能：读取键盘输入的一个字符，如果直接按回车，则返回指定的默认值；否则返回输入的那个字符
     * @param defaultValue 指定的默认值
     * @return 默认值或输入的字符
     */
    
    public static char readChar(char defaultValue) {
        String str = readKeyBoard(1, true);//要么是空字符串，要么是一个字符
        return (str.length() == 0) ? defaultValue : str.charAt(0);
    }
	
    /**
     * 功能：读取键盘输入的整型，长度小于2位
     * @return 整数
     */
    public static int readInt() {
        int n;
        for (; ; ) {
            String str = readKeyBoard(10, false);//一个整数，长度<=2位
            try {
                n = Integer.parseInt(str);//将字符串转换成整数
                break;
            } catch (NumberFormatException e) {
                System.out.print("数字输入错误，请重新输入：");
            }
        }
        return n;
    }
    /**
     * 功能：读取键盘输入的 整数或默认值，如果直接回车，则返回默认值，否则返回输入的整数
     * @param defaultValue 指定的默认值
     * @return 整数或默认值
     */
    public static int readInt(int defaultValue) {
        int n;
        for (; ; ) {
            String str = readKeyBoard(10, true);
            if (str.equals("")) {
                return defaultValue;
            }
			
			//异常处理...
            try {
                n = Integer.parseInt(str);
                break;
            } catch (NumberFormatException e) {
                System.out.print("数字输入错误，请重新输入：");
            }
        }
        return n;
    }

    /**
     * 功能：读取键盘输入的指定长度的字符串
     * @param limit 限制的长度
     * @return 指定长度的字符串
     */

    public static String readString(int limit) {
        return readKeyBoard(limit, false);
    }

    /**
     * 功能：读取键盘输入的指定长度的字符串或默认值，如果直接回车，返回默认值，否则返回字符串
     * @param limit 限制的长度
     * @param defaultValue 指定的默认值
     * @return 指定长度的字符串
     */
	
    public static String readString(int limit, String defaultValue) {
        String str = readKeyBoard(limit, true);
        return str.equals("")? defaultValue : str;
    }


	/**
	 * 功能：读取键盘输入的确认选项，Y或N
	 * 将小的功能，封装到一个方法中.
	 * @return Y或N
	 */
    public static char readConfirmSelection() {
        System.out.println("请输入你的选择(Y/N)");
        char c;
        for (; ; ) {//无限循环
        	//在这里，将接受到字符，转成了大写字母
        	//y => Y n=>N
            String str = readKeyBoard(1, false).toUpperCase();
            c = str.charAt(0);
            if (c == 'Y' || c == 'N') {
                break;
            } else {
                System.out.print("选择错误，请重新输入：");
            }
        }
        return c;
    }

    /**
     * 功能： 读取一个字符串
     * @param limit 读取的长度
     * @param blankReturn 如果为true ,表示 可以读空字符串。 
     * 					  如果为false表示 不能读空字符串。
     * 			
	 *	如果输入为空，或者输入大于limit的长度，就会提示重新输入。
     * @return
     */
    private static String readKeyBoard(int limit, boolean blankReturn) {
        
		//定义了字符串
		String line = "";

		//scanner.hasNextLine() 判断有没有下一行
        while (scanner.hasNextLine()) {
            line = scanner.nextLine();//读取这一行
           
			//如果line.length=0, 即用户没有输入任何内容，直接回车
			if (line.length() == 0) {
                if (blankReturn) return line;//如果blankReturn=true,可以返回空串
                else continue; //如果blankReturn=false,不接受空串，必须输入内容
            }

			//如果用户输入的内容大于了 limit，就提示重写输入  
			//如果用户如的内容 >0 <= limit ,我就接受
            if (line.length() < 1 || line.length() > limit) {
                System.out.print("输入长度（不能大于" + limit + "）错误，请重新输入：");
                continue;
            }
            break;
        }

        return line;
    }
}























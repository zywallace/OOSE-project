# Yu Zhao
# JHED: yzhao86

1. (1) If the code between the assignment to the temperate variable and the use of the temperate variable changed the value of the expression, this refactoring would fail.
   ```
   int quantity = 300;
   double itemPrice = 2.5;

   double calculateTotal() {
       if (basePrice() > 1000) {
           itemPrice = 5;
           return basePrice() * 0.95;
       } else {
           return basePrice() * 0.98;
       }
   }

   double basePrice() {
       return quantity * itemPrice;
   }
   ```
   Like above, the result would be 1470 while the original one should return 735.

   (2) Private field would make this refactoring problematic. For example:
   ```
   class People{
       private String name, phoneNumber;
       public void setInfo(String num, String name){
           setPhoneNumber(num);
           setName(name);
       }
       private void setPhoneNumber(String num){
           phoneNumber = num;
       }
   }
   //after refactoring
   class People{
       private String name;
       private Phone phone;
       public void setInfo(String num, String name){
           phone.setPhoneNumber(num);
           setName(name);
       }
   }

   class Phone{
       private String phoneNumber;
       //if it's not public method it would cause an error
       private void setPhoneNumber(String num){
           phoneNumber = num;
       }
   }
   ```

   (3) If original class has subclass, it might fail. For example,
   ```
   class Project {
       Person[] participants;
   }

   class Person{
       int id;
       boolean participate(Project p) {
           for(int i = 0; i < p.participants.length; i++) {
  	           if (p.participants[i].id == id)
                   return true;
           }
           return false;
       }   
   }
   class Student extends Person{
     ;
   }
   Student x = new Student();
   if(x.participate(p)){
     //code
   }
   ```
   After refactoring, it would be like:
   ```
   class Project {
       Person[] participants;
       boolean participate(Person x) {
           for(int i = 0; i < participants.length; i++) {
  	           if (participants[i].id == x.id)
                   return true;
           }
           return false;
       }   
   }

   class Person {
       int id;
   }
   class Student extends Person{
     //code
   }
   Student x = new Student();
   //code below should have compile error;
   if(x.participate(p)){
     ;
   }
   ```
   (4)
   ```
   class MyStack extends MyVector{  
   }
   MyVector a = MyStack();
   //After refactoring
   class MyStack{  
        MyVector v = new MyVector();
   }
   //below would cause exception
   MyVector a = MyStack();
   ```

   (5) Private variable would cause some problem. For example:
   ```
   class Bird{
       private double weight;
   }
   // after refactoring
   abstract class Bird{
       private double weight;
   }
   class Jay extends Bird{
       public double getSpeed(){
           //if calculation used weight, it might not have access to it
       }
   }
   ```

   (6) It might have the same problem as (1).
   ```
   int basePrice = quantity * itemPrice;
   double seasonDiscount = this.getSeasonalDiscount();
   double fees = this.getFees();
   this.setFees(100);
   double finalPrice = discountedPrice(basePrice, seasonDiscount, fees);
   ```
   and
   ```
   int basePrice = quantity * itemPrice;
   this.setFees(100);
   double finalPrice = discountedPrice(basePrice);
   ```
   may have different result.

   (7) If the superclass has more than one subclass, it may fail. For example:
   ```
   class Transport{
     ;
   }
   class Car extends Transport{
     public String getDriver();
   }
   class Plane extends Transport{
     ;
   }
   ```
   If we merge `Car` into `Transport`, then we could also call `getDriver()` for the
   instance of `Plane`.

   (8) Below it's a trivial case for this one since primitives are passed by value in Java
   ```
   public void swap(int a, int b){
       int t = a;
       a = b;
       b = t;
   }
   //after refactoring
   public void swap(Data data){
       int t = data.a;
       data.a = data.b;
       data.b = t;
   }
   class Data{
       int a, b;
       public Data(int a, int b){
            this.a = a;
            this.b = b;
       }
   }
   public static void main(String[] args){
       int a = 1, b = 2;
       swap(a, b);
       //a = 1 and b = 2 still
       Data data = new Data(1, 2);
       //data.a = 1 data.b = 2
       swap(data);
       //data.a = 2 data.b = 1
   }
   ```
2. (a) Replace Conditional with Polymorphism or Replace Type Code with State/Strategy.

   (b) Replace Inheritance with Delegation

   (c) Form Template Method

   (d) Incline Temp

   (e) Replace Inheritance With Delegation and Replace Delegation With Inheritance. Incline/Exact Class and Incline/Exact Method

   (f) Replace Inheritance With Delegation and Replace Delegation With Inheritance
3. (a) Replace Conditional with Polymorphism

   (b) Incline Temp and Incline Method

   (c) Replace Inheritance with Delegation

   (d) Replace Parameter with Method Call or Introduce Parameter Object

   (e) Exact class

   (f) Exact method

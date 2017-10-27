1. 1. If the code between the assignment to the temperate variable and the use of the temperate variable changed the value of the expression, this refactoring would fail.
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
   1. If the class also has setter, it would
   ```
   class Person implements Employee{
     public String getPhoneNumber(){
       //code
     }
   }
   ```
   Refactoring of extract class would have a separate class `TelephoneNumber` and getter,
   but it would
   1. If original class has subclass, it might fail. For example,
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
   1. 1
   1. 1
   1. It might have the same problem as i.
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
   1. If the superclass has more than one subclass, it may fail. For example:
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
   1.
1. 1. Replace Conditional with Polymorphism or Replace Type Code with State/Strategy.
   1. Replace Inheritance with Delegation
   1. Form Template Method
   1. Incline Temp
   1. Replace Inheritance With Delegation and Replace Delegation With Inheritance. Incline/Exact Class and Incline/Exact Method
   1. Replace Inheritance With Delegation and Replace Delegation With Inheritance
1. 1. Replace Conditional with Polymorphism
   1. Incline Temp and Incline Method
   1. Replace Inheritance with Delegation
   1. Replace Parameter with Method Call or Introduce Parameter Object
   1. Exact class
   1. Exact method

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
  1.
1. 1. Replace Conditional with Polymorphism or Replace Type Code with State/Strategy.
   1. Replace Inheritance with Delegation
   1. Form Template Method
   1. Incline Temp
   1. Replace Inheritance With Delegation and Replace Delegation With Inheritance. Incline/Exact Class and Incline/Exact Method
   1. Replace Inheritance With Delegation and Replace Delegation With Inheritance
1. 1.
1. 1. Replace Conditional with Polymorphism
   1. Incline Temp and Incline Method
   1. Replace Inheritance with Delegation
   1. Replace Parameter with Method Call or Introduce Parameter Object
   1. Exact class
   1. Exact method

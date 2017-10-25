1. 1. If the code between the assignment to the temperate variable and the use of the temperate variable changed the value of the expression, this refactoring would fail.
```
int quantity = 300;
double itemPrice = 2.5;

double calculateTotal() {
  if (basePrice() > 1000) {
    return basePrice() * 0.95;
  } else {
    return basePrice() * 0.98;
  }
}

double basePrice() {
  return quantity * itemPrice;
}

void changePrice() {
  itemPrice = 5;
}
```  
Like above, if other called `changePrice()` after the first `basePrice()` call, the result would be 1470 while the original one should return 735.
  1.

1. 1.
1. 1. Replace Conditional with Polymorphism
  2. Incline Temp and Incline Method
  3. Replace Inheritance with Delegation
  4. Replace Parameter with Method Call or Introduce Parameter Object
  5. Exact class
  6. Exact method

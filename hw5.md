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
  1.

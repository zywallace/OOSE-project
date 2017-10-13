# DESIGN PRINCIPLES
Name: **Yu Zhao** JHED: **yzhao86**

1. - It violates _**LSP**_ since `Set` could be invalid substitute for `MyMultiSet`. For example
```
MyMultiSet<T> m = new Set<T>();
m.add(v);
assert(m.count(v) != m.add(v).count(v))
```
above would fail for correct implementation of `Set`.
 - use `abstract class` to implement methods except `add()` and then use concrete class to implement `add()`
 ```
 abstract class Base<T> implements Collection<T>{
       private List<T> data;
       public Base() {
           data = new LinkedList<T>();
       }
       public void remove(T v) {
           data.remove(v);
       }
       public int count(T v) {
           int c = 0;
           for(T i : data) {
               if (v.equals(i)) c++ ;
           }
           return c;
       }
}
 ```
 ```
class MyMultiSet<T> extends Base<T>{
       public void add(T v) {
           data.add(v);
       }
}
class Set<T> extends Base<T>{
       public void add(T v) {
           if (count(v) == 0) {
               super.add(v);    
           }
       }
}
 ```
2. - It violates _**SRP**_ and _**God Class**_, class `Game` shouldn't have all methods in it and condition checking could be more concise.
  - 
  ```
  class Game {
        private Board board;
        public void move() {
            /* Read user input */
            if (board.isEmpty(source) || !board.isEmpty(dest))
                throw new IllegalMoveException();
            /* ... More rules here .. */
            /* Print out the current state of the board */
            board.printBoard();
        }
        private Point readCoordinateFromInput() {
            /* Read input from the terminal and convert to a point */
        }
}
class Board{
        private Piece[][] board;
        private void printBoard() {
            /* Printing code here */
        }
        public boolean isEmpty(Point a){
            return board[a.x][a.y] == null;
        }
}
```
3. - It violates _**DRY**_. It just computes the average of all parameters and displays them, which could be done in more concise code.
   - 
   ```
   class WeatherStation {
        void updateDisplay () {
            String[] params = {"Temps", "Directions"};
            int N = 10;
            double[] avgs = new double[params.length];
            for(int i = 0; i < N; i++){
                for(int j = 0; j < params.length; j++){
                  switch(params[i]){
                    case "Temps": avgs[i] += sensor.getCurrentTemp();break;
                    //other cases
                  }
                }
                TimeUnit.SECONDS.sleep(1);
            }
            for(int i = 0; i < params.length; i++){
                avgs[i] /= N;
                switch(params[i]){
                  case "Temps": display.setTemp(avgs[i]);break;
                  //other cases
                }
            }
        }
    }
      ```
4. - It might not violate any principle (may be _**DRY**_ if two methods `slashWithSword` and `pokeWithSpear` are mostly similar). Perhaps it should make `slashWithSword` and `pokeWithSpear` `private` as well.
  - 
  ```
public class Player
{
    private int weaponType;
    public void attack(Monster target) {
        switch(weaponType) {
            case SWORD:
                slashWithSword(target);
                break;
            case SPEAR:
                pokeWithSpear(target);
                break;
            /* Cases for other weapons here */
        }
    }
    public void slashWithSword(Monster target) {
        int swordDamage;
        /* Do some work here to compute the damage */
        target.addDamage(swordDamage);
    }
    public void pokeWithSpear(Monster target) {
        int spearDamage;
        /* Do some work here to compute the damage */
        target.addDamage(spearDamage);
    }
    /* Other code and definitions here */
}
```
5. - It violates _**OCP**_ and _**DRY**_. Condition checking code is ugly and code to move the piece to the new position is repeated.
  -
  ```
  class Game {
        /* Other code and definitions here */
        private void canMoveBetween(Point src, Point dest) {
            //no piece at src or there is piece at dest
            if(isAvailable(src) || !isAvailable(dest)){
              throw new IllegalMoveException();
            }
            /* Check if we are moving along a valid edge. Also ensure that hounds cannot move backwards */
            if (!isHoundMovingBack(src, dest) && isAccessible(src, dest)) {
                /* Code to move the piece to the new position */
            }else{
              throw new IllegalMoveException();
            }
        }    
        private boolean isAccessible(Point src, Point dest){
            /* code to check if src and dest are adjacent*/
        }
        public boolean isHoundMovingBack(Point src, Point dest){
            //hound moves backwards
            if(getPieceAt(src).getPieceType() == PieceType.HOUND && src.x > dest.x){
              return true;
            }
            return false;
        }
        private boolean isAvailable(Point a){
            return getPieceAt(a) == null;
        }
}
  ```

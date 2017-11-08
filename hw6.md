# Yu Zhao
# JHED: yzhao86
1.
   1. Delegation of OO is like the pointer/reference of a method. It lets program run method of receiver in the context(like parameters in class) of the sender.
   2.
      1. Yes since `Observable` would hold a list of `Observer` and call `update()` in `notifyObservers()`.
      2. No.
      3. No.
      4. Yes since Command class has a receiver and `execute()` method would call `receiver.action()`
      5. No.
      6. Yes since for state-dependent methods, they now are moved to the objects of state.
      7. Yes and the reason is the same as the state pattern.
      8. Yes since a method of decorator would call the same method on the decoratee and then run the rest with the return of decoratee.
      9. Yes since adapter class gets the original object and delegate to the desired interface.
      10. Yes since facade just provides an united interface to a set of interfaces so its main functionality is to just delegate to other objects.
      11. No.
      12. Yes since proxy provides a surrogate for another object to control access to it and this is basically delegation.
      13. No.
      14. Yes since `Component` would hold a list of its child (also `Component`) and calling `print()` would also call `print()` in its child.
2.
   1. It means program should only know the functionality and don't care the detail of implementation.
   2.
      1. Yes since `Observer` in this case should be interface and Observable holds a list of concrete implementation of `Observer`.
      2. Yes since there is an interface which has the factory or method declared. And implementers specialize this factory to create the kinds of objects they need.
      3. Yes and it has the same reason as 2.
      4. Yes since `Command` should be an interface of all commands and concrete command would specify which receiver to call.
      5. No.
      6. Yes since State defines a common interface for all concrete states which makes states interchangeable.
      7. Yes and it has the same reason as 6.
      8. Yes since decorator implements the same interface as the component they are going to decorate.
      9. Yes since adapter implements the target interface so client would use adapter directly.
      10. Yes since facade itself is an united interface to a set of interfaces.
      11. Yes since iterator itself is an interface that all iterator should implement.
      12. Yes since the proxy object and real object are both implementations of `Subject` interface.
      13. No.
      14. Yes since leaf and other composites may have different implementations of `Component` interface.
3.
   1. Facade pattern
   ```
   class MyFacade {
		private List<Object> decorator;

		public MyFacade(List<Object> A, List<Object> B) {
			this.decorator = new ListDecorator(A, B);
		}

		public List<Object> get() {
			return this.decorator;
		}
	}

  class ListDecorator implements List<Object>{
    private List<Object> A;
    private List<Object> B;

    public ListDecorator (List<Object> A, List<Object> B) {
        this.A = A;
        this.B = B
    }

    public void add(Object e) {
   		if (this.B.contains(e)) {
   			this.A.add(e);
   		} else {
   			System.out.println("element not in list B");
   		}
 	  }
    //other methods that grants access to A only, those methods should be identical to A's methods except for methods may change the objects in A, like `add()` `addAll()` `set()`.
  }

   ```
   2. State pattern. I would have 3 state objects: `newOrder` `paidOrder` and `shippedOrder`. All of them would have `change()` and `cancel()` methods respectively. `Order` class should have these three objects as fields and an state field to indicate current state. `pay()` or some other methods may change the current state and `Order.change()` or `Order.cancel()` will just call `this.state.change()` or `this.state.cancel()`.
4.
   1. State pattern. In order to get rid of switch statement, we could combine `level` and other related methods into state interface. It shall have 3 state classes implements State interface respectively and states now have clear reifications as class names. Then `FitnessCustomer` should have a field to indicate current state and `setState()` method to replace `setLevel()` method.
   2. Strategy pattern. This is the typical usage of Strategy pattern: perform different algorithm with different state. It would simplify the code (get rid of hideous switch case statement) and in this problem, improve the performance.
   3. Observer pattern. Busy waiting should be expected in the while loop and it would use tons of CPU resource. So we could have a thread pool as Observable and whenever a new thread is created, we add it to the thread pool. Then when a thread is finished, thread pool calls `update()` to invoke other threads' `update()` method, which tells they could do their cleanup process.
5.
   - Observer: `addListener()` `removeListener()` and `fireEvent()` use observer pattern
   - Decorator: `read()` method
   - Proxy: `private InputStream backer;` and `read()` calls `this.backer.read()`

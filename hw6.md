# Yu Zhao
# JHED: yzhao86
1.
   1. Delegation of OO is like the pointer/reference of a method. It lets program run method of receiver in the context(parameters) of the sender.
   2.
      1. Yes since `Observable` would hold a list of `Observer` and call `update()` in `notifyObservers()`
      2. No
      3. No
      4. Yes since `execute()` method in Command class would call `receiver.action()`
      5. No
      6. Yes since for state-dependent methods, they now are moved to the objects of state.
      7. Yes and the reason is the same as the state pattern.
      8. Yes since a method of decorator would call the same method on the decoratee and then run the rest with the return of decoratee.
      9. Yes since adapter class gets the original object and delegate to the desired interface.
      10. Yes since facade just provides an united interface to a set of interfaces so its main functionality is to just delegate to other objects.
      11. No
      12. Yes since proxy provides a surrogate for another object to control access to it and this is basically delegation.
      13. No
      14. Yes since `Component` would hold a list of its child (also `Component`) and calling `print()` would also call `print()` in its child.
2.
   1. It means program should know the functionality and don't care the detail of implementation
   2. 1.
      2. No
      3. No
      4. Yes since `execute()` method in Command class would call `receiver.action()`
      5. No
      6. Yes since for state-dependent methods, they now are moved to the objects of state.
      7. Yes and the reason is the same as the state pattern.
      8. Yes since a method of decorator would call the same method on the decoratee and then run the rest with the return of decoratee.
      9. Yes since adapter class gets the original object and delegate to the desired interface.
      10. Yes since facade just provides an united interface to a set of interfaces so its main functionality is to just delegate to other objects.
      11. No
      12. Yes since proxy provides a surrogate for another object to control access to it and this is basically delegation.
      13. No
      14. Yes
3.
   1. Facade pattern
   ```
   class MyFacade {
		private List<Object> A;
		private List<Object> B;

		public MyFacade() {
			this.A = new ArrayList<>();
			this.B = new ArrayList<>();
		}

		public List<Object> get() {
			return this.A;
		}

		public void add(Object e) {
			if (this.B.contains(e)) {
				this.A.add(e);
			} else {
				System.out.println("element not in list B");
			}
		}
	}
   ```
   2. State pattern. I would have 3 state objects: `newOrder` `paidOrder` and `shippedOrder`. All of them would have `change()` and `cancel()` methods respectively. `Order` class should have these three objects as fields and an state field to indicate current state. `pay()` or some other methods may change the current state and `Order.change()` or `Order.cancel()` will just call `this.state.change()` or `this.state.cancel()`
4.
   1. State pattern. In order to get rid of switch statement, we could combine `level` and other related methods into state. It shall have 3 state variables respectively and states now have clear reifications as class names.
   2. Strategy pattern. This is the typical usage of Strategy pattern: perform different algorithm with different state.
   3.
5.
   - Observer: `addListener()` `removeListener()` and `fireEvent()` use observer pattern
   - Decorator: `read()` method
   - Proxy: `private InputStream backer;` and `read()` calls `this.backer.read()`

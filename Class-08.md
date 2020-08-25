# Dunder Methods
Dunder methods let you emulate the behavior of built-in types
example: 
For example, to get the length of a string you can call len('string'). But an empty class definition doesn’t support this behavior  you can add a __len__ dunder method to your class:

```
    class LenSupport:
    def __len__(self):
        return 42

>>> obj = LenSupport()
>>> len(obj)
 42
 ```
we can list various dunder methods to unlock the following language features:

* Initialization of new objects
    for object Initialization we use  __init__
     ```    
     class Account:
    """A simple account class"""

    def __init__(self, owner, amount=0):
        """
        This is the constructor that lets us create
        objects from this class
        """
        self.owner = owner
        self.amount = amount
        self._transactions = []

        #this class will be used throughout the rest of examples 

     ```
* Object representation
    object Representation can be done using __str__, __repr__

    ``` 
    class Account:
    # ... (see above)

    def __repr__(self):
        return 'Account({!r}, {!r})'.format(self.owner, self.amount)

    def __str__(self):
        return 'Account of {} with starting amount: {}'.format(
            self.owner, self.amount)
    ```

* Enable iteration
   In order to iterate over our account object we can use  __len__, __getitem__, __reversed__

   ```
   class Account:
    # ... (see above)

    def __len__(self):
        return len(self._transactions)

    def __getitem__(self, position):
        return self._transactions[position]

    ``` 

* Operator overloading (comparison)
    Operator Overloading for Comparing Accounts: __eq__, __lt__
     
     ```
     from functools import total_ordering

        @total_ordering
        class Account:
        # ... (see above)

        def __eq__(self, other):
            return self.balance == other.balance

        def __lt__(self, other):
            return self.balance < other.balance

     ```

* Operator overloading (addition)
    Operator Overloading for Merging Accounts: __add__

    ```
    def __add__(self, other):
    owner = '{}&{}'.format(self.owner, other.owner)
    start_amount = self.amount + other.amount
    acc = Account(owner, start_amount)
    for t in list(self) + list(other):
        acc.add_transaction(t)
    return acc

    ```
* Method invocation

    You can make an object callable like a regular function by adding the __call__ dunder method

        class Account:
        # ... (see above)

        def __call__(self):
            print('Start amount: {}'.format(self.amount))
            print('Transactions: ')
            for transaction in self:
                print(transaction)
            print('\nBalance: {}'.format(self.balance))
       


* Context manager support (with statement)

    __enter__, __exit__ 

    ```
        class Account:
    # ... (see above)

    def __enter__(self):
        print('ENTER WITH: Making backup of transactions for rollback')
        self._copy_transactions = list(self._transactions)
        return self

    def __exit__(self, exc_type, exc_val, exc_tb):
        print('EXIT WITH:', end=' ')
        if exc_type:
            self._transactions = self._copy_transactions
            print('Rolling back to previous transactions')
            print('Transaction resulted in {} ({})'.format(
                exc_type.__name__, exc_val))
        else:
            print('Transaction OK')
    ```

resrouce for code snippts: https://dbader.org/blog/python-dunder-methods


### 1. How much is the current memory capacity of a canister?

Answer: Canisters can store upto 48GB of Stable memory

### 2. What is the issue with the following code sample?
```
actor {
  let counter : Nat = 0;
  public func increment_counter() : async () {
    counter := counter + 1;
  };
}
```
Answer: the variable `counter` was declared using `let` keyward which means that `counter` is immutable. so the code will throw error at line `counter := counter + 1;`

### 3. What is the issue with the following code sample?
```
actor {
  var message : Text = 0;

  public query func change_message(new_message : Text) : async () {
    message := new_message;
    return;
  };
  
  public query func see_message() : async Text {
    return(message);
  };
}
```

Answer: there are 2 issues in the above code
1. In the line `var message : Text = 0;` the `message` variable is assigned a type `Text` but being initializied with `0`
2. the `change_message` function is trying to update the `message` variable in a `query` call function. `query` call is for reading data not updating data

### 4. False or True: we can remove the keyword async for return argument of a query function since queries are faster to answer.

Answer: False
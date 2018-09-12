## Streams

# Effectively final variable.

```
//Incorrect
for (int i = 0; i < 10; i++) {
    new Thread(() -> {
     System.out.println("i = " + i); // Does not compile!
    }).start();
}
```
```
//Correct
for (int i = 0; i < 10; i++) {
    j = i; //effectively final
    new Thread(() -> System.out.println("i = " + j)).start();
}
```
```    
//Incorrect
for (int i = 0; i < 10; i++) {
    int j = i;
    new Thread(() -> System.out.println("i = " + j)).start();
    j++;
}
```

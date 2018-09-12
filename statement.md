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
```java runnable
// { autofold
class Main {
    public static void main(String[] args) {
// }
        for (int i = 0; i < 10; i++) {
            int j = i; //effectively final
            new Thread(() -> System.out.println("i = " + j)).start();
        }
// { autofold
    }
}
// }

```
```    
//Incorrect
for (int i = 0; i < 10; i++) {
    int j = i;
    new Thread(() -> System.out.println("i = " + j)).start();
    j++;
}
```

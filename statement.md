## Streams

# Effectively final variable.

```java runnable
// { autofold
class Main {
    public static void main(String[] args) {
// }
//Incorrect
for (int i = 0; i < 10; i++) {
    new Thread(() -> {
     System.out.println("i = " + i); // Does not compile!
    }).start();
}
// { autofold
    }
}
// }
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

```java runnable
// { autofold
class Main {
    public static void main(String[] args) {
// }    
//Incorrect
for (int i = 0; i < 10; i++) {
    int j = i;
    new Thread(() -> System.out.println("i = " + j)).start();
    j++;
}
// { autofold
    }
}
// }
```

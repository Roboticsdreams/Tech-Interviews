# Random Problems

[Tech-Interviews](../../README.md) -> [Workouts](../../Workouts/Workouts.md) -> [Random Problems](../Random%20Problems/RandomProblems.md)

1. How to print the list of numbers from 1 to n with not to end with 5 using java streams?
```java Java 7
public static void PrintNumbersNotEndWith5(int n) {
    for (int i = 1; i < n; i++) {
        if (i % 10 != 5) {
            System.out.println(i);
        }
    }
}
```
```java Java 8
public static void PrintNumbersNotEndWith5(int n) {
    IntStream.range(1, n).filter(i -> i % 10 != 5).forEach(System.out::println);
}
```
2. Print the non repeated characters in a string?
```java Java 7
public static void PrintNonRepeatedCharacters(String str) {
    Set<Character> set = new HashSet<>();
    for (int i = 0; i < str.length(); i++) {
        set.add(str.charAt(i));
    }
    for (int i = 0; i < str.length(); i++) {
        if (!set.contains(str.charAt(i))) {
            System.out.print(str.charAt(i));
            break;
        }
    }
}
```
```java Java 8
public static void PrintNonRepeatedCharacters(String str) {
    Character result = str.chars()
        .mapToObj(c -> Character.toLowerCase(Character.valueOf((char) c)))
        .collect(Collectors.groupingBy(Function.identity(), LinkedHashMap::new, Collectors.counting()))
        .entrySet().stream()
        .filter(e -> e.getValue() == 1)
        .map(e -> e.getKey())
        .findFirst().orElse(null);
    
    System.out.println(result);   
}
```
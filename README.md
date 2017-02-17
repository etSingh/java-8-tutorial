# java-8-tutorial
---
Writing a custom Comparator

`Main Class`

```java
// Java Util Function<T, R>
        Function<Person, Comparable> f1 = p -> p.getAge();

        Comparator<Person> cmpPersonAge = Comparator.comparing(f1);
        // you could have called it as Comparator.comparing(p -> p.getAge())
        // or Comparator.comparing(Person::getAge)

        Comparator<Person> cmpPersonLName =
                Comparator.comparing(Person::getLastName);

        Comparator<Person> cmp0 = cmpPersonAge.thenComparing(
                cmpPersonLName);

        Comparator<Person> cmp = Comparator
                .comparing(Person::getLastName) // Extract Property and compare
                .thenComparing(Person::getFirstName)
                .thenComparing(Person::getAge);

        // The above Comparator was made possible by the introduction
        // of default and static methods in Java

         Person arr[] = new Person[]{
            new Person("Harpreet", "Singh", 22),
                    new Person("Hardeep", "Singh", 21),
                    new Person("Gurdeep", "Singh", 53),
                    new Person("Bhupinder", "Kour", 49)
        };


        Arrays.sort(arr, cmp::compare);
```

`Comparator Interface`

```java
@FunctionalInterface
public interface Comparator<T>  {

    // Abstract method
    int compare(T t1, T t2);

    /**
     * <T> Comparator <T> return type is a Comparator of generic
     * type T which has to be told to the compiler beforehand
     * for a static method
     * Comparable is an interface implemented by both String
     * and Integer classes, it provides the compareTo method
     * returns an int because Comparator<T> needs to return an int as defined
     * by the abstract method int compare(T t1, T t2);
     * R apply (T t) = applies function to a given argument (t is the
     * function argument)
     * @param f a function which takes in a Person and returns a Comparable
     *          object
     * @return an Integer by applying the function to the arguments
     * and then passing them to the compare to method
     */
    static <T> Comparator<T> comparing(
            Function<T, Comparable> f){
        return (p1, p2) -> f.apply(p1).compareTo(f.apply(p2));
    }

    /**
     * Default method to fall back on the 2nd comparator if the
     * 1st comparator returns 0
     * @param cmp Argument of type Comparator<T>
     * @return returns an implementation of the abstract method
     * int compare(T t, T t1) which returns an int
     */

    default Comparator<T> thenComparing(
            Comparator<T> cmp){
                return (p1, p2) ->
                        this.compare(p1, p2) == 0 ?
                                cmp.compare(p1, p2) : this.compare(p1, p2);
    }

    /**
     * 1) This method takes a Function instead of a Comparator
     * 2) Then it obtains the Comparator from that function
     *    by calling the comparing method
     * 3) Finally, it returns the output of the thenComparing method
     *    defined above
     * @param f a function
     * @return implementation of int compare
     */
    default Comparator<T> thenComparing(
            Function<T, Comparable> f){
                Comparator<T> cmp = comparing(f);
        return thenComparing(cmp);
    }
}
```
http://www.ticketmaster.ie/event/18005147D449DD0E

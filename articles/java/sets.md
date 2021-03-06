---
title:  "Sets in Java"
date: 2018-11-05 00:00:00
---

### <a href="#overview" name="overview"><i class="fa fa-link anchor" aria-hidden="true"></i></a> Overview

A [Set](https://docs.oracle.com/javase/8/docs/api/java/util/Set.html) is a [Collection](https://docs.oracle.com/javase/8/docs/api/java/util/Collection.html) which cannot contain duplicated elements. In other words, the same object cannot occur more than once in a Set.

### <a href="#interface" name="interface"><i class="fa fa-link anchor" aria-hidden="true"></i></a> Interface

A Set interface contains only methods, inherited from Collection interface + it adds it's own methods:

```
public interface Set<E> extends Collection<E> {
    int size();
    boolean isEmpty();
    boolean contains(Object o);
    Iterator<E> iterator();
    Object[] toArray();
    <T> T[] toArray(T[] a);
    boolean add(E e);
    boolean remove(Object o);
    boolean containsAll(Collection<?> c);
    boolean addAll(Collection<? extends E> c);
    boolean retainAll(Collection<?> c);
    boolean removeAll(Collection<?> c);
    void clear();
    boolean equals(Object o);
    int hashCode();
    default Spliterator<E> spliterator() { /* ... */ }
}
```

### <a href="#when_to_use" name="when_to_use"><i class="fa fa-link anchor" aria-hidden="true"></i></a> When to use

Set should be used in situations when you don't want to see duplicated elements.

### <a href="#implementations" name="implementations"><i class="fa fa-link anchor" aria-hidden="true"></i></a> Implementations

Set interface has three basic implementations, available in Collections framework: [HashSet](https://docs.oracle.com/javase/8/docs/api/java/util/HashSet.html), [TreeSet](https://docs.oracle.com/javase/8/docs/api/java/util/TreeSet.html) and [LinkedHashSet](https://docs.oracle.com/javase/8/docs/api/java/util/LinkedHashSet.html):
* HashSet, a default implementation, backed by HashMap. Gives no guarantee about ordering.
* TreeSet, order set structure, gives guarantee about ordering.
* LinkedHashSet should be used if you want to maintain insertion order, without duplicates.

### <a href="#how-to-create" name="how-to-create"><i class="fa fa-link anchor" aria-hidden="true"></i></a> How to create

The default way of creating sets is following:
```
Set<String> hashSet = new HashSet<>();
Set<String> treeSet = new TreeSet<>();
Set<String> linkedHashSet = new LinkedHashSet<>();
```

### <a href="#basic-operations" name="basic-operations"><i class="fa fa-link anchor" aria-hidden="true"></i></a> Basic operations

Here are the basic operations described:

```
Set<String> set = new HashSet<>();

set.add("element1");

set.addAll(Arrays.asList("element1", "element2"));
set.size(); // 2
set.contains("element1"); // true
set.containsAll(Arrays.asList("element1", "element2"));

set.isEmpty(); // false

set.add("element3");
set.size(); // 3
set.removeIf(item -> "element3".equals(item));
set.size(); // 2

set.stream() // stream operations
        .forEach(item -> System.out.println(item));

set.clear();

set.isEmpty(); // true
```

### <a href="#bulk-operations" name="bulk-operations"><i class="fa fa-link anchor" aria-hidden="true"></i></a> Bulk operations

There are bulk operations, available for Set interface:
```
Set<String> set = new HashSet<>();

set.addAll(Arrays.asList("element1", "element2", "element3")); // [element1, element2, element3]
set.containsAll(Arrays.asList("element1", "element2")); // true
set.retainAll(Arrays.asList("element1", "element2")); // [element1, element2]
set.removeAll(Arrays.asList("element1", "element2")); // []
set.size(); // 0
```


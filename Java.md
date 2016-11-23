```java
@Override
public int compareTo(TestObject o) {
    String title = ((TestObject) o).getTitle();
    return this.title.compareTo(title);
}
```

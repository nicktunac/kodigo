#Python#

Kodigo for Java

Sorting with objects in Java
```java
import java.util.Comparator;

public class TestObject implements Comparable<TestObject>{

    private String title;
    private String category;
    private String town;

    // getter and setter

    public TestObject(String title, String category, String town) {
        this.title = title;
        this.category = category;
        this.town = town;
    }

    @Override
    public int compareTo(TestObject o) {
        String title = ((TestObject) o).getTitle();
        return this.title.compareTo(title);
    }

    public static Comparator<TestObject> TestCategoryComparator = new Comparator<TestObject>() {
        @Override
        public int compare(TestObject o1, TestObject o2) {

            String o1Category = o1.getCategory().toUpperCase();
            String o2Category = o2.getCategory().toUpperCase();

            return o1Category.compareTo(o2Category);
        }
    };
}
```

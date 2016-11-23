```java
import java.util.Comparator;

/**
 * Created by DTunac on 11/23/2016.
 */
public class TestObject implements Comparable<TestObject>{

    private String title;
    private String category;
    private String town;

    public String getTitle() {
        return title;
    }

    public void setTitle(String title) {
        this.title = title;
    }

    public String getCategory() {
        return category;
    }

    public void setCategory(String category) {
        this.category = category;
    }

    public String getTown() {
        return town;
    }

    public void setTown(String town) {
        this.town = town;
    }

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

    @Override
    public String toString() {
        return "TestObject{" +
                "title='" + title + '\'' +
                ", category='" + category + '\'' +
                ", town='" + town + '\'' +
                '}';
    }
}
```

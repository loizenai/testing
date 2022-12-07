Question 1:


<pre>
import java.util.ArrayList;
import java.util.Arrays;
import java.util.List;

public class Main {
    public static void main(String[] args) {
        Integer[][] a = {
                {3, 2, 9, 15},
                {5,10,7,14},
                {11, 6, 8, 1},
                {12, 4, 17, 13}
        };
        func(a);
    }

    private static void func(Integer a[][]) {
        var lst = twoDArrayToList(a);
        printFunc(lst);
    }

    private static <T> List<T> twoDArrayToList(T[][] twoDArray) {
        List<T> list = new ArrayList<T>();
        for (T[] array : twoDArray) {
            list.addAll(Arrays.asList(array));
        }
        return list;
    }

    private static void printFunc(List<Integer> lst) {
        var size = lst.size();
        for (int i = 0; i<size - 1; i ++) {
            var v1 = lst.get(i);
            for (int j=i + 1; j<lst.size(); j++) {
                var v2 =  lst.get(j);
                if ((v1+v2)  % 3 == 0) {
                    System.out.println(v1 + " " + v2);
                }
            }
        }
    }
}
</pre>

Question 1:


```
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
        // - question - a
        findPairds(a);
        // - question - b
        find3Max(a);
    }

    private static void findPairds(Integer a[][]) {
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

    private static void find3Max(Integer[][] a) {
        int max1 = Integer.MIN_VALUE;
        int max2 = Integer.MIN_VALUE;
        int max3 = Integer.MIN_VALUE;

        for (int i = 0; i < a.length; ++i) {
            for(int j = 0; j < a[i].length; ++j) {
                var v = a[i][j];
                if (v > max1) {
                    max3 = max2;
                    max2 = max1;
                    max1 = v;
                } else if (v > max2) {
                    max3 = max2;
                    max2 = v;
                } else if (v > max3) {
                    max3 = v;
                }
            }
        }
        System.out.println("3 max numbers --- " + ": " + max1 + " " + max2 + " " + max3);
    }
}
```


Question 2:

```
UPDATE TB_ORDER
SET TB_ORDER.Total = tb_f.TOTAL
FROM
    SELECT sum(tb_hd1_qty.QTY * item.UNIT_PRICE) as TOTAL
    FROM
        (SELECT ID, sum(QTY) as QTY from TB_ORDER_DETAIL where ORD_NO = "HD1" group by ID) as tb_hd1_qty
        inner join TB_ITEM as item
        on r1.ID = item.ID
WHERE ORD_NO = "HD1";
```

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
// -- a
UPDATE TB_ORDER
SET TB_ORDER.Total = TB_F.TOTAL
FROM
    (SELECT sum(TB_HD1_QTY.QTY * TB_ITEM.UNIT_PRICE) as TOTAL
     FROM
        (SELECT ID, sum(QTY) as QTY from TB_ORDER_DETAIL where ORD_NO = "HD1" group by ID) as TB_HD1_QTY
        inner join TB_ITEM
        on TB_HD1_QTY.ID = TB_ITEM.ID
    ) as TB_F
WHERE TB_ORDER.ORD_NO = "HD1";

// -- b
UPDATE TB_ITEM
SET TB_ITEM.QTY = TB_F.REMAIN_QTY
FROM
    (SELECT ID, (TB_ITEM.QTY - TB_CAL_ORDER.ORDER_QTY) as REMAIN_QTY
    FROM
        (SELECT ID, sum(QTY) as ORDER_QTY from TB_ORDER_DETAIL group by ID) as TB_CAL_ORDER
            inner join TB_ITEM
                       on TB_CAL_ORDER.ID = TB_ITEM.ID) as TB_F
WHERE TB_ITEM.ID = TB_F.ID

// -- c
SELECT SUM(Total * Discount / 100) FROM TB_ORDER WHERE ORD_DATE = "01/01/2021"

// -- d
SELECT * FROM TB_ITEM
WHERE
    TB_ITEM.ID = SELECT ID
                 FROM (SELECT ID, MAX(SELL_QTY)
                        FROM
                            SELECT ID, SUM(QTY) AS SELL_QTY FROM TB_ORDER_DETAIL GROUP BY ID AS TB_QTY)
```

Question 3:

<img width="670" alt="image" src="https://user-images.githubusercontent.com/62205284/206278182-37720757-2371-43f3-bf03-4db090b8c564.png">

<img width="778" alt="image" src="https://user-images.githubusercontent.com/62205284/206278589-025cfc7e-cead-476f-ade1-21805c9329fa.png">

React Tutorial
https://ozenero.com/react-tutorials

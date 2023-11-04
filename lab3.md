Brandon Panuco<br>
Lab 3<br>

Part 1<br><br>
a) I chose to debug the filter method in ListExamples.java file. I started by creating a file called ListTests where I created a testList method. The testList method initialized an 
arrayList named "input1" and another one called "expected". "input1" arrayList is the object I used to compare to the correct outcome, which I saved inside the "expected" object.
I then used assertEquals on both objects. As for the StringChecker interface, to begin testing without fixing any code errors, I decided to implement the checkString method inside 
the second "filter" method argument, so it can be passed into the "filter" method. My checkString implemented method says that if a string's length is larger than 1, then it should
not be included in the new ArrayList. My "input1" object contains 4 Strings: "aaa","b","ccc","a". According to the rule described for the filter method, ["b","a"] should be the
new Strings saved into a new ArrayList. Hence, I initialized the "expected" arrayList with  ["b","a"].<br>
Here is the unbugged code for the ListTests file (ListExamples remains unchanged):<br>
```
import static org.junit.Assert.*; 
import org.junit.*;
import java.util.ArrayList;
import java.util.Arrays;
import java.util.List;
public class ListTests {
    @Test 
	public void testList() 
        List <String> input1 = new ArrayList<>();
        input1.add("aaaa");
        input1.add("b");
        input1.add("ccc");
        input1.add("a");
        List <String> expected = Arrays.asList("b","a");
        assertEquals(expected, ListExamples.filter(input1,new StringChecker() {
            @Override
            public boolean checkString(String s) {
                if (s.length() > 1)
                    return false;
                return true;
            }  
        }));
	}
}
```
![Image](failureWithBug.png)<br>
b) I decided to remove String "a" from the "input1" ArrayList in order to purposely make the program believe that the filter method works as intended. By removing String 
"a", String "b" remains as the only element with String length 1, so the order rule in the filter method does not apply here.<br>
Here is the unbugged code that does not produce a failure (ListExamples remains unchanged):<br>
```
import static org.junit.Assert.*;
import org.junit.*;

import java.util.ArrayList;
import java.util.Arrays;
import java.util.List;

public class ListTests {
    @Test 
	public void testList() {

        List <String> input1 = new ArrayList<>();
        input1.add("aaaa");
        input1.add("b");
        input1.add("ccc");
        //input1.add("a");
        List <String> expected = Arrays.asList("b");
        assertEquals(expected, ListExamples.filter(input1,new StringChecker() {
            @Override
            public boolean checkString(String s) {
                if (s.length() > 1)
                    return false;
                return true;
            }  
        }));

	}

}
```
![Image](successWithBug.png)<br>
c) In order to fix the bug, I had to change the way in which Strings were being added into the result ArrayList inside the filter method. The code in filter basically followed
the rules given by the StringChecker interface. An if statement inside the filter method determines whether a String is valid to get added into the result ArrayList. The 
bug being the line: ```result.add(0,s); ```. This line makes is so that Strings get added in the reversed order from their original ArrayList. The reason why this occurs is
because when a new item is added at index 0, the items shift to the rigth since index 0 has been occupied by a new String. To fix the bug, removing the first argument from the
add method will make it so that incoming Strings get added at the end of the ArrayList as expected. Here is the correction: ```result.add(s); ``` .<br>
Here is the bugged version:<br>
```
import java.util.ArrayList;
import java.util.List;

interface StringChecker { boolean checkString(String s); }

class ListExamples {

  // Returns a new list that has all the elements of the input list for which
  // the StringChecker returns true, and not the elements that return false, in
  // the same order they appeared in the input list;
  static List<String> filter(List<String> list, StringChecker sc) {
    List<String> result = new ArrayList<>();
    for(String s: list) {
      if(sc.checkString(s)) {
        result.add(0,s);
      }
    }
    return result;
  }
}
```
Here is the unbugged version:<br>
```
import java.util.ArrayList;
import java.util.List;

interface StringChecker { boolean checkString(String s); }

class ListExamples {

  // Returns a new list that has all the elements of the input list for which
  // the StringChecker returns true, and not the elements that return false, in
  // the same order they appeared in the input list;
  static List<String> filter(List<String> list, StringChecker sc) {
    List<String> result = new ArrayList<>();
    for(String s: list) {
      if(sc.checkString(s)) {
        result.add(s);
      }
    }
    return result;
  }
}
```
Here is the ListTests class code:<br>
```
import static org.junit.Assert.*;
import org.junit.*;

import java.util.ArrayList;
import java.util.Arrays;
import java.util.List;

public class ListTests {
    @Test 
	public void testList() {

        List <String> input1 = new ArrayList<>();
        input1.add("aaaa");
        input1.add("b");
        input1.add("ccc");
        input1.add("a");
        List <String> expected = Arrays.asList("b","a");
        assertEquals(expected, ListExamples.filter(input1,new StringChecker() {
            @Override
            public boolean checkString(String s) {
                if (s.length() > 1)
                    return false;
                return true;
            }  
        }));

	}

}
```
<br>Part 2<br><br>

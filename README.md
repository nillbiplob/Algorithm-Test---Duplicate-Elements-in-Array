# Algorithm-Test---Duplicate-Elements-in-Array
Java Program to find duplicate elements in array - 3 ways to compare time/space complexity


Solution 1 :
Our first solution is very simple. All we are doing here is to loop over an array and comparing each element to every other element. For doing this, we are using two loops, inner loop, and outer loop. We are also making sure that we are ignoring comparing of elements to itself by checking for i != j before printing duplicates. Since we are comparing every element to every other element, this solution has quadratic time complexity i.e. O(n^2). This solution has the worst complexity in all three solutions.



Solution 2 :

The second solution is even simpler than this. All you need to know is that Set doesn't allow duplicates in Java. Which means if you have added an element into Set and trying to insert duplicate element again, it will not be allowed. In Java, you can use the HashSet class to solve this problem. Just loop over array elements, insert them into HashSet using add() method, and check the return value.

If add() returns false it means that element is not allowed in the Set and that is your duplicate. Here is the code sample to do this :

 for (String name : names) {
     if (set.add(name) == false) {
        // your duplicate element
     }
}

The complexity of this solution is O(n) because you are only going through the array one time, but it also has a space complexity of O(n) because of the HashSet data structure, which contains your unique elements. So if an array contains 1 million elements, in the worst case you would need a HashSet to store those 1 million elements.



Solution 3 :

Our third solution takes advantage of another useful data structure, hash table. All you need to do is loop through the array using enhanced for loop and insert each element and its count into hash table. You can use HashMap class of JDK to solve this problem. It is the general purpose hash table implementation in Java. In order to build table, you check if hash table contains the elements or not, if it is then increment the count otherwise insert element with count 1. Once you have this table ready, you can iterate over hashtable and print all those keys which has values greater than one. These are your duplicate elements. This is in fact a very good solution because you can extend it to found count of duplicates as well. If you remember, I have used this approach to find duplicate characters in String earlier. Here is how you code will look like :

// build hash table with count
        for (String name : names) {
            Integer count = nameAndCount.get(name);
            if (count == null) {
                nameAndCount.put(name, 1);
            } else {
                nameAndCount.put(name, ++count);
            }
        }

        // Print duplicate elements from array in Java
        Set<Entry<String, Integer>> entrySet = nameAndCount.entrySet();
        for (Entry<String, Integer> entry : entrySet) {
            if (entry.getValue() > 1) {
                System.out.printf("duplicate element '%s' and count '%d' :", entry.getKey(), entry.getValue());
            }
        }

Time complexity of this solution is O(2n) because we are iterating over array twice and space complexity is same as previous solution O(n). In worst case you would need a hash table with size of array itself.





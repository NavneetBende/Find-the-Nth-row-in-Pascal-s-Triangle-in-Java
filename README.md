# Find-the-Nth-row-in-Pascal-s-Triangle-in-Java

Nth row of Pascal’s Triangle in Java
Here, in this page we will discuss the program to find Nth row of pascal’s triangle in Java Programming language. We are given with a non-negative integer and we need to print the Nth row. We are assuming zero based starting of the rows

N-th Row of Pascal's Triangle
Example
Pascal Triangle :
1
1 1
1 2 1
1 3 3 1
1 4 6 4 1 
For N=3,
Output : 1 3 3 1
Method 1 (Using recursion):
Create a recursive function say getRow(int index).
Declare a vector say cur_row
Now, as the 1-st element of every row is 1 so, push 1 in cur_row vector.
Check if index == 0, then return cur_row.
Create a vector to hold the previous row, say prev and set prev = getRow(index-1)
Run a loop from [1, prev.size())
Take variable say curr = prev[i-1] + prev[i]
and push it to cur_row
As the last element of every row is 1 so again push 1 to cur_row vector.
And return cur_row
Method 1 : Code in Java
Run
import java.util.ArrayList;
public class Main {
 
    public static ArrayList getRow(int rowIndex)
    {
        ArrayList <Integer> currow = new ArrayList();
        
        currow.add(1);
 
        if (rowIndex == 0) {
            return currow;
        }
        
        ArrayList <Integer> prev = getRow(rowIndex- 1);
 
        for (int i = 1; i < prev.size(); i++) {

            int curr = prev.get(i - 1) + prev.get(i);
            currow.add(curr);
        }
        currow.add(1);
 
        
        return currow;
    }
 
    // Driver Program
    public static void main(String[] args)
    {
        int n = 3;
        ArrayList arr = getRow(n);
 
        for (int i = 0; i < arr.size(); i++) {
            if (i == arr.size() - 1)
                System.out.print(arr.get(i));
            else
                System.out.print(arr.get(i)  + ", ");
        }
    }
}
Output :
1, 3, 3, 1
Method 2 :
In this method we will discuss the efficient way to find the Nth row of the triangle.

Nth row = nC 0 nC1 nC2 … nCn
So, by using the above concept to find the nth row.
nCr = (nCr-1 * (n – r + 1))/r
Take a variable say prev=1 (as, nC0=1)and print prev.
Now, Run a loop from [1, N], take a variable say curr, and set curr = (prev * (N – i + 1)) / i;
And, Print Curr.
Row of Pascal's Triangle
Method 2 : Code in Java
Run
import java.io.*;
 
class Main{

static void generateNthrow(int N)
{
 
    int prev = 1;
    System.out.print(prev);
     
    for(int i = 1; i <= N; i++)
    {
       int curr = (prev * (N - i + 1)) / i;
       System.out.print(", " + curr);
       prev = curr;
    }
}
     
// Driver code
public static void main (String[] args)
{
    int N = 3;
    generateNthrow(N);
}
}
Output :
1, 3, 3, 1

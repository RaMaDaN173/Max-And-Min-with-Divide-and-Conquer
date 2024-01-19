# Max-And-Min-with-Divide-and-Conquer
The Divide and Conquer algorithm is a problem-solving technique that involves breaking down a complex problem into smaller, more manageable subproblems. The approach consists of three main steps:

1. Divide: Break the problem into smaller, independent subproblems. This step involves partitioning the problem into more manageable parts.

2. Conquer: Solve each subproblem recursively. This step involves finding solutions to the smaller subproblems either directly or by further dividing them into even smaller sub-subproblems.

3. Combine: Combine the solutions of the subproblems to obtain the solution to the original problem. This step involves aggregating the results from the subproblems to construct a solution for the entire problem.

The Divide and Conquer paradigm is often used to efficiently solve problems in various domains, such as sorting algorithms like Merge Sort and Quick Sort, matrix multiplication, and various searching algorithms. By breaking down complex problems into smaller parts and solving them independently, this technique can lead to more efficient and elegant solutions.

---

The provided Java code implements a Divide and Conquer algorithm to find the maximum and minimum values in an array.
The MaxMin_DAC function recursively divides the array into subproblems until reaching base cases (1 or 2 elements), and then combines the results to determine the overall maximum and minimum values.
The program demonstrates the functionality by applying the algorithm to a predefined array and printing the resulting maximum and minimum values.
And use The Pair class in Java defines a simple structure to hold two integer values: MAX and MIN. It provides accessor methods (getMAX and getMIN) to retrieve the values and mutator methods (setMAX and setMIN) to set the values for MAX and MIN. This class is commonly used to store a pair of maximum and minimum values together, such as in algorithms where both values need to be tracked simultaneously.
## Class Pair Code 
    public class Pair {
    
    private int MAX, MIN;

    public int getMAX() {
        return MAX;
    }

    public void setMAX(int MAX) {
        this.MAX = MAX;
    }

    public int getMIN() {
        return MIN;
    }

    public void setMIN(int MIN) {
        this.MIN = MIN;
    }
}

## Main Class With Method Divide and Conquer Algorithm To find Max aand min value in Array

    import java.util.Scanner;

    public class DAC_MAX_MIN {
    public static void main(String[] args) {
        int[] Array = {12, 15, 3, 90, 14, -68, 72, -54, 10, 13, 9, 2, 66};//90 -68
    //        Scanner sc = new Scanner(System.in);
    //        System.out.println("Enter Size Of Array");
    //        int Size = sc.nextInt();
    //        int[] Array = new int[Size];
    //        for (int i = 0; i < Size; i++) {
    //            System.out.println("Enter Element Number " + (i + 1));
    //            int Element = sc.nextInt();
    //            Array[i] = Element;
    //        }
        Pair pair = new Pair();
        pair = MaxMin_DAC(Array, 0, Array.length - 1);
        System.out.println(pair.getMAX());
        System.out.println(pair.getMIN());
    }

    public static Pair MaxMin_DAC(int[] Array, int StartIndix, int EndIndix) {
        Pair P = new Pair();
        if (StartIndix == EndIndix/*List has 1 value*/) {
            P.setMAX(Array[StartIndix]);
            P.setMIN(Array[StartIndix]);
        } else if (EndIndix - StartIndix == 1/*List has 2 values*/) {
            P.setMAX(Math.max(Array[StartIndix], Array[EndIndix]));
            P.setMIN(Math.min(Array[StartIndix], Array[EndIndix]));
        } else/*List has more than 2 values*/ {
            int mid = (EndIndix + StartIndix) / 2;
            Pair Temp/* use in second  */ = new Pair();
            P = MaxMin_DAC(Array, StartIndix, mid);
            Temp = MaxMin_DAC(Array, mid + 1, EndIndix);
            if (Temp.getMAX() > P.getMAX()) {
                P.setMAX(Temp.getMAX());
            }
            if (Temp.getMIN() < P.getMIN()) {
                P.setMIN(Temp.getMIN());
            }
        }
        return P;
    }
    }

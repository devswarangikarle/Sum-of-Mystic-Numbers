# Sum-of-Mystic-Numbers

In a mysterious kingdom, a mathematician named Dev is fascinated by special numbers known as Mystic Numbers. A number is called a Mystic Number with respect to an integer N if it meets the following conditions:
The GCD (Greatest Common Divisor) of the Mystic Number and N is 1.
The LCM (Least Common Multiple) of the Mystic Number and N is divisible by N.
The Mystic Number cannot have any factor between 2 and N-1 (both inclusive).
Dev’s task is to find the sum of all such Mystic Numbers that are less than or equal to N. Since the result could be very large, the sum must be returned modulo 1000000007.
Can you help Dev calculate the sum of these Mystic Numbers?

import java.util.Scanner;  
  
public class Main {  
   public static void main(String[] args) {  
      Scanner scanner = new Scanner(System.in);  
      int n = scanner.nextInt();  
      System.out.println(calculateSumOfMysticNumbers(n));  
   }  
  
   public static long calculateSumOfMysticNumbers(int n) {  
      boolean[] isPrime = new boolean[n + 1];  
      for (int i = 0; i <= n; i++) {  
        isPrime[i] = true;  
      }  
      isPrime[0] = isPrime[1] = false;  
  
      for (int i = 2; i * i <= n; i++) {  
        if (isPrime[i]) {  
           for (int j = i * i; j <= n; j += i) {  
              isPrime[j] = false;  
           }  
        }  
      }  
  
      long sum = 1; // 1 is a Mystic Number  
      for (int i = 2; i <= n; i++) {  
        if (isPrime[i]) {  
           sum = (sum + i) % 1000000007;  
        }  
      }  
  
      return sum;  
   }  
}

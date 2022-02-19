# Data Structure and Algorithms

## Mathematics


#### Arithmetic and Geometric Progressions
        AP:
        2,4,6,8,10.......

        an: In this sequence '2' is the first term and denoted by a = 2.
        d = comman difference
        second term = a+d
        third term = a+2d
        .
        .
        a+(n-1)d -> nth term

      **Average = sum/n
        Sum = avg*n

            = ((first+last)/2)*n
            =n/2(a+a+(n-1)d)
        Sum =n/2[2a+(n-1)d].

        --------------

        GP: ratio of two conservative term is same in below example is r= 2.
        2,4,8,16,32...........

        r = ratio of two conservative term.
        ar = second term
        ar^2 = third term
        .
        .
        .
        ar^(n-1) = nth term

        Sum = a(1-r^n)/1-r


#### Quadratic Equations.
    ax^2 + bx + c = 0 

    roots : values of x which satisfy this equation.
    
    Note: In quadratic equation there are two max root.
    this all depend on a factor which is called descriminant.

    D = b^2 - 4ac

    x = (-b(+-)+D^1/2)/2a

    if D<0 : imaginary roots
       D=0 : two equal roots
       D>0 : two distinct roots




#### Mean and Meadian.
    Mean: The mean is found by adding up all of the given data and dividing
          by the number of data entries.
    
    Example: the mean of 4,1,and 7 is (4+1+7)/3 = 12/3 = 4

    Meadian : The middle number; found by ordering all data points and picking
              out of the one in the middle( or if there are two middle numbers,
              taking the mean of those two numbers).

    Example: The median of 4,1 and 7 is 4 bcz when the numbers are put in order {1,4,7}
             the number 4 is the middle.   








#### Prime Numbers.
      A number which is divisible by 1 and itself called prime number.

     first few prime numbers are: 2,3,5,7,11......

     Facts:
     * Every prime number can represented in form of 6n+1 or 6n-1 except 2 
       and 3, where n is natural number.
     *Two and Three are only two consecutive natural numbers which are prime
      too.








#### LCM and HCF.

    Factors: All the numbers that divide a number completely, i.e., without 
             leaving any remainder, are called factors of that number.
    Example: 24 is completely divisible by 1,2,3,4,6,8,12,24.
             Each of these are the factor of 24. and 24 is called a multiple
             of each of these numbers.



    LCM: The Least Common Multiple, or LCM, of two or more number is the smallest
         number other than zero that's a multiple of each number.
    Example: LCM OF 4 and 6?.
        Multiple of 4:    4,8,12,16,20,24.........
        Multiple of 6:    6,12,18,24........
        Least Common Multiple : 12. That is the answer.


    HCF: HCF of two or more given numbers is the highest number which exactly 
         divides all the numbers.


    Example: HCF of 12 and 16?.
    Factor of 12: 1,2,3,4,6,12..........
    Factor of 16: 1,2,4,8,16............
    Common Factors : 1,2,4
    Highest Common Factor : 4








#### Factorials.
    * Factorial of a positive integer n, denoted by n!, is the product of all
      positive integers less than or equal to n.

    * 0! = 1
    * n! = 1*2*3*4............*(n-1)*(n-2)*n






#### Permutations and Combinations.
     * Permutation: is defined as arrangement of r things that can be done
                    out of total n things.
            This is denoted by nPr, which is equal to n!/(n-r)!.


     * Combination : Combination is defined as selection of r things that can
                     be done out of total n things.

            This is denoted by nCr, which is equal to n!/r!(n-r)!







#### Modular(%) Arithmetic.
     * The remainder obtained after the division operation on two operands 
       is known as modulo operation.

     * For ex: a%b = c which means when a is divided by b it gives the 
       remainder c, 7%2=1, 17%3=2









### Count Digits
#### Find Number of Digits in a Number ->
        Iterative Solution:->
            int countDigit(long n){
                int count = 0;
                while(n!=0){
                    n=n/10;
                    ++count;
                }
                return count;
            }

        Recursive Solution:->
            int countDigit(long n){
                if(n==0)
                    return 0;
                return 1+countDigit(n/10);
            }

        Logarithmic Solution
            int countDigit(long n){
                return floor(log10(n)+1);
            }







### Palindrome Numbers
    if the reverse of number is same as the number than it called 
    palindrome numbers.
    Example: n = 78987 , rev = 78987 => palindrome
    n=21-> not
    n=3-> yes

    Note: Each single digit number is always a palindrome number.

    {rev = rev*10 + n%10
    n = n/10}

    boolean isPal(int n){
        int rev = 0;
        int temp = n;
        while(temp!=0){
            int ld = temp%10;
            rev = rev*10+ld;
            temp = temp/10;
        }
        return (rev==n);
    }





### Factorial of a Numbers
    //iterative solution
    int fact(int n){
        int res = 1;
        for(int i=2;i<=n;i++){
            res = res*i;
        }
        return res;
    } Tn=O(n), Sn = O(1).


    //recursivly solution
    int fact(int n){
        if(n==0)
            return 1;
        return n*fact(n-1);
    }
    Tn = T(n-1)+c
    Tn = O(n),Sn = O(n).







### Trailing Zeros in Factorial
    After calculating factorial of a number count total number of zero 
    in the end.

    Example:
    ip: n=5         op: 1   [1*2*3*4*5=120 /here is only one zero]

    ip: n=10        op: 2   [1*2*3*4*5*6*7*8*9*10=3628800]

    ip: n=100       op: 24

    //Naive Solution.
    int countZero(int n){
        int fact = 1;
        for(int i=2;i<=n;i++)
            fact = fact*i;
        int res = 0;
        while(fact%10 == 0){
            res++
            fact = fact/10;
        }
        return res;
    }
    Tn = theta(n).
    
    Note: for large number int size overflow.


    //Efficient Solution.
    
    1*2*3*4*5*6*7*8*9*10*11*12*13*14*15*.....*25......*n
            |          |                       |.....



    Trailing zero count=[n/5]+[n/25]+[n/125]+.........



    int countTrailingZeros(int n){
        int res = 0;
        for(int i=5;i<=n;i++)
            res = res+n/i;
        return res;
    }






### GCD or HCF of two Numbers
    Largest number which can divide both number.
    [largest square which can fill the a*b square]
    Example:
    a=4, b=6   => op: 2
    ip: a=100, b=200   => op:100
    ip: a=7,b=13    => op: 1


    Naive Solution                    |     a = 10,b=15
    int gcd(int a,int b){             |     res = 10
        int res = Math.min(a,b);      |     res = 9
        while(res>0){                 |     res = 8
            if(a%res==0 && b%res==0)  |     res = 7
                break;                |     res = 6
            res--;                    |     res = 5
        }                             |
        return res;
    }
    Tn = O(min(a,b));



    -------- Eucliclean Algorithm
    Basic Idea: Let 'b' be smaller than 'a'
                    gcd(a,b) = gcd(a-b,b)
    Why?    
        let 'g' be gcd of 'a' and 'b'
            a = gx, b=gy and gcd(x,y)=1;
            (a-b)=g(x-y);



        int gcd(int a, int b){  |   a=12,   b=15
            while(a!=b){        |   a=12,   b=3
                if(a>b)         |   a=9,    b=3
                    a=a-b;      |   a=6,    b=3
                else            |   a=3,    b=3
                    b=b-a       | return anyone when both are equals
            }
            return a;
        }
        -------------optimized Implementation
        int gcd(int a,int b){
            if(b==0)
                return a;
            else
                return gcd(b,a%b);
        }





### LCM of Two Numbers 
    ip: a=4,b=6        op: 12   |ip: a=3,b=7    op:21
    ip: a=12,b=15      op: 60   |ip: a=2,b=8    op:8


    //Naive Solution.
    int lcm(int a,int b){
        int res = Math.max(a,b);
        while(true){
            if(res%a==0 && res%b==0)
                return res;
            res++;
        }
        return res;
    }
    Tn = O(a*b-max(a,b));




    //Efficient Solution.
    int gcd(int a,int b){
        if(b==0)
            return a;
        return gcd(b,a%b);      --->O(log(min(a,b)));
    }
    int lcm(int a,int b){
        return (a*b)/gcd(a,b);      ---->O(1)
    }
    Tn = O(log(min(a,b)));

    Note: a*b = gcd(a,b)*lcm(a,b);











### Check for Prime
    A number said to be prime which divisibile by it self and 1.

    ip: n=13  => Yes   // 13 has divisors as 1 and 13 only.
    ip: n=14 => No     //14 has divisors as 1,2,7,14.
    ip: n=101 => Yes   //101 has divisors as 1 and 101 only.

    Note: first prime numbers: 2,3,5,7,11,13,17,19,.......

    4,6,8,9,10---->have other factor called composite number.
    1-> is not prime and not composite number.




    //Naive Solution.
    boolean isPrime(int n){
        if(n==1) return false;

        for(int i=2;i<n;i++){
            if(n%i==0)
                return false.
        }
        return true;
    }
    Tn : O(n)







    //Efficient Solution
    
    Idea: Divisors always appear in Pairs.
    30 : (1,30), (2,15), (3,10), (5,6).
    65 : (1,65), (5,13).
    25 : (1,25), (5,5).

    if (x,y) is a Pair x*y=n
        And if x<=y [x is smaller divisor]
               x*x<=n
               x<=n^1/2;



    boolean isPrime(int n){
        if(n==1) return false;
        for(int i=2;i*i<=n;i++){
            if(n%i==0)
                return false;
        }
        return true;
    }
    Tn : O(n^1/2).








    //more Efficienct (for largs n).
    Values of i for large n.

    2,3,4,5,6,7,8,9,10,11,12,13,14,15,16,17,18,19,20,21,22........n^1/2.

    Idea: By checking n%2==0 and n%3==0, we can save many iterations for large n.
    we don't need to check multiple of 2 and 3.

    like for 2: 4,6,8,10,12.....
         for 3: 3,6,9,12,15,18,21....



    boolean isPrime(int n){
        if(n==1) return false;
        if(n==2 || n==3) return true;

        if(n%2==0 || n%3==0)
            return false;
        for(int i=5;i*i<=n;i=i+6)
            if(n%i==0 || n%(i+2)==0)
                return false;
        return true;
    }

    it is 3 time faster than efficient approach.









### Prime Factors
    All the devisor of a number which is prime.

    ip: n=12             n>1
    op: 2 2 3

    ip: n=13
    op: 13

    ip: n=315
    op: 3 3 5 7



    //Naive Solution
    void primeFactors(int n){
        for(int i=2;i<=n;i++){
            if(isPrime(i)){
               int x = i;
               while(n%x==0){   -> O(log(n))
                   print(i);
                   x=x*i;
               } 
            }
        }
    }

    Tn : O(n^2log(n));



    //Efficient Solution.
    1. Divisors always appear in pairs
        30 : (1,30), (2,15), (3,10), (5,6)
    2. A number n can be written as multiplcations of powers of prime functions
        12 = 2^2*3
        450 = 2^1 * 3^2 * 5^2



    void primeFactor(int n){      | n=450   
        if(n<=1) return;          | i=2;
                                  | print(2)---------
        for(int i=2;i*i<=n;i++){  | n = 225
            while(n%i==0){        | i=3;
                print(i);         | print(3);---------
                n = n/i;          | n=75
            }                     | print(3);---------
        }                         | n=25;
        if(n>1)                   | i=4;
            print(n);             | i=5;
    }                             | print(5);---------
                                  | n=5;
                                  | print(5);---------
                                  | n=1;
                            Note: 450 = 2^1 * 3^2 * 5^2



    // more Efficient Solution.
    void printPrimeFactors(int n){
        if(n<=1) return ;

        while(n%2==0){ ------------> check for 2
            print(2); n = n/2;
        }
        while(n%3==0){  -----------> check for 3
            print(3); n = n/3;
        }
        for(int i=5;i*i<=n;i=i+6){
            while(n%i==0){
                print(i); n= n/i;
            }
            while(n%(i+2)==0){
                print(i+2);
                n=n/(i+2);
            }
        }
        if(n>3)
            print(n);
    }

    Tn : theta(n^1/2) for composit number.













### All Divisors of a Number


















### Sieve of Eratosthenes
















### Computing Power














### Iterative Power

























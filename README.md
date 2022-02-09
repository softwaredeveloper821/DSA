# Data Structure and Algorithms

## Introduction:
-----------------
### Analysis of Algorithms(Background):
    It is helpfull for analysis that which algorithm is best in terms of 
    space and time complexity.

    Example:    Poblem: Find sum of first N natural Number.

    input:  n=3
    output: b   //1+2+3

    input:  n=5
    output: 15  //1+2+3+4+5

    Three different solution are:

        int fun1(int n){
            return n+(n+1)/2;
        }
        -------------
        int fun2(int n){
            int sum =0;
            for(int i=1;i<=n;i++){
                sum+=i;
            }
            return sum;
        }
        ------------
        int fun3(int n){
            int sum =0;
            for(int i=1;i<=n;i++){
                for(int j=1;j<=i;j++){
                    sum++;
                }
            }
            return sum;
        }


### Asymptotic Analysis:
        * The idea is to measure order of growth.
        * Does not depend upon machine, programming language, etc.
        * No need to implement, we can analyze algorithms.

                Example: sum of first n natural numbers.

                int fun1(int n){
                    return n+(n+1)/2;
                }   
                Time Taken fn : C
                -------------
                int fun2(int n){
                    int sum =0;
                    for(int i=1;i<=n;i++){
                        sum+=i;
                    }
                    return sum;
                }
                Time Taken fn : c2n+c3
                ------------
                int fun3(int n){
                    int sum =0;
                    for(int i=1;i<=n;i++){
                        for(int j=1;j<=i;j++){
                            sum++;
                        }
                    }
                    return sum;
                }
                Time Taken fn : c4n^2 + c5n+c6

       
       Direct Way to Find and Compare Growths:
            1. Ignore Lower Order Terms
            2. Ignore Leading Terms Constant

       How do we Compare terms?. : Growths orders terms

            C < loglogn < logn < n^1/3 < n^1/2 < n < n^2 < n^3 < n^4 < 2^n < n^n 



### Best, Average and Worst Cases:

        Example: Simple function with same order of growth for every input.

        int getSum(int arr[],int n){
            int sum = 0;
            for(int i=0;i<n;i++){
                sum = sum + arr[i];
            }
            return sum;
        }

        Time Taken : c1n+c2
        order of growith : n

        -------------
        Example:
            int getSum(int arr[],int n){
            if(n%2==0)
                return 0;
            int sum = 0;
            for(int i=0;i<n;i++){
                sum = sum+arr[i];
            }
            return sum;
        }

        -------------
        Example: Multiple orders of Growths.
        
        Best Case: Constant.
        Average Case: Liner(under the assumption that even and odd cases are equally likely).
        Worst Case: Liner.



### Asymptotic Notations:
        are the mathematic notation to represent order of mathematical function.

        There are manly three types of notation.
            1. Big O : Exact or Upper
            2. Theta : Exact
            3. Omega : Exact or Lower(not majorly used)

        Example: Linear Search.

            int search(int arr[],int n,int x){     //arr[] = {10,15,30,40,80}
                for(int i=0;i<n;i++){
                    if(arr[i]==x){
                        return i;
                    }
                }
                return -1;
            }

            Tn  : O(n)-> c1n + c2



            Note:
                    theta(1) & O(1)  = contant.
                    But Omega(1) = constant or greater than it.


### Analysis of Common Loops:
        n: User Input
        c: constant
                    -------------------
                        for(int i=0;i<n;i=i+c){
                            //some theta(1).
                        }
                n=10 & c=0 loop run 5 time
                n=20 & c=5 loop run 4 time  

                        Loop Runs [n/c] times Tn : theta(n).     //constant ignore.
                    -----------------------
                        for(int i=n;i>0;i=i-c){
                            
                           
                        }



                    -------------------
                    :O(1)-> if doesn't contain loop/[run for fix number of time], recursion and
                                call to any other non-constant time function.

                    //Here c is a constant.....
                    for(int i=1;i<=c;i++){
                        //some O(1) expression
                    }
                    Tn : O(1)


                    ------------------
                    O(n): if loop variables incrementd/decremented by a contant amount.

                    //Here c is a positive integer constant
                    for(int i=1;i<=n;i+=c){
                        //some O(1) expressions
                    }

                    for(int i=n;i>0;i-=c){
                        //some O(1) expressions
                    }
                    Tn : O(n)


                    ------------------
                    O(n^2): Tn of nexted loops is equals to the number of times the innermost statement
                            is executed. 
                    for(int i=1;i<=n;i+=c){
                        for(int j=1;j<=;j+=c){
                            /some O(1) expressions
                        }
                    }

                    for(int i=n;i>0;i-=c){
                        for(int j=i+1;j<=n;j+=c){
                            //some O(1) expressions.
                        }
                    }
                    Tn = O(n^2).


                    -------------------
                    O(long(n)): if loop is considered as O(log(n)) if the loop variables is devided/multipled by a 
                                constant amount.

                    for(int i=1;i<=n;i*=c){
                        //some O(1) expressions.
                    }

                    for(int i=n;i>0;i/=c){
                        //some O(1) expressions
                    }
                    Tn = O(Log(n)).

                    ------------------
                    O(loglog(n)): Tn of a loop is considered as O(loglog(n)) if the loop variables is 
                    reduced/increased exponentially by a constant amount.

                    for(int i=2;i<=n;i=pow(i,c)){
                        //some O(1) expresseion.
                    }


                    //Here fun() is fun() is function to find square root or cuberoot
                    // or any other constant root.
                    for(int i=n;i>1;i=fun(i)){
                        //som O(1) expression
                    }

            Note: for consecutive loops, we calculate time complexity as sum of time complexities of
            individual loops.

                    for(int i=1;i<=m;i+=c){
                        //some O(1) expressions
                    }

                    for(int i=1;i<=n;i+=c){
                        //some O(1) expressions
                    }

                Time complexity of above code is O(m)+O(n) which is O(m+n)
                if m==n, the time complexity becomes O(2n) which is O(n).

    
    How to calculate time complexity when there are many if, else statements inside loops?:
    As discussed earlier, the worst-case time complexity is the most useful among best, average and
    worst. Therefore we need to consider the worst case. We evaluate the situation when values in if-else 
    conditions cause a maximum number of statements to be executed.

    For example, consider the linear search function where we considered the case when an element is 
    present at the end or not present at all.

    When the code is too complex to consider all if-else cases, we can get an upper bound by ignoring
    if else and other complex control statements.






























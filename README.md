 Console.Write("Enter a number: ");
            int number = Convert.ToInt32(Console.ReadLine());
            
            if (IsHappyNumber(number))
            {
                Console.WriteLine($"{number} is a happy number :D");
            }
            else
            {
                Console.WriteLine($"{number} is a sad number :(");
            }
        }

        static bool IsHappyNumber(int num)
        {
            int slow = num;
            int fast = GetNext(num);

            // Floyd's cycle detection
            while (fast != 1 && slow != fast)
            {
                slow = GetNext(slow);
                fast = GetNext(GetNext(fast)); 
            }

            return fast == 1;
        }

        // Computes the sum of squares of digits
        static int GetNext(int n)
        {
            int sum = 0;
            while (n > 0)
            {
                int digit = n % 10;
                sum += digit * digit;
                n /= 10;
            }
            return sum;

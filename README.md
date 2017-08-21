# date_calculator
using System;
using System.Globalization;

namespace dateCalculator
{
    class Program
    {
        static void Main()
        {
            bool error = false;
            DateTime endTime = new DateTime(), startTime = new DateTime();  
            do
            {
                if (error)
                {
	                Console.WriteLine("Invalid input!");
                }

				error = false;
                Console.WriteLine("Please insert the first date(mm-dd-yyyy): ");
                try
                {
                    startTime = DateTime.ParseExact(Console.ReadLine(), "mm-dd-yyyy", CultureInfo.InvariantCulture);
                }
                catch (Exception)
                {
                    error = true;
                }
            } while (error);
            do
            {
                if (error)
					
                    Console.WriteLine("Invalid input!");
					
                error = false;
                Console.WriteLine("Please insert the second date(mm-dd-yyyy): ");
                try
                {
                    endTime = DateTime.ParseExact(Console.ReadLine(), "mm-dd-yyyy", CultureInfo.InvariantCulture);
                }
                catch (Exception)
                {
                    error = true;
                }
            } while (error);

            TimeSpan span = endTime.Subtract(startTime);
            int days = span.Days;
            if (days < 0)
                days *= -1; 

            String spanMsg = string.Format("{0} years, {1} months, {2} days, {3} hours, {4} minutes, {5} seconds",
                days / 365, days / 12, days, days * 24, days * 24 * 60, days * 24 * 60 * 60);
            Console.WriteLine(spanMsg);
            Console.ReadLine();
            
            
        }
    }
}

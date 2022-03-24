# Assignment3

Create a new project in Visual Studio.
Copy the following code into the .cs file.
Run program.


using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Threading.Tasks;

namespace A2CavanaghLonnyP1L

{
    class Program
    {
        static void Main(string[] args)
        {
            //Declare Variables.
            decimal adjustedCost;
            decimal refSubCost;
            decimal subCost;
            decimal taxedCost;
            decimal totalAdjustment;
            decimal totalBeforeTaxes;
            decimal totalTaxes;
            int customerAge;
            string age;
            string currency;
            string month;
            string name;
            string referral;

            //Initialize Varaibles.
            age = "";
            currency = "";
            customerAge = 0;
            month = "";
            adjustedCost = 0;
            name = "";
            referral = "";
            refSubCost = 0;
            subCost = 0;
            taxedCost = 0;
            totalAdjustment = 0;
            totalBeforeTaxes = 0;
            totalTaxes = 0;

            Console.WriteLine("Welcome to Fun Times Books!");

            Console.Write("Please enter your name: ");
            name = Console.ReadLine();

            Console.Write("Please enter your age: ");
            age = Console.ReadLine();
            customerAge = int.Parse(age);

            Console.WriteLine("Please note, Fun Times Books only accepts BTC, CAD, and USD.");
            Console.Write("Please enter the currency you will be using: ");
            currency = Console.ReadLine();

            Console.Write("Were you referred to Fun Times Books by an existing client? Y/N: ");
            referral = Console.ReadLine();

            Console.Write("Please enter the month you wish to start your subscription (01 - 12): ");
            month = Console.ReadLine();

            //Calculate age based Subscription Fee.
            if (customerAge <= 19)
            {
                subCost = 37.00M;
            }
            else if (customerAge >= 20 && customerAge < 30)
            {
                subCost = 50.00M;
            }
            else if (customerAge >= 30 && customerAge < 64)
            {
                subCost = 53.50M;
            }
            else if (customerAge > 64)
            {
                subCost = 0.00M;
            }

            //Apply referral discount.
            if (referral == "Y" || referral == "y")
            {
                refSubCost = subCost - 50;
            }
            else
            {
                refSubCost = subCost;
            }

           //Apply start month adjustment.
            switch (month)
            {
                case "01":
                    adjustedCost = refSubCost - 2M;
                    break;
                case "02":
                    adjustedCost = refSubCost - 2M;
                    break;
                case "03":
                    adjustedCost = refSubCost - 2M;
                    break;
                case "04":
                    adjustedCost = refSubCost - 2M;
                    break;
                case "05":
                    adjustedCost = refSubCost + 25M;
                    break;
            }

            //Apply Taxes.
            if (customerAge <= 19)
            {
                taxedCost = adjustedCost * 1M;
            }
            else if (customerAge >= 20 && customerAge < 30)
            {
                taxedCost = adjustedCost * 1.22M;
            }
            else if (customerAge >= 30 && customerAge < 64)
            {
                taxedCost = adjustedCost * 1.22M;
            }
            else if (customerAge > 64)
            {
                taxedCost = adjustedCost * 1M;
            }

            //Round decimal to two places.
            taxedCost = decimal.Round(taxedCost, 2);
            
            // Determine total taxes.
            totalTaxes = taxedCost - adjustedCost;

            //Set negative amount to zero.
            if (totalTaxes <= 0)
            {
                totalTaxes = 0.00M;
            }
            else
            {
                totalTaxes = totalTaxes;
            }

            //Determine total adjustment.
            totalAdjustment = adjustedCost - subCost;
            
            //Determine total before taxes.
            totalBeforeTaxes = taxedCost - totalTaxes;

            //Set negative amount to zero.
            if (taxedCost <= 0)
            {
                taxedCost = 0.00M;
            }
            else
            {
                taxedCost = taxedCost;
            }

            Console.WriteLine();
            Console.WriteLine(name + ", your charges are as follows: ");
            Console.WriteLine("Registration Fee: " + subCost);
            Console.WriteLine("Total Adjustments: " + totalAdjustment);
            Console.WriteLine("Total Before Taxes: " + adjustedCost);
            Console.WriteLine("Total Taxes Due: " + totalTaxes);
            Console.WriteLine("Total Amount Due: " + taxedCost + " " + currency);

            if (taxedCost > 0.00M)
            {
                Console.WriteLine("Thank you!  Upon receipt of payment, your subscription will start 01/" + month + " of this year.");
            }
            else
            {
                Console.WriteLine("Thank you!  Your subscription will start 01/" + month + " of this year.");
            }
        }
    }
}

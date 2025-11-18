using System;

namespace GiaiPhuongTrinh
{
    
    class LinearEquation
    {
        protected double a, b;

        public LinearEquation(double a, double b)
        {
            this.a = a;
            this.b = b;
        }

        public virtual void Solve()
        {
            if (a == 0)
            {
                if (b == 0)
                    Console.WriteLine("Phuong trinh vo so nghiem.");
                else
                    Console.WriteLine("Phuong trinh vo nghiem.");
            }
            else
            {
                double x = -b / a;
                Console.WriteLine($"Nghiem cua phuong trinh bac 1: x = {x}");
            }
        }
    }

    
    class QuadraticEquation : LinearEquation
    {
        private double c;

        public QuadraticEquation(double a, double b, double c) : base(a, b)
        {
            this.c = c;
        }

        public override void Solve()
        {
            if (a == 0)
            {
                Console.WriteLine("a = 0 → Phuong trinh tro thanh bac 1:");
                base.Solve();  
                return;
            }

            double delta = b * b - 4 * a * c;

            if (delta < 0)
            {
                Console.WriteLine("Phuong trinh vo nghiem.");
            }
            else if (delta == 0)
            {
                double x = -b / (2 * a);
                Console.WriteLine($"Phuong trinh co nghiem kep: x = {x}");
            }
            else
            {
                double x1 = (-b + Math.Sqrt(delta)) / (2 * a);
                double x2 = (-b - Math.Sqrt(delta)) / (2 * a);
                Console.WriteLine($"Phuong trinh co 2 nghiem phan biet: x1 = {x1}, x2 = {x2}");
            }
        }
    }

    
    class Program
    {
        static void Main(string[] args)
        {
            Console.Write("Nhap a: ");
            double a = double.Parse(Console.ReadLine());

            Console.Write("Nhap b: ");
            double b = double.Parse(Console.ReadLine());

            Console.Write("Nhap c: ");
            double c = double.Parse(Console.ReadLine());

            QuadraticEquation qe = new QuadraticEquation(a, b, c);

            Console.WriteLine("\n--- KET QUA ---");
            qe.Solve();

            Console.WriteLine("\nNhan Enter de thoat...");
            Console.ReadLine();
        }
    }
}

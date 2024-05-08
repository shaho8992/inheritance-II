# inheritance-II

//using System;
//using System.Collections.Generic;
//using System.Linq;
//using System.Text;
//using System.Threading.Tasks;

//namespace Inheritance_11
//{

//    class A
//    {
//        public int i = 0;
//    }
//    // Create a derived class.
//    class B : A
//    {
//        int i; // this i hides the i in A
//        public B(int b)
//        {
//            i = b; // i in B
//        }
//        public void Show()
//        {
//            Console.WriteLine("i in derived class: " + i);
//        }
//    }



//    internal class Program
//    {
//        static void Main(string[] args)
//        {

//            B ob = new B(2);
//            ob.Show();

//        }
//    }
//}

/*using System;
class A
{
    public int i = 0;
}
// Create a derived class.
class B : A
{
    int i; // this i hides the i in A
    public B(int a, int b)
    {
        base.i = a; // this uncovers the i in A
        i = b; // i in B
    }
    public void Show()
    {
        // This displays the i in A.
        Console.WriteLine("i in base class: " + base.i);
        // This displays the i in B.
        Console.WriteLine("i in derived class: " + i);
    }
}

namespace Inher1
{
    class Program
    {
        static void Main(string[] args)
        {
            B ob = new B(1, 2);
            ob.Show();
        }
    }
}
*/

/////////////////////////////////////////Creating a Multilevel Hierarchy
///




/*using System;

///
class TwoDShape
{
    double pri_width;
    double pri_height;
    // Default constructor.
    public TwoDShape()
    {
        Width = Height = 0.0;
    }
    // Constructor for TwoDShape.
    public TwoDShape(double w, double h)
    {
        Width = w;
        Height = h;
    }
    // Construct object with equal width and height.
    public TwoDShape(double x)
    {
        Width = Height = x;
    }
    // Properties for Width and Height.
    public double Width
    {
        get { return pri_width; }
        set { pri_width = value < 0 ? -value : value; }
    }
    public double Height
    {
        get { return pri_height; }
        set { pri_height = value < 0 ? -value : value; }
    }
    public void ShowDim()
    {
        Console.WriteLine("Width and height are " +
        Width + " and " + Height);
    }
}
// A derived class of TwoDShape for triangles.
class Triangle : TwoDShape
{
    string Style; // private
    /* A default constructor. This invokes the default
    constructor of TwoDShape. */
/* public Triangle()
 {
     Style = "null";
 }
 // Constructor.
 public Triangle(string s, double w, double h)
     : base(w, h)
 {
     Style = s;
 }
 // Construct an isosceles triangle.
 public Triangle(double x)
     : base(x)
 {
     Style = "isosceles";
 }
 // Return area of triangle.
 public double Area()
 {
     return Width * Height / 2;
 }
 // Display a triangle's style.
 public void ShowStyle()
 {
     Console.WriteLine("Triangle is " + Style);
 }
}

// Extend Triangle.
class ColorTriangle : Triangle
{
 string color;
 public ColorTriangle(string c, string s,
 double w, double h)
     : base(s, w, h)
 {
     color = c;
 }
 // Display the color.
 public void ShowColor()
 {
     Console.WriteLine("Color is " + color);
 }
}

namespace Inher1
{
 class Program
 {
     static void Main(string[] args)
     {
         ColorTriangle t1 =
        new ColorTriangle("Blue", "right", 8.0, 12.0);
         ColorTriangle t2 =
         new ColorTriangle("Red", "isosceles", 2.0, 2.0);
         Console.WriteLine("Info for t1: ");
         t1.ShowStyle();
         t1.ShowDim();
         t1.ShowColor();
         Console.WriteLine("Area is " + t1.Area());
         Console.WriteLine();
         Console.WriteLine("Info for t2: ");
         t2.ShowStyle();
         t2.ShowDim();
         t2.ShowColor();
         Console.WriteLine("Area is " + t2.Area());
     }
 }
}
*/





////////////////////////////////////When Are Constructors Called?


/*using System;
// Create a base class.
class A
{
    public A()
    {
        Console.WriteLine("Constructing A.");
    }
    ~A()
    {
        Console.WriteLine("Destructing A.");
    }
}
// Create a class derived from A.
class B : A
{
    public B()
    {
        Console.WriteLine("Constructing B.");
    }
    ~B()
    {
        Console.WriteLine("Destructing B.");
    }

}
// Create a class derived from B.
class C : B
{
    public C()
    {
        Console.WriteLine("Constructing C.");
    }
    ~C()
    {
        Console.WriteLine("Destructing C.");
    }

}
namespace Inher1
{
    class Program
    {
        static void Main(string[] args)
        {
            C c = new C();

            c = null;
        }
    }
}
*/


//////////////////////////////////////////Base Class References and Derived Objects


// This program will not compile.

/*using System;

///
class X
{
    public int a;
    public X(int i)
    {
        a = i;
    }
}
class Y : X
{
    public int b;
    public Y(int i, int j)
        : base(j)
    {
        b = i;
    }
}

namespace BaseRef
{
    class Program
    {
        static void Main(string[] args)
        {
            X x = new X(10);
            X x2;
            Y y = new Y(5, 6);
            x2 = x; // OK, both of same type
            Console.WriteLine("x2.a: " + x2.a);

            x2 = y; // OK because Y is derived from X
            Console.WriteLine("x2.a: " + x2.a);
            // X references know only about X members

            x2.a = 19; // OK
            // x2.b = 27; // Error, X doesn't have a b member
        }
    }
}
*/

////////////////////////////////Using sealed to Prevent Inheritance

//using System;

/////
//class GenericDemo
//{
//    static void Main()
//    {
//        object[] ga = new object[10];
//        // Store ints.
//        for (int i = 0; i < 3; i++)
//            ga[i] = i;
//        // Store doubles.
//        for (int i = 3; i < 6; i++)
//            ga[i] = (double)i / 2;
//        // Store two strings, a bool, and a char.
//        ga[6] = "Hello";
//        ga[7] = true;
//        ga[8] = 'X';
//        ga[9] = "end";
//        for (int i = 0; i < ga.Length; i++)
//            Console.WriteLine("ga[" + i + "]: " + ga[i] + " ");
//    }
//}

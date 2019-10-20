# Coding
C++ 基础

1、变量命名的要求
C++规定标识符只能由字母、数字和下划线3种字符组成，且第一个字符必须为字母或下划线。
定义变量：C语言要求变量的定义应该放在所有的执行语句之前，而C++则放松了限制，只要求在第一次使用该变量之前进行定义即可。
“先定义，后使用”的目的是：
1）编译时候检查变量是否经过声明，方便用户发现错误，避免变量名使用时出错；
2）在编译的时候可以分配存储空间；
3）在编译的时候可以检查对变量进行的运算是否合法。

例如：___是合法的变量名。

2、C++的基本数据类型
类型  字节  范围
bool   1   0,1
char   1   -2^7- 2^7-1      0-2^8-1
short int   2
int         4
long int    8
float       4
double      8
long double 16
string     一般为8+，有24，28或40等
size_t      4或8
wchar_t     2 或 4  1 个宽字符

另外变量类型还有枚举、指针、数组、引用、数据结构、类等

（2）枚举类型(enumeration)
枚举：用户定义的若干枚举常量的集合。
使用：enum color{red, blue=5, green} c；//color为，c为变量
默认情况下，若无任何初始化，则按照0，1，2顺序取值；若有初始化，则初始化后面的每个名称都会比它前面一个名称大 1，但 red 的值依然为 0。
注意：1）可以先声明后定义，也可以同时声明和定义；
2）枚举常量只能以标识符形式表示，而不能是整型、字符型等文字常量；
 //enum letter_set { 'a', 'd', 'F', 's', 'T' }; //枚举常量不能是字符常量
 //enum year_set { 2000, 2001, 2002, 2003, 2004, 2005 }; //枚举常量不能是整型常量
3）枚举值是常量不是变量，不能被赋值；
4）枚举变量可以被赋值为同类型的枚举变量或者枚举常量；
5）枚举变量占用内存的大小与整型数相同；
6）枚举变量只能参与赋值和关系运算以及输出操作，常被用在switch语句中。
链接：https://www.runoob.com/w3cnote/cpp-enum-intro.html

（3）常量
整型常量：前缀0x表示16进制，0开头表示8进制，无前缀表示10进制，后缀u或者表示无符号数，l或者L表示长整数
浮点常量：当使用小数形式表示时，必须包含整数部分、小数点，小数部分，或同时包含两者（.14159表示0.14159）。当使用指数形式表示时， 必须包含小数点、指数，或同时包含两者（314159E-5L表示3.14159）。
布尔常量：true 或者 false
字符常量：
字符串常量：括在双引号 "" 中的，包含普通的字符、转义序列和通用的字符。

局部变量：在函数内部定义，只能被函数内部或者代码块内部的语句使用，需要用户自行初始化。
全局变量：在函数外部定义（程序头），可以被任何函数访问，值会被系统默认初始化为0或nullptr，全局变量的值在程序的整个生命周期内都是有效的。
注意：函数内，局部变量的值会覆盖全局变量的值。

（4）运算符：
算术运算符：+ - * / % ++ --（7）
逻辑运算符：||  &&  ！ （3）
关系运算符：> >= < <= == !=   （6）
位运算符：|  &  ^  ~  >>  <<   （6）
赋值运算符： =  （11=1+5+5）
其他运算符：sizeof（返回变量的大小），（顺序执行一系列运算） .  ->（成员运算符）  Condition? A: B(三目运算符)
 Cast（强制数据类型转换） &（返回变量的地址）  *（指向一个变量）     （8）
 
 优先顺序：


（5）
循环类型  while  do while  for
判断类型   if...else  switch

C++ 中的函数定义的一般形式如下：
return_type function_name( parameter list ) { body of the function }
返回类型、函数名称、参数列表（函数参数的类型、顺序、数量）、函数主体

调用类型： 
传值调用（把参数的实际值复制给函数的形式参数）
指针调用（把参数的地址复制给形式参数）
引用调用（把参数的引用复制给形式参数）
区别：传递效率、执行效率


typedef 作用：为一个已有的类型取一个新的名字。
使用方法：typedef int feet;  feet dis;
 
typedef enum Suit { Diamonds, Hearts, Clubs, Spades } mySuit;
mySuit a;
mySuit b, c;

typedef enum Suit { Diamonds, Hearts, Clubs, Spades } Suit;
enum Suit a;
enum Suit b, c;  //为什么？

typedef enum Suit { Diamonds, Hearts, Clubs, Spades };
enum Suit a;
enum Suit b, c;  //为什么？

switch参数的类型要求
switch 语句中的 expression 必须是一个整型或枚举类型，或者是一个 class 类型，其中 class 有一个单一的转换函数将其转换为整型或枚举类型。
传递给 switch 和case 语句的参数应该是enum、 int、 short、 char 或者 byte（因为byte,short,char都可以隐含转换为int）。

数据类型修饰符：
signed
unsigned
long
short

C++ 中的类型限定符
类型限定符提供了变量的额外信息。

const
const 类型的对象在程序执行期间不能被修改改变。
volatile
修饰符 volatile 告诉编译器不需要优化volatile声明的变量，让程序可以直接从内存中读取变量。对于一般的变量编译器会对变量进行优化，将内存中的变量值放在寄存器中以加快读写效率。volatile 往往会用于多线程的修饰。
restrict
由 restrict 修饰的指针是唯一一种访问它所指向的对象的方式。只有 C99 增加了新的类型限定符 restrict。
explicit
声明为explicit的构造函数不能在隐式转换中使用。explicit构造函数只能被显式调用。

定义
使用关键字：define或者const
#define identifier value   例如：#define id 1
const type variable = value;   例如：const int max = 1e9+7；
注意：通常把常量定义为大写字母形式。

宏定义 #define 和常量 const 的区别：
1）#define是字符替换，没有类型安全检查，const是常量的声明，有类型区别，编译时需要进行类型检查。
2）宏定义是一个"编译时"概念，在预处理阶段展开，不能对宏定义进行调试，生命周期结束于编译时期；
const常量是一个"运行时"概念，在程序运行使用，类似于一个只读行数据。
3）#define是直接替换，不需要分配内存，存储在代码段；const常量需要分配内存，存储在数据段。
4）定义域不同，#define是全局，const定义域仅在其定义的范围内。
5）宏定义可以通过#undef来使之前的宏定义失效，const常量定义后将在定义域内永久有效。
6）#define 不可以作为函数参数，const可以。

C++ 存储类
是什么：C++ 程序中变量/函数的范围（可见性）和生命周期。这些说明符放置在它们所修饰的类型之前。
下面列出 C++ 程序中可用的存储类：
auto：根据初始化表达式自动推断被声明的变量的类型，C++11中已删除；for(auto &m: map)
register：用于定义存储在寄存器中而不是 RAM 中的局部变量（变量可能存储在寄存器中，这取决于硬件和实现的限制）
static：指示编译器在程序的生命周期内保持局部变量的存在，而不需要在每次它进入和离开作用域时进行创建和销毁。
作用：1）使用 static 修饰局部变量可以在函数调用之间保持局部变量的值；静态局部变量保存在全局数据区，而不是保存在栈中，每次的值保持到下一次调用，直到下次赋新值。它始终驻留在全局数据区，直到程序运行结束。但其作用域为局部作用域，当定义它的函数或语句块结束时，其作用域随之结束。
2）static 修饰全局变量时，会使变量的作用域限制在声明它的文件内；
3）static用在类数据成员上时，会导致仅有一个该成员的副本被类的所有对象共享，即无论创建多少个类的对象，静态成员都只有一个副本。
注意：不能把静态成员的初始化放置在类的定义中，但是可以在类的外部通过使用范围解析运算符 :: 来重新声明静态变量从而对它进行初始化。
4）静态成员函数，即使在类对象不存在的情况下也能被调用，只要使用类名加范围解析运算符 :: 就可以访问（可以使用静态成员函数来判断类的某些对象是否已被创建），例如创建对象前后分别调用Box::getCount()。
注意：静态成员函数没有 this 指针，只能访问静态成员（包括静态成员变量和静态成员函数）；普通成员函数有 this 指针，可以访问类中的任意成员。
extern：用于提供一个全局变量的引用，全局变量对所有的程序文件都是可见的。extern 修饰符通常用于当有两个或多个文件共享相同的全局变量或函数的时候。
mutable：仅适用于类的对象，允许对象的成员替代常量。
thread_local (C++11)：其声明的变量仅可在它其上创建的线程上访问。 变量在创建线程时创建，并在销毁线程时销毁。 每个线程都有其自己的变量副本。


可见性和生命周期不一致：



C++ 随机数
#include <ctime> 
#include <cstdlib>
srand( (unsigned)time( NULL ) );  // 设置种子
int  j= rand();  // 生成实际的随机数

洗牌算法：

代码：




3、指针、数组名  对指针操作
数组：固定大小的相同类型元素的顺序集合，内存连续，数组元素可以通过索引访问。
#include <iomanip>   //参数化的流操纵器
using std::setw;
setw() 函数来格式化输出  setw( 7 ) 

int a[];
vector<int> a;

1）指向数组的指针：数组内的元素可通过指向数组名称的指针来访问
举例：double *p;double balance[10];    p = balance;  *(p+i)    
char *ptr;  //字符指针
(int *)ptr //强制类型转换，返回指针的值，即指针所指向变量的地址
*ptr  //指针指向变量的取值

注意：把指针运算符 * 应用到 balance 上是完全可以的，但修改 balance 的值是非法的。这是因为 balance 是一个指向数组开头的常量，不能作为左值。

2）传递数组给函数（作为形参）：就函数而言，数组的长度是无关紧要的，因为 C++ 不会对形式参数执行边界检查。
形式参数是一个指针：int *param
形式参数是一个已定义大小的数组：int param[10]
形式参数是一个未定义大小的数组：int param[]

3）从函数返回数组（作为返回值）：
C++ 不允许返回一个完整的数组作为函数的参数。但是，您可以通过指定不带索引的数组名来返回一个指向数组的指针。
int * getRandom( ) {
 static int r[10];  //C++ 不支持在函数外返回局部变量的地址，除非定义局部变量为 static 变量。
return r; 
}

字符串  #include <cstring>
strcpy(s1, s2);  //复制s2到s1。
strcat(s1, s2);  //连接字符串 s2 到字符串 s1 的末尾。
strlen(s1);  //返回字符串 s1 的长度。
strcmp(s1, s2);  //比较 s1 和 s2 大小
strchr(s1, ch);  //返回一个指针，指向字符串 s1 中字符 ch 的第一次出现的位置。
strstr(s1, s2);   //返回一个指针，指向字符串 s1 中字符串 s2 的第一次出现的位置。

指针：是一个变量，其值为另一个变量（所指向变量）的地址
指向函数的指针：
int (*fun)() = add;
int result = (*fun)(1,2);  
返回指针的函数：
char * upper(char *str)

指针的算术运算：
1）递增变量指针，以便顺序访问数组中的每一个元素；
2）递减一个指针，对指针进行递减运算，即把值减去其数据类型的字节数；
3）指针的比较：指针可以用关系运算符进行比较，如 ==、< 和 >。

指针数组
int var[MAX] = {10, 100, 200};
int *ptr[MAX];
ptr[i] = &var[i]; // 赋值为整数的地址
*ptr[i]   //为var中元素的值
  
const char *names[MAX] = { "Zara Ali", "Hina Ali", "Nuha Ali", "Sara Ali", };
names[i]  //为数组中元素的值

指向指针的指针（多级间接寻址）
相当于指针链。通常，一个指针包含一个变量的地址。当我们定义一个指向指针的指针时，第一个指针包含了第二个指针的地址，第二个指针指向包含实际值的位置。

传递指针给函数：只需要简单地声明函数参数为指针类型即可。


引用：是一个别名，是某个已存在变量的另一个名字。
与指针的主要区别：（定义、是否需要初始化、是否可以为空、值是否可以改变）
不存在空引用。引用必须连接到一块合法的内存。
一旦引用被初始化为一个对象，就不能被指向到另一个对象。指针可以在任何时候指向到另一个对象。
引用必须在创建时被初始化。指针可以在任何时间被初始化。

把引用作为参数
通过形参引用可以改变实参的值。

把引用作为返回值
函数返回一个引用时，则返回一个指向返回值的隐式指针。

标准输出流（cout）、标准输入流（cin）：iostream 类的一个实例
标准错误流（cerr）：是非缓冲的，且每个流插入到 cerr 都会立即输出；
标准日志流（clog）：是缓冲的，每个流插入到 clog 都会先存储在缓冲区，直到缓冲填满或者缓冲区刷新时才会输出。
提示：使用 cerr 流来显示错误消息，而其他的日志消息则使用 clog 流来输出。

结构体：C++ 中另一种用户自定义的可用的数据类型，它允许您存储不同类型的数据项。
struct Books { char title[50]; char author[50]; char subject[100]; int book_id; } book;

结构作为函数参数：传参方式与其他类型的变量或指针类似。

struct Books *struct_pointer;  //指向结构的指针
struct_pointer = &book;
使用typedef 关键字定义结构体：可以为创建的类型取一个"别名"。

常量指针与指针常量的区别：

void指针
空指针：赋为 NULL 值的指针被称为空指针。NULL 指针是一个定义在标准库中的值为零的常量。它表明该指针不指向一个可访问的内存位置。
智能指针
野指针
this指针

4、类、对象
面向对象编程的特点：封装性、继承、多态、
C++ 类定义：class Box { public: double length; // 盒子的长度 double breadth; // 盒子的宽度 double height; // 盒子的高度 };
定义 C++ 对象：Box Box1; // 声明 Box1
访问数据成员：类的对象的公共数据成员可以使用直接成员访问运算符 (.) 来访问。  Box1.breadth
类的成员函数是指那些把定义和原型写在类定义内部的函数。类成员函数是类的一个成员，它可以操作类的任意对象，可以访问对象中的所有成员。成员函数可以定义在类定义内部，或者单独使用范围解析运算符 :: 来定义。

inline ：为了解决一些频繁调用的小函数大量消耗栈空间（栈内存）的问题。
适用情况：函数短小且频繁被调用
不适应情况：1）如果函数体内的代码比较长，使用内联将导致内存消耗代价较高。
2）如果函数体内出现循环，那么执行函数体内代码的时间要比函数调用的开销大。
优缺点：内联是以代码膨胀（复制）为代价，仅仅省去了函数调用的开销，从而提高函数的执行效率。
注意：关键字 inline 必须与函数定义体放在一起才能使函数成为内联。

数据封装：防止函数直接访问类类型的内部成员。类成员的访问限制是通过标记 public、private、protected 来指定的。
类访问修饰符
关键字 public、private（默认）、protected 
public：公有成员在程序中类的外部是可访问的，可以不使用任何成员函数来设置和获取公有变量的值。
private：私有成员变量或函数在类的外部是不可访问的，甚至是不可查看的。只有类和友元函数可以访问私有成员。
protected ：保护成员变量或函数与私有成员十分相似，但保护成员在派生类（即子类）中是可访问的。

注意：1）private 成员只能被本类成员（类内）和友元访问，不能被派生类访问；2）protected 成员可以被派生类访问；
3）在外部访问private 成员是通过类对象调用成员函数来访问的，而不能直接用成员访问运算符 (类名称.) 来访问；4）一句话总结：在类外按照继承之后得到的变化了的访问限制方式来访问，即只有public继承方式下的子类能够在外面访问基类的public成员，而在类内不管哪种继承方式，子类除了不能访问基类的private成员之外，其余都能访问。

友元函数/友元类
是什么：定义在类外部，不是类成员函数，但有权访问类的所有私有（private）成员和保护（protected）成员
怎么用：在类定义中该函数原型前使用关键字 friend。
例如：    friend void printWidth(Box box);   //友元函数
    friend class BigBox;  //友元类

注意：友元函数没有this指针，则参数要有三种情况：
1）要访问非static成员时，需要对象做参数；
2）要访问static成员或全局变量时，不需要对象做参数。

内联函数
是什么：通常与类一起使用，在类定义中的定义的函数都是内联函数，即使没有使用 inline 说明符。在编译时，编译器会把该函数的代码副本放置在每个调用该函数的地方（编译器将程序中出现的内联函数的调用表达式用内联函数的函数体进行替换，而对于其他的函数，都是在运行时候才被替代，即以空间代价换时间）
作用：目的是为了解决程序中函数调用的效率问题。
怎么用：在函数名前面放置关键字 inline
适用情况：1）在内联函数内不允许使用循环语句和switch语句；
2）内联函数的定义必须出现在第一次调用之前；
3）类结构中所在的类说明内部定义的函数是内联函数。
优缺点：当函数体比较小的时候, 内联该函数可以令目标代码更加高效；滥用内联将导致程序变慢（因为有隐含的成员和基类析构函数被调用）。

注意：有些函数即使声明为内联的也不一定会被编译器内联, 比如虚函数和递归函数就不会被正常内联（递归层数在编译时可能是未知的，虚函数内联的主要原因则是想把它的函数体放在类定义内）

this指针
是什么：this 指针是所有成员函数的隐含参数，每一个对象都能通过 this 指针来访问自己的地址。友元函数没有 this 指针，因为友元不是类的成员。任何对类成员的直接访问都被看作是对 this 的隐式引用。
怎么用：每一个对象都能通过 this 指针来访问自己的地址。
适用情况：在以下场景中，经常需要显式引用 this 指针：
1）为实现对象的链式引用；
2）为避免对同一对象进行赋值操作；
3）在实现一些数据结构时，如 list。

注意： this 是一个常量指针，不允许改变 this 中保存的地址。

指向类的指针
是什么：指向 C++ 类的指针与指向结构的指针类似，访问指向类的指针的成员，需要使用成员访问运算符 ->，就像访问指向结构的指针一样。
怎么用：先定义，然后必须在使用指针之前，对指针进行初始化。


类的构造函数
是什么：类的一种特殊的成员函数，名称与类的名称是完全相同，并且不会返回任何类型，它会在每次创建类的新对象时执行。
作用：构造函数可用于为某些成员变量设置初始值。
有几种方式：1）默认无参数：Line();
2）带参数：Line(double len);
3）使用初始化列表来初始化字段：class CMyClass {
    CMyClass(int x, int y);
    int m_x;
    int m_y;};
CMyClass::CMyClass(int x, int y) : m_y(x), m_x(y){};   //注意m_x和m_y为类成员，需要按照声明顺序进行初始化/或者按照初始化顺序来声明成员变量！！只要成员变量的初始化不依赖其他成员变量，即使顺序不同也能正确的初始化。

类中特殊成员变量的初始化问题：

即静态变量中只有整型常量可以在定义时候初始化，其他需要在类内定义而类外初始化，其余非静态变量必须通过构造函数参数列表进行初始化。

析构函数
是什么：类的一种特殊的成员函数，名称与类的名称是完全相同的，只是在前面加了个波浪号（~）作为前缀，它不会返回任何值，它会在每次删除所创建的对象时执行。
作用：在跳出程序（比如关闭文件、释放内存等）前释放资源。

注意：构造与析构函数的调用情况（析构时先执行析构函数中的语句（此时成员还都在），再具体析构对象成员，且顺序和构造时（或申明顺序?）相反）
顺序：先构造父类再构造子类，先析构子类再析构父类

类的拷贝构造函数
是什么：特殊的构造函数，它在创建对象时，是使用同一类中之前创建的对象来初始化新创建的对象。
作用及什么时候使用：（1）一个对象以值传递的方式传入函数体；
（2）一个对象以值传递的方式从函数返回；
（3）一个对象需要通过另外一个对象进行初始化。

继承：


多态
是什么：C++ 多态意味着调用成员函数时，会根据调用函数的对象的类型来执行不同的函数。
适用情况：当类之间存在层次结构，并且类之间是通过继承关联时，就会用到多态（有了多态，您可以有多个不同的类，都带有同一个名称但具有不同实现的函数，函数的参数甚至可以是相同的。）
a.编译时多态性：通过重载函数实现
b 运行时多态性：通过虚函数实现。
基类的虚函数和子类的虚函数：子类可以不实现基类的虚函数
基类的纯虚函数和子类的纯虚函数：子类必须实现基类的纯虚函数
调用区别
调用非虚成员函数：和调用非成员函数一样，通过对象确定对象所属的类，然后找到类的成员函数。此过程不会涉及到对象的内容，只会涉及对象的类型，是一种静态绑定；
调用虚函数：虚函数表存放在每个对象中，不能再编译期间实现。只能在运行时绑定，是一种动态绑定。

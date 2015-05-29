# C++程序设计 #
[郭炜](http://weibo.com/guoweiofpku) [blog](http://blog.sina.com.cn/u/3266490431)

[刘家瑛](http://weibo.com/pkuliujiaying)
# Week 1 #
## 函数指针 ##
类型名（*指针变量名）（参数类型1，参数类型2，……）；

	int (*pf)(int, char);

	void qsort(void *base, int nelem, unsigned int width, 
			int (*pfCompare)(const void*, const void*));

对数组排序，需要知道：

数组起始地址，数组元素的个数，每个元素的大小，元素谁在前谁在后的规则。

## 命令行参数 ##

	int main(int argc, char *argv[])
## 位运算 ##
& | ^ ~ << >>

按位与：通常用来将某变量中的某些位清零且同时保留其他位不变，也可以用来获取某变量中的某一位。

按位或：通常用来将变量中的某些位置1且保留其他位不变。

按位异或：通常用来将某变量中的某些位取反且保留其他位不变。

	a ^ b = c --> c ^ b = a, c ^ a = b

不通过临时变量，交换两个变量的值。(穷举法)

	a = a ^ b;
	b = b ^ a;
	a = a ^ b;

按位非

左移运算符：左移n位，等于乘以2^n。

右移运算符：大多数C/C++编译器规定，如果原符号位为1，则右移时高位就补充1。

	(a >> n) & 1 // 0 <= n <=31
	(a & 1 << n)) >> n // 0 <= n < 31, 符号位的风险

## 引用 ##
类型名 &引用名 = 某变量名；

某个变量的引用，等价于这个变量，相当于该变量的一个别名。

定义引用时一定要将其初始化成引用某个变量。

初始化后，它就一直引用该变量，不会再引用别的变量了。

引用只能引用变量，不能引用常量和表达式。

	void swap(int *a, int *b); // C
	swap(&n1, &n2);

	void swap(int &a, int &b); // C++
	swap(n1, n2);

引用作为函数的返回值(并未说明其实际价值)

	int n = 4;
	int &SetValue() { return n; }
	SetValue() = 40;
	cout << n;

常引用：不能通过常引用去修改其引用的内容。

	const int &r = n;

const T & 和 T &是不同的类型。T &类型的引用或T类型的变量可以用来初始化const T &类型的引用。const T类型的常变量和const T &类型的引用则不能用来初始化T &类型的引用，除非进行强制类型转换。
## const ##
定义常量，便于类型检查

	const int MAX_VAL = 23;

定义常量指针，不可通过常量指针修改其指向的内容，但指向可以变化

	const int *p = &n;

定义常量指针，不能把常量指针赋值给非常量指针，反过来可以

	const int *p1; int *p2;
	p1 = p2; // ok
	p2 = p1; // error
	p2 = （int*) p1; // ok，强制类型转换

函数参数为常量指针时，可避免函数内部不小心改变参数指针所指地方的内容。

	void MyPrint(const char *p);
	strcpy(p, "this"); // 编译出错，strcpy第一个参数char*，类型不匹配，故编译出错

定义常引用，不能通过常引用修改其引用的变量。
## 动态内存分配 ##
用new运算符实现动态内存分配

分配一个变量

	T *P = new T;
	p = new int;

分配一个数组

	P = new T[N];

用new动态分配的内存空间，一定要用delete运算符进行释放。

	delete 指针;
	delete []p;

### [C++二维数组new小结(zz)](http://www.cnblogs.com/beyondstorm/archive/2008/08/26/1276278.html) ###

## 内联函数、函数重载、函数缺省参数 ##
### 内联函数 ###
函数调用是有时间开销的。如果函数本身只有几条语句，执行非常快，而且函数被反复执行很多次，相比之下，调用函数所产生的这个开销就会显得比较大。

为了减少函数调用的开销，引入了内联函数机制。编译器处理对内联函数的调用语句时，是将整个函数的代码插入到调用语句处，而不会产生调用函数的语句。

	inline int Max(int a, int b);

	k = Max(n1, n2);
	if (n1 > n2)
		tmp = n1;
	else
		tmp = n2;
	k = tmp;

可执行程序的体积会增大。
### 函数重载 ###
一个或多个函数，名字相同，然而参数个数或参数类型不相同，这叫做函数的重载。

函数重载使得函数命名变得简单。

编译器根据调用语句中的实参的个数和类型判断应该调用哪个函数。
### 函数缺省参数 ###
C++中，定义函数的时候可以让**最右边**的连续若干个参数由缺省值，那么调用函数的时候，若相应位置不写参数，参数就是缺省值。

函数参数可缺省的目的在于提高程序的可扩充性。

如果某个写好的函数要添加新的参数，而原先那些调用该函数的语句，未必需要使用新增的参数，那么为了避免对原先那些函数调用语句的修改，就可以使用缺省参数。

比如画圆，之后加入颜色支持。

# week2 #
## 面向对象程序设计方法 ##
结构化程序设计，自顶向下，逐步求精。理解难，修改难，查错难，重用难。

面向对象的程序设计方法

一类事物----抽象----> 共同属性-->数据结构，行为-->函数----封装---->类

类的定义

	class 类名
	{
		访问范围说明符：
			成员变量
			成员函数声明
	};
## 面向对象程序设计语言的发展历程 ##
1973，AT&T Dennis Ritchie，C

1983，AT&T Bjarne Stroustrup，C++

The C++ Programming Language
## 从客观事物抽象出类的例子 ##
类，带函数的结构体。

	class CRectangle {
		public:
			int w, h;
		void Init(int w_, int h_) {
			w = w_; h = h_;
		}
		int Area() {...}
		int Perimeter();
	};
	int CRectangle::Perimeter() {
		return 2 * (w + h);
	}
	CRectangle r;
	r.Init(w, h);

类定义的变量-->类的实例-->对象

对象的内存空间。对象的大小=所有成员变量的大小之和。

对象之间可以用“=”进行赋值，其他需要运算符重载。

	void PrintRectangle(CRectangle &r);
## 类成员的可访问范围 ##
private, public, protected

缺省为私有成员

类的成员函数内部，可以访问：

当前对象的全部属性、函数

同类其它对象的全部属性、函数

设置私有成员的目的：强制对成员变量的访问一定要通过成员函数进行。隐藏私有成员。
## 内联成员函数和重载成员函数 ##
内联成员函数

inline+成员函数

整个函数体出现在类定义内部

	class B {
		inline void func1();
		void func2() {...};
	};

使用缺省参数要注意避免有函数重载时的二义性
## 构造函数 ##
成员函数的一种，名字与类名相同，可以有参数，不能有返回值。作用是对对象进行初始化。

	CSample array2[2] = {4, 5};
	Test array1[3] = {1, Test(1, 2)}
	Test * pArray[3] = {new Test(3), new Test(1, 2)}; // pArray[2]未经初始化的指针
# week 3 #
## 复制构造函数 ##
copy constructor

只有一个参数，即**对同类对象的引用**

	X::X(X&)
	X::X(const X&) // 能以常量对象作为参数

如果没有定义复制构造函数，那么编译器生成默认复制构造函数。默认的复制构造函数完成复制功能。

	class Complex {
		private:
			double real, imag;
	};

	Complex c1; // 调用无参构造函数
	Complex c2(c1); // 调用缺省的复制构造函数，将c2初始化成和c1一样

	class Complex {
		Complex (const Complex &c) {
			real = c.real;
			imag = c.imag;
			cout << "Copy Constructor Called.";
		}
	};

1. 当用一个对象去初始化同类的另一个对象时。

	Complex c2(c1);
	Complex c2 = c1; // 初始化语句，非赋值语句，与上句等价

2. 如果某函数有一个参数是类A的对象，那么该函数被调用时，类A的复制构造函数将被调用。

	void Func(A a1) {}
	int main() {
		A a2;
		Func(a2);
		return 0;
	}

3. 如果函数的返回值是类A的对象时，则函数返回时，A的复制构造函数被调用。

为什么要自己写复制构造函数？
## 类型转换构造函数 ##
目的：实现类型的自动转换

特点：只有一个参数，不是复制构造函数

编译系统会自动调用转换构造函数，建立一个**临时对象/临时变量**

	class Complex {
		public:
			Complex(int i) { // 类型转换构造函数
			}
	};

	int main() {
		Complex c1(7, 8);
		Complex c2 = 12; // =是初始化的意思，不是赋值
		c1 = 9; // 9被自动转换成一个临时Complex对象
	}

## 析构函数 ##
没有参数和返回值，一个类最多只有一个析构函数

	~

对象消亡时，自动被调用，在对象消亡前做善后工作，如释放分配的空间等。

定义类时没写析构函数，则编译器生成缺省析构函数，不涉及释放用户申请的内存释放等清理工作

对象数组生命期结束时，对象数组的每个元素的析构函数都会被调用。（main函数结束时）

delete运算导致析构函数调用

先被构造的对象最后被析构掉。（**验证**）

构造函数和析构函数在不同编译器中的表现，个别调用情况不一致，编译器有bug，代码优化措施。本课程针对C++标准。
## 静态成员变量和静态成员函数 ##
静态成员：在定义前面加了static关键字的成员。

	static int nTotalArea;
	public:
		static void PrintTotal();

普通成员变量每个对象有各自的一份，而静态成员变量一共就一份，为所有对象共享

sizeof运算符不会计算静态成员变量

普通成员函数必须具体作用于某个对象，而静态成员函数并不具体作用于某个对象，因此，静态成员不需要通过对象就能访问

	CRectangle::PrintTotal(); // 类名::成员名
	r.PrintTotal(); // 对象名.成员名
	p->PrintTotal(); // 指针->成员名
	int n = ref.nTotalNumber; // 引用.成员名

静态成员变量本质上是全局变量，哪怕一个对象都不存在，类的静态成员变量也存在

静态成员函数本质上是全局函数

设置静态成员这种机制的目的是将和某些类紧密相关的全局变量和函数写到类里面，看上去像一个整体，易于理解和维护

	CRectangle::CRectangle(int w_, int h_) { // 是否所有构造函数都用这个构造函数初始化？
		w = w_;
		nTotalNumber++;
	}
	CRectangle::~CRectangle() {
		nTotalNumber--；
	}

必须在定义类的文件中对静态成员变量进行一次说明或初始化，否则编译能通过，链接不能通过

	int CRectangle::nTotalNumber = 0;

在静态成员函数中，不能访问非静态成员变量，也不能调用非静态成员函数
	
	CRectangle::PrintTotal();

编译器会自动生成复制构造函数（形参、返回值、临时对象）
## 成员对象和封闭类 ##
成员对象：一个类的成员变量是另一个类的对象

包含成员对象的类叫封闭类（Enclosing）

	class CType {
		public:
			CType(int r, int w): radius(r), width(w){}
	};
	CCar::CCar(int p, int tr, int w): price(p), tyre(tr, w){}

如果CCar类不定义构造函数，则编译器不知道car.tyre该如何初始化，没有参数则没有问题，用默认的构造函数

定义封闭类的构造函数时，添加初始化列表

当封闭类对象生成时，首先执行所有成员对象的构造函数，然后执行封闭类的构造函数

成员对象的构造函数调用顺序，和成员对象在类中的说明顺序一致，与在成员初始化列表中出现的顺序无关

当封闭类的对象消亡时，首先执行封闭类的析构函数，然后执行成员对象的析构函数

## 友元 ##
Friend：友元函数、友元类

一个类的友元函数可以访问该类的私有成员

	class CCar;
	class CDriver {
		public:
			void ModifyCar(CCar *pCar);
	};
	class CCar {
		private:
			int price;
		friend int MostExpensiveCar(CCar cars[], int total);
		friend void CDriver::ModifyCar(CCar *pCar);
	};

将一个类的成员函数（包括构造、析构函数）定义为另一个类的友元

A是B的友元类，A的成员函数可以访问B的私有成员

	class CCar {
		friend class CDriver;
	};

友元类之间的关系不能传递，不能继承
## this指针 ##
C++程序到C程序的翻译

	class CCar {
		public:
			int price;
			void SetPrice(int p);
	};

	int main() {
		CCar car;
		car.SetPrice(100);
		return 0;
	}
	struct CCar {
		int price;
	};
	void SetPrice(struct CCar *this, int p) {
		this->price = p;
	}
	int main() {
		struct CCar car;
		SetPrice(&car, 100);
		return 0;
	}

	Complex AddOne() {
		this->real++; // real++;
		return *this;
	}


this指针的作用就是指向成员函数所作用的对象

非静态成员函数中可以直接使用this来代表指向该函数作用的对象的指针

	A *p = NULL;
	p->Hello(); // -->Hello(p);

	void Hello() { cout << "hello" << endl; }
	-->void Hello(A *this) { cout << "hello" << endl; }

静态成员函数不能使用this指针，因为静态成员函数并不具体作用于某个对象。因此，静态成员函数的真实的参数的个数，就是程序中写出的参数个数。
## 常量对象、常量成员函数和常引用 ##
如果不希望某个对象的值被改变，则定义该对象的时候可以在前面加const关键字

在类的成员函数说明后面可以加const关键字，则该成员函数成为常量成员函数

常量成员函数执行期间不应修改其所作用的对象。因此，在常量成员函数中不能修改成员变量的值（静态成员变量除外，不属于对象的一部分），也不能调用同类的非常量成员函数（静态成员函数除外）

	class Sample {
	public:
		void GetValue() const;
	};

两个成员函数，名字和参数表都一样，但是一个是const，一个不是，算重载，而非重复定义

对象作为函数的参数时，生成该参数需要调用复制构造函数，效率比较低。用指针作参数，代码又不好看。可以用对象的引用作为参数。

	void PrintfObj(Sample &o);

对象引用作为函数的参数有一定的风险。若函数中不小心修改了形参o，则实参也跟着变。可以用对象的常引用作为参数

	void PrintfObj(const Sample &o);

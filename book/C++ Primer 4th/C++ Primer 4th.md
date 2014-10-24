C++ Primer 第4版

Stanley B. Lippman, Jose Lajoie, and Barbara E. Moo
## 第1章 快速入门 ##
本章介绍C++的大部分基本要素：内置类型、库类型、类类型、变量、表达式、语句和函数。在这一过程中还会简要说明如何编译和运行程序。

iostream

std::cin

在注释的每一行以星号开始，指明整个范围是多行注释的一部分。

按错误报告的顺序改正错误是个好习惯，通常一个错误可能会产生一连串的影响，并导致编译器报告非常多的错误。最好在每次修改后，或最多改正了一些显而易见的错误后，就重新编译代码。

从键盘输入文件结束符。Windows，ctrl+z。Unix，ctrl+D。

一般来说，我们将类定义放入一个文件中，要使用该类的任何程序都必须包含这个文件。
# 第一部分 基本语言 #
## 第2章 变量和基本类型 ##
C++中，把负值赋给unsigned对象是完全合法的，其结果是该负数对该类型的取值个数求模后的值。

通过在数值后面加L或者l指定常量为long类型。在数值后面加U或者u定义unsigned类型。

在字符字面值前加L就能够得到wchar_t类型的宽字符字面值。如：L'a'

我们可以将任何字符表示为以下形式的通用转义字符：\ooo \xddd

在一行的末尾加一反斜线符号可将此行和下一行当做同一行处理。

C++是一门静态类型语言，在编译时会作类型检查。

**变量**提供了程序可以操作的有名字的存储区。C++中的每一个变量都有特定的类型，该类型决定了变量的内存大小和布局、能够存储于该内存中的值的取值范围以及可应用在该变量上的操作集。

**对象**就是内存中具有类型的区域。

变量命名习惯

- 变量名一般用小写字母。
- 标识符应使用能帮助记忆的名字。
- 包含多个词的标识符书写为在每个词之间添加一个下划线，或者每个内嵌的词的第一个字母都大写。student_loan, studentLoan
- _也可以作为变量名。

C++支持两种初始化变量的形式：复制初始化（copy-initialization）和直接初始化（direct-initialization）。复制初始化语法用等号（=），直接初始化则是把初始化式放在括号中：
	
	int ival(1024);
	int ival = 1024;

直接初始化语法更灵活且效率更高。

初始化指创建变量并给它赋初始值，而赋值则是擦除对象的当前值并用新值代替。 

定义如何进行初始化的成员函数成为构造函数（constructor）。

内置类型变量是否自动初始化取决于变量定义的位置。在函数体外定义的变量都初始化成0，在函数体里定义的内置类型变量不进行自动初始化。

如果定义某个类的变量时没有提供初始化式，这个类也可以定义初始化时的操作。它是通过定义一个特殊的构造函数即默认构造函数（default constructor）来实现的。

为了让多个文件访问相同的变量，C++区分了声明和定义。
变量的定义（definition）用于为变量分配存储空间，还可以为变量指定初始值。在一个程序中，变量有且仅有一个定义。
声明（declaration）用于向程序表明变量的类型和名字。定义也是声明：当定义变量时我们声明了它的类型和名字。可以通过使用extern关键字声明变量名而不定义它。
extern声明不是定义，也不分配存储空间。
只有当声明也是定义时，声明才可以有初始化式，因为只有定义才分配存储空间。如果声明有初始化式，那么它可被当作是定义，即使声明标记为extern。只有当extern声明位于函数外部时，才可以含有初始化式。

用来区分名字的不同意义的上下文称为作用域（scope）。定义在所有函数外部的名字具有全局作用域（global scope）。局部作用域（local scope）。语句作用域（statement scope）。类作用域（class scope）。命名空间作用域（namespace scope）。

通常把一个对象定义在它首次使用的地方是一个很好的办法。
### 2.4 const 限定符 ###
定义一个变量代表某一常数的方法有一个严重的问题，这个变量可以被修改。const限定符提供了一个解决办法，它把一个对象转换成一个常量。因为常量在定义后就不能被修改，所以定义时必须初始化。

	const int bufSize = 512;

非const变量默认为extern。要使const变量能够在其他的文件中访问，必须显式地指定它为extern。在全局作用域声明的const变量是定义该对象的文件的局部变量，此变量只存在于那个文件中，不能被其他文件访问。

### 2.5 引用 ###
引用（reference）就是对象的另一个名字。在实际程序中，引用主要用作函数的形式参数。

引用只是它绑定的对象的另一个名字，作用在引用上的所有操作事实上都是作用在该引用绑定的对象上。这一规则的结果是必须在定义引用时进行初始化。初始化是指明引用指向哪个对象的唯一方法。

const应用的意思是指向const对象的应用。非const引用表示指向非const类型的引用。非const引用只能绑定到与该引用同类型的对象。const引用则可以绑定到不同但相关的类型的对象或绑定到右值。
### 2.6 typedef 名字 ###
typedef可以用来定义类型的同义词。通常被用于以下三种目的。

- 为了隐藏特定类型的实现，强调使用类型的目的。
- 简化复杂的类型定义，使其更易理解。
- 允许一种类型用于多个目的，同时使得每次使用该类型的目的明确。

<code>

	typedef double wages;
	typedef wages salary;
</code>

### 2.7 枚举 ###
枚举（enumeration）不但定义了整数常量集，而且还把它们聚集成组。枚举的定义包括关键字enum，其后是一个可选的枚举类型名，和一个用花括号括起来，用逗号分开的枚举成员（enumerator）列表。默认地，第一个枚举成员赋值为0，后面的每个枚举成员赋的值比前面的大1。枚举成员值可以是不唯一的。

	enum Points { point2d = 2, point2w, point3d = 3, point3w };

每个enum都定义了一种新的类型。枚举类型的对象的初始化和赋值，只能通过其枚举成员或同一枚举类型的其他对象来进行。

	Points pt3d = point3d;
### 2.8 类类型 ###
类定义以关键字class开始，其后是该类的名字标识符。类体位于花括号里面。花括号后面必须要跟一个分号。类体可以为空。类体定义了组成该类型的数据和操作。这些操作和数据是类的一部分，也称为类的成员（member）。操作称为成员函数，而数据则称为数据成员（data member）。类不是在类定义里定义数据成员时初始化数据成员，而是通过称为构造函数的特殊成员函数控制初始化。

如果使用class关键字来定义类，那么定义在第一个访问标号前的任何成员都隐式指定为private；如果使用struct关键字，那么这些成员都是public。使用class还是struct关键字来定义类，仅仅影响默认的初始访问级别。
### 2.9 编写自己的头文件 ###
头文件为相关声明提供了一个集中存放的位置。头文件一般包含类的定义、extern变量的声明和函数的声明。

当设计头文件时，记住定义和声明的区别是很重要的。定义只可以出现一次，而声明则可以出现多次。因为头文件包含在多个源文件中，所以不应该含有变量或函数的定义。对于头文件不应该含有定义这一规则，有三个例外。头文件可以定义类、值在编译时就已知道的const对象和inline函数。

const变量默认时是定义该变量的文件的局部变量，这样设置默认情况的原因在于允许const变量定义在头文件中。

C++中的任何变量都只能定义一次。定义会分配存储空间，而所有对该变量的使用都关联到同一存储空间。当我们在头文件中定义了const变量后，每个包含该头文件的源文件都有了自己的const变量，其名称和值都一样。

在实践中，大部分的编译器在编译时都会用相应的变量表达式来替换对这些const变量的使用，所以，在实践中不会有任何存储空间用于存储用常量表达式初始化的const变量。

设计头文件时，应使其可以多次包含在同一源文件中。我们必须保证多次包含同一头文件不会引起头文件定义的类和对象被多次定义。使得头文件安全的通用做法，是使用预处理器定义头文件保护符（header guard）。头文件保护符用于避免在已经见到头文件的情况下重新处理该头文件的内容。

预处理器允许我们自定义变量。预处理器变量有两种状态：已定义或未定义。#define指示接受一个名字并定义该名字为预处理器变量。#ifndef指示检测指定的预处理器变量是否未定义。如果预处理器变量未定义，那么跟在其后的所有指示都被处理，知道出现#endif。

	#ifndef SALESITEM_H
	#define SALESITEM_H

	#endif

## 第3章 标准库类型 ##
C++还定义了一个内容丰富的抽象数据类型标准库。
### 3.1 命名空间的 using 声明 ###
使用using声明可以在不需要加前缀namespace_name::的情况下访问命名空间中的名字。

	using namespace::name;

有一种情况下，必须总是使用完全限定的标准库名字，即在头文件中。理由是头文件的内容会被预处理器复制到程序中。如果在头文件中放置using声明，就相当于在包含该头文件的每个程序中都放置了同一using声明，不论该程序是否需要using声明。
### 3.2 标准库 string 类型 ###
	
	#include <string>
	using std::string;
	string s1;
	string s2(s1);
	string s3("value");
	string s4(n, 'c');
	getline(cin, line);

string的size和empty操作
size操作返回的是string::size\_type类型的值。string类类型和许多其他库类型都定义了一些配套类型（companion type）。通过这些配套类型，库类型的使用就能与机器无关（machine-independent）。size\_type就是这些配套类型中的一种。它定义为与unsigned型（unsigned int或unsigned long）具有相同的含义，而且可以保证足够大能够存储任意string对象的长度。任何存储string的size操作结果的变量必须为string::size\_type类型。特别重要的是，不要把size的返回值赋给一个int变量。

在多数计算机上，大写的字母位于小写字母之前，任何一个大写字母都小于任意的小写字母。

string对象的加法被定义为连接（concatenation）。当进行string对象和字符串字面值混合连接操作时，+操作符的左右操作数必须至少有一个是string类型的。

	string s5 = s1 + "," + "world"; // ok: each + has string operand
	string s6 = "hello" + "," + s2; // error: can't add string literals

string类型通过下标操作符来访问string对象中的单个字符。下标操作符需要取一个size_type类型的值，来标明要访问字符的位置。

	string str("some string");
	for (string::size_type ix = 0; ix != str.size(); ++ix)
		cout << str[ix] << endl;

任何可产生整型值的表达式都可用作下标操作符的索引。

字符操作函数在ccytpe头文件中定义。

C标准库头文件命名形式为name.h，而C++版本则命名为cname。c表示这个头文件源自C标准库。因此，cctype与ctype.h文件的内容是一样的，只是采用了更适合C++程序的形式。特别地，cname头文件中定义的名字都定义在命名空间std内，而.h版本中的名字却不是这样。
### 3.3 标准库 vector 类型 ###
vector是同一种类型的对象的集合，每个对象都有一个对应的整数索引值。若要创建非空的vector对象，必须给出初始化元素的值。

	#include <vector>
	using std::vector;
	vector<int> ivec;
	vector<T> v1;
	vector<T> v2(v1);
	vector<T> v3(n, i);
	vector<T> v4(n);

vector不是一种数据类型，而只是一个类模板，可用来定义任意多种数据类型。

vector对象（以及其他标准库容器对象）的重要属性就在于可以在运行时高效地添加元素。因为vector增长的效率高，在元素值已知的情况下，最好是动态地添加元素。虽然可以对给定元素个数的vector对象预先分配内存，但更有效的方法是先初始化一个空vector对象，然后再动态地增加元素。

	vector<int>::size_type
	push_back

C++程序员习惯于优先选用!=而不是<来编写循环判断条件。

必须是已存在的元素才能用下标操作符进行索引。通过下标操作进行赋值时，不会添加任何元素。
### 3.4 迭代器简介 ###
迭代器（iterator）是一种检查容器内元素并遍历元素的数据类型。所有的标准库容器都定义了相应的迭代器类型，而只有少数的容器支持下标操作。

	vector<int>::iterator iter = ivec.begin();
	*iter = 12;
	ivec[0] = 12;
	++iter;

begin返回迭代器指向的第一个元素。end操作返回的迭代器指向vector的末端元素的下一个。通常称为超出末端迭代器（off-the-end iterator），表明它指向了一个不存在的元素。如果vector为空，begin返回的迭代器与end返回的迭代器相同。由end操作返回的迭代器并不指向vector中任何实际的元素，相反，它只是起一个哨兵（sentinel）的作用，表示我们已处理完vector中所有元素。

迭代器类型可使用解引用操作符（*操作符）来访问迭代器所指向的元素。

==/!=，如果两个迭代器对象指向同一个元素，则它们相等，否则就不相等。

const_iterator类型只能用于读取容器中的元素，但不能改变其值。

声明一个const迭代器时，必须初始化迭代器，一旦被初始化后，就不能改变它的值。

	//an iterator that cannot write elements
	vector<int>::const_iterator
	// an iterator whose value cannot change
	const vector<int>::iterator
	const vector<int> nines(10, 9);
	const vector<int>::iterator cit2 = nines.begin(); // error
	vector<int>::const_iterator it = nines.begin(); // ok
	*it = 10; // error
	++it; // ok

iter1 - iter2，该表达式用来计算两个迭代器对象的距离，该距离是名为 difference_type的signed类型的值。

任何改变vector长度的操作都会使已存在的迭代器失效。例如，在调用push_back之后，就不能再信赖指向vector的迭代器的值了。
### 3.5 标准库bitset类型 ###

	#include <bitset>
	using std::bitset;
	bitset<n> b;
	bitset<n> b(u);	// b是unsigned long型u的一个副本
	bitset<n> b(s);	// b是string对象s中含有的位串的副本
	bitset<n> b(s, pos, n);

当用string对象初始化bitset对象时，string对象直接表示为位模式。string对象和bitset对象之间是反向转化的：string对象的最右边字符（即下标最大的那个字符）用来初始化bitset对象的低阶位。

count操作的返回类型是标准库中名为size_t的类型。size_t类型定义在cstddef头文件中。
## 第4章 数组和指针 ##
只有当性能测试表明使用vector无法达到必要的速度要求时，数组被严格限制于程序内部使用。
### 4.1 数组 ###
数组由类型名、标识符和维数组成的复合数据类型。数组的维数必须用值大于等于1的常量表达式定义。此常量表达式只能包含整型字面值常量、枚举常量或者用常量表达式初始化的整型const对象。

	int staff_size = 27;
	double salaries[staff_size]; // error: non const variable

与vector不同，一个数组不能用另外一个数组初始化，也不能将一个数组赋值给另一个数组，这些操作都是非法的。

数组下标的正确类型是size_t。
### 4.2 指针的引入 ###
如果可能的话，除非所指向的对象已经存在，否则不要先定义指针，这样可避免定义一个未初始化的指针。如果必须分开定义指针和其所指向的对象，则将指针初始化为0。因为编译器可检测出0值的指针，程序可判断该指针并未指向一个对象。NULL，cstdlib。

C++提供了一种特殊的指针类型void\*，它可以保存任何类型对象的地址。void\*指针只支持几种有限的操作：与另一个指针进行比较；向函数传递void\*指针或从函数返回void\*指针；给另一个void\*指针赋值。不允许使用void\*指针操纵它所指向的对象。

	string s("hell, world");
	string *sp = &s;
	cout << *sp;
	*sp = "goodbye"; // contents of s now changed

虽然使用引用和指针都可间接访问另一个值，但它们之间有两个重要区别。第一个区别在于引用总是指向某个对象；定义引用时没有初始化是错误的。第二个重要区别则是赋值行为的差异：给引用赋值修改的是该引用所关联的对象的值，而并不是使引用与另一个对象关联。引用一经初始化，就始终指向另一个特定对象（这就是为什么引用必须在定义时初始化的原因）。

两个指针减法操作的结果是标准库类型 ptrdiff_t 的数据。与size_t了类型一样，ptrdiff_t也是一种与机器相关的类型，在cstddef头文件中定义。size_t是unsigned类型，而ptrdiff_t则是signed类型。

C++允许计算数组或对象的超出末端的地址，但不允许对此地址进行解引用操作。而计算数组超出末端位置之后或数组首地址之前的地址都是不合法的。

在实际的程序中，指向const的指针（const int *）常用作函数的形参。将形参定义为指向const的指针以此确保传递给函数的实际对象在函数中不因为形参而被修改。

const指针，本身的值不能修改。指针本身是const的事实并没有说明是否能使用该指针修改它所指向对象的值。指针所指对象的值能否修改完全取决于该对象的类型。

	int errNumb = 0;
	int *const curErr = &errNumb; // curErr is a constant pointer

指向const对象的const指针，既不能修改pi_ptr所指向对象的值，也不允许修改该指针的指向。

	const double pi = 3.14159;
	const double *const pi_ptr = &pi;

指针和typedef

	typedef string *pstring;
	const pstring cstr;
	string *const cstr;
### 4.3 C风格字符串 ###

	#include <cstring>

strncat和strncpy比strcat和strcpy函数更安全。

对于大部分的应用而言，使用标准库类型string，除了增强安全性外，效率也提高了，因此应该尽量避免使用C风格字符串。

每一个程序在执行时都占用一块可用的内存空间，用于存放动态分配的对象，此内存空间称为程序的自由存储区（free store）或堆（heap）。

	int *pia = new int[10];
	int *pia = new int[10] ();
	delete [] pia;

动态分配数组时，如果数组元素具有类类型，将使用该类的默认构造函数实现初始化；如果数组元素是内置类型，则无初始化。也可以使用跟在数组长度后面的一对空圆括号，对数组元素做值初始化。

对于动态分配的数组，其元素只能初始化为元素类型的默认值，而不能像数组变量一样，用初始化列表为数组元素提供各不相同的初值。

C++虽然不允许定义长度为0的数组变量，但明确指出，调用new动态创建长度为0的数组是合法的。

c_str返回的指针指向const char类型的数组，这样做是为了避免修改该数组。c_str返回的数组并不保证一定是有效的，接下来对st2的操作有可能会改变st2的值，使刚才返回的数组失效。如果程序需要持续访问该数据，则应该复制c_str函数返回的数组。

	const char *str = st2.c_str();

C++允许使用数组初始化vector对象。使用数组初始化vector对象，必须指出用于初始化式的第一个元素以及数组最后一个元素的下一位置的地址。

	const size_t arr_size = 6;
	int int_arr[arr_size] = {0, 1, 2, 3, 4, 5};
	vector<int> ivec(int_arr, int_arr + arr_size);
#### 4.4 多维数组 ####
严格地说，C++中没有多维数组，通常所指的多维数组其实就是数组的数组。

	int ia[3][4];
	int (*ip)[4] = ia;
	ip = &ia[2];
	int *ip[4];	// array of pointers to int
	int (*ip)[4]; // pointer to an array of 4 ints

用typedef简化指向多维数组的指针

	typedef int int_array[4];
	int_array *ip = ia;
## 第5章 表达式 ##
要理解由多个操作符组成的表达式，必须先理解操作符的优先级（precedence）、结合性（associativity）和操作数的求值顺序（order of evaluation）。
### 5.1 算术操作符 ###
如果两个操作数都是负数，求模操作的结果则为负数（或零）；如果只有一个操作数为负数，除法和求模结果的符号取决于机器。
### 5.2 关系操作符和逻辑操作符 ###
逻辑与和逻辑或操作符总是先计算其左操作数，然后再计算其右操作数。只有在仅靠做操作数的值无法确定该逻辑表达式的结果时，才会求解其右操作数。我们常常称这种求值策略为短路求值（short-circuit evaluation）。
### 5.3 位操作符 ###
对于位操作符，由于系统不能确保如何处理其操作数的符号位，所以强烈建议使用unsigned整型操作数。

对于移位操作符，如果操作数是有符号数，则插入符号位的副本或者0值，如何选择需依据具体的实现而定。

一般而言，标准库提供的bitset操作更直接、更容易阅读和书写、正确使用的可能性更高。而且，bitset对象的大小不受unsigned数的位数限制。通常来说，bitset优于整型数据的低级直接位操作。

移位操作符具有中等优先级：其优先级比算术操作符低，但比关系操作符、赋值操作符和条件操作符优先级高。若IO表达式的操作数包含了比IO操作符优先级低的操作符，相关的优先级别将影响书写该表达式的方式。

	cout << (10 < 42);
### 5.4 赋值操作符 ###
赋值操作具有右结合特性。当表达式含有多个赋值操作符时，从右向左结合。
### 5.5 自增和自减操作符 ###
前置操作需要做的工作更少，只需加1后返回加1后的结果即可。而后置操作符则必须先保存操作数原来的值，以便返回未加1之前的值作为操作的结果。

后自增操作的优先级高于解引用操作。

	*iter++
	*(iter++) // 后自增操作返回其操作数原值的副本
### 5.6 箭头操作符 ###
解引用的优先级低于点操作符。
### 5.7 条件操作符 ###

### 5.8 sizeof操作符 ###
sizeof操作符的作用是返回一个对象或类型名的长度，返回值的类型为size_t，长度的单位是字节。

	sizeof (type name);
	sizeof (expr);
	sizeof expr;

	Sales_item item, *p;
	sizeof (Sales_item);
	sizeof item;
	sizeof *p;

	int sz = sizeof(ia) / sizeof(*ia); // returns the number of elements in ia
### 5.9 逗号操作符 ###

### 5.10 复合表达式的求值 ###

### 5.11 new和delete表达式 ###
一旦删除了指针所指向的对象，立即将指针置为0，这样就非常清楚地表明指针不再指向任何对象。

	int i(1024);
	int *pi = new int(1024);
	string s(10, '9');
	string *ps = new string(10, '9');
	string *ps = new string; // initialized to empty string
	int *pi = new int; // pi points to an uninitialized int
	string *ps = new string();
	int *pi = new int(); // pi points to an int value-initialized to 0
	cls *pc = new cls();

如果new表达式无法获取需要的内存空间，系统将抛出名为bad_alloc的异常。
### 5.12 类型转换 ###
显示转换也称为强制类型转换（cast），包括以下名字命名的强制类型转换操作符：static\_cast, dynamic\_cast, const\_cast, reinterpret\_cast.

	double dval;
	int ival;
	ival *= dval;
	ival *= static_cast<int>(dval);
	ival += int (dval); // static_cast: converts double to int

	cast-name<type>(expression);

dynamic\_cast支持运行时识别指针或引用所指向的对象。

const\_cast，将转换掉表达式的const性质。假设有函数string_copy，我们对其唯一的char\*类型的参数只读不写。在访问该函数时，最好的选择是修改它让它接受const char\*类型的参数。

	const char *pc_str;
	char *pc = string_copy(const_cast<char*>(pc_str));
	string_copy((char*)pc_str); // const_cast: casts away const

只有使用const_cast才能将const性质转换掉。在这种情况下，试图使用其他三种形式的强制类型转换都会导致编译时的错误。类似地，除了添加或删除const特性，用const_cast符来执行其他任何类型转换，都会引起编译错误。

编译器隐式执行的任何类型转换都可以由static\_cast显式完成。

	double d = 97.0;
	char ch = static_cast<char>(d);

	void *p = &d;
	double *dp = static_cast<double*>(p);

reinterpret\_cast通常为操作数的位模式提供较低层次的重新解释。reinterpret\_cast本质上依赖于机器。为了安全地使用reinterpret\_cast，要求程序员完全理解所涉及的数据类型，以及编译器实现强制类型转换的细节。

	int *ip;
	char *pc = reinterpret_cast<char*>(ip);
	char *pc = (char*)ip; // reinterpret_cast: treats int* as char*

程序员必须永远记得pc所指向的真实对象其实是int型，而并非字符数组。任何假设pc是普通字符指针的应用，都有可能带来有趣的运行时错误。
## 第6章 语句 ##
### 6.1 简单语句 ###
### 6.2 声明语句 ###
### 6.3 复合语句（块） ###
### 6.4 语句作用域 ###
### 6.5 if语句 ###
### 6.6 switch语句 ###
cast标号必须是整型常量表达式。

对于switch结构，只能在它的最后一个case标号或default标号后面定义变量。制定这个规则是为了避免出现代码跳过变量的定义和初始化的情况。如果需要为某个特殊的case定义变量，则可以引入块语句。
### 6.7 while语句 ###
### 6.8 for循环语句 ###
### 6.9 do while语句 ###
与while语句不同，do while语句总是以分号结束。
### 6.10 break语句 ###
### 6.11 continue语句 ###
### 6.12 goto语句 ###
goto语句不能跨越变量的定义语句向前跳转。向前跳过未执行的变量定义语句，意味着变量可能在没有定义的情况下使用。如果确实需要在goto和其跳转对应的标号之间定义变量，则定义必须放在一个块语句中。
### 6.13 try块和异常处理 ###

	Sales_item item1,item2;
	std::cin >> item1 >> item2;
	if (item1.same_isbn(item2)) {
		std::cout << item1 + item2 << std::endl;
		return 0;
	} else {
		std::cerr << "Data must refer to same ISBN" << std::endl;
		return -1;
	}

	if (!item1.same_isbn(item2))
		throw runtime_error("Data must refer to same ISBN");
	std::cout << item1 + item2 << std::endl;

runtime_error类型是标准库异常类中的一种，在stdexcept头文件中定义。

	try {
		program-statements
	} catch (exception-specifier) {
		handler-statements
	} catch (exception-specifier) {
		handler-statements
	}

	catch (runtime_error err) {
		cout << err.what() << endl;
	}

如果不存在处理该异常的catch子句，程序的运行就要跳转到名为terminate的标准库函数，该函数在exception头文件中定义。这个标准库函数的行为依赖于系统，通常情况下，它的执行将导致程序非正常退出。

C++标准库定义了一组类，用于报告在标准库中的函数遇到的问题。标准库异常类定义在4个头文件中。

（1）exception头文件定义了最常见的异常类，它的类名是exception。这个类只通知异常的产生，但不会提供更多的信息。

（2）stdexcept头文件定义了几种常见的异常类。

exception	最常见的问题

runtime_error	运行时错误：仅在运行时才能检测到的问题

range_error	运行时错误：生成的结果超出了有意义的值域范围

overflow_error	运行时错误：计算上溢

underflow_error	运行时错误：计算下溢

logic_error	逻辑错误：可在运行前检测到的问题

domain_error	逻辑错误：参数的结果值不存在

invalid_argument	逻辑错误：不合适的参数

length_error	逻辑错误：试图生成一个超出该类型最大长度的对象

out_of_range	逻辑错误：使用一个超出有效范围的值

（3）new头文件定义了bad_alloc异常类型，提供因无法分配内存而由new抛出的异常。

（4）type_info头文件定义了bad_cast异常类型。
### 6.14 使用预处理器进行调试 ###
可使用NDEBUG预处理变量实现有条件的调试代码。

	#ifndef NDEBUG
	cerr << "starting main" << endl;
	#endif
	$ CC -DNDEBUG main.c

这样的命令行等效于在main.c的开头提供#define NDEBUG预处理命令。

预处理器还定义了其余4种在调试时非常有用的常量：

\_\_FILE\_\_ 文件名

\_\_LINE\_\_ 当前行号

\_\_TIME\_\_ 文件被编译的时间

\_\_DATE\_\_ 文件被编译的日期

另一个常见的调试技术是使用NDEBUG预处理变量以及assert（断言）预处理宏（preprocessor macro）。assert宏是在cassert头文件中定义的。   
## 第7章 函数 ##
### 7.1 函数的定义 ###

### 7.2 参数传递 ###
形参的初始化与变量的初始化一样，如果形参具有**非引用类型**，则复制实参的值，如果形参为引用类型，则它只是实参的别名。

使用引用形参返回额外的信息。

利用const引用避免复制。

应该将不需要修改的引用形参定义为const引用。普通的非const引用形参在使用时不太灵活。这样的形参既不能用const对象初始化，也不能用字面值或产生右值的表达式实参初始化。

传递指向指针的引用	

	void ptrswap(int *&v1, int *&v2) {
		int *tmp = v2;
		v2 = v1;
		v1 = tmp;
	}

v1是一个引用，与指向int型对象的指针相关联。

从避免复制vector的角度出发，应考虑将形参声明为引用类型。C++程序员倾向于通过传递指向容器中需要处理的元素的迭代器来传递容器。

	void print(vector<int>::const_iterator beg, vector<int>::const_iterator end)

如果形参是数组的引用，编译器不会将数组实参转化为指针，而是传递数组的引用本身。在这种情况下，数组大小成为形参和实参类型的一部分。编译器检查数组实参的大小与形参的大小是否匹配。

	void printValues(int (&arr)[10]);

多维数组的元素本身就是数组。除了第一维以外的所有维的长度都是元素类型的一部分，必须明确指定。

	void printValues(int (matrix*)[10], int rowSize);

含有可变形参的函数。varargs

	void foo(parm_list, ...);
	void foo(...);
### 7.3 return语句 ###
cstdlib头文件定义了两个预处理变量，分别用于表示程序运行成功和失败。EXIT_FAILURE, EXIT_SUCCESS

当函数返回引用类型时，没有复制返回值。相反，返回的是对象本身。

	const string &shorterString(const string &s1, const string &s2) {
		return s1.size() < s2.size() ? s1 : s2;
	}

千万不能返回局部变量的引用。

千万不要返回指向局部对象的指针。

	char &get_val(string &str, string::size_type ix) {
		return str[ix];
	}
	get_val(s, 0) = 'A'; // changes s[0] to A
### 7.4 函数声明 ###
默认实参是通过给形参表中的形参提供明确的初始值来指定的。但是，如果有一个形参具有默认实参，那么，它后面所有的形参都必须有默认实参。
### 7.5 局部变量 ###
只有当定义它的函数被调用时才存在的对象称为自动对象（automatic object）。

static局部对象（static local object），一旦被创建，在程序结束前都不会被撤销。
### 7.6 内联函数 ###

	const string &shorterString(const string &s1, const string &s2) {
		return s1.size() < s2.size() ? s1 : s2;
	}

调用函数比求解等价表达式要慢得多。

将函数指定为内联函数，就是将它在程序中每个调用点上“内联地”展开。在函数返回类型前加上关键字inline就可以将函数指定为内联函数。

内联说明（inline specification）对于编译器来说只是一个建议，编译器可以选择忽略这个建议。

内联函数应该在头文件中定义，这一点不同于其他函数。在头文件中加入或修改内联函数时，使用了该头文件的所有源文件都必须重新编译。
### 7.7 类的成员函数 ###

	class Sales_item {
	public:
		double avg_price() const;
		bool same_isbn(const Sales_item &rhs) const
			{return isbn == rhs.isbn;}
	private:
		std::string isbn;
		unsigned units_sold;
		double revenue;
	};

编译器隐式地将在类内定义的成员函数当作内联函数。

类的成员函数可以访问该类的private成员。

每个成员函数都有一个额外的、隐含的形参this。在调用成员函数时，形参this初始化为调用函数的对象的地址。为了理解成员函数的调用，我们可以认为我们写

	total.same_isbn(trans);

时，就像编译器将这个调用重写为

	Sales_item::same_isbn(&total, trans);

跟在成员函数声明的形参表后面的const的作用：const改变了隐含的this形参的类型。在调用total.same_isbn(trans)时，隐含的this形参将是一个指向total对象的const Sales_Item*类型的指针。就像如下编写same_isbn的函数体一样：

	bool Sales_item::same_isbn(const Sales_item *const this, 
							   const Sales_item &rhs) const
	{return isbn == rhs.isbn;}

用这种方式使用const的函数称为常量成员函数（const member function）。由于this是指向const对象的指针，const成员函数不能修改调用该函数的对象。因此，函数avg_price和函数same_isbn只能读取而不能修改调用它们的对象的数据成员。

const对象、指向const对象的指针或引用只能用于调用其const成员函数，如果尝试用它们来调用非const成员函数，则是错误的。

在类的定义外面定义成员函数必须指明它们是类的成员：

	double Sales_item::avg_price() const
	{
		if(units_sold)
			return revenue/units_sold;
		else
			return 0;
	}

如果函数被声明为const成员函数，那么函数定义时形参表后面也必须有const。

	// default constructor needed to initialize members of built-in type
	Sales_item(): units_sold(0), revenue(0.0) {}

除非在初始化列表中有其他表述，否则具有类类型的成员皆被其默认构造函数自动初始化。

如果没有为一个类显式定义任何构造函数，编译器将自动为这个类生成默认构造函数。由编译器创建的默认构造函数通常称为合成的默认构造函数（synthesized default constructor）。合成的默认构造函数一般适用于仅包含类类型成员的类。而对于含有内置了性或复合类型成员的类，则通常应该定义他们自己的默认构造函数初始化这些成员。

	Sales_item.h
	Sales_item.cc
### 7.8 重载函数 ###
出现在相同作用域中的两个函数，如果具有相同的名字而形参表不同，则称为重载函数（overloaded function）。函数不能仅仅基于不同的返回类型而实现重载。	

	Record lookup(const Account&);
	Record lookup(const Phone&);
	Record r1, r2;
	r1 = lookup(acct);
	r2 = lookup(phone);

	Record lookup(Phone);
	Record lookup(const Phone); // redeclaration

第二个函数声明被视为第一个的重复声明。其原因在于实参传递的方式。复制形参时不考虑形参是否为const--函数操纵的只是副本。函数无法修改实参。结果，既可将const对象传递给const形参，也可传递给非const形参，这两种形参并无本质区别。值得注意的是，形参与const形参的等价行仅适用于非引用形参。有const引用形参的函数与有非const引用形参的函数是不同的。类似地，如果函数带有指向const类型的指针形参，则与带有指向相同类型的非const对象的指针形参的函数不相同。

如果局部地声明一个函数，则该函数将屏蔽而不是重载在外层作用域中声明的同名函数。由此推论，每一个版本的重载函数都应在同一个作用域中声明。

函数重载确定（overload resolution，即函数匹配function matching）是将函数调用与重载函数集合中的一个函数相关联的过程。如果有且仅有一个函数满足下列条件，则匹配成功。

（1）其每个实参的匹配都不劣于其他可行函数需要的匹配。

（2）至少有一个实参的匹配优于其他可行函数提供的匹配。

为了确定最佳匹配，编译器将实参类型到相应形参类型的转换划分等级。转换等级以降序排列如下：

（1）精确匹配（exact match）。实参与形参类型相同。

（2）通过类型提升（promotion）实现的匹配。

（3）通过标准转换（standard conversion）实现的匹配。

（4）通过类类型转换（class-type conversion）实现的匹配。
### 7.9 指向函数的指针 ###
函数指针是指指向函数而非指向对象的指针。

	bool (*pf) (const string &, const string &);
	typedef bool (*cmpFcn)(const string &, const string &);

函数指针只能通过同类型的函数或函数指针或0值常量表达式进行初始化或赋值。将函数指针初始化为0，表示该指针不指向任何函数。

函数指针形参

	void useBigger(const string &, const string &, bool(const string &, const string &));
	void useBigger(const string &, const string &, bool (*)(const string &, const string &));

返回指向函数的指针

	int (*ff(int))(int*, int);
	typedef int (*PF)(int*, int);
	PF ff(int);

阅读函数指针生命的最佳方法是从声明的名字开始由里而外理解。

允许将形参定义为函数类型，但函数的返回类型则必须是指向函数的指针，而不能是函数。

	typedef int func(int*, int);
	void f1(func);
	func f2(int); // error
	func *f3(int);

指向重载函数的指针。指针的类型必须与重载函数的一个版本精确匹配。如果没有精确匹配的函数，则对该指针的初始化或赋值都将导致编译错误。

	extern void ff(vector<double>);
	extern void ff(unsigned int);
	void (*pf1)(unsigned int) = &ff;
## 第8章 标准IO库 ##

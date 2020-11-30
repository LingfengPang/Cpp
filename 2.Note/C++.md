#LINUX指令
g++ test.cpp  
需要链接C++库时候：g++ test.cpp -lg++
编译多个文件：g++ test1.cpp test2.cpp
重新编译(假设只改动了test1.cpp)：g++ test1.cpp test2.o
g++ -o test.exe test.cpp
需要搜寻一些外部库时候g++ -o test.cpp -lm

#进制
int a = 42 10进制
int a = 042 8进制
int a = 0x42 16进制

cout<<1000 1000存储类型为int

#wchat_t（宽字符类型）
存储P到bob，然后输出，输入可以用wcin
wchart_t bob = L'P';
wcout << L"tall"<< endl;

#char16_t/char32_t
两者都是无符号的，表示字符常量或字符串常量
char16_t ch1 = u'q';
char32_t ch2 = U'\U0000222B';

#常量
C++中尽量不要使用#define，应该使用const

#浮点
float精确到小数点后六位
double  15位

ios_base::fixed作用：
               设置cout为定点输出格式
ios_base::floatfield作用：
               设置输出时按浮点格式，小数点后有6位数字


#强制转换
（long） a
a (long)
char {66}
int('Q')
static_cast&lt;long&gt; a


#数组初始化
int a[4]={1,2,3,4};
int a[4];
a[4] = {1,2,3,4}是不允许的
a = b 是不允许的

int a[4] = {1,2}只初始化前面两个、其余为0
int a[4] = {0}只初始化前面1个，其余为0

int a[] ={1,2,3,4}初始化长度为4的数组
int a[4] {1,2,3,4}
int a[4] {}所有元素都为0
数组长度：int len = sizeof(a)/sizeof(int)
#输入输出
##输出
cout.write(str,size)；输出str前size个数组
cout << hex;//以16进制输出
cout << oct;//以8进制输出
dec(cout);//以10进制输出
cout.width(n)；//调整字宽，一次有效
cout.fill(ch);//以ch填充，可以配合字宽使用
cout.precision(n);//调整精度，显示n位小数，但不会显示末尾的0
cout.setf(iosbase::showpoint);//显示末尾的0
cout<< setw(n) << setprecision(n2);设置字宽位n,小数点精度为n2
cout << setfill(ch) 以ch填充
##字符/字符串输入
cin以空格，制表符，换行决定字符串结束的位置
cin.getline（）读取一行，能读取空格，丢弃换行
cin.getline（str,100,':'）读取至‘：’，缓存区会丢弃‘：’
cin.get（str,100,':'）读取至‘：’，缓存区会保留‘：’
如果缓存区还有字符串
可以通过cin.ignore(str,'\n')清除


cin.get（）读取一行，能读取空格，保留换行
用法如下：ch = cin.get（）,将读取的值赋给ch
cin.get(ch)，读取字符赋值给ch，能读取空格
cin.get(a,20);读取一行
cin.get();读取新行；换行必须有这个
cin.get(b,20)读取第二行
cin.getline().getline()拼接字符串
cout << R"+*显示原始字符

cin.read(char*,size);读取指定长度字符，不能转化为字符串
cin.peak();返回流中的下一个字符，但不抽出流
cin.putback(ch);将ch插入字符串

#String类
有很多和字符数组操作相似
但有如下不同
赋值  str1 = str2;
拼接 str1 += str2;
字符串长度，str.size()

##构造函数
string(const char *s)	使用c风格字符串初始化string对象
string(size_type n, char c)	创建一个含有n个元素的string对象，其中每个元素都被初始化为字符c
string(const string &str)	将一个string对象初始化为string对象
string（）	创建一个默认的string对象，长度为0.
string（const char *s, size_type n）	将string对象初始化为s指向的C字符串的前n个字符，即使超过了s的结尾
string(const string &str, size_type pos=0, size_type n = pos)	将一个string对象初始化为对象str中从位置pos开始到结尾的字符，或者从pos开始的n个字符。
template< class Iter>string[Iter begin, Iter end)	将string对象初始化为区间[begin, end)内的字符，其中begin和end的行为就像指针，用于指定位置。

##string类输入
cin >>str//输入一个单词
getline(cin,str)//输入一行，丢弃空格
getline(str,' : ')//输入一行，丢弃空格读取至‘：’丢弃‘：’

##find函数
fing(str,pos)从pos开始，返回字符串str的索引，没有则返回string::npos;
find(str,pos,size) 从pos开始，长度为size,返回字符串str的索引，没有则返回string::npos;
find_first_of(str)返回字符串内第一个str的索引
last_first_of(str)返回字符串内最后一个str的索引
find_first_not_off（str）返回第一个字符串内不包含的索引 

#结构体
struct A{
    unsigned in SN:4 //定义为4位

}

#共用体union
只能存储int long double
共用体结构的值是共享的

#枚举
太简单了

#指针
取址符号&，&a表示变量a的地址
在指针定义之后要指向一个地址（很重要）
可以使用new 来分配地址
int *p = new int;

delete用来释放new分配的内存（不能释放不是new分配的内存，对于指定的内存也不建议用delete）。然而，对空指针使用delete是安全的。

int *p = new p;
int jugs = 5;
p = &jug;
delete p;//这样子是不允许的，会将jug的内存释放掉

##使用new创建动态数组
int *p = new int [10];
delete [] p

##数组和指针
int a[10];
p = &a[0]或者p = a

##数组的地址
int a[10]
cout<<a,a[0]的地址
cout<<&a,数组a的全部地址

##动态数组
int size
int *p = new int [size]

##智能指针，可以将new获得的地址赋给对象，智能指针过期时会自动释放内存
std::auto_ptr< typename > p (new typename)
用这个定义的指针不能相互赋值（赋值时会释放内存操作）
std::shared_ptr< typename > p (new typename)
std::uniqued_ptr< typename > p (new typename)
```
std::uniqued_ptr< string > p1 (new string "aa");
std::uniqued_ptr< string > p2 ;
p2 = p1;//not allowed
p3 =std::uniqued_ptr< string >(new string "aa");//allowed
```

#模板类
##vector
vi.erase(vi.begin(),vi.begin()+2)//擦除
vi.size()//尺寸
vi.end()//末尾
vi.push_back(e)//在Vector最后添加一个元素e
v.insert(v.begin(),8);//在最前面插入新元素8
v.insert(v.begin()+3,1);//在迭代器中下标为3的元素前插入新元素
v.insert(v.end(),3);//在向量末尾追加新元素
v.insert(v.end(),3,0);//在尾部插入3个0
##array
这些的下标是允许越界的，但会造成不必要的麻烦
array的长度是固定的，用于代替数组
##valarray
适合数据运算
```
valarry<double> v1;//一个double
valarry<double> v1（8）;//大小为8的double
valarry<double> v1（10,8）;//大小为8的double,每个元素为10的
valarry<double> v1（a,8）;//大小为8的double,且初始化为指定数组a的元素
valarry<double> v1 = {1，2，3，45}；

vector<int> vi
vector<int> vi(8)
vi.begin()
auto p = vi.begin()
vi.erase(vi.begin(),vi.begin()+2)//擦除
vi.size()//尺寸

array<int,5> ai//包含5个int类型
array<double,4>ad = {1.2,2.1,3.43,2.2}
```

#for循环
for(设置初始值；执行测试，判断循环是否进行；更新用于测试的值){
    执行循环操作
}

#指针的递增和递减
1\*p++ ,先取值，后指针++
2\*++p,先指针++，后取值
3++\*p,先取值，后值++
4（*p）++,先取值，后值++

#string比较
可以直接比较
word != "mate"

#基于范围的for
```
int a[5] = {1,2,3,4,5}
for(int i:a){//i表示a数组的第一个元素，每次循环增加
    cout << i <<endl;
}
```
for(int i:{1,2,3,4,5}){//i表示a数组的第一个元素，每次循环增加
    cout << i <<endl;
}

for_each(begin,end,fun)
eg. for_each(v.begin(),v.end(),show)





#二维数组

```
char *city[5]={
    "Beijing",
    "Shanghai",
    "Chongqing",
    "Chengdu",
    "Hangzhou"
}
```

#字符函数（P179）
```
isalnum()

如果参数是字母数字，即字母或者数字，函数返回true

isalpha()

如果参数是字母，函数返回true

isblank()

如果参数是水平制表符或空格，函数返回true

iscntrl()

如果参数是控制字符，函数返回true

isdigit()

如果参数是数字（0－9），函数返回true

isgraph()

如果参数是除空格之外的打印字符，函数返回true

islower()

如果参数是小写字母，函数返回true

isprint()

如果参数是打印字符（包括空格），函数返回true

ispunct()

如果参数是标点符号，函数返回true

isspace()

如果参数是标准空白字符，如空格、换行符、水平或垂直制表符，函数返回true

isupper()

如果参数是大写字母，函数返回true

isxdigit()

如果参数是十六进制数字，即0－9、a－f、A－F，函数返回true

tolower()

如果参数是大写字符，返回其小写，否则返回该参数

toupper()

如果参数是小写字符，返回其大写，否则返回该参数
```
#？：运算符
A?B:C
若A为1则执行B，否则执行C。

#continue 和 break
```
while(xx){
    if(xx)
        continue//跳过循环的剩余部分，开始下一轮循环
    if(xx)
        break//结束循环
}
```

#const
##const和指针
int age =39
const int *p =&age;
p指向const int,不能用p修改age,但可以修改age，但p可以指向新得地址

const int age =39
const int *p =&age;
p指向const int,不能用p修改age,age也无法修改


int age =39
const int *p =&age;//p是指向常数的指针,ps不能修改age,但能指向另一个位置
int * const pt = &age//pt是指向int的常指针,pt可以修改age，不能指向另一个地址

int age =39
const int * const p =&age;//p指向age,不能修改age,也不能指向另一个地址

##const和函数
1.作为函数参数时，表示参数不能被修改
2.修饰返回值 const char* fun();
表示返回值不能修改，只能赋给const变量
3.修饰成员变量 char* fun const
表示不能修改类成员变量
#函数指针
double (*pf)(int)
double pam (int);
pf =pam;

#内敛inline
能加快函数的运行时间，但会占用更多的内存

#引用&
int &a =b;//必须声明时就初始化  
a和b有相同的值和地址

swap(int a, int b)//不能交换a,b
swap(int *a, int *b)//能交换a,b
swap(int &a, int &b)//能交换a,b
```
int cube(double &r){
    r = r * r * r;
    return r;
}
```
上述r的值会改变
cube(x+0.5)//也不能这样用

但是如果引用是const时
实参类型正确，但不是左值如x+0.5
或者类型不正确，如，long l,cube(l)
或类型正确，但没名称，如 cube(0.7)
会产生临时变量，在函数调用后删除


函数返回引用时注意变量的持续性
```
const int &fun(&a){
    return a;//a时引用，可以这么用
}


const int &fun(&a){
    int b;
    b = a;
    return b;//b做调用结束后被删除，不能这么用
}

const int &fun(&a){
    int *p
    *p = a
    return *p;//可以这么干
}

```

引用用于继承
void file_if(ostream &os,double fo,const double fe[],int n);
file_if(fout,objective,eps,5);//写入文件
file_if(cout,objective,eps,5);//显示在屏幕哈桑

#默认参数
int price(int m,int n = 4);如果调用时没给n值，则默认为4
price(5)//m为5，为4

#函数重载
函数名和类型相同，但形参不同
```
double fun(char *a);
double fun(const char *ca)//是重载
double fun(int a,int b)//是重载
double fun(char *b)//不是重载
int fun(char *a)//不是重载
```
C++内部会对重载函数命名

#模板

template T
SWAP (T &A, T&b)

最佳到最差
1.常规函数优于模板函数
2.提升转化char,short转换为int,float转化为double
3.标准转化，int转化为char,long转化为double
4.较具体的模板更优先
template < class T > void fun(T t)
template <> void fun< int >(int &t)
下面的优先级更高
template < class T1,class T2 > void fun(T1 t1，T2 t2)
在T1,T2，类型未知情况下如果实现
sum = t1 + t2,sum类型未知
可以使用decltype
decltype(t1+t2) sum = t1+t2;

但是如果函数return(t1+t2)不能使用decltype，可以使用auto,如下使用：
```
template < class T1,class T2 >
auto gt(T1 X,T2 Y) ->decltype(x+y)
{
    return (x+y)
}
```

#寄存器变量
register 建议使用CPU寄存器存储，提高访问速度

#静态变量static

在文件1中：int a
文件2中：int a 
是不允许的，但是
在文件1中：static int a
文件2中：int a 
是可以的

函数里的静态变量不会被释放哦

#说明符和限定符
thread_local用于线程之间
mutable 某个const结构的mutable成员可以修改
volatile 表示变量没有对其内存修改其值也可能改变

#new
用new进行初始化
int *pi = new int (6),初始化值为6
int *pi = new int
int *pi = new（sizeof(int)）
int *pi = new int [ 40 ]
int *pi = new(40 * sizeof(int))

定位运算
char buffer
char *p2 = new(buffer) int[ 20 ],将数组放入buffer2中
用于定位的new不能被delete释放

#类的初始化
```
Bozo b = Bozo("name",1);
Bozo *b = new Bozo("name",1);
Bozo b("name",1);
```

#类的构造函数
```
class A{
public:
    A() = default;//使用系统默认的构造函数
    A & operator =(cosnt A &) = delete//禁止编译器使用特定的类
}
```

#this指针
在C++中，当成员函数中某个变量与成员变量名字相同，则使用this关键字来表示成员变量。

 或者，需要返回类变量或者结构体变量的时候，使用this关键字。
```
const  Stock & compare(const Stock &s) const;//在类中的声明


const Stock & Stock :: compare(const Stock &s) const{
    if(s.total_val>total_val)
        return s;
    else
    {
        return *this;
    }
    
}
```

#对象数组
Bozo b[4]={
    Bozo（）,
    Bozo(),
    Bozo(),
    Bozo()
}

#作用域内枚举
enum class egg{small,middle,big};
egg a = egg::small;

#类的析构
注意在形参为类的函数时，如果传入不是引用，在函数调用后会被删除而调用析构函数！！！

#类的复制
类可以直接复制
Person A = B;
但是不能私有变量复制，如下是不允许的：
A.name = B.name

#派生类
派生类包含基类对象，公有派生--基类公有成员会成为派生类的公有成员，基类的私有成员也会成为派生类的一部分，但只能通过基类的公有和保护方法访问
派生类不能直接访问基类的私有成员，需要使用基类的公有方法进行访问。
派生类构造函数应该通过成员初始化列表将基类信息传递给基类构造函数
派生类构造函数应该初始化派生类新增的数据成员

派生类和基类是 is - a的关系

#虚函数virtual
1.基类和派生类声明虚函数时，在调用时会类来使用方法，虚函数一般用在派生类重写基类的方法
2.析构函数声明为虚函数可以确保释放派生对象时，按正确的顺序调用虚构函数，必须要有一个虚析构函数，即使它什么都不做
3.构造函数和友元函数不能是虚函数，析构函数一定是虚函数
4.派生类没有重新定义虚函数则使用基类的方法
5.虚函数不能重载

#protect
派生类能访问基类的protect成员，但不能直接访问私有成员

#动态内存分派
注意一些类的赋值

#explicit
关闭隐式转换

#私有继承
基类的公有成员和保护成员都将成为派生类的私有成员


#保护继承
基类的公有成员和保护成员都将成为派生类的私有成员
基类的保护和私有成员都会成为派生类的保护成员

#虚基类
class Granpa;
class father : vitural public Granpa{} 
class mother : public vitural Granpa{}
class me : public father,public mother {}
me就可以使用 Granpa的构造函数
如果不声明虚基类，无法使用Granpa的构造函数

#模板类
目前不支持将类定义和方法实现放在两个不同的文件里

#友元类
```
Class A{
    public:
    friend Class B;
}
//类B可以访问A的私有成员
```
#嵌套类
| 声明位置| 该类是否能使用 | 派生类能否使用 |外部能否使用|
| :-----| ----: | :----: |:----:|
| private | 1 | 0 |1 |
| protect | 1 | 1 |1 |
| public | 1 | 1 |1,通过类限定符来使用 |

#异常
abort();//程序异常终止
```
try-catch-throw异常处理
try{

    throw  ".."//抛出异常
}//可能出现异常
catch (const char *){
    //处理异常
}
```
在函数后加 noexcept()表示函数不会引发异常
void fun() noexcept;

嵌套的异常可能会一直传递到最上层

#RTTI
RTTI是在程序运行阶段确定对象类型的提供的一种标准方式

##dynamic_cast 
用一个指向基类的指针来生成一个指向派生类的指针，否则返回0
```
Super *pm = dynamic_cast <Super*>(pg)
```
pg如果可以转换为Super，则返回对象的地址，否则返回Null
##typeid 
返回一个指出对象类型的值
typeid(Super) == typeid(*pm)
cout << typeid(*pm).name()//输出Super
##type_infou
结构存储了有关特定类型的信息

#类型转换
##dynamic_cast 
用一个指向基类的指针来生成一个指向派生类的指针，否则返回0
```
Super *pm = dynamic_cast <Super*>(pg)
```
##const_cast
将值改变为cosnt或volatile
const High *pbar 
High *pb = const_cast<High *>(pbar)//pb删除const

##static_cast
High *pb = static_cast<Low *>(pbar)//pb删除const

##reinterpret_cast
用于危险的转换

#STL
//创建一个输出迭代器，输入为int,输出为char
ostream_iterator< int,char > out_iter(cout," ");

##list
##queue
##stack

##关联容器
将key和value关联在一起
容器X
###set
键是唯一的，不能存储多个相同的值
set< typename > A(pos,pos+n)
set_union(A.begin(),A.end(),B.begin(),B.end(),out);并集
set_intersection(A.begin(),A.end(),B.begin(),B.end(),out);交集
set_union(A.begin(),A.end(),B.begin(),B.end(),out);差集
###multimap
multimap< keytype,valuetype > A
multimap< int ,string > A
count(keytype)查询键，返回具有该键的元素数目
euqal_range(keytype)返回当前键的元素(两个值，key和value,存放在pair中 )

##slice
slice(1,4,3)创建初值为1，长度为4，等差为3的数列

##initializer
必须包含头文件< initializer >
包含了begin,end,size

#文件
##写文件
```
ofstream fout;
fout.open("1.txt");

ofstream fout("1.txt");
fout<<str;//将str放至文件
fout.close()
```

##读文件

```
ifstream fin;
fin.open("1.txt");
if(fin.fail()){//if(!fin.is_open())

}
ofstream fin("1.txt");

char ch;
fin >> ch;
char buff[80];
fin >> buff;
str line;
getline(fin,line);
fin.close();
```
##ios_base
in 只读打开文件
out 只写杜凯文件
ate 移到文件末尾
app 追加到文件尾
binary 二进制文件

##二进制文件读写
fout.write((char *) &p,sizeof p);
ifstream fin;
fin('xxx.txt',ios_base::in|ios_base::binary)
fin.read((char *) &p,sizeof p)

##随机文件读取
fin.seekg(n,ios_base::beg)开头30字节 
fin.seekg(0,ios_base::end)文件结尾
fin.seekg(n)第n个字节

#lambda
[](int x){return x % 3 == 0};
auto mod3 = [](int x){return x % 3 == 0};

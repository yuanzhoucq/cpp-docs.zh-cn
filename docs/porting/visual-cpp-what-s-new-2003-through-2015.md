---
title: "Visual C++ 新增功能（2003 - 2015）| Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
ms.assetid: c4afde6f-3d75-40bf-986f-be57e3818e26
caps.latest.revision: 6
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Human Translation
ms.sourcegitcommit: a937c9d083a7e4331af63323a19fb207142604a0
ms.openlocfilehash: c6ac9fb7400bd0c37d1da5a0c6bd66ccbf7abd6c
ms.lasthandoff: 02/24/2017

---
# <a name="visual-c-what39s-new-2003-through-2015"></a>Visual C++ 新增功能（2003 - 2015）

**注意**：有关 Visual Studio 2017 的信息，请参阅 [Visual Studio 2017 中 Visual C++ 的新增功能](../what-s-new-for-visual-cpp-in-visual-studio.md)和 [Visual Studio 2017 中 Visual C++ 的符合性改进](../cpp-conformance-improvements-2017.md)。

在 Visual C++ 2015 及更高版本中，对编译器符合性的持续改进有时会改变编译器理解现有源代码的方式。 发生这种情况时，可能会在生成过程中遇到新的或不同的错误，甚至以前生成且似乎运行正常的代码也可能出现行为差异。  
  
 幸运的是，这些差异对大部分源代码没有影响或影响极小，而且需要更改源代码或进行其他更改以解决这些差异时，修补程序通常小型且简单。 我们列出了以前可接受、现在可能需要更改的许多源代码示例（之前）及其修补程序（之后）。  
  
 虽然这些差异可能会影响源代码或其他生成项目，但其不会影响 Visual C++ 版本更新之间的二进制文件兼容性。 重大更改是严重性较高的更改，可能会影响二进制文件兼容性，但此类二进制文件兼容性中断问题仅发生在 Visual C++ 的主版本之间。 例如，在 Visual C ++ 2013 和 Visual C ++ 2015 之间。 有关 Visual C++ 2013 和 Visual C++ 2015 之间的重大更改的详细信息，请参阅 [Visual C++ 更改历史记录（2003 - 2015）](../porting/visual-cpp-change-history-2003-2015.md)。  
  
-   [Visual C++ 2015 中的符合性改进](#VS_RTM)  
  
-   [更新 1 中的符合性改进](#VS_Update1)  
  
-   [更新 2 中的符合性改进](#VS_Update2)  
  
-   [更新 3 中的符合性改进](#VS_Update3)  
  
##  <a name="VS_RTM"></a>Visual C++ 2015 中的符合性改进  
  
-   /Zc:forScope- 选项  
  
     编译器选项 **/Zc:forScope-** 已弃用，并且将在将来版本中删除。  
  
    ```  
    Command line warning  D9035: option 'Zc:forScope-' has been deprecated and will be removed in a future release  
    ```  
  
     以前会经常用到此选项，以便允许非标准代码在点的位置之后使用循环变量，根据标准规范，这些变量本应该在范围之外。 仅当使用 /Za 选项进行编译时才需要，因为没有 /Za，将始终允许在循环结束后使用 for 循环变量。 如果你不关心标准符合性（例如，如果你的代码不是为了移植到其他编译器），你可以关闭 /Za 选项（或将“禁用语言扩展”属性设置为“否”）。 如果你确实关心编写可移植且符合标准的代码，则应重写代码，以便通过将此类变量的声明移到循环以外的点使其符合标准。  
  
    ```  
    // zc_forScope.cpp  
    // compile with: /Zc:forScope- /Za  
    // C2065 expected  
    int main() {  
       // Uncomment the following line to resolve.  
       // int i;  
       for (int i =0; i < 1; i++)  
          ;  
       i = 20;   // i has already gone out of scope under /Za  
    }  
    ```  
  
-   **/Zg 编译器选项**  
  
     /Zg 编译器选项（生成函数原型）不再可用。 此此编译器选项已被弃用。  
  
-   你无法再使用 mstest.exe 从命令行运行 C++/CLI 单元测试。 请改用 vstest.console.exe。 请参阅 [VSTest.Console.exe 命令行选项](/devops-test-docs/test/vstest-console-exe-command-line-options)。  
  
-   **可变关键字**  
  
     在之前其正确编译的位置，不再允许存在 `mutable` 存储类说明符。 现在，编译器报告错误 C2071（非法存储类）。 根据标准，可变说明符仅可应用于类数据成员的名称，不能应用于声明为 const 或 static 的名称，也不能应用于引用成员。  
  
     例如，考虑以下代码：  
  
    ```  
    struct S {  
        mutable int &r;  
    };  
    ```  
  
     早期版本的 Visual C++ 编译器接受此代码，但现在编译器则报告以下错误：  
  
    ```Output  
    error C2071: 'S::r': illegal storage class  
    ```  
  
     若要修复此错误，只需删除冗余的可变关键字。  
  
-   **char_16_t 和 char32_t**  
  
     你不能再使用 `char16_t` 或 `char32_t` 作为 typedef 中的别名，因为这些类型现在被视为内置。 用户和库作者通常会将 char16_t 和 char32_t 分别定义为 uint16_t 和 uint32_t 的别名。  
  
    ```  
    #include <cstdint>  
  
    typedef uint16_t char16_t; //C2628  
    typedef uint32_t char32_t; //C2628  
  
    int main(int argc, char* argv[])  
    {  
    uint16_t x = 1; uint32_t y = 2;  
    char16_t a = x;   
    char32_t b = y;   
    return 0;  
    }  
    ```  
  
     若要更新你的代码，请删除 typedef 声明，并重命名与这些名称发生冲突的任何其他标识符。  
  
-   **非类型模板参数**  
  
     现在会在提供显式模板参数时准确检查包含非类型模板参数的某些代码的类型符合性。 例如，在早期版本的 Visual C++ 中正确编译的以下代码。  
  
    ```  
    struct S1  
    {  
    void f(int);  
    void f(int, int);  
    };  
  
    struct S2  
    {  
    template <class C, void (C::*Function)(int) const> void f() {}  
    };  
  
    void f()  
    {  
    S2 s2;  
    s2.f<S1, &S1::f>();  
    }  
  
    ```  
  
     当前编译器可以准确报告错误，因为模板参数类型不匹配模板参数（该参数是指向 const 成员的指针，但函数为非 const）：  
  
    ```Output  
    error C2893: Failed to specialize function template 'void S2::f(void)'note: With the following template arguments:note: 'C=S1'note: 'Function=S1::f'  
    ```  
  
     若要在代码中修复此错误，请确保你使用的模板自变量类型匹配模板参数声明的类型。  
  
-   **__declspec(align)**  
  
     编译器不再接受函数上的 `__declspec(align)` 。 以前会始终忽略此项，但现在会产生编译器错误。  
  
    ```  
    error C3323: 'alignas' and '__declspec(align)' are not allowed on function declarations  
    ```  
  
     若要解决此问题，请从函数声明中删除 `__declspec(align)` 。 因为它不起作用，将其删除不会更改任何内容。  
  
-   **异常处理**  
  
     有几个对异常处理的更改。 首先，异常对象必须可复制或可移动。 在 [!INCLUDE[cpp_dev12_long](../build/reference/includes/cpp_dev12_long_md.md)] 中编译的以下代码却不能在 [!INCLUDE[cpp_dev14_long](../porting/includes/cpp_dev14_long_md.md)] 中进行编译：  
  
    ```  
    struct S {  
    public:  
        S();  
    private:  
        S(const S &);  
    };  
  
    int main()  
    {  
        throw S(); // error  
    }  
  
    ```  
  
     问题在于，复制构造函数是私有的，因此对象无法像处理异常的标准过程那样进行复制。 当复制构造函数为声明的 `explicit`时，这同样适用。  
  
    ```  
    struct S {  
        S();  
        explicit S(const S &);  
    };  
  
    int main()  
    {  
        throw S(); // error  
    }  
  
    ```  
  
     若要更新你的代码，请确保异常对象的复制构造函数是公用的且未标记为 `explicit`。  
  
     通过值捕获异常还要求异常对象可复制。 在 [!INCLUDE[cpp_dev12_long](../build/reference/includes/cpp_dev12_long_md.md)] 中编译的以下代码却不能在 [!INCLUDE[cpp_dev14_long](../porting/includes/cpp_dev14_long_md.md)] 中进行编译：  
  
    ```  
    struct B {  
    public:  
        B();  
    private:  
        B(const B &);  
    };  
  
    struct D : public B {  
    };  
  
    int main()  
    {  
        try  
        {  
        }  
        catch (D d) // error  
        {  
        }  
    }  
  
    ```  
  
     可以通过将 `catch` 的参数类型更改为引用来解决此问题。  
  
    ```  
    catch(D& d)  
    {  
    }  
    ```  
  
-   **后跟宏的字符串文本**  
  
     编译器现在支持用户定义的文本。 因此，宏之前没有任何干预空格的字符串文本被视为用户定义的文本，这可能会产生错误或意外结果。 例如，在早期的编译器中，成功编译了以下代码：  
  
    ```  
    #define _x "there"  
    char* func() {  
        return "hello"_x;  
    }  
    int main()  
    {  
        char * p = func();  
        return 0;  
    }  
    ```  
  
     编译器将此视为后跟宏的字符串文本“hello”，该宏是展开的“there”，然后两个字符串串联成一个。 在 [!INCLUDE[cpp_dev14_long](../porting/includes/cpp_dev14_long_md.md)] 中，编译器将此解释为用户定义的文字，但由于没有定义匹配的用户定义的 _x 文本，它将报告错误。  
  
    ```  
    error C3688: invalid literal suffix '_x'; literal operator or literal operator template 'operator ""_x' not found  
    note: Did you forget a space between the string literal and the prefix of the following string literal?  
  
    ```  
  
     若要解决此问题，请在字符串文本和宏之间添加一个空格。  
  
-   **相邻字符串文本**  
  
     与上文类似，由于字符串分析中的相关变化，没有任何空格的相邻字符串文本（或宽或窄的字符字符串文本）被视为 Visaul C++ 早期版本中的单个串联字符串。 在 [!INCLUDE[cpp_dev14_long](../porting/includes/cpp_dev14_long_md.md)] 中，现在必须在两个字符串之间添加空格。 例如，必须更改以下代码：  
  
    ```  
    char * str = "abc""def";  
    ```  
  
     只需在两个字符串之间添加空间。  
  
    ```  
    char * str = "abc" "def";  
    ```  
  
-   **placement new 和 placement delete**  
  
     对 delete 运算符做出更改以使其符合 C++14 标准。 标准更改的详细信息位于 [C++ 调整了大小的释放](http://isocpp.org/files/papers/n3778.html)。 这些更改将添加采用大小参数的全局 delete 运算符的形式。 重大更改为，如果你之前使用的是具有相同签名的运算符 delete（以与 placement new 运算符对应），你将收到编译器错误（C2956，在使用 placement new 的点位置出现，因为在代码中的该位置，编译器会尝试标识适当匹配的 delete 运算符）。  
  
     函数 `void operator delete(void *, size_t)` 是与 C++11 中的 placement new 函数“void \* operator new(size_t, size_t)”对应的 placement delete 运算符。 使用 C++14 调整了大小的释放，此 delete 函数现在是 *常用释放函数* （全局 delete 运算符）。 标准要求为，如果使用 placement new 查找相应的 delete 函数和常用释放函数，则程序会出现格式错误。  
  
     例如，假设你的代码同时定义了 placement new 和 placement delete：  
  
    ```  
    void * operator new(std::size_t, std::size_t);  
    void operator delete(void*, std::size_t) noexcept;  
  
    ```  
  
     由于定义的 placement delete 运算符和新的全局调整大小的 delete 运算符之间的函数签名匹配，因此就会出现问题。 考虑是否可以使用任何 placement new 和 placement delete 运算符的其他类型（size_t 除外）。  请注意，size_t typedef 的类型取决于编译器；在 Visual C++ 中，它是一个无符号整型的 typedef。 较好的解决办法就是使用如下的枚举类型：  
  
    ```  
    enum class my_type : size_t {};  
  
    ```  
  
     然后，更改你对 placement new 和 placement delete 的定义，以使用此类型作为第二个参数（而不是 size_t）。 你还需要更新对 placement new 的调用以传递新类型（例如，通过使用 `static_cast<my_type>` 从整数值转换）并更新 new 和 delete 的定义以强制转换回整数类型。 你无需为此使用枚举；具有 size_t 成员的类类型也将起作用。  
  
     你还可以将 placement new 全部消除作为备选解决方案。 如果你的代码使用 placement new 实现内存池，其中位置参数是分配或删除的对象的大小，则调整了大小的释放功能可能适合替换你自定义的内存池代码，且你可以去掉位置函数，仅使用自己两个参数的 delete 运算符（而不是位置函数）。  
  
     如果你不想立即更新代码，可以通过使用编译器选项 /Zc:sizedDealloc- 恢复到旧行为。 如果使用此选项，则不存在两个参数的 delete 函数，并且也不会导致与 placement delete 运算符发生冲突。  
  
-   **联合数据成员**  
  
     联合数据成员不再具有引用类型。 以下代码在 [!INCLUDE[cpp_dev12_long](../build/reference/includes/cpp_dev12_long_md.md)]中成功编译，但在 [!INCLUDE[cpp_dev14_long](../porting/includes/cpp_dev14_long_md.md)] 中产生错误。  
  
    ```  
    union U1 {  
        const int i;  
    };  
    union U2 {  
       int &i;  
    };  
    union U3 {  
        struct {int &i;};  
    };  
    ```  
  
     前面的代码产生以下错误：  
  
    ```Output  
    test.cpp(67): error C2625: 'U2::i': illegal union member; type 'int &' is reference type  
    test.cpp(70): error C2625: 'U3::i': illegal union member; type 'int &' is reference type  
    ```  
  
     若要解决此问题，请将引用类型更改为指针或值。 更改指针类型需要对使用联合字段的代码进行更改。 将代码更改为值将更改存储在联合中的数据，这会影响其他字段，因为联合类型中的字段共享相同的内存。 根据值的大小，它还可能更改联合的大小。  
  
-   匿名联合现在更符合标准。 早期版本的编译器生成了匿名联合的显式构造函数和析构函数。 这些在 [!INCLUDE[cpp_dev14_long](../porting/includes/cpp_dev14_long_md.md)] 中已删除。  
  
    ```  
    struct S {  
      S();  
     };  
  
     union {  
      struct {  
       S s;  
      };  
     } u; // C2280  
    ```  
  
     前面的代码在 [!INCLUDE[cpp_dev14_long](../porting/includes/cpp_dev14_long_md.md)] 中生成以下错误：  
  
    ```  
    error C2280: '<unnamed-type-u>::<unnamed-type-u>(void)': attempting to reference a deleted function  
    note: compiler has generated '<unnamed-type-u>::<unnamed-type-u>' here  
    ```  
  
     若要解决此问题，请提供你对构造函数和/或析构函数的定义。  
  
    ```  
    struct S {  
    // Provide a default constructor by adding an empty function body.  
    S() {}   
    };  
  
    union {  
    struct {  
    S s;  
    };  
    } u;  
    ```  
  
-   **具有匿名结构的联合**  
  
     为了符合标准，已对联合中的匿名结构的成员更改了运行时行为。 创建此类联合时，将不再隐式调用联合中的匿名结构成员的构造函数。 此外，联合超出范围时，不再隐式调用联合中的匿名结构成员的析构函数。 请考虑以下代码，其中联合 U 包含一个匿名结构，此匿名结构包含的成员是一个具有析构函数的命名结构 S。  
  
    ```  
    #include <stdio.h>  
    struct S {  
        S() { printf("Creating S\n"); }  
        ~S(){ printf("Destroying S\n"); }  
    };  
    union U {  
        struct {  
        S s;  
    };  
        U() {}  
        ~U(){}  
    };  
  
    void f()  
    {  
        U u;  
        // Destructor implicitly called here.  
    }  
  
    int main()  
    {  
        f();  
  
        char s[1024];  
        printf("Press any key.\n");  
        gets_s(s);  
        return 0;  
    }  
    ```  
  
     在 [!INCLUDE[cpp_dev12_long](../build/reference/includes/cpp_dev12_long_md.md)] 中，创建联合时会调用 S 的构造函数，清理函数 f 的堆栈时会调用 S 的析构函数。 但在 [!INCLUDE[cpp_dev14_long](../porting/includes/cpp_dev14_long_md.md)] 中，不会调用构造函数和析构函数。 编译器会对关于此行为的更改发出警告。  
  
    ```Output  
    warning C4587: 'U::s': behavior change: constructor is no longer implicitly calledwarning C4588: 'U::s': behavior change: destructor is no longer implicitly called  
    ```  
  
     若要还原原始行为，请赋予匿名结构一个名称。 无论编译器版本为何，非匿名结构的运行时行为都是相同的。  
  
    ```  
    #include <stdio.h>  
  
    struct S {  
        S() { printf("Creating S.\n"); }  
        ~S() { printf("Destroying S\n"); }  
    };  
    union U {  
        struct {  
            S s;  
        } namedStruct;  
        U() {}  
        ~U() {}  
    };  
  
    void f()  
    {  
        U u;  
    }  
  
    int main()  
    {  
        f();  
  
        char s[1024];  
        printf("Press any key.\n");  
        gets_s(s);  
        return 0;  
    }  
    ```  
  
     或者，尝试将构造函数和析构函数代码移到新的函数中，并从联合的构造函数和析构函数添加对这些函数的调用。  
  
    ```  
    #include <stdio.h>  
  
    struct S {  
        void Create() { printf("Creating S.\n"); }  
        void Destroy() { printf("Destroying S\n"); }  
    };  
    union U {  
        struct {  
            S s;  
        };  
        U() { s.Create();  }  
        ~U() { s.Destroy(); }  
    };  
  
    void f()  
    {  
        U u;  
    }  
  
    int main()  
    {  
        f();  
  
    char s[1024];  
    printf("Press any key.\n");  
    gets_s(s);  
    return 0;  
    }  
    ```  
  
-   **模板解析**  
  
     对模板的名称解析进行了更改。 在 C++ 中，考虑名称解析的候选对象时，可能会出现作为潜在匹配项考虑的一个或多个名称生成无效的模板实例化的情况。 这些无效的实例化通常不会导致编译器错误，这被称为 SFINAE（替换失败不是错误）原则。  
  
     现在，如果 SFINAE 要求编译器将类模板专用化进行实例化，则在此过程中发生的任何错误都是编译器错误。 在早期版本中，编译器会忽略此类错误。 例如，考虑以下代码：  
  
    ```  
    #include <type_traits>  
  
    template<typename T>  
    struct S  
    {  
    S() = default;  
    S(const S&);  
    S(S&&);  
  
    template<typename U, typename = typename std::enable_if<std::is_base_of<T, U>::value>::type>  
    S(S<U>&&);  
    };  
  
    struct D;  
  
    void f1()  
    {  
    S<D> s1;  
        S<D> s2(s1);  
    }  
  
    struct B  
    {  
    };  
  
    struct D : public B  
    {  
    };  
  
    void f2()  
    {  
    S<D> s1;  
        S<D> s2(s1);  
    }  
  
    ```  
  
     如果使用当前编译器进行编译，将得到以下错误：  
  
    ```Output  
    type_traits(1110): error C2139: 'D': an undefined class is not allowed as an argument to compiler intrinsic type trait '__is_base_of'  
    ..\t331.cpp(14): note: see declaration of 'D'  
    ..\t331.cpp(10): note: see reference to class template instantiation 'std::is_base_of<T,U>' being compiled  
            with  
            [  
                T=D,  
                U=D  
            ]  
    ```  
  
     这是因为在第一次调用 is_base_of 时，尚未定义类“D”。  
  
     在这种情况下，解决方法是在定义类之前，不使用此类类型特征。 如果将 D 和 B 的定义移到代码文件的开头，错误将得到解决。 如果定义位于标头文件中，请检查标头文件的 include 语句的顺序，以确保在使用有问题的模板之前，对任何类定义进行了编译。  
  
-   **复制构造函数**  
  
     在 [!INCLUDE[vs_dev12](../atl-mfc-shared/includes/vs_dev12_md.md)] 和 [!INCLUDE[vs_dev14](../ide/includes/vs_dev14_md.md)]中，如果该类具有用户定义的移动构造函数，但没有用户定义的复制构造函数，则编译器生成类的复制构造函数。 在 Dev14 中，此隐式生成的复制构造函数也标记为“= delete”。  
  
##  <a name="VS_Update1"></a>更新 1 中的符合性改进  
  
-   **私有虚拟基类和间接继承**  
  
     早期版本的编译器允许派生类调用 *间接派生*`private virtual` 基类的成员函数。 这种旧行为不正确，也不符合 C++ 标准。 编译器不再接受这种方式编写的代码，因此会发出编译器错误 C2280。  
  
    ```Output  
    error C2280: 'void *S3::__delDtor(unsigned int)': attempting to reference a deleted function  
    ```  
  
     示例（之前）  
  
    ```cpp  
    class base  
    {  
    protected:  
        base();  
        ~base();  
    };  
  
    class middle: private virtual base {};class top: public virtual middle {};  
  
    void destroy(top *p)  
    {  
        delete p;  //   
    }  
    ```  
  
     示例（之后）  
  
    ```cpp  
    class base;  // as above  
  
    class middle: protected virtual base {};  
    class top: public virtual middle {};  
  
    void destroy(top *p)  
    {  
        delete p;  
    }  
    ```  
  
     - 或 -  
  
    ```  
    class base;  // as above  
  
    class middle: private virtual base {};  
    class top: public virtual middle, private virtual bottom {};  
  
    void destroy(top *p)  
    {  
        delete p;  
    }  
    ```  
  
-   **重载的 new 运算符和 delete 运算符**  
  
     早期版本的编译器允许非成员 `operator new` 和非成员 `operator delete` 声明为静态，并在全局命名空间之外的命名空间中声明。  这种旧行为会引发风险，导致程序无法按按程序员的预期调用 `new` 或 `delete` 运算符实现，从而导致无提示的运行时行为错误。 编译器不再接受这种方式编写的代码，因此会发出编译器错误 C2323。  
  
    ```Output  
    error C2323: 'operator new': non-member operator new or delete functions may not be declared static or in a namespace other than the global namespace.  
    ```  
  
     示例（之前）  
  
    ```cpp  
    static inline void * __cdecl operator new(size_t cb, const std::nothrow_t&)  // error C2323  
    ```  
  
     示例（之后）  
  
    ```cpp  
    void * __cdecl operator new(size_t cb, const std::nothrow_t&)  // removed 'static inline'  
    ```  
  
     此外，尽管编译器不能进行具体诊断，但内联运算符 new 会被视为格式不正确。  
  
-   **对非类类型调用“operator type**()”（用户定义的转换）**  
  
     早期版本的编译器允许以无提示忽略的方式对非类类型调用“operator *type*()”。 这种旧行为会导致无提示代码生成错误风险，从而导致不可预知的运行时行为。 编译器不再接受这种方式编写的代码，因此会发出编译器错误 C2228。  
  
    ```Output  
    error C2228: left of '.operator type' must have class/struct/union  
    ```  
  
     示例（之前）  
  
    ```cpp  
    typedef int index_t;  
  
    void bounds_check(index_t index);  
  
    void login(int column)  
    {  
        bounds_check(column.operator index_t());  // error C2228  
    }  
    ```  
  
     示例（之后）  
  
    ```cpp  
    typedef int index_t;  
  
    void bounds_check(index_t index);  
  
    void login(int column)  
    {  
        bounds_check(column);  // removed cast to 'index_t', 'index_t' is an alias of 'int'  
    }  
    ```  
  
-   **详细的类型说明符中的多余 typename**  
  
     早期版本的编译器允许详细的类型说明符中出现 `typename` ；用这种方式编写的代码在语义上不正确。 编译器不再接受这种方式编写的代码，因此会发出编译器错误 C3406。  
  
    ```Output  
    error C3406: 'typename' cannot be used in an elaborated type specifier  
    ```  
  
     示例（之前）  
  
    ```cpp  
    template <typename class T>  
    class container;  
    ```  
  
     示例（之后）  
  
    ```cpp  
    template <class T>  // alternatively, could be 'template <typename T>'; 'typename' is not elaborating a type specifier in this case  
    class container;  
    ```  
  
-   **初始值设定项列表中数组的类型推断**  
  
     早期版本的编译器不支持对初始值设定项列表中的数组进行类型推断。 编译器现在支持这种形式的类型推断，因此调用使用初始值设定项列表的函数模板现在可能会不明确，或者选择一个与以前版本的编译器不同的重载。 要解决这些问题，程序现在必须显式指定程序员所需的重载。  
  
     当这一新行为导致重载解决方法要考虑与以往候选一样好的其他候选时，调用变得不明确，编译器会发出编译器错误 C2668。  
  
    ```Output  
    error C2668: 'function' : ambiguous call to overloaded function.  
    ```  
  
     示例 1： 对重载函数的调用不明确（之前）  
  
    ```cpp  
    // In previous versions of the compiler, code written in this way would unambiguously call f(int, Args...)  
    template <typename... Args>  
    void f(int, Args...);  //   
  
    template <int N, typename... Args>  
    void f(const int (&)[N], Args...);  
  
    int main()  
    {  
        // The compiler now considers this call ambiguous, and issues a compiler error  
        f({3});  error C2668: 'f' ambiguous call to overloaded function  
    }  
    ```  
  
     示例 1： 对重载函数的调用不明确（之后）  
  
    ```cpp  
    template <typename... Args>  
    void f(int, Args...);  //   
  
    template <int N, typename... Args>  
    void f(const int (&)[N], Args...);  
  
    int main()  
    {  
        // To call f(int, Args...) when there is just one expression in the initializer list, remove the braces from it.  
        f(3);  
    }  
    ```  
  
     这一新行为会导致重载解决方法要考虑比以往候选更适合的其他候选时，调用将明确地解析为新候选，导致程序行为的更改可能与程序员的需要有所不同。  
  
     示例 2：重载解决方法的更改（之前）  
  
    ```cpp  
    // In previous versions of the compiler, code written in this way would unambiguously call f(S, Args...)  
    struct S  
    {  
        int i;  
        int j;  
    };  
  
    template <typename... Args>  
    void f(S, Args...);  
  
    template <int N, typename... Args>  
    void f(const int *&)[N], Args...);  
  
    int main()  
    {  
        // The compiler now resolves this call to f(const int (&)[N], Args...) instead  
        f({1, 2});  
    }  
    ```  
  
     示例 2：重载解决方法的更改（之后）  
  
    ```cpp  
    struct S;  // as before  
  
    template <typename... Args>  
    void f(S, Args...);  
  
    template <int N, typename... Args>  
    void f(const int *&)[N], Args...);  
  
    int main()  
    {  
        // To call f(S, Args...), perform an explicit cast to S on the initializer list.  
        f(S{1, 2});  
    }  
    ```  
  
-   **switch 语句警告的还原**  
  
     前一个版本的编译器删除了之前存在的与 `switch` 语句相关的警告；现在已还原所有这些警告。 编译器现在将发出还原的警告，并且现在会在包含有问题用例的行中发出与特定用例（包括默认情况下）相关的警告，而不是在 switch 语句的最后一行发出。 因此，现在发出这些警告的行与过去不同，按照需要使用 `#pragma warning(disable:####)` 可不再禁止显示以前禁止显示的警告。 要按照需要禁止显示这些警告，可能需要将 `#pragma warning(disable:####)` 指令移到第一个可能有问题的用例上面的行。 以下是还原的警告。  
  
    ```Output  
    warning C4060: switch statement contains no 'case' or 'default' labels  
    ```  
  
    ```Output  
    warning C4061: enumerator 'bit1' in switch of enum 'flags' is not explicitly handled by a case label  
    ```  
  
    ```Output  
    warning C4062: enumerator 'bit1' in switch of enum 'flags' is not handled  
    ```  
  
    ```Output  
    warning C4063: case 'bit32' is not a valid value for switch of enum 'flags'  
    ```  
  
    ```Output  
    warning C4064: switch of incomplete enum 'flags'  
    ```  
  
    ```Output  
    warning C4065: switch statement contains 'default' but no 'case' labels  
    ```  
  
    ```Output  
    warning C4808: case 'value' is not a valid value for switch condition of type 'bool'  
    ```  
  
    ```Output  
    Warning C4809: switch statement has redundant 'default' label; all possible 'case' labels are given  
    ```  
  
     C4063 示例（之前）  
  
    ```cpp  
    class settings  
    {  
    public:  
        enum flags  
        {  
            bit0 = 0x1,  
            bit1 = 0x2,  
            ...  
        };  
        ...  
    };  
  
    int main()  
    {  
        auto val = settings::bit1;  
  
        switch (val)  
        {  
        case settings::bit0:  
            break;  
  
        case settings::bit1:  
            break;  
  
        case settings::bit0 | settings::bit1:  // warning C4063  
            break;  
        }  
    };  
    ```  
  
     C4063 示例（之后）  
  
    ```cpp  
    class settings {...};  // as above  
  
    int main()  
    {  
        // since C++11, use std::underlying_type to determine the underlying type of an enum  
        typedef std::underlying_type<settings::flags>::type flags_t;  
  
        auto val = settings::bit1;  
  
        switch (static_cast<flags_t>(val))  
        {  
        case settings::bit0:  
            break;  
  
        case settings::bit1:  
            break;  
  
        case settings::bit0 | settings::bit1:  // ok  
            break;  
        }  
    };  
    ```  
  
     在其文档中提供了其他还原警告的示例。  
  
-   **#include：在路径名中使用父目录说明符“..”** （只影响 /Wall/WX）  
  
     早期版本的编译器没有检测到使用父目录说明符“..” （在  `#include` 指令的路径名中）。 以这种方式编写的代码通常用于包含因不正确使用项目相对路径而留在项目外的标头。 这一旧行为会引发风险，导致编译程序时包含了程序员不需要的源文件来，或这些相对路径不能移植到其他生成环境中。 编译器现在会检测以这种方式编写的代码并通知程序员，并发出可选编译器警告 C4464（如果已启用）。  
  
    ```Output  
    warning C4464: relative include path contains '..'  
    ```  
  
     示例（之前）  
  
    ```cpp  
    #include "..\headers\C4426.h"  // emits warning C4464  
    ```  
  
     示例（之后）  
  
    ```cpp  
    #include "C4426.h"  // add absolute path to 'headers\' to your project's include directories  
    ```  
  
     此外，虽然编译器并不会进行具体诊断，但建议不应将父目录说明符“..”用于指定项目的包含目录。  
  
-   **#pragma optimize() 超出标头文件的末尾** （只影响 /Wall/WX）  
  
     早期版本的编译器无法检测到对转义翻译单元中包含的标头文件的优化标志设置的更改。 编译器现在会检测以这种方式编写的代码并通知程序员，并在有问题的 `#include`的位置发出可选编译器警告 C4426（如果已启用）。 只有更改与编译器命令行参数设置的优化标志发生冲突时，才发出此警告。  
  
    ```Output  
    warning C4426: optimization flags changed after including header, may be due to #pragma optimize()  
    ```  
  
     示例（之前）  
  
    ```cpp  
    // C4426.h  
    #pragma optimize("g", off)  
    ...  
    // C4426.h ends  
  
    // C4426.cpp  
    #include "C4426.h"  // warning C4426  
    ```  
  
     示例（之后）  
  
    ```cpp  
    // C4426.h  
    #pragma optimize("g", off)  
    ...  
    #pragma optimize("", on)  // restores optimization flags set via command-line arguments  
    // C4426.h ends  
  
    // C4426.cpp  
    #include "C4426.h"  
    ```  
  
-   **#pragma warning(push)** 和 **#pragma warning(pop)** （只影响 /Wall/WX）  
  
     早期版本的编译器无法检测到不同源文件中与 `#pragma warning(pop)` 状态更改配对的 `#pragma warning(push)` 状态更改，这并不是我们所预期的。 这种旧行为会引发风险，导致程序编译时会启用一组程序员不希望出现的警告，可能会导致无提示的运行时行为错误。 编译器现在能够检测以这种方式编写的代码并通知程序员，并在匹配 `#pragma warning(pop)` 位置发出可选编译器警告 C5031（如果已启用）。 此警告包括引用相应 #pragma warning(push) 的位置的注释。  
  
    ```Output  
    warning C5031: #pragma warning(pop): likely mismatch, popping warning state pushed in different file  
    ```  
  
     示例（之前）  
  
    ```cpp  
    // C5031_part1.h  
    #pragma warning(push)  
    #pragma warning(disable:####)  
    ...  
    // C5031_part1.h ends without #pragma warning(pop)  
  
    // C5031_part2.h  
    ...  
    #pragma warning(pop)  // pops a warning state not pushed in this source file   
    ...  
    // C5031_part1.h ends  
  
    // C5031.cpp  
    #include "C5031_part1.h" // leaves #pragma warning(push) 'dangling'  
    ...  
    #include "C5031_part2.h" // matches 'dangling' #pragma warning(push), resulting in warning C5031  
    ...  
  
    ```  
  
     示例（之后）  
  
    ```cpp  
    // C5031_part1.h  
    #pragma warning(push)  
    #pragma warning(disable:####)  
    ...  
    #pragma warning(pop)  // pops the warning state pushed in this source file  
    // C5031_part1.h ends without #pragma warning(pop)  
  
    // C5031_part2.h  
    #pragma warning(push)  // pushes the warning state pushed in this source file  
    #pragma warning(disable:####)  
    ...  
    #pragma warning(pop)  
    // C5031_part1.h ends  
  
    // C5031.cpp  
    #include "C5031_part1.h" // #pragma warning state changes are self-contained and independent of other source files or their #include order.  
    ...  
    #include "C5031_part2.h"  
    ...  
  
    ```  
  
     虽然不常见，但是有时会故意以这种方式编写代码。 以这种方式编写的代码对于 `#include` 顺序的更改比较敏感；如果可能，我们建议源代码文件以自包含的方式管理警告状态。  
  
-   **#pragma warning(push) 不匹配** （只影响 /Wall/WX）  
  
     早期版本的编译器无法检测到翻译单元末尾出现的不匹配 `#pragma warning(push)` 状态更改。 编译器现在能够检测以这种方式编写的代码并通知程序员，并在不匹配的 #pragma warning(push) 位置发出可选编译器警告 C5032（如果已启用）。 只有翻译单元中没有任何编译错误时，才会发出此警告。  
  
    ```Output  
    warning C5032: detected #pragma warning(push) with no corresponding #pragma warning(pop)  
    ```  
  
     示例（之前）  
  
    ```cpp  
    // C5032.h  
    #pragma warning(push)  
    #pragma warning(disable:####)  
    ...  
    // C5032.h ends without #pragma warning(pop)  
  
    // C5032.cpp  
    #include "C5032.h"  
    ...  
    // C5032.cpp ends -- the translation unit is completed without #pragma warning(pop), resulting in warning C5032 on line 1 of C5032.h  
    ```  
  
     示例（之后）  
  
    ```cpp  
    // C5032.h  
    #pragma warning(push)  
    #pragma warning(disable:####)  
    ...  
    #pragma warning(pop) // matches #pragma warning (push) on line 1  
    // C5032.h ends  
  
    // C5032.cpp  
    #include "C5032.h"  
    ...  
    // C5032.cpp ends -- the translation unit is completed without unmatched #pragma warning(push)  
    ```  
  
-   **#pragma 警告状态跟踪改进后可能会发出更多警告**  
  
     早期版本的编译器无法有效跟踪 #pragma 警告状态更改，因而无法发出所有所需的警告。 这种行为会引发风险，导致在程序不希望的情况下有效禁止显示某些警告。 编译器现在能够更加可靠地跟踪 #pragma 警告状态，尤其与模板内部的 #pragma 警告状态更改相关，并选择性发出新警告 C5031 和 C5032，旨在帮助程序员找到意外使用 `#pragma warning(push)` 和 `#pragma warning(pop)`。  
  
     由于改进了 #pragma 警告状态更改跟踪，现在可能会发出以前错误地禁止显示的警告或与以前误诊问题的相关警告。  
  
-   **对无法访问代码标识的改进**  
  
     针对早期版本的编译器进行的 C++ 标准库的更改和内联函数调用能力改进可能会使编译器能够证明某些代码现在无法访问。 这一新行为可能导致新警告并更频繁地发出警告 C4720 实例。  
  
    ```Output  
    warning C4720: unreachable code  
    ```  
  
     在许多情况下，只有启用优化进行编译时，才会发出此警告，因为优化可能嵌入更多函数调用，消除冗余代码或者能够确定某些代码是否无法访问。 我们观察到，警告 C4720 的新实例在 try/catch 块中经常发生，尤其是在使用 [std::find](assetId:///std::find?qualifyHint=False&autoUpgrade=True)时。  
  
     示例（之前）  
  
    ```cpp  
    try   
    {   
        auto iter = std::find(v.begin(), v.end(), 5);   
    }   
    catch(...)   
    {   
        do_something();  // ok   
    }  
    ```  
  
     示例（之后）  
  
    ```cpp  
    try   
    {   
        auto iter = std::find(v.begin(), v.end(), 5);   
    }   
    catch(...)   
    {   
        do_something();  // warning C4702: unreachable code  
    }  
    ```  
  
##  <a name="VS_Update2"></a>更新 2 中的符合性改进  
  
-   **可能会因对表达式 SFINAE 的部分支持而发出其他警告和错误**  
  
     由于缺少对表达式 SFINAE 的支持，编译器的早期版本无法分析 `decltype` 说明符中特定类型的表达式。 这种旧行为不正确，也不符合 C++ 标准。 由于持续的符合性改进，此编译器现已可分析这些表达式，并能为表达式 SFINAE 提供部分支持。 因此，此编译器现在可发出在编译器的早期版本无法分析的表达式中找到的警告和错误。  
  
     此新行为分析包含尚未声明类型的 `decltype` 表达式时，将导致编译器发出编译器错误 C2039。  
  
    ```Output  
    error C2039: 'type': is not a member of '`global namespace''  
    ```  
  
     示例 1：使用未声明的类型（之前）  
  
    ```cpp  
    struct s1  
    {  
      template <typename T>  
      auto f() -> decltype(s2<T>::type::f());  // error C2039  
  
      template<typename>  
      struct s2 {};  
    }  
    ```  
  
     示例 1（之后）  
  
    ```cpp  
    struct s1  
    {  
      template <typename>  // forward declare s2struct s2;  
  
      template <typename T>  
      auto f() -> decltype(s2<T>::type::f());  
  
      template<typename>  
      struct s2 {};  
    }  
    ```  
  
     此新行为分析 `decltype` 表达式时（该表达式缺少将依赖名称指定为类型所必须使用的关键字 `typename`），编译器将发出编译器警告 C4346 和编译器错误 C2923。  
  
    ```Output  
    warning C4346: 'S2<T>::Type': dependent name is not a type  
    ```  
  
    ```Output  
    error C2923: 's1': 'S2<T>::Type' is not a valid template type argument for parameter 'T'  
    ```  
  
     示例 2：依赖名称不是类型（之前）  
  
    ```cpp  
    template <typename T>  
    struct s1  
    {  
      typedef T type;  
    };  
  
    template <typename T>  
    struct s2  
    {  
      typedef T type;  
    };  
  
    template <typename T>  
    T declval();  
  
    struct s  
    {  
      template <typename T>  
      auto f(T t) -> decltype(t(declval<S1<S2<T>::type>::type>()));  // warning C4346, error C2923  
    };  
    ```  
  
     示例 2（之后）  
  
    ```cpp  
    template <typename T> struct s1 {...};  // as above  
    template <typename T> struct s2 {...};  // as above  
  
    template <typename T>  
    T declval();  
  
    struct s  
    {  
      template <typename T>  
      auto f(T t) -> decltype(t(declval<S1<typename S2<T>::type>::type>()));  
    };  
    ```  
  
-   `volatile` **成员变量将防止出现隐式定义的构造函数和赋值运算符**  
  
     编译器的早期版本允许具有 `volatile` 成员变量的类自动生成默认复制/移动构造函数和默认复制/移动赋值运算符。 这种旧行为不正确，也不符合 C++ 标准。 编译器现在认为拥有可变成员变量的类具有非常用构造函数和赋值运算符，这将防止自动生成这些运算符的默认实现。  当此类为某一联合（或类中的匿名联合）的成员时，会将联合（或包含匿名联合的类）的复制/移动构造函数和复制/移动赋值运算符的隐式定义为已删除。 尝试构造或复制联合（或包含匿名联合的类）而不显式定义它们是错误的，将导致编译器发出编译器错误 C2280。  
  
    ```Output  
    error C2280: 'B::B(const B &)': attempting to reference a deleted function  
    ```  
  
     示例（之前）  
  
    ```cpp  
    struct A  
    {  
      volatile int i;  
      volatile int j;  
    };  
  
    extern A* pa;  
  
    struct B  
    {  
      union  
      {  
        A a;  
        int i;  
      };  
    };  
  
    B b1 {*pa};  
    B b2 (b1);  // error C2280  
    ```  
  
     示例（之后）  
  
    ```cpp  
    struct A  
    {  
      int i;int j;  
    };  
  
    extern volatile A* pa;  
  
    A getA()  // returns an A instance copied from contents of pa  
    {  
      A a;  
      a.i = pa->i;  
      a.j = pa->j;  
      return a;  
    }  
  
    struct B;  // as above  
  
    B b1 {GetA()};  
    B b2 (b1);  // error C2280  
    ```  
  
-   **静态成员函数不支持 cv 限定符。**  
  
     Visual C++ 2015 的早期版本允许静态成员函数具有 cv 限定符。 此行为是由于 Visual C++ 2015 和 Visual C++ 2015 Update 1 中的回归而导致的；Visual C++ 2013 和 Visual C++ 的早期版本拒绝接受以这种方式编写的代码。 Visual C++ 2015 和 Visual C++ 2015 Update 1 的行为不正确且不符合 C++ 标准。  Visual Studio 2015 Update 2 拒绝接受以这种方式编写的代码，并改为发出编译器错误 C2511。  
  
    ```Output  
    error C2511: 'void A::func(void) const': overloaded member function not found in 'A'  
    ```  
  
     示例（之前）  
  
    ```  
    struct A  
    {  
      static void func();  
    };  
  
    void A::func() const {}  // C2511  
  
    ```  
  
     示例（之后）  
  
    ```  
    struct A  
    {  
      static void func();  
    };  
  
    void A::func() {}  // removed const  
  
    ```  
  
-   **WinRT 代码中不允许枚举的前向声明**（仅影响 /ZW）  
  
     为 Windows 运行时 (WinRT) 编译的代码不允许前向声明 `enum` 类型，这与使用 /clr 编译器开关为 .Net Framework 编译托管 C++ 代码时相似。 此行为可确保枚举大小始终为已知，并可将其正确映射到 WinRT 类型系统。 编译器将拒绝接受以这种方式编写的代码，并发出编译器错误 C2599 和编译器错误 C3197。  
  
    ```Output  
    error C2599: 'CustomEnum': the forward declaration of a WinRT enum is not allowed  
    ```  
  
    ```Output  
    error C3197: 'public': can only be used in definitions  
    ```  
  
     示例（之前）  
  
    ```cpp  
    namespace A {  
      public enum class CustomEnum: int32;  // forward declaration; error C2599, error C3197  
    }  
  
    namespace A {  
      public enum class CustomEnum: int32  
      {  
        Value1  
      };  
    }  
  
    public ref class Component sealed  
    {  
    public:  
      CustomEnum f()  
      {  
        return CustomEnum::Value1;  
      }  
    };  
    ```  
  
     示例（之后）  
  
    ```cpp  
              // forward declaration of CustomEnum removed  
  
    namespace A {  
      public enum class CustomEnum: int32  
      {  
        Value1  
      };  
    }  
  
    public ref class Component sealed  
    {  
    public:  
      CustomEnum f()  
      {  
        return CustomEnum::Value1;  
      }  
    };  
    ```  
  
-   **重载的非成员运算符 new 和运算符 delete 可能不是以内联方式声明的**（默认开启等级 1 (/W1)）  
  
     当以内联方式声明非成员运算符 new 和运算符 delete 函数时，编译器的早期版本不会发出警告。 以这种方式编写的代码格式不正确（无需诊断），并且可能由于不匹配的 new 和 delete 运算符（尤其是与调整了大小的释放共同使用时）而导致难以诊断的内存问题。   编译器现将发出编译器警告 C4595 以帮助识别以这种方式编写的代码。  
  
    ```Output  
    warning C4595: 'operator new': non-member operator new or delete functions may not be declared inline  
    ```  
  
     示例（之前）  
  
    ```cpp  
              inline void* operator new(size_t sz)  // warning C4595  
    {  
      ...  
    }  
    ```  
  
     示例（之后）  
  
    ```cpp  
              void* operator new(size_t sz)  // removed inline  
    {  
      ...  
    }  
    ```  
  
     修复以这种方式编写的代码可能需要将运算符定义从头文件移动到相应的源文件中。  
  
##  <a name="VS_Update3"></a>更新 3 中的符合性改进  
  
-   **现在，std::is_convertable 可以检测自我赋值**（标准库）  
  
     以前版本的 `std::is_convertable` type-trait 在其复制构造函数被删除或私有时，无法正确检测类类型的自我赋值。 现在，当应用于具有已删除或私有复制构造函数的类类型时，`std::is_convertable<>::value` 已正确设置为 `false`。  
  
     没有与此更改相关联的编译器诊断。  
  
     示例  
  
    ```cpp  
    #include <type_traits>  
  
    class X1  
    {  
    public:  
        X1(const X1&) = delete;  
    };  
  
    class X2  
    {  
    private:  
        X2(const X2&);  
    };  
  
    static_assert(std::is_convertible<X1&, X1>::value, "BOOM");static_assert(std::is_convertible<X2&, X2>::value, "BOOM");  
    ```  
  
     在以前版本的 Visual C++ 中，此示例底部的静态断言可传递，因为 `std::is_convertable<>::value` 错误地设置为 `true`。 现在，`std::is_convertable<>::value` 正确设置为 `false`，使静态断言失败。  
  
-   **默认设置或已删除的日常复制和移动构造函数遵从访问说明符**  
  
     对于默认设置或已删除的日常复制和移动构造函数的访问说明符，早期版本的编译器在允许调用之前不进行检查。 这种旧行为不正确，也不符合 C++ 标准。 在某些情况下，这种旧行为会导致无提示代码生成错误风险，从而导致不可预知的运行时行为。 现在，编译器检查默认设置或已删除的日常复制和移动构造函数的访问说明符，以确定是否能调用它，如果不能，则发出编译器警告 C2248。  
  
    ```Output  
    error C2248: 'S::S' cannot access private member declared in class 'S'  
    ```  
  
     示例（之前）  
  
    ```cpp  
    class S {  
    public:  
           S() = default;  
    private:  
        S(const S&) = default;  
    };  
  
    void f(S);  // pass S by value  
  
    int main()  
    {  
        S s;  
        f(s);  // error C2248, can't invoke private copy constructor  
    }  
    ```  
  
     示例（之后）  
  
    ```cpp  
    class S {  
    public:  
           S() = default;  
    private:  
        S(const S&) = default;  
    };  
  
    void f(const S&);  // pass S by reference  
  
    int main()  
    {  
        S s;  
        f(s);  
    }  
    ```  
  
-   **弃用属性化 ATL 代码支持**（默认开启等级 1 (/W1)）  
  
     以前版本的编译器支持属性化 ATL 代码。 由于下一阶段将删除[从 Visual C++ 2008](https://msdn.microsoft.com/library/bb384632\(v=vs.90\).aspx) 开始的属性化 ATL 代码支持，所以已弃用属性化 ATL 代码。 编译器现将发出编译器警告 C4467 以帮助识别这类已弃用的代码。  
  
    ```Output  
    warning C4467: Usage of ATL attributes is deprecated  
    ```  
  
     若要在编译器删除支持之前继续使用属性化 ATL 代码，可以通过将 `/Wv:18` 或 `/wd:4467` 命令行参数传递给编译器或在源代码中添加 `#pragma warning(disable:4467)` 来禁用此警告。  
  
     示例 1（之前）  
  
    ```cpp  
              [uuid("594382D9-44B0-461A-8DE3-E06A3E73C5EB")]  
    class A {};  
    ```  
  
     示例 1（之后）  
  
    ```cpp  
    __declspec(uuid("594382D9-44B0-461A-8DE3-E06A3E73C5EB")) A {};  
  
    ```  
  
     有时需要创建 IDL 文件以避免使用已弃用的 ATL 属性，如以下示例代码所示  
  
     示例 2（之前）  
  
    ```cpp  
    [emitidl];  
    [module(name="Foo")];  
  
    [object, local, uuid("9e66a290-4365-11d2-a997-00c04fa37ddb")]  
    __interface ICustom {  
        HRESULT Custom([in] long l, [out, retval] long *pLong);  
        [local] HRESULT CustomLocal([in] long l, [out, retval] long *pLong);  
    };  
  
    [coclass, appobject, uuid("9e66a294-4365-11d2-a997-00c04fa37ddb")]  
    class CFoo : public ICustom  
    {  
        // ...  
    };  
    ```  
  
     首先，创建 *.idl 文件；vc140.idl 生成的文件可用于获取包含接口和注释的 \*.idl文件。  
  
     然后，将 MIDL 步骤添加到生成中以确保生成 C++ 接口定义。  
  
     示例 2 IDL（之后）  
  
    ```cpp  
    import "docobj.idl";  
  
    [  
        object,local,uuid(9e66a290-4365-11d2-a997-00c04fa37ddb)  
    ]  
  
    interface ICustom : IUnknown {  
        HRESULT  Custom([in] long l, [out,retval] long *pLong);  
        [local] HRESULT  CustomLocal([in] long l, [out,retval] long *pLong);  
    };  
  
    [ version(1.0), uuid(29079a2c-5f3f-3325-99a1-3ec9c40988bb) ]  
    library Foo  
    {  
        importlib("stdole2.tlb");  
        importlib("olepro32.dll");  
            [  
                version(1.0),  
                appobject,uuid(9e66a294-4365-11d2-a997-00c04fa37ddb)  
            ]  
  
        coclass CFoo {  
            interface ICustom;  
        };  
    }  
    ```  
  
     然后，在实现文件中直接使用 ATL，如以下示例代码所示。  
  
     示例 2 实现（之后）  
  
    ```cpp  
    #include <idl.header.h>  
    #include <atlbase.h>  
  
    class ATL_NO_VTABLE CFooImpl :  
        public ICustom,  
        public ATL::CComObjectRootEx<CComMultiThreadModel>  
    {  
    public:  
        BEGIN_COM_MAP(CFooImpl)  
        COM_INTERFACE_ENTRY(ICustom)  
        END_COM_MAP()  
    };  
    ```  
  
-   **预编译标头 (PCH) 文件和不匹配的 #include 指令**（仅影响 /Wall /WX）  
  
     使用预编译标头 (PCH) 文件时，以前版本的编译器接受 `-Yc` 和 `-Yu` 编译之间的源文件中不匹配的 `#include` 指令。 编译器不再接受以这种方式编写的代码。   使用 PCH 文件时，编译器现将发出编译器警告 CC4598 以帮助识别不匹配的 `#include` 指令。  
  
    ```Output  
    warning C4598: 'b.h': included header file specified for Ycc.h at position 2 does not match Yuc.h at that position  
    ```  
  
     示例（之前）：  
  
     X.cpp (-Ycc.h)  
  
    ```cpp  
    #include "a.h"  
    #include "b.h"  
    #include "c.h"  
    ```  
  
     Z.cpp (-Yuc.h)  
  
    ```cpp  
    #include "b.h"  
    #include "a.h"  // mismatched order relative to X.cpp  
    #include "c.h"  
    ```  
  
     示例（之后）  
  
     X.cpp (-Ycc.h)  
  
    ```cpp  
    #include "a.h"  
    #include "b.h"   
    #include "c.h"  
    ```  
  
     Z.cpp (-Yuc.h)  
  
    ```cpp  
    #include "a.h"  
    #include "b.h" // matched order relative to X.cpp  
    #include "c.h"  
    ```  
  
-   **预编译标头 (PCH) 文件和不匹配的包含目录**（仅影响 /Wall /WX）  
  
     使用预编译标头 (PCH) 文件时，对于 `-Yc` 和 `-Yu` 编译之间的编译器，以前版本的编译器接受不匹配的包含目录 (`-I`) 命令行参数。 编译器不再接受以这种方式编写的代码。   使用 PCH 文件时，编译器现将发出编译器警告 CC4599 以帮助识别不匹配的包含目录 (`-I`) 命令行参数。  
  
    ```Output  
    warning C4599: '-I..' : specified for Ycc.h at position 1 does not match Yuc.h at that position  
    ```  
  
     示例（之前）  
  
    ```ms-dos  
    cl /c /Wall /Ycc.h -I.. X.cpp  
    cl /c /Wall /Yuc.h Z.cpp  
    ```  
  
     示例（之后）  
  
    ```ms-dos  
    cl /c /Wall /Ycc.h -I.. X.cpp  
    cl /c /Wall /Yuc.h -I.. Z.cpp  
    ```

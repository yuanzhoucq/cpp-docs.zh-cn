---
title: "Visual C++ 2015 中的重大更改 | Microsoft Docs"
ms.custom: ""
ms.date: "12/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "重大更改 [C++]"
ms.assetid: b38385a9-a483-4de9-99a6-797488bc5110
caps.latest.revision: 124
caps.handback.revision: 117
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Visual C++ 2015 中的重大更改
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

当你升级到 Visual C\+\+ 编译器的新版本后，可能会在之前编译并正常运行的代码中遇到编译和\/或运行时错误。 新版本中会引起这类问题的更改称为*重大更改*，通常，修改 C\+\+ 语言标准、函数签名或内存中的对象布局时需要进行这种更改。  
  
 若要避免难以检测和诊断的运行时错误，我们建议你永远不静态链接到使用不同编译器版本编译的二进制文件。 此外，当你升级 EXE 或 DLL 项目时，请确保升级它所链接的库。 如果使用 CRT（C 运行时库）或 STL（标准模板库）类型，请勿在使用不同编译器版本编译的二进制文件（包括 DLL）之间传递这些类型。 有关详细信息，请参阅 [跨 DLL 边界传递 CRT 对象时可能的错误](../c-runtime-library/potential-errors-passing-crt-objects-across-dll-boundaries.md)。  
  
 我们进一步建议，你在编写代码时永远不依赖除 COM 接口或 POD 对象以外的特定对象布局。 如果确实要编写此类代码，则必须在升级后确保其正常运行。 有关详细信息，请参阅 [ABI 边界处的可移植性](../cpp/portability-at-abi-boundaries-modern-cpp.md)。  
  
 本文的其余部分介绍了 [!INCLUDE[cpp_dev14_long](../porting/includes/cpp_dev14_long_md.md)] 中具体的重大更改，并且在本文中，术语“新行为”或“现在”均指该版本。 术语“旧行为”和“之前”指 Visual Studio 2013 和早期版本。 有关在 Visual Studio 2015 更新 1 中的其他更改的信息，请参见 [更新 1 中的重大更改](../misc/breaking-changes-in-visual-cpp-2015-update-1.md)。  
  
1.  [编译器的重大更改](#BK_compiler)  
  
2.  [C 运行时 \(CRT\) 库的重大更改](#BK_CRT)  
  
3.  [标准 C\+\+ 和标准模板库 \(STL\) 的重大更改](#BK_STL)  
  
4.  [MFC 和 ATL 的重大更改](#BK_MFC)  
  
5.  [并发运行时重大更改](#BK_ConcRT)  
  
##  <a name="BK_compiler"></a> Visual C\+\+ 编译器  
  
-   \/Zc:forScope\- 选项  
  
     编译器选项 **\/Zc:forScope\-** 已弃用，并且将在将来版本中删除。  
  
    ```  
    Command line warning  D9035: option 'Zc:forScope-' has been deprecated and will be removed in a future release  
    ```  
  
     以前会经常用到此选项，以便允许非标准代码在点的位置之后使用循环变量，根据标准规范，这些变量本应该在范围之外。 仅当使用 \/Za 选项进行编译时才需要，因为没有 \/Za，将始终允许在循环结束后使用 for 循环变量。 如果你不关心标准一致性（例如，如果你的代码不是为了移植到其他编译器），你可以关闭 \/Za 选项（或将“禁用语言扩展”属性设置为“否”）。 如果你确实关心编写可移植且符合标准的代码，则应重写代码，以便通过将此类变量的声明移到循环以外的点使其符合标准。  
  
    ```  
    // zc_forScope.cpp // compile with: /Zc:forScope- /Za // C2065 expected int main() { // Uncomment the following line to resolve. // int i; for (int i =0; i < 1; i++) ; i = 20;   // i has already gone out of scope under /Za }  
    ```  
  
-   **\/Zg 编译器选项**  
  
     \/Zg 编译器选项（生成函数原型）不再可用。 此此编译器选项已被弃用。  
  
-   你无法再使用 mstest.exe 从命令行运行 C\+\+\/CLI 单元测试。 请改用 vstest.console.exe。 请参阅 [VSTest.Console.exe 命令行选项](../Topic/VSTest.Console.exe%20command-line%20options.md)。  
  
-   **可变关键字**  
  
     在之前其正确编译的位置，不再允许存在 `mutable` 存储类说明符。 现在，编译器报告错误 C2071（非法存储类）。 根据标准，可变说明符仅可应用于类数据成员的名称，不能应用于声明为 const 或 static 的名称，也不能应用于引用成员。  
  
     例如，考虑以下代码：  
  
    ```  
    struct S { mutable int &r; };  
    ```  
  
     早期版本的 Visual C\+\+ 编译器接受此代码，但现在编译器则报告以下错误：  
  
    ```Output  
    错误 C2071: 'S::r'：非法存储类  
    ```  
  
     若要修复此错误，只需删除冗余的可变关键字。  
  
-   **char\_16\_t 和 char32\_t**  
  
     你不能再使用 `char16_t` 或 `char32_t` 作为 typedef 中的别名，因为这些类型现在被视为内置。 用户和库作者通常会将 char16\_t 和 char32\_t 分别定义为 uint16\_t 和 uint32\_t 的别名。  
  
    ```  
    #include <cstdint> typedef uint16_t char16_t; //C2628 typedef uint32_t char32_t; //C2628 int main(int argc, char* argv[]) { uint16_t x = 1; uint32_t y = 2; char16_t a = x; char32_t b = y; return 0; }  
    ```  
  
     若要更新你的代码，请删除 typedef 声明，并重命名与这些名称发生冲突的任何其他标识符。  
  
-   **非类型模板参数**  
  
     现在会在提供显式模板参数时准确检查包含非类型模板参数的某些代码的类型符合性。 例如，在早期版本的 Visual C\+\+ 中正确编译的以下代码。  
  
    ```  
    struct S1 { void f(int); void f(int, int); }; struct S2 { template <class C, void (C::*Function)(int) const> void f() {} }; void f() { S2 s2; s2.f<S1, &S1::f>(); }  
  
    ```  
  
     当前编译器可以准确报告错误，因为模板参数类型不匹配模板参数（该参数是指向 const 成员的指针，但函数为非 const）：  
  
    ```Output  
    错误 C2893：未能特殊化函数模板“void S2::f(void)”备注：使用以下模板参数：备注：“C=S1”备注：“Function=S1::f”  
    ```  
  
     若要在代码中修复此错误，请确保你使用的模板参数类型匹配模板参数声明的类型。  
  
-   **\_\_declspec\(align\)**  
  
     编译器不再接受函数上的 `__declspec(align)`。 以前会始终忽略此项，但现在会产生编译器错误。  
  
    ```  
    error C3323: 'alignas' and '__declspec(align)' are not allowed on function declarations  
    ```  
  
     若要解决此问题，请从函数声明中删除 `__declspec(align)`。 因为它不起作用，将其删除不会更改任何内容。  
  
-   **异常处理**  
  
     有几个对异常处理的更改。 首先，异常对象必须可复制或可移动。 在 [!INCLUDE[cpp_dev12_long](../build/reference/includes/cpp_dev12_long_md.md)] 中编译的以下代码却不能在 [!INCLUDE[cpp_dev14_long](../porting/includes/cpp_dev14_long_md.md)] 中进行编译：  
  
    ```  
    struct S { public: S(); private: S(const S &); }; int main() { throw S(); // error }  
  
    ```  
  
     问题在于，复制构造函数是私有的，因此对象无法像处理异常的标准过程那样进行复制。 当复制构造函数为声明的 `explicit` 时，这同样适用。  
  
    ```  
    struct S { S(); explicit S(const S &); }; int main() { throw S(); // error }  
  
    ```  
  
     若要更新你的代码，请确保异常对象的复制构造函数是公用的且未标记为 `explicit`。  
  
     通过值捕获异常还要求异常对象可复制。 在 [!INCLUDE[cpp_dev12_long](../build/reference/includes/cpp_dev12_long_md.md)] 中编译的以下代码却不能在 [!INCLUDE[cpp_dev14_long](../porting/includes/cpp_dev14_long_md.md)] 中进行编译：  
  
    ```  
    struct B { public: B(); private: B(const B &); }; struct D : public B { }; int main() { try { } catch (D d) // error { } }  
  
    ```  
  
     可以通过将 `catch` 的参数类型更改为引用来解决此问题。  
  
    ```  
    catch(D& d) { }  
    ```  
  
-   **后跟宏的字符串文本**  
  
     编译器现在支持用户定义的文本。 因此，宏之前没有任何干预空格的字符串文本被视为用户定义的文本，这可能会产生错误或意外结果。 例如，在早期的编译器中，成功编译了以下代码：  
  
    ```  
    #define _x "there" char* func() { return "hello"_x; } int main() { char * p = func(); return 0; }  
    ```  
  
     编译器将此视为后跟宏的字符串文本“hello”，该宏是展开的“there”，然后两个字符串串联成一个。 在 [!INCLUDE[cpp_dev14_long](../porting/includes/cpp_dev14_long_md.md)] 中，编译器将此解释为用户定义的文字，但由于没有定义匹配的用户定义的 \_x 文本，它将报告错误。  
  
    ```  
    error C3688: invalid literal suffix '_x'; literal operator or literal operator template 'operator ""_x' not found note: Did you forget a space between the string literal and the prefix of the following string literal?  
  
    ```  
  
     若要解决此问题，请在字符串文本和宏之间添加一个空格。  
  
-   **相邻字符串文本**  
  
     与上文类似，由于字符串分析中的相关变化，没有任何空格的相邻字符串文本（或宽或窄的字符字符串文本）被视为 Visaul C\+\+ 早期版本中的单个串联字符串。 在 [!INCLUDE[cpp_dev14_long](../porting/includes/cpp_dev14_long_md.md)] 中，现在必须在两个字符串之间添加空格。 例如，必须更改以下代码：  
  
    ```  
    char * str = "abc""def";  
    ```  
  
     只需在两个字符串之间添加空间。  
  
    ```  
    char * str = "abc" "def";  
    ```  
  
-   **placement new 和 placement delete**  
  
     对 delete 运算符做出更改以使其符合 C\+\+14 标准。 标准更改的详细信息位于 [C\+\+ 调整了大小的释放](http://isocpp.org/files/papers/n3778.html)。 这些更改将添加采用大小参数的全局 delete 运算符的形式。 重大更改为，如果你之前使用的是具有相同签名的运算符 delete（以与 placement new 运算符对应），你将收到编译器错误（C2956，在使用 placement new 的点位置出现，因为在代码中的该位置，编译器会尝试标识适当匹配的 delete 运算符）。  
  
     函数 `void operator delete(void *, size_t)` 是与 C\+\+11 中的 placement new 函数“void \* operator new\(size\_t, size\_t\)”对应的 placement delete 运算符。 使用 C\+\+14 调整了大小的释放，此 delete 函数现在是*常用释放函数*（全局 delete 运算符）。 标准要求为，如果使用 placement new 查找相应的 delete 函数和常用释放函数，则程序会出现格式错误。  
  
     例如，假设你的代码同时定义了 placement new 和 placement delete：  
  
    ```  
    void * operator new(std::size_t, std::size_t); void operator delete(void*, std::size_t) noexcept;  
  
    ```  
  
     由于定义的 placement delete 运算符和新的全局调整大小的 delete 运算符之间的函数签名匹配，因此就会出现问题。 考虑是否可以使用任何 placement new 和 placement delete 运算符的其他类型（size\_t 除外）。  请注意，size\_t typedef 的类型取决于编译器；在 Visual C\+\+ 中，它是一个无符号整型的 typedef。 较好的解决办法就是使用如下的枚举类型：  
  
    ```  
    enum class my_type : size_t {};  
  
    ```  
  
     然后，更改你对 placement new 和 placement delete 的定义，以使用此类型作为第二个参数（而不是 size\_t）。 你还需要更新对 placement new 的调用以传递新类型（例如，通过使用 `static_cast<my_type>` 从整数值转换）并更新 new 和 delete 的定义以强制转换回整数类型。 你无需为此使用枚举；具有 size\_t 成员的类类型也将起作用。  
  
     你还可以将 placement new 全部消除作为备选解决方案。 如果你的代码使用 placement new 实现内存池，其中位置参数是分配或删除的对象的大小，则调整了大小的释放功能可能适合替换你自定义的内存池代码，且你可以去掉位置函数，仅使用自己两个参数的 delete 运算符（而不是位置函数）。  
  
     如果你不想立即更新代码，可以通过使用编译器选项 \/Zc:sizedDealloc\- 恢复到旧行为。 如果使用此选项，则不存在两个参数的 delete 函数，并且也不会导致与 placement delete 运算符发生冲突。  
  
-   **联合数据成员**  
  
     联合数据成员不再具有引用类型。 以下代码在 [!INCLUDE[cpp_dev12_long](../build/reference/includes/cpp_dev12_long_md.md)]中成功编译，但在 [!INCLUDE[cpp_dev14_long](../porting/includes/cpp_dev14_long_md.md)] 中产生错误。  
  
    ```  
    union U1 { const int i; }; union U2 { int &i; }; union U3 { struct {int &i;}; };  
    ```  
  
     前面的代码产生以下错误：  
  
    ```Output  
    test.cpp(67)：错误 C2625：U2::i：非法的联合成员；类型“int &”为引用类型 test.cpp(70)：错误 C2625：U3::i：非法的联合成员；类型“int &”为引用类型  
    ```  
  
     若要解决此问题，请将引用类型更改为指针或值。 更改指针类型需要对使用联合字段的代码进行更改。 将代码更改为值将更改存储在联合中的数据，这会影响其他字段，因为联合类型中的字段共享相同的内存。 根据值的大小，它还可能更改联合的大小。  
  
-   匿名联合现在更符合标准。 早期版本的编译器生成了匿名联合的显式构造函数和析构函数。 这些在 [!INCLUDE[cpp_dev14_long](../porting/includes/cpp_dev14_long_md.md)] 中已删除。  
  
    ```  
    struct S { S(); }; union { struct { S s; }; } u; // C2280  
    ```  
  
     前面的代码在 [!INCLUDE[cpp_dev14_long](../porting/includes/cpp_dev14_long_md.md)] 中生成以下错误：  
  
    ```  
    error C2280: '<unnamed-type-u>::<unnamed-type-u>(void)': attempting to reference a deleted function note: compiler has generated '<unnamed-type-u>::<unnamed-type-u>' here  
    ```  
  
     若要解决此问题，请提供你对构造函数和\/或析构函数的定义。  
  
    ```  
    struct S { // Provide a default constructor by adding an empty function body. S() {} }; union { struct { S s; }; } u;  
    ```  
  
-   **具有匿名结构的联合**  
  
     为了符合标准，已对联合中的匿名结构的成员更改了运行时行为。 创建此类联合时，将不再隐式调用联合中的匿名结构成员的构造函数。 此外，联合超出范围时，不再隐式调用联合中的匿名结构成员的析构函数。 请考虑以下代码，其中联合 U 包含一个匿名结构，此匿名结构包含的成员是一个具有析构函数的命名结构 S。  
  
    ```  
    #include <stdio.h> struct S { S() { printf("Creating S\n"); } ~S(){ printf("Destroying S\n"); } }; union U { struct { S s; }; U() {} ~U(){} }; void f() { U u; // Destructor implicitly called here. } int main() { f(); char s[1024]; printf("Press any key.\n"); gets_s(s); return 0; }  
    ```  
  
     在 [!INCLUDE[cpp_dev12_long](../build/reference/includes/cpp_dev12_long_md.md)] 中，创建联合时会调用 S 的构造函数，清理函数 f 的堆栈时会调用 S 的析构函数。 但在 [!INCLUDE[cpp_dev14_long](../porting/includes/cpp_dev14_long_md.md)] 中，不会调用构造函数和析构函数。 编译器会对关于此行为的更改发出警告。  
  
    ```Output  
    警告 C4587：U::s：行为更改：不再隐式调用构造函数 警告 C4588：U::s：行为更改：不再隐式调用析构函数  
    ```  
  
     若要还原原始行为，请赋予匿名结构一个名称。 无论编译器版本为何，非匿名结构的运行时行为都是相同的。  
  
    ```  
    #include <stdio.h> struct S { S() { printf("Creating S.\n"); } ~S() { printf("Destroying S\n"); } }; union U { struct { S s; } namedStruct; U() {} ~U() {} }; void f() { U u; } int main() { f(); char s[1024]; printf("Press any key.\n"); gets_s(s); return 0; }  
    ```  
  
     或者，尝试将构造函数和析构函数代码移到新的函数中，并从联合的构造函数和析构函数添加对这些函数的调用。  
  
    ```  
    #include <stdio.h> struct S { void Create() { printf("Creating S.\n"); } void Destroy() { printf("Destroying S\n"); } }; union U { struct { S s; }; U() { s.Create();  } ~U() { s.Destroy(); } }; void f() { U u; } int main() { f(); char s[1024]; printf("Press any key.\n"); gets_s(s); return 0; }  
    ```  
  
-   **模板解析**  
  
     对模板的名称解析进行了更改。 在 C\+\+ 中，考虑名称解析的候选对象时，可能会出现作为潜在匹配项考虑的一个或多个名称生成无效的模板实例化的情况。 这些无效的实例化通常不会导致编译器错误，这被称为 SFINAE（替换失败不是错误）原则。  
  
     现在，如果 SFINAE 要求编译器将类模板专用化进行实例化，则在此过程中发生的任何错误都是编译器错误。 在早期版本中，编译器会忽略此类错误。 例如，考虑以下代码：  
  
    ```  
    #include <type_traits> template<typename T> struct S { S() = default; S(const S&); S(S&&); template<typename U, typename = typename std::enable_if<std::is_base_of<T, U>::value>::type> S(S<U>&&); }; struct D; void f1() { S<D> s1; S<D> s2(s1); } struct B { }; struct D : public B { }; void f2() { S<D> s1; S<D> s2(s1); }  
  
    ```  
  
     如果使用当前编译器进行编译，将得到以下错误：  
  
    ```Output  
    type_traits(1110)：错误 C2139：“D”：未定义的类不允许作为编译器内部类型特征“__is_base_of”的参数 ..\t331.cpp(14)：备注：请参阅“D”的声明 ..\t331.cpp(10)：备注：请参阅对正在使用 [ T=D, U=D ] 编译的类模板实例化“std::is_base_of<T,U>”的引用  
    ```  
  
     这是因为在第一次调用 is\_base\_of 时，尚未定义类“D”。  
  
     在这种情况下，解决方法是在定义类之前，不使用此类类型特征。 如果将 D 和 B 的定义移到代码文件的开头，错误将得到解决。 如果定义位于标头文件中，请检查标头文件的 include 语句的顺序，以确保在使用有问题的模板之前，对任何类定义进行了编译。  
  
-   **复制构造函数**  
  
     在 [!INCLUDE[vs_dev12](../atl-mfc-shared/includes/vs_dev12_md.md)] 和 [!INCLUDE[vs_dev14](../ide/includes/vs_dev14_md.md)] 中，如果该类具有用户定义的移动构造函数，但没有用户定义的复制构造函数，则编译器生成类的复制构造函数。 在 Dev14 中，此隐式生成的复制构造函数也标记为“\= delete”。  
  
##  <a name="BK_CRT"></a> C 运行库 \(CRT\)  
  
### 常规更改  
  
-   **重构的二进制文件**  
  
     CRT 库被重构为两个不同的二进制文件、一个通用 CRT \(ucrtbase\)（其中包含大多数标准功能）和一个 VC 运行时库 \(vcruntime140\)（其中包含与编译器相关的功能，如异常处理和内部函数）。 如果你使用的是默认项目设置，则此更改不会对你产生影响，因为链接器将自动使用新的默认库。 如果将项目的“链接器”属性“忽略所有默认库”设置为“是”，或你使用的是命令行上的 \/NODEFAULTLIB 链接器选项，则必须更新库的列表（位于“附加依赖项”属性）以包括新的重构库。 将旧的 CRT 库（libcmt.lib、libcmtd.lib、msvcrt.lib、msvcrtd.lib）替换为等效的重构库。 对于两个中的每个重构库，都存在静态 \(.lib\) 和动态 \(.dll\) 版本，发行（无后缀）和调试版本（使用“d”后缀）。 动态版本具有与之链接的导入库。 两个重构库是通用的 CRT（特别是 ucrtbase.dll 或 .lib、ucrtbased.dll 或 .lib）和 VC 运行时库（libvcruntime.lib、libvcruntime.dll、libvcruntimed.lib 和 libvcruntimed.dll）。 请参阅 [CRT 库功能](../c-runtime-library/crt-library-features.md)。  
  
### \<locale.h\>  
  
-   **localeconv**  
  
     启用[每个线程区域设置](../parallel/multithreading-and-locales.md)后，locale.h 中声明的 [Localeconv](../c-runtime-library/reference/localeconv.md) 函数现在正常工作。 在早期版本的库中，此函数将返回全局区域设置（而不是线程的区域设置）的 lconv 数据。  
  
     如果使用每个线程区域设置，应该检查 localeconv 的使用以查看你的代码是否假定返回的 lconv 数据代表全局区域设置，并相应地对其进行修改。  
  
### \<math.h\>  
  
-   **数学库函数的 C\+\+ 重载**  
  
     在早期版本中，\<math.h\> 定义了部分（而不是全部）数学库函数的 C\+\+ 重载。 \<cmath\> 定义了其余的重载，因此为了获取所有重载，其中一个需要包括 \<cmath\> 标头。 这就会导致只包括 \<math.h\> 的代码中的函数重载解析出现问题。 现在，已从 \<math.h\> 中删除了所有 C\+\+ 重载，现在仅包含在 \<cmath\> 中。  
  
     若要解决错误，包括 \<cmath\> 以获取已从 \<math.h\> 中删除的函数的声明。 下表列出了移动的函数。  
  
     移动的函数：  
  
    1.  双精度型 abs\(double\) 和浮点型 abs\(float\)  
  
    2.  双精度型 pow\(double, int\)、浮点型 pow\(float, float\)、浮点型 pow\(float, int\)、长双精度型 pow\(long double, long double\)、长双精度型 pow\(long double, int\)  
  
    3.  浮点型和长双精度型版本的浮点函数 acos、acosh、asin、asinh、atan、atanh、atan2、cbrt、ceil、copysign、cos、cosh、erf、erfc、exp、exp2、expm1、fabs、fdim、floor、fma、fmax、fmin、fmod、frexp、hypot、ilogb、ldexp、lgamma、llrint、llround、log、log10、log1p、log2、lrint、lround、modf、nearbyint、nextafter、nexttoward、remainder、remquo、rint、round、scalbln、scalbn、sin、sinh、sqrt、tan、tanh、tgamma、trunc  
  
     如果你的代码使用具有仅包含 math.h 标头的浮点型的 abs，则浮点版本将不再可用，因此调用（即使具有浮点参数）现在已解析为 abs\(int\)。 这将产生错误：  
  
    ```Output  
    警告 C4244：“参数”：从“float”转换为“int”，可能丢失数据  
    ```  
  
     此警告的解决方法是将对 abs 的调用替换为浮点版本的 abs（例如双精度型参数的 fabs 或浮点型参数的 fabsf）或包含 cmath 标头并继续使用 abs。  
  
-   **浮点一致性**  
  
     对数学库所做的许多更改都用以使特例输入（如 NaN 和无穷大）更符合 IEEE\-754 和 C11 附录 F 规范。 例如，在早期版本的库中通常被视为错误的 quiet NaN 输入已不再被视为错误。 请参阅 [IEEE 754 标准](http://grouper.ieee.org/groups/754) 和 [C11 标准](http://www.iso-9899.info/wiki/The_Standard)的附录 F。  
  
     这些更改不会导致编译时错误，但可能会根据标准使程序以不同的方式更准确地运行。  
  
-   **FLT\_ROUNDS**  
  
     在 Visual Studio 2013 中，FLT\_ROUNDS 宏扩展为常量表达式，这是错误的，因为舍入模式在运行时是可配置的，例如，通过调用 fesetround。 FLT\_ROUNDS 宏现在是动态的，并正确反映当前的舍入模式。  
  
### \<new\> 和 \<new.h\>  
  
-   **new 和 delete**  
  
     在早期版本的库中，实现定义的运算符 new 和 delete 函数已从运行时库 DLL（例如，msvcr120.dll）中导出。 这些运算符函数现在始终以静态方式链接到二进制文件，即使是使用运行时库 DLL 时也是如此。  
  
     这对于本机或混合代码 \(\/clr\) 而言不是一项重大更改，但是对于编译为 [\/clr:pure](../build/reference/clr-common-language-runtime-compilation.md) 的代码而言，这可能会导致代码无法进行编译。 如果将代码编译为 \/clr:pure，可能需要添加 \#include \<new\> 或 \#include \<new.h\> 以解决由于此更改导致的生成错误。 请注意，\/clr:pure 在[!INCLUDE[vs_dev14](../ide/includes/vs_dev14_md.md)] 中已被弃用，并且可能在未来版本中删除。  
  
### \<process.h\>  
  
-   **\_beginthread 和 \_beginthreadex**  
  
     现在，[\_Beginthread](../c-runtime-library/reference/beginthread-beginthreadex.md) 和 [\_beginthreadex](../c-runtime-library/reference/beginthread-beginthreadex.md) 函数保存对模块的引用，在该模块中，已针对线程持续时间定义了线程过程。 这有助于确保线程在完成运行之后才卸载模块。  
  
### \<stdarg.h\>  
  
-   **va\_start 和引用类型**  
  
     编译 C\+\+ 代码时，[va\_start](../c-runtime-library/reference/va-arg-va-copy-va-end-va-start.md) 现在会在编译时验证传递给它的参数是否为引用类型。 C\+\+ 标准禁止引用类型的参数。  
  
### \<stdio.h\> 和 \<conio.h\>  
  
-   **Printf 和 scanf 系列函数现在采用内联方式进行定义。**  
  
     所有 printf 和 scanf 函数的定义已以内联方式移动到 \<stdio.h\>、\<conio.h\> 和其他 CRT 标头中。 这项重大更改会导致本地声明这些函数（没有适当的 CRT 标头）的任何程序发生链接器错误（LNK2019、无法解析的外部符号）。 如果可能，应更新代码以包括 CRT 标头（即，添加 \#include \<stdio.h\>）和内联函数，但如果不想修改代码以包括这些标头文件，则可以选择将其他库添加到链接器输入 \(legacy\_stdio\_definitions.lib\)。  
  
     若要将此库添加到 IDE 中的链接器输入，请打开项目节点的上下文菜单，选择“属性”，然后在“项目属性”对话框中选择“链接器”，编辑“链接器输入”以将 legacy\_stdio\_definitions.lib 添加到用分号隔开的列表。  
  
     如果项目链接的静态库是使用早于 2015 的 Visual C\+\+ 版本编译的，则链接器可能会报告无法解析的外部符号。 这些错误可能会引用 \_imp\_ \* 窗体中某些 stdio 函数的 \_iob、\_iob\_func 或相关导入的内部 stdio 定义。 Microsoft 建议在升级项目时使用最新版本的 Visual C\+\+ 编译器和库编译所有静态库。 如果库是第三方库并且第三方库的源不可用，则应请求来自第三方更新后的二进制文件，或者将你对此库的用法封装到单独的 DLL（使用旧版 Visual C\+\+ 或库编译的）。  
  
    > [!WARNING]
    >  如果你链接的是 Windows SDK 8.1 或更早版本，可能会遇到这些无法解析的外部符号错误。 在这种情况下，应通过将 legacy\_stdio\_definitions.lib 添加到链接器输入（如上文所述）来解决该错误。  
  
     若要解决无法解析的符号错误，可以尝试使用 [dumpbin.exe](../build/reference/dumpbin-reference.md) 来检查二进制文件中定义的符号。 请尝试使用下面的命令行来查看在库中定义的符号。  
  
    ```  
    dumpbin.exe /LINKERMEMBER somelibrary.lib  
    ```  
  
-   **gets 和 \_getws**  
  
     已删除 [gets](../c-runtime-library/gets-getws.md) 和 [\_getws](../c-runtime-library/gets-getws.md) 函数。 已从 C11 中的 C 标准库删除 gets 函数，因为其不能安全使用。 \_getws 函数是与 gets 等效（但可用于宽字符串）的 Microsoft 扩展。 作为这些函数的替代，请考虑使用 [fgets](../c-runtime-library/reference/fgets-fgetws.md)、[fgetws](../c-runtime-library/reference/fgets-fgetws.md)、[gets\_s](../c-runtime-library/reference/gets-s-getws-s.md) 和 [\_getws\_s](../c-runtime-library/reference/gets-s-getws-s.md)。  
  
-   **\_cgets 和 \_cgetws**  
  
     已删除 [\_Cgets](../c-runtime-library/cgets-cgetws.md) 和 [\_cgetws](../c-runtime-library/cgets-cgetws.md) 函数。 作为这些函数替代，请考虑使用 [\_cgets\_s](../c-runtime-library/reference/cgets-s-cgetws-s.md) 和 [\_cgetws\_s](../c-runtime-library/reference/cgets-s-cgetws-s.md)。  
  
-   **无穷大和 NaN 格式设置**  
  
     在早期版本中，可以使用 Visual C\+\+ 特定的 sentinel 字符串集进行无穷大和 NaN 格式设置。  
  
    -   无穷大：1.\#INF  
  
    -   静默 NaN：1.\#QNAN  
  
    -   信号 NaN：1.\#SNAN  
  
    -   无穷大 NaN：1.\#IND  
  
     这些字符串的任何一种都可能已采用符号作为前缀并且格式设置也可能略有不同，具体取决于字段宽度和精度（有时会起到不寻常的作用，例如，printf\("%.2f\\n", INFINITY\) 可以打印 1.\#J，因为 \#INF 会“四舍五入”为 2 位数的精度）。 C99 引入了有关如何设置无穷大和 NaN 格式的新要求。 现在，Visual C\+\+ 实现符合这些要求。 新字符串如下所示：  
  
    -   无穷大：inf  
  
    -   静默 NaN：nan  
  
    -   信号 NaN：nan\(snan\)  
  
    -   不定 NaN：nan\(ind\)  
  
     可能以符号作为其中任何一种字符串的前缀。 如果使用了大写格式说明符（%F 而不是 %f），则字符串将按要求以大写字母形式（INF 而不是 inf）打印。  
  
     已修改 [scanf](../c-runtime-library/reference/scanf-scanf-l-wscanf-wscanf-l.md) 函数以便分析这些新的字符串，因此这些字符串会通过 printf 和 scanf 往返。  
  
-   **浮点格式设置和分析**  
  
     引入了新浮点格式设置和分析算法以提高正确性。 此更改会影响 [printf](../c-runtime-library/reference/printf-printf-l-wprintf-wprintf-l.md) 和 [scanf](../c-runtime-library/reference/scanf-scanf-l-wscanf-wscanf-l.md) 系列函数，以及像 [strtod](../c-runtime-library/reference/strtod-strtod-l-wcstod-wcstod-l.md) 这样的函数。  
  
     旧的格式设置算法将仅生成有限数量的数字，然后将用零填充其余的小数位数。 这是通常足以生成将往返回原始浮点值的字符串，但如果你想要精确值（或最接近十进制的表示），则不够完美。 新的格式设置算法会尽可能多地生成数字来表示值（或填充指定的精度）。 作为改进的一个例子；打印两个中指数较大的一个时，请考虑结果：  
  
    ```  
    printf("%.0f\n", pow(2.0, 80))  
  
    ```  
  
    ```Output  
        旧版本：1208925819614629200000000    新版本：1208925819614629174706176  
    ```  
  
     旧版本分析算法考虑的输入字符串中有效位数仅达 17，并将丢弃其余数位。 这不足以生成由字符串表示的近似值，结果通常是非常接近正确舍入的结果。 新版本的实现会考虑所有存在的数字，并生成所有输入（长度多达 768 位）的正确舍入的结果。 此外，这些函数现在遵循舍入模式（可通过 fesetround 控制）。  这可能是重大的行为更改，因为这些函数可能会输出不同的结果。 新版本的结果始终比旧版本的结果更准确。  
  
-   **十六进制和无穷大\/NaN 浮点分析**  
  
     浮点分析算法现在将分析十六进制浮点字符串（例如，那些由 %a 和 %A printf 格式说明符生成的字符串）和由 printf 函数生成的所有无穷大和 NaN 字符串（如上文所述）。  
  
-   **%A 和 %a 零填充**  
  
     %a 和 %A 格式说明符将浮点数转化为十六进制的尾数和二进制指数。 在早期版本中，printf 函数可能会错误地用零填充字符串。 例如，printf \("%07.0a\\n", 1.0\) 可能会打印 00x1p\+0，而它本应打印 0x01p\+0。 已解决此问题。  
  
-   **%A 和 %a 精度**  
  
     在早期版本的库中，%A 和 %a 格式说明符的默认精度是 6。 为了符合 C 标准，现在默认精度为 13。  
  
     这是使用带 %A 或 %a 的格式字符串的任一函数输出中的运行时行为更改。 在旧版本行为中，使用 %A 说明符的输出可能是“1.1A2B3Cp\+111”。 现在相同值的输出是“1.1A2B3C4D5E6F7p\+111”。 若要获取旧版本行为，则可以指定精度（例如，%.6A）。 请参阅 [精度规范](../c-runtime-library/precision-specification.md)。  
  
-   **%F 说明符**  
  
     现在支持 %F 格式\/转换说明符。 它在功能上等效于 %f 格式说明符，但使用大写字母形式进行格式设置的无穷大和 Nan 除外。  
  
     在早期版本中，实现过去通常将 F 和 N 分析为长度修饰符。 此行为追溯到分段地址空间的时代：这些长度修饰符分别用于指示或近或远的指针（如 %Fp 或 %Ns 中所示）。 此行为已被删除。 如果遇到 %F，现在则将其视为 %F 格式说明符；如果遇到 %N，现在则将其视为无效的参数。  
  
-   **指数格式设置**  
  
     %e 和 %E 格式说明符将浮点数转化为十进制的尾数和指数。 %g 和 %G 格式说明符在某些情况下也以此形式设置格式位数。 在早期版本中，CRT 会始终生成具有三个数字指数的字符串。 例如，printf \("%e\\n", 1.0\) 可能会打印 1.000000e\+000。 这是错误的：根据 C 要求，如果可使用一个或两个数字表示指数，则仅打印两个数字。  
  
     Visual Studio 2005 中添加了全局一致性切换：[\_set\_output\_format](../c-runtime-library/set-output-format.md)。 程序可以调用参数为 \_TWO\_DIGIT\_EXPONENT 的此函数，以启用符合标准的指数打印。 已将默认行为更改为符合标准的指数打印模式。  
  
-   **格式字符串验证**  
  
     在早期版本中，printf 和 scanf 函数以静默方式接受许多无效格式字符串，有时会起到不寻常的作用。 例如，%hlhlhld 将被视为 %d。 现在所有无效格式字符串都被视为无效的参数。  
  
-   **fopen 模式字符串验证**  
  
     在早期版本中，fopen 系列函数以静默方式接受某些无效的模式字符串（例如，r\+b\+）。 现在可检测无效的模式字符串并将其视为无效的参数。  
  
-   **\_O\_U8TEXT 模式**  
  
     [\_Setmode](../c-runtime-library/reference/setmode.md) 函数现在可以准确报告在 in\_O\_U8TEXT 模式中打开的流模式。 在早期版本的库中，它将报告正在 \_O\_WTEXT 中打开的此类流。  
  
     如果你的代码解释其中编码为 UTF\-8 的流的 \_O\_WTEXT 模式，这则是一项重大更改。 如果你的应用程序不支持 UTF\_8，请考虑为此越来越常见的编码添加支持。  
  
-   **snprintf 和 vsnprintf**  
  
     现在已实现 [Snprintf](../c-runtime-library/reference/snprintf-snprintf-snprintf-l-snwprintf-snwprintf-l.md) 和 [vsnprintf](../c-runtime-library/reference/vsnprintf-vsnprintf-vsnprintf-l-vsnwprintf-vsnwprintf-l.md) 函数。 较旧的代码通常为宏版本的这些函数提供定义，因为它们未由 CRT 库实现，但在较新版本中则不再需要这些。 如果将 [snprintf](../c-runtime-library/reference/snprintf-snprintf-snprintf-l-snwprintf-snwprintf-l.md) 或 [vsnprintf](../c-runtime-library/reference/vsnprintf-vsnprintf-vsnprintf-l-vsnwprintf-vsnwprintf-l.md) 在包括 \<stdio.h\> 之前定义为宏，则现在编译失败并显示错误，该错误指示定义了宏的位置。  
  
     通常情况下，解决此问题的方法是删除用户代码中 snprintf 或 vsnprintf 的任何声明。  
  
-   **tmpnam 生成可用文件名**  
  
     在早期版本中，tmpnam 和 tmpnam\_s 函数在驱动器根目录（如 \\sd3c）中生成文件名。 这些函数现在在临时目录中生成可用的文件名路径。  
  
-   **文件封装**  
  
     在早期版本中，完全在 \<stdio.h\> 中定义文件类型，因此用户代码可以进入文件并修改其内部结构。 已对 stdio 库进行了更改以隐藏实现细节。 作为此操作的一部分，\<stdio.h\> 中所定义的文件现在是不透明类型且无法从 CRT 自身外部访问其成员。  
  
-   **\_outp 和 \_inp**  
  
     已删除函数 [\_outp](../c-runtime-library/outp-outpw-outpd.md)、[\_outpw](../c-runtime-library/outp-outpw-outpd.md)、[\_outpd](../c-runtime-library/outp-outpw-outpd.md)、[\_inp](../c-runtime-library/inp-inpw-inpd.md)、[\_inpw](../c-runtime-library/inp-inpw-inpd.md) 和 [\_inpd](../c-runtime-library/inp-inpw-inpd.md)。  
  
### \<stdlib.h\>、\<malloc.h\> 和 \<sys\/stat.h\>  
  
-   **strtof 和 wcstof**  
  
     当值不是以浮点形式表示时，Strtof 和 wcstof 函数无法将 errno 设置为 ERANGE。 已解决此问题。 （请注意此错误只特定于这两个函数；strtod、wcstod、strtold 和 wcstold 函数不受影响。） 这是运行时重大更改。  
  
-   **对齐的分配函数**  
  
     在早期版本中，对齐的分配函数（\_aligned\_malloc、\_aligned\_offset\_malloc 等） 以静默方式接受带 0 的对齐方式的块的请求。 请求的对齐方式幂必须是 2（而不是零）。 已解决此问题，且请求的 0 的对齐方式现在被视为无效的参数。 这是运行时重大更改。  
  
-   **堆函数**  
  
     删除了 \_heapadd、\_heapset 和 \_heapused 函数。 这些函数已不起作用，因为 CRT 已更新为使用 Windows 堆。  
  
-   **smallheap**  
  
     删除了 smalheap 链接选项。 请参阅 [链接选项](../c-runtime-library/link-options.md)。  
  
### \<string.h\>  
  
-   **wcstok**  
  
     更改了 wcstok 函数的签名，以便匹配 C 标准所要求的内容。 在早期版本的库中，此函数的签名为：  
  
    ```  
    wchar_t* wcstok(wchar_t*, wchar_t const*)  
    ```  
  
     它使用内部的每个线程上下文来跟踪跨状态调用（就像为 strtok 所进行的操作一样）。 该函数现在具有签名 wchar\_t\* wcstok\(wchar\_t\*、wchar\_t const\*、wchar\_t\*\*\)，并要求调用方将上下文作为第三个参数传递给函数。  
  
     添加了新的 \_wcstok 函数，并具有旧签名以便进行迁移。 编译 C\+\+ 代码时，还存在具有旧签名的 wcstok 的内联重载。 已声明弃用此重载。 在 C 代码中，你可能会定义 \_CRT\_NON\_CONFORMING\_WCSTOK 以使 \_wcstok 用于替换 wcstok。  
  
### \<time.h\>  
  
-   **clock**  
  
     在早期版本中，已使用 Windows API [GetSystemTimeAsFileTime](http://msdn.microsoft.com/library/windows/desktop/ms724397.aspx) 实现了 [clock](../c-runtime-library/reference/clock.md) 函数。 使用此实现，clock 函数对系统时间比较敏感，因此不一定是单一的。 已根据 [QueryPerformanceCounter](https://msdn.microsoft.com/library/windows/desktop/ms644904.aspx) 重新实现了 clock 函数，现在它是单一的。  
  
-   **fstat 和 \_utime**  
  
     在早期版本中，[\_stat](../c-runtime-library/reference/stat-functions.md)、[fstat](../c-runtime-library/reference/fstat-fstat32-fstat64-fstati64-fstat32i64-fstat64i32.md) 和 [\_utime](../c-runtime-library/reference/utime-utime32-utime64-wutime-wutime32-wutime64.md) 函数对夏时制的处理方式不正确。 在 Visual Studio 2013 之前的版本中，所有这些函数错误调整标准时时间，就像处于夏时制时间内一样。  
  
     在 Visual Studio 2013 中，解决了 \_stat 系列函数中的此问题，但未解决 fstat 和 \_utime 系列函数中的类似问题。 这就导致了由于问题函数之间的不一致引起的问题。 现在已修复 fstat 和 \_utime 系列函数，因此所有这些函数现在可正确且一致地处理夏时制。  
  
-   **asctime**  
  
     在早期版本中，[asctime](../c-runtime-library/reference/asctime-wasctime.md) 函数会以前导零填充单位数的日期（例如：Fri Jun 06 08:00:00 2014）。 规范要求此类日期应以前导空格填充，例如 Fri Jun  6 08:00:00 2014。 已解决此问题。  
  
-   **strftime 和 wcsftime**  
  
     Strftime 和 wcsftime 函数现在支持 %C、%D、%e、%F、%g、%G、%h、%n、%r、%R、%t、%T、%u 和 %V 格式说明符。 此外，分析但忽略了 E 和 O 修饰符。  
  
     指定 %c 格式说明符生成当前区域设置的“相应的日期和时间表示形式”。 在 C 区域设置中，要求这种表示形式与 %a %b %e %T %Y 相同。 这与 asctime 生成的形式相同。 在早期版本中，使用 MM\/DD\/YY HH:MM:SS 表示形式，%c 格式说明符设置的时间格式不正确。 已解决此问题。  
  
-   **timespec 和 TIME\_UTC**  
  
     现在，\<time.h\> 标头根据 C11 标准定义 timespec 类型和 timespec\_get 函数。 此外，现在可定义与 timespec\_get 函数连用的 TIME\_UTC 宏。 这对于在任一这些方面具有冲突定义的代码而言，是一项重大更改。  
  
-   **CLOCKS\_PER\_SEC**  
  
     现在，CLOCKS\_PER\_SEC 宏根据 C 语言要求扩展为整数类型 clock\_t。  
  
###  <a name="BK_STL"></a> 标准模板库  
 为了实现新的优化和调试检查，C\+\+ 标准库的 Visual Studio 实现特意破坏了连续两个版本之间的二进制兼容性。 因此，在使用 C\+\+ 标准库时，使用不同版本编译的对象文件和静态库不能混合在同一二进制文件（EXE 或 DLL）中，并且不能在使用不同版本编译的二进制文件之间传递 C\+\+ 标准库对象。 这样混合会发出关于 \_MSC\_VER 不匹配的链接器错误。 （\_MSC\_VER 是包含编译器主版本的宏，例如，Visual Studio 2013 的 1800。） 此检查无法检测 DLL 混合，也无法检测涉及 Visual C\+\+ 2008 或早期版本的混合。  
  
-   **STL 包含文件**  
  
     对 STL 标头中的 include 结构进行了一些更改。 允许 STL 标头以未指定的方式相互包含。 一般情况下，应编写你的代码，以便其根据 C\+\+ 标准谨慎包括其需要的所有标头，且不依赖于哪些 STL 标头包含哪些其他 STL 标头。 这使得代码可跨版本和平台进行移植。 至少更改 [!INCLUDE[vs_dev14](../ide/includes/vs_dev14_md.md)] 的两个标头才会影响用户代码。 首先，\<string\> 不再包括 \<iterator\>。 第二，\<tuple\> 现在用于声明 std::array 但不包括所有 \<array\>，这可能中断代码通过以下代码构造的组合：代码具有名为“array”的变量，你具有 using 指令“using namespace std;” 和你包括含有 \<tuple\> 的 STL 标头（如 \<functional\>），其现在用于声明 std::array。  
  
-   **steady\_clock**  
  
     已更改 [steady\_clock](../standard-library/steady-clock-struct.md) 的 \<chrono\> 实现，以便满足 C\+\+ 标准对稳定性和单一性的要求。 steady\_clock 现在以 [QueryPerformanceCounter](https://msdn.microsoft.com/library/windows/desktop/ms644904.aspx) 为基础，而 high\_resolution\_clock 现在是 steady\_clock 的 typedef。 因此，在 Visual C\+\+ 中，steady\_clock::time\_point 现在是 chrono::time\_point\<steady\_clock\> 的 typedef；但是，其他实现不一定是这种情况。  
  
-   **分配器和 const**  
  
     现在，我们要求分配器进行相等\/不等比较，以接受两端上的 const 参数。  如果你的分配器如下定义这些运算符：  
  
    ```  
    bool operator==(const MyAlloc& other)  
    ```  
  
     你应更新这些以将它们声明为 const 成员。  
  
    ```  
    bool operator==(const MyAlloc& other) const  
    ```  
  
-   **const 元素**  
  
     C \+ \+ 标准始终禁止 const 元素（如 vector\<const T\> 或 set\<const T\>）的容器。 Visual C\+\+ 2013 及更早版本接受此类容器。 在当前版本中，此类容器无法编译。  
  
-   **std::allocator::deallocate**  
  
     在 Visual C\+\+ 2013 和早期版本中，std::allocator::deallocate\(p, n\) 忽略了传入用于 n 的参数。  C \+ \+ 标准始终要求 n 应等于作为第一个参数传递给调用分配（返回 p）的值。 但是，在当前版本中将检查 n 的值。 在运行时，为 n 传递不同于标准要求的参数的代码可能会崩溃。  
  
-   **hash\_map 和 hash\_set**  
  
     非标准标头文件 hash\_map 和 hash\_set 在 [!INCLUDE[vs_dev14](../ide/includes/vs_dev14_md.md)] 中已被弃用，并且将在未来版本中移除。 请改用 unordered\_map 和 unordered\_set。  
  
-   **比较运算符和 operator\(\)**  
  
     关联容器（\<map\> 系列）现在要求其比较运算符具有可调用 const 的函数调用运算符。 现在比较运算符类声明中的以下代码无法进行编译：  
  
    ```  
    bool operator()(const X& a, const X& b)  
    ```  
  
     若要解决此错误，请将函数声明更改为：  
  
    ```  
    bool operator()(const X& a, const X& b) const  
    ```  
  
-   **类型特征**  
  
     早期版本的 C\+\+ 草稿标准中删除了类型特征的旧名称。 C\+\+11 中已对这些进行了更改，并且已更新为 [!INCLUDE[vs_dev14](../ide/includes/vs_dev14_md.md)] 中的 C\+\+11 值。 下表显示了旧名称和新名称。  
  
    |旧名称|新名称|  
    |---------|---------|  
    |add\_reference|add\_lvalue\_reference|  
    |has\_default\_constructor|is\_default\_constructible|  
    |has\_copy\_constructor|is\_copy\_constructible|  
    |has\_move\_constructor|is\_move\_constructible|  
    |has\_nothrow\_constructor|is\_nothrow\_default\_constructible|  
    |has\_nothrow\_default\_constructor|is\_nothrow\_default\_constructible|  
    |has\_nothrow\_copy|is\_nothrow\_copy\_constructible|  
    |has\_nothrow\_copy\_constructor|is\_nothrow\_copy\_constructible|  
    |has\_nothrow\_move\_constructor|is\_nothrow\_move\_constructible|  
    |has\_nothrow\_assign|is\_nothrow\_copy\_assignable|  
    |has\_nothrow\_copy\_assign|is\_nothrow\_copy\_assignable|  
    |has\_nothrow\_move\_assign|is\_nothrow\_move\_assignable|  
    |has\_trivial\_constructor|is\_trivially\_default\_constructible|  
    |has\_trivial\_default\_constructor|is\_trivially\_default\_constructible|  
    |has\_trivial\_copy|is\_trivially\_copy\_constructible|  
    |has\_trivial\_move\_constructor|is\_trivially\_move\_constructible|  
    |has\_trivial\_assign|is\_trivially\_copy\_assignable|  
    |has\_trivial\_move\_assign|is\_trivially\_move\_assignable|  
    |has\_trivial\_destructor|is\_trivially\_destructible|  
  
-   **launch::any 和 launch::sync 策略**  
  
     已删除非标准的 launch::any 和 launch::sync 策略。 相反，对于 launch::any，请使用 launch:async &#124; launch:deferred。 对于 launch::sync，请使用 launch::deferred。 请参阅 [launch 枚举](../Topic/launch%20Enumeration.md)。  
  
###  <a name="BK_MFC"></a> MFC 和 ATL  
  
-   **Microsoft 基础类 \(MFC\)** 由于其尺寸大不再包含在 Visual Studio 的“典型”安装中。 若要安装 MFC，请在 Visual Studio 2015 安装程序中选择自定义安装选项。 如果你已安装 Visual Studio 2015，可以通过重新运行 Visual Studio 安装程序，选择自定义安装选项，并选择 Microsoft 基础类来安装 MFC。 可从控制面板、程序和功能，或从安装媒体重新运行 Visual Studio 安装程序。  
  
     Visual C\+\+ 可再发行组件包仍包含此库。  
  
###  <a name="BK_ConcRT"></a> 并发运行时  
  
-   **与 concurrency::Context::Yield 冲突的 Windows.h 中的 Yield 宏**  
  
     并发运行时之前使用 \#undef 来取消定义 Yield 宏，以避免 Windows.h h 中定义的 Yield 宏和 concurrency::Context::Yield 函数之间的冲突。 已删除此 \#undef，并添加了新的非冲突等效 API 调用 [concurrency::Context::YieldExecution](../Topic/Context::YieldExecution%20Method.md)。 若要解决与 Yield 的冲突，可以改为更新代码以调用 YieldExecution 函数，或在调用站点用括号将 Yield 函数名括起来，如下例所示：  
  
    ```  
    (concurrency::Context::Yield)();  
    ```  
  
## 请参阅  
 [Getting Started](../misc/getting-started-with-visual-cpp-in-visual-studio-2015.md)   
 [Visual C\+\+ 2013 中的重大更改](https://msdn.microsoft.com/library/hh409293.aspx)
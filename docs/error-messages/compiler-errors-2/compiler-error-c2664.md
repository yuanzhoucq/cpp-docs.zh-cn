---
title: 编译器错误 C2664 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2664
dev_langs:
- C++
helpviewer_keywords:
- C2664
ms.assetid: 3595d66e-cf87-4fda-a896-c0cd81f95db4
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: bfc1243f55828ec7649956b9d8b3630e644ec325
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-error-c2664"></a>编译器错误 C2664
“函数”: 无法将自变量 n 从“类型 1”转换为“类型 2”  
  
 如果创建了某个类的实例，然后尝试了对用 `explicit` 关键字标记的构造函数进行隐式转换，则可能会发生此参数转换问题。 有关显式转换的详细信息，请参阅[用户定义类型转换](../../cpp/user-defined-type-conversions-cpp.md)。  
  
 如果将临时对象传递给采用指向对象的引用作为参数的函数，则该引用必须是 `const` 引用。  
  
 如果使用不是函数所预期的类型的参数传递该函数，则使用适当的构造函数可创建临时对象。 然后将该临时对象传递给函数。 在这种情况下，该临时对象用于初始化引用。 在该语言的早期版本中，所有的引用都可以由临时对象进行初始化。  
  
 若要修复 C2664，请执行以下操作  
  
-   再次检查给定函数的原型，并改正错误信息中指出的自变量。  
  
-   如果需要的话，提供显式转换。  
  
 如果某个类在它的一个基类中隐藏了成员，也可能生成 C2664。  
  
 有关详细信息，请参阅[如何： 转换 system:: string 到 wchar_t * 或 char\*](../../dotnet/how-to-convert-system-string-to-wchar-t-star-or-char-star.md)。  
  
## <a name="example"></a>示例  
 下面的示例生成 C2664，并演示如何修复此错误。  
  
```  
// C2664.cpp  
// C2664   
struct A {  
   void f(int i) {};  
};  
  
struct B : public A {  
   // To fix, uncomment the following line.  
   // using A::f;  
   void f(A a) {};  
};  
  
int main() {  
   B b;  
   int i = 1;  
   b.f(i);   // B::F hides A::f Uncomment the using declaration in B.  
}  
```  
  
## <a name="example"></a>示例  
 此示例也生成 C2664，并演示如何修复此错误。  
  
```  
// C2664b.cpp  
// C2664 expected  
struct A {  
   // To fix, uncomment the following line.  
   // A(int i){}  
};  
  
void func( int, A ) {}  
  
int main() {  
   func( 1, 1 );   // No conversion from int to A.  
}  
```  
  
## <a name="example"></a>示例  
 下一个示例通过使用字符串调用 `Test` 来演示 C2664，并演示如何修复此错误。 因为该参数是 `szString` 引用，所以必须使用适当的构造函数创建对象。 结果是一个无法用于初始化该引用的临时对象。  
  
```  
// C2664c.cpp  
// compile with: /EHsc  
// C2664 expected  
#include <iostream>  
#include <string.h>  
using namespace std;  
  
class szString {  
   int slen;  
   char *str;  
  
public:  
   szString(const char *);  
   int len() const {   
      return slen;   
   }  
};  
  
// Simple reference cannot bind to temp var.  
void Test(szString &a) {}  
  
// To fix, uncomment the following line.  
// void Test(const szString &a) {}  
  
szString::szString(const char * newstr) : slen(0), str(NULL) {  
   slen=strlen(newstr);  
   str = new char[slen + 1];  
   if (str)  
      strcpy_s(str, (slen + 1), newstr);  
}  
  
int main() {  
   Test("hello");  
}  
```  
  
## <a name="example"></a>示例  
 编译器强制实施应用 `const` 的 C++ 标准要求。 此示例生成 C2664：  
  
```  
// C2664d.cpp  
// C2664 expected  
#include <windows.h>  
  
void func1(LPCSTR &s)  
{  
  
}  
  
void func2(LPSTR &s)  
{  
   func1(s);  
}  
  
int main()  
{  
   return 0;  
}  
```  
  
## <a name="example"></a>示例  
 下面是生成 C2664 的更复杂情况，包括有关如何修复此错误的说明：  
  
```  
// C2664e.cpp  
// compile with: /EHsc  
// C2664 expected  
#define _INTL  
#include <locale>  
#include <iostream>  
  
using namespace std;  
#define LEN 90  
  
int main( ) {  
   char* pszExt = "This is the string to be converted!";  
   wchar_t pwszInt [LEN+1];  
   memset(&pwszInt[0], 0, (sizeof(wchar_t))*(LEN+1));  
  
   // To fix, delete the following line.  
   char* pszNext;  
  
   // To fix, uncomment the following line.  
   // const char* pszNext;  
  
   wchar_t* pwszNext;  
   mbstate_t state;  
   locale loc("C");    
   int res = use_facet<codecvt<wchar_t, char, mbstate_t> >  
      ( loc ).in( state,  
      pszExt, &pszExt[strlen(pszExt)], pszNext,  
      pwszInt, &pwszInt[strlen(pszExt)], pwszNext );  
   // See earlier comment.  
      pwszInt[strlen(pszExt)] = 0;  
   wcout << ( (res!=codecvt_base::error) ?   
                       L"It worked! " : L"It didn't work! " )  
   << L"The converted string is:\n ["  
   << &pwszInt[0]  
   << L"]" << endl;  
  
   exit(-1);  
}  
```  
  
## <a name="example"></a>示例  
 枚举变量未转换为其满足函数调用的基础类型。 有关详细信息，请参阅[枚举类](../../windows/enum-class-cpp-component-extensions.md)。 下面的示例生成 C2664，并演示如何修复此错误。  
  
```  
// C2664f.cpp  
// compile with: /clr  
using namespace System;  
public enum class A : Char {  
   None = 0,  
   NonSilent = 1,  
};  
  
void Test(Char c) {}  
  
int main() {  
   A aa = A::None;  
   Test(aa);   // C2664  
   Test(Char(aa));   // OK - fix by using a conversion cast  
}  
```  
  
## <a name="example"></a>示例  
 midl 编译器中的 Bug 导致 wchar_t 类型作为类型库中的 unsigned short 发出。 若要纠正此错误，请在 C++ 源代码中强制转换类型，或者在 idl 文件中将类型定义为字符串。  
  
```  
// C2664g.idl  
import "prsht.idl";  
  
[ object, uuid(8402B8F1-BF7F-4B49-92D4-C2B9DF4543E9) ]  
  
interface IMyObj1 : IUnknown {  
   HRESULT  teststr([in, string] wchar_t *wstr);  
   HRESULT  testarr([in, size_is(len)] wchar_t wstr[], [in] int len);  
   HRESULT  testbstr([in] BSTR bstr);  
};  
  
[  uuid(44463307-CBFC-47A6-8B4F-13CD0A83B436) ]  
library myproj1 {  
   [  version(1.0), uuid(D8622C12-5448-42B8-8F0E-E3AD6B8470C1) ]  
   coclass CMyObj1 { interface IMyObj1; };  
}  
```  
  
 将代码从 Visual C++ 6.0 移植到更高版本时，使用 `wchar_t` 也会引发 C2664。 在 Visual C++ 6.0 和更早版本中，`wchar_t` 是 `typedef` 的 `unsigned short`，因此也可隐式转换为该类型。 在 Visual C++ 6.0 后，`wchar_t` 是它自己的内置类型（在 C++ 标准中指定），因此不再能隐式转换为 `unsigned short`。 请参阅[/zc: wchar_t （wchar_t 是本机类型）](../../build/reference/zc-wchar-t-wchar-t-is-native-type.md)。  
  
## <a name="example"></a>示例  
 下面的示例生成 C2664，并演示如何修复此错误。  
  
```  
// C2664h.cpp  
#import "C2664g.tlb"  
using namespace myproj1;  
  
int main() {  
   IMyObj1Ptr ptr;  
  
   wchar_t * mybuff = 0;  
   BSTR bstr = 0;  
   int len;  
   ptr->teststr(mybuff);  
   ptr->testbstr(bstr);  
   ptr->testarr(mybuff, len);   // C2664  
   ptr->testarr((unsigned short *)mybuff, len);   // OK - Fix by using a cast  
}  
```  
  
## <a name="example"></a>示例  
 如果编译器无法推导出模板自变量，则也会导致 C2664。  
  
```  
// C2664i.cpp  
#include <stdio.h>  
template <class T, int iType=0>  
class CTypedImg {  
public:  
   CTypedImg() {}  
   void run() {}  
  
   operator CTypedImg<T>& () {  
      return *((CTypedImg<T>*)this);  
    }  
};  
  
template <class t1>  
void test(CTypedImg<t1>& myarg) {  
   myarg.run();  
}  
  
int main() {  
   CTypedImg<float,2> img;  
  
   test((CTypedImg<float>&)img);   // OK  
   test<float>(img);   // OK  
   test(img);   // C2664 - qualify as above to fix  
}  
```
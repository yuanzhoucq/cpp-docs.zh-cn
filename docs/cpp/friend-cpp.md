---
title: "友元 （c + +） |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: friend_cpp
dev_langs: C++
helpviewer_keywords:
- member access, from friend functions
- friend classes [C++]
- friend keyword [C++]
ms.assetid: 8fe9ee55-d56f-40cd-9075-d9fb1375aff4
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: b30b49825d14e72c06f569c343f96c7cf091a62f
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="friend-c"></a>友元 (C++)
在某些情况下，它会更方便，以授予成员级别的访问的不是类的成员的函数或单独类中的所有成员。 仅类实现器可以声明其友元。 函数或类不能将其自身声明为任何类的友元。 在类定义中，使用`friend`关键字和非成员函数或其他类，以允许其访问你的类的私有和受保护成员的名称。         在模板定义中，类型参数可以声明为友元。  
  
## <a name="syntax"></a>语法  
  
```  
class friend F  
friend F;  
```  
  
## <a name="friend-declarations"></a>友元声明  
 如果声明以前未声明的友元函数，则该函数将被导出到封闭非类范围。  
  
 友元声明中声明的函数被视为已使用 `extern` 关键字声明。 (有关详细信息`extern`，请参阅[静态存储类说明符](http://msdn.microsoft.com/en-us/3ba9289a-a412-4a17-b319-ceb2c087df48)。)  
  
 尽管具有全局范围的函数可以在其原型之前声明为友元函数，但是成员函数在它们的完整类声明出现前不能声明为友元函数。 以下代码演示此失败的原因：  
  
```cpp  
class ForwardDeclared;   // Class name is known.  
class HasFriends  
{  
    friend int ForwardDeclared::IsAFriend();   // C2039 error expected  
};  
```  
  
 前面的示例将类名 `ForwardDeclared` 输入到范围中，但是完整的声明（具体而言，声明函数 `IsAFriend` 的部分）是未知的。 因此，`friend` 类中的 `HasFriends` 声明会生成一个错误。  
  
 从 C + + 11 开始，有两种形式的类的友元声明：  
  
```cpp  
friend class F;  
friend F;  
```  
  
 如果该名称没有任何现有类位于最内部的命名空间，则第一个窗体引入了新类 F。  **C + + 11**： 第二个窗体不会引入的新类; 当已声明的类，并声明模板类型参数或为友元的 typedef 时，必须使用它可以使用它。  
  
 使用`class friend F`时引用的类型具有尚未声明：  
  
```cpp  
namespace NS  
{  
    class M  
    {  
        class friend F;  // Introduces F but doesn't define it  
    };  
}  
```  
  
```cpp  
namespace NS  
{  
    class M  
    {  
        friend F; // error C2433: 'NS::F': 'friend' not permitted on data declarations  
    };  
}  
```  
  
 在下面的示例中，`friend F`指`F`NS 的作用域之外声明的类。  
  
```cpp  
class F {};  
namespace NS  
{  
    class M  
    {  
        friend F;  // OK   
    };  
}  
```  
  
 使用`friend F`若要声明为友元模板参数：  
  
```cpp  
template <typename T>  
class my_class  
{  
    friend T;  
    //...  
};  
```  
  
 使用`friend F`声明为友元的 typedef:  
  
```cpp  
class Foo {};  
typedef Foo F;  
  
class G  
{  
    friend F; // OK  
    friend class F // Error C2371 -- redefinition  
};  
```  
  
 若要声明两个互为友元的类，则必须将整个第二个类指定为第一个类的友元。 此限制的原因是该编译器仅在声明第二个类的位置有足够的信息来声明各个友元函数。  
  
> [!NOTE]
>  尽管整个第二个类必须是第一个类的友元，但是可以选择将第一个类中的哪些函数作为第二个类的友元。  
  
## <a name="friend-functions"></a>友元函数  
 `friend` 函数是一个不为类成员的函数，但它可以访问类的私有和受保护的成员。 友元函数不被视为类成员；它们是获得了特殊访问权限的普通外部函数。 友元不在类的范围，并且不调用使用成员选择运算符 (**。** 和-**>**) 除非它们是另一个类的成员。 `friend` 函数由授予访问权限的类声明。 可将 `friend` 声明放置在类声明中的任何位置。 它不受访问控制关键字的影响。  
  
 以下示例显示 `Point` 类和友元函数 `ChangePrivate`。 `friend` 函数可以访问其接受为参数的 `Point` 对象的私有数据成员。  
  
```cpp  
// friend_functions.cpp  
// compile with: /EHsc  
#include <iostream>  
  
using namespace std;  
class Point  
{  
    friend void ChangePrivate( Point & );  
public:  
    Point( void ) : m_i(0) {}  
    void PrintPrivate( void ){cout << m_i << endl; }  
  
private:  
    int m_i;  
};  
  
void ChangePrivate ( Point &i ) { i.m_i++; }  
  
int main()  
{  
   Point sPoint;  
   sPoint.PrintPrivate();  
   ChangePrivate(sPoint);  
   sPoint.PrintPrivate();  
// Output: 0  
           1  
}  
```  
  
## <a name="class-members-as-friends"></a>作为友元的类成员  
 类成员函数可以声明为其他类中的友元。 请看下面的示例：  
  
```cpp  
// classes_as_friends1.cpp  
// compile with: /c  
class B;  
  
class A {  
public:  
   int Func1( B& b );  
  
private:  
   int Func2( B& b );  
};  
  
class B {  
private:  
   int _b;  
  
   // A::Func1 is a friend function to class B  
   // so A::Func1 has access to all members of B  
   friend int A::Func1( B& );  
};  
  
int A::Func1( B& b ) { return b._b; }   // OK  
int A::Func2( B& b ) { return b._b; }   // C2248  
```  
  
 在前面的示例中，仅为函数 `A::Func1( B& )` 授予对类 `B` 的友元访问权限。 因此，访问私有成员`_b`中是正确`Func1`类的`A`但未显示在`Func2`。  
  
 `friend` 类是其所有成员函数都是类的友元函数的类，即，其成员函数具有对类的私有成员和受保护成员访问权限。 假定类 `friend` 中的 `B` 声明是：  
  
```cpp  
friend class A;  
```  
  
 在这种情况下，将为类 `A` 中所有成员函数授予对类 `B` 的友元访问权限。 以下代码是友元类的示例：  
  
```cpp  
// classes_as_friends2.cpp  
// compile with: /EHsc  
#include <iostream>  
  
using namespace std;  
class YourClass {  
friend class YourOtherClass;  // Declare a friend class  
public:  
   YourClass() : topSecret(0){}  
   void printMember() { cout << topSecret << endl; }  
private:  
   int topSecret;  
};  
  
class YourOtherClass {  
public:  
   void change( YourClass& yc, int x ){yc.topSecret = x;}  
};  
  
int main() {  
   YourClass yc1;  
   YourOtherClass yoc1;  
   yc1.printMember();  
   yoc1.change( yc1, 5 );  
   yc1.printMember();  
}  
```  
  
 友元关系不是相互的，除非如此显式指定。 在上面的示例中，`YourClass` 的成员函数无法访问 `YourOtherClass` 的私有成员。  
  
 托管类型不能具有任何友元函数、友元类或友元接口。  
  
 友元关系不能继承，这意味着从 `YourOtherClass` 派生的类不能访问 `YourClass` 的私有成员。 友元关系不可传递，因此 `YourOtherClass` 的友元类无法访问 `YourClass` 的私有成员。  
  
 下图显示了 4 个类声明：`Base`、`Derived`、`aFriend` 和 `anotherFriend`。 只有类 `aFriend` 具有对 `Base` 的私有成员（以及对 `Base` 可能已继承的所有成员）的直接访问权限。  
  
 ![友元关系含义](../cpp/media/vc38v41.gif "vc38V41")  
友元关系含义  
  
## <a name="inline-friend-definitions"></a>内联友元定义  
 可以在类声明中定义友元函数。 这些函数是内联函数，类似于成员内联函数，其行为就像它们在所有类成员显示后但在类范围关闭前（类声明的结尾）被定义时的行为一样。  
  
 类声明中定义的友元函数不被认为在封闭类的范围内；它们在文件范围内。  
  
## <a name="see-also"></a>另请参阅  
 [关键字](../cpp/keywords-cpp.md)
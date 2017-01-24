---
title: "值类型（现代 C++） | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
ms.assetid: f63bb62c-60da-40d5-ac14-4366608fe260
caps.latest.revision: 15
caps.handback.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 值类型（现代 C++）
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

C\+\+ 类是默认值类型。  本主题提供值类型和引入问题概述与它们的使用相关。  
  
## 值与类型引用  
 如前所述，C\+\+ 类是默认值类型。  它们可指定为引用类型，多态性使行为支持面向对象的编程。  从内存和值类型布局控件的角度有时，显示，而引用类型则是有关基类中虚函数多态的目的。  默认情况下，值类型 copyable，即始终具有复制构造函数和复制赋值运算符。  对于引用类型，则不 copyable 使类 \(请禁用复制构造函数和复制赋值运算符\) 并使用虚析构函数，以支持他们计划的多态性。  值类型也是有关内容，那么，当它们复制时，始终为您提供两独立值可以分别修改。  引用类型是有关标识 \- 它是何种对象？  因此，“”引用类型也称为“多态类型”。  
  
 如果事实上您需要一个与引用类型 \(类的基，虚函数\)，如以下代码所示的 `MyRefType` 类，则需要显式禁用复制。  
  
```cpp  
  
// cl /EHsc /nologo /W4  
  
class MyRefType {  
private:  
    MyRefType & operator=(const MyRefType &);  
    MyRefType(const MyRefType &);  
public:  
    MyRefType () {}  
};  
  
int main()  
{  
    MyRefType Data1, Data2;  
    // ...  
    Data1 = Data2;  
}  
```  
  
 编译上述代码产生以下错误：  
  
  **个 test.cpp \(15\):错误 C2248:“MyRefType::operator \=”:无法访问在类的声明 MyRefType 的私有成员”。**  
 **meow.cpp \(5\):请参见“MyRefType::operator 的 \=”声明**  
 **meow.cpp \(3\):请参见“MyRefType "声明**   
## 将值类型和效率  
 复制赋值避免开销并由此新的副本进行优化。  例如，在中，如果的字符串中间矢量插入字符串，则不会复制系统开销，重新分配，只移动，即使它导致矢量的增大。  这也适用于其他操作，例如两对非常大对象的一添加操作。  您如何启用这些优化操作值？  在的某些 C\+\+ 编译器，编译器将隐式启用此您的，这一点非常像复制构造函数可由编译器自动生成。  但是，用 Visual C\+\+，您的类将需要使用“选择”通过声明其移动分配和构造函数在类中定义。  这是实现通过在适当的成员函数声明和定义移动构造函数并将分配方法的双重" and "符 \(&&\) rvalue 引用。还需要插入正确的代码“胆量窃取”从源对象。  
  
 您如何决定是否需要启用移动？  如果您已知道需要拧的复制构造，可能希望启用移动，则可能修复的深层复制。  但是，在中，如果您知道需要将支持，不一定表示您希望启用的副本。  此情况后将调用“移动类型”。  一个示例已经在标准库中是 `unique_ptr`。  作为旁注，旧 `auto_ptr` 的 `unique_ptr` 已替换和精确由于缺少将 C\+\+ 早期版本的支持。  
  
 使用移动语义可返回按值或插入在中间。  移动是复制的优化。  对分配堆的需要作为工作区。  考虑以下伪代码：  
  
```cpp  
  
#include <set>  
#include <vector>  
#include <string>  
using namespace std;  
  
//...  
set<widget> LoadHugeData() {  
    set<widget> ret;  
    // ... load data from disk and populate ret  
    return ret;  
}  
//...  
widgets = LoadHugeData();   // efficient, no deep copy  
  
vector<string> v = IfIHadAMillionStrings();  
v.insert( begin(v)+v.size()/2, "scott" );   // efficient, no deep copy-shuffle  
v.insert( begin(v)+v.size()/2, "Andrei" );  // (just 1M ptr/len assignments)  
//...  
HugeMatrix operator+(const HugeMatrix& , const HugeMatrix& );  
HugeMatrix operator+(const HugeMatrix& ,       HugeMatrix&&);  
HugeMatrix operator+(      HugeMatrix&&, const HugeMatrix& );  
HugeMatrix operator+(      HugeMatrix&&,       HugeMatrix&&);  
//...  
hm5 = hm1+hm2+hm3+hm4+hm5;   // efficient, no extra copies  
```  
  
### 启用相应的值类型的移动  
 对于移动的深层副本。廉价的类似于的类值，结构启用移动和移动分配有效的。  考虑以下伪代码：  
  
```cpp  
  
#include <memory>  
#include <stdexcept>  
using namespace std;  
// ...  
class my_class {  
    unique_ptr<BigHugeData> data;  
public:  
    my_class( my_class&& other )   // move construction  
        : data( move( other.data ) ) { }  
    my_class& operator=( my_class&& other )   // move assignment  
    { data = move( other.data ); return *this; }  
    // ...  
    void method() {   // check (if appropriate)  
        if( !data )   
            throw std::runtime_error("RUNTIME ERROR: Insufficient resources!");  
    }  
};  
  
```  
  
 如果使复制构造\/分配，也不允许构造\/移动分配，则可能修复的深层复制。  
  
 这些 *非值* 类型是移动，例如，您无法克隆资源时，只有所有权。  示例：`unique_ptr`。  
  
## 节  
 内容  
  
## 请参阅  
 [C\+\+ 类型系统](../cpp/cpp-type-system-modern-cpp.md)   
 [欢迎回到 C\+\+](../cpp/welcome-back-to-cpp-modern-cpp.md)   
 [C\+\+ 语言参考](../cpp/cpp-language-reference.md)   
 [C\+\+ 标准库](../standard-library/cpp-standard-library-reference.md)
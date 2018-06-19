---
title: 值类型 （现代 C++） |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: f63bb62c-60da-40d5-ac14-4366608fe260
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: e7e49c97bca86b8d2debde2f5b132f7dde16998e
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
ms.locfileid: "32423413"
---
# <a name="value-types-modern-c"></a>值类型（现代 C++）
C++ 类是由默认值类型。 本主题提供介绍性概述的值类型和与其使用相关的问题。  
  
## <a name="value-vs-reference-types"></a>值与引用类型  
 如前面所述，C++ 类是由默认值类型。 它们可以指定为引用类型，实现多态行为以支持面向对象的编程。 有时从内存和布局控制的角度查看值类型，而引用类型的多态的目的是有关基类和虚拟函数。 默认情况下，值类型是可复制，这意味着没有始终复制构造函数和复制赋值运算符。 对于引用类型，您使类不可复制 （禁用复制构造函数和复制赋值运算符） 和使用虚拟的析构函数，它支持其预期的多态性。 值类型也是有关的内容，这，它们复制时，始终让你可以单独修改的两个独立值。 有关标识-哪种类型的对象是它有引用类型？ 因此，"引用类型"也称为"多态类型"。  
  
 如果你确实想类似引用的类型 （基类、 虚函数），你需要显式禁用复制中, 所示`MyRefType`下面的代码中的类。  
  
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
  
 编译上面的代码将导致以下错误：  
  
```Output  
test.cpp(15) : error C2248: 'MyRefType::operator =' : cannot access private member declared in class 'MyRefType'  
        meow.cpp(5) : see declaration of 'MyRefType::operator ='  
        meow.cpp(3) : see declaration of 'MyRefType'  
  
```  
  
## <a name="value-types-and-move-efficiency"></a>值类型和移动效率  
 由于新副本优化就避免复制分配系统开销。 例如，当插入中间的字符串向量的字符串时，将有副本重新分配开销，仅移动-即使导致向量本身的增加。 这也适用于其他操作，例如执行添加操作在两个非常大的对象。 如何启用这些值操作优化？ 在某些 C++ 编译器，编译器将启用这为你隐式一样可以由编译器自动生成复制构造函数。 但是，在 Visual C++，您的类将需要"选择加入"将通过声明在类定义的分配和构造函数。 这可以通过使用双与号 (& &) 右值引用在相应的成员函数声明和定义的移动构造函数和移动赋值方法。  你还需要插入正确的代码以超出源对象的"窃用具体编码"。  
  
 如何决定是否您需要移动启用？ 如果你已经知道需要复制启用的构造，你可能希望移动已启用，是否可以将其价格低于的深层副本。 但是，如果你知道需要移动支持，它并不一定意味着你需要启用的副本。 "仅移动类型"，将调用此后一种情况。 已在标准库的一个示例是`unique_ptr`。 注意，旧`auto_ptr`已弃用，并已被取代`unique_ptr`精确由于缺乏 C++ 早期版本中的移动语义支持。  
  
 通过使用移动语义中，你可以返回的值或插入的中部。 移动是副本的一种优化。 就需堆分配一种解决方法。 请看下面的伪代码：  
  
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
  
### <a name="enabling-move-for-appropriate-value-types"></a>启用适当的值类型的移动  
 对于类似于值的类，其中移动可以是价格低于的深层副本，启用的移动构造和移动赋值为提高效率。 请看下面的伪代码：  
  
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
  
 如果你启用复制构造/赋值，还启用移动构造/赋值，如果它可以是价格低于的深层副本。  
  
 某些*非值*类型是只移动的如当无法克隆资源，仅传输所有权。 示例：`unique_ptr`。  
  
## <a name="section"></a>节  
 内容  
  
## <a name="see-also"></a>请参阅  
 [C++ 类型系统](../cpp/cpp-type-system-modern-cpp.md)   
 [欢迎回到 C++](../cpp/welcome-back-to-cpp-modern-cpp.md)   
 [C++ 语言参考](../cpp/cpp-language-reference.md)   
 [C++ 标准库](../standard-library/cpp-standard-library-reference.md)
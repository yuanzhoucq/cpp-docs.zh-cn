---
title: "deque 类 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "std.deque"
  - "deque"
  - "std::deque"
  - "deque/std::deque"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "deque 类，关于 deque 类"
  - "deque 类"
ms.assetid: 64842ee5-057a-4063-8c16-4267a0332584
caps.latest.revision: 22
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 23
---
# deque 类
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

对线性排列中给定类型的元素进行排序，并且类似于矢量，允许快速随机访问任何元素并在容器后面高效插入和删除。 但是，和矢量不同的是，`deque` 类还支持在容器前面高效插入和删除。  
  
## <a name="syntax"></a>语法  
  
```unstlib  
template <class Type,   
    class Allocator =allocator<Type>>  
class deque  
```  
  
#### <a name="parameters"></a>参数  
 `Type`  
 要存储在 deque 中的元素数据类型。  
  
 `Allocator`  
 表示所存储分配器对象的类型，该分配器对象封装有关 deque 的内存分配和解除分配的详细信息。 此参数是可选的而默认值是 **分配器 \< 类型>***。*  
  
## <a name="remarks"></a>备注  
 容器类型选择通常应根据应用程序所需的搜索和插入的类型。 [向量](../standard-library/vector-class.md) 应该是当对任何元素的随机访问超出限制并且插入或删除元素时仅管理序列的首选的容器要求在序列末尾。 List 容器的性能，是上级时高效插入和删除序列内任何位置 （以常量时间） 值得称道。 序列中间的此类操作需要元素副本和与序列中的元素数量成正比的分配（线性时间）。  
  
 当成员函数必须插入或清除序列中的元素时，将发生 deque 的重新分配：  
  
-   如果一个元素插入到一个空序列，或者如果某个元素将擦除留空序列，然后迭代器前面由 [开始](#deque__begin) 和 [结束](#deque__end) 变得无效。  
  
-   如果在 deque 的第一个位置插入一个元素，则所有指定现有元素的迭代器（但没有引用）将变为无效。  
  
-   如果一个元素插入末尾的 e q u e，然后 [结束](#deque__end) 和所有迭代器，但没有指定的引用，都将失效的现有元素。  
  
-   如果在 deque 的前面清除元素，只有该迭代器和对已清除元素的引用变得无效。  
  
-   如果从 deque 的末尾清除最后一个元素，则仅指向最后一个元素的迭代器和对清除元素的引用将变为无效。  
  
 否则，插入或清除元素将使所有迭代器和引用失效。  
  
### <a name="constructors"></a>构造函数  
  
|||  
|-|-|  
|[e q u e](#deque__deque)|构造 `deque.` 提供了几个构造函数来设置的新内容 `deque` 以不同的方式︰ 空; 加载了指定数量的空元素; 内容已移动或复制另一个 `deque`; 内容通过复制或移动使用迭代器; 然后将一个元素复制到 `deque`` count` 时间。 一些构造函数可实现使用自定义 `allocator` 创建元素。|  
  
### <a name="typedefs"></a>Typedef  
  
|||  
|-|-|  
|[allocator_type](#deque__allocator_type)|一种类型，此类型表示 `allocator` 对象的 `deque` 类。|  
|[const_iterator](#deque__const_iterator)|一种类型，此类型提供可访问和读取 `deque` 中作为 `const` 的元素的随机访问迭代器|  
|[const_pointer](#deque__const_pointer)|一种类型，用于提供指向 `deque` 中作为 `const.` 的元素的指针|  
|[const_reference](#deque__const_reference)|一种类型，此类型提供对 `deque` 中作为 `const.` 用于读取和其他操作的元素的引用|  
|[const_reverse_iterator](#deque__const_reverse_iterator)|一种类型，此类型提供可访问和读取 `deque` 中作为 `const` 的元素的随机访问迭代器。 以相反顺序查看 deque。 有关详细信息，请参阅 [reverse_iterator 类](../standard-library/reverse-iterator-class.md)|  
|[difference_type](#deque__difference_type)|一种类型，该类型提供引用同一 `deque` 中的元素的两个随机访问迭代器之间的差异。|  
|[迭代器](#deque__iterator)|一种类型，此类型提供可读取或修改 `deque` 中的任何元素的随机访问迭代器。|  
|[指针](#deque__pointer)|一种类型，它提供指向 `deque` 中的某个元素的指针。|  
|[引用](#deque__reference)|一种类型，此类型提供对存储在 `deque` 中的元素的引用。|  
|[reverse_iterator](#deque__reverse_iterator)|一种类型，此类型提供可读取或修改 `deque` 中的某个元素的随机访问迭代器。 以相反顺序查看 deque。|  
|[size_type](#deque__size_type)|一种类型，此类型计算 `deque` 中的元素数目。|  
|[value_type](#deque__value_type)|一种类型，此类型表示存储在 `deque` 中的数据类型。|  
  
### <a name="member-functions"></a>成员函数  
  
|||  
|-|-|  
|[分配](#deque__assign)|将元素从 `deque` 中清除并将新的元素序列复制到目标 `deque`。|  
|[在](#deque__at)|返回对 `deque` 中指定位置的元素的引用。|  
|[返回](#deque__back)|返回对 `deque` 中最后一个元素的引用。|  
|[开始](#deque__begin)|返回发现 `deque` 中第一个元素的随机访问迭代器。|  
|[deque:: cbegin](#deque__cbegin)|返回一个指向 `deque` 中第一个元素的常量迭代器。|  
|[deque:: cend](#deque__cend)|返回指向刚超出 `deque` 末尾位置的随机访问 `const` 迭代器。|  
|[清除](#deque__clear)|清除 `deque` 的所有元素。|  
|[deque:: crbegin](#deque__crbegin)|返回一个指向以相反顺序查看的 `deque` 中的第一个元素的随机访问常量迭代器。|  
|[deque:: crend](#deque__crend)|返回一个指向以相反顺序查看的 `deque` 中的第一个元素的随机访问常量迭代器。|  
|[deque:: emplace](#deque__emplace)|将就地构造的元素插入到指定位置的 `deque` 中。|  
|[deque:: emplace_back](#deque__emplace_back)|将就地构造的元素添加到 `deque` 的末尾。|  
|[deque:: emplace_front](#deque__emplace_front)|将就地构造的元素添加到 `deque` 的开头。|  
|[为空](#deque__empty)|如果 `deque` 包含零个元素，则返回 `true`；如果它包含一个或多个元素，则返回 `false`。|  
|[结束](#deque__end)|返回指向刚超出 `deque` 末尾位置的随机访问迭代器。|  
|[擦除](#deque__erase)|从指定位置删除 `deque` 中一个或一系列元素。|  
|[前端](#deque__front)|返回对 `deque` 中第一个元素的引用。|  
|[get_allocator](#deque__get_allocator)|返回用于构造 `allocator` 的 `deque` 对象的副本。|  
|[插入](#deque__insert)|将一个、多个或一系列元素插入到指定位置的 `deque` 中。|  
|[max_size](#deque__max_size)|返回 `deque` 的最大可取长度。|  
|[pop_back](#deque__pop_back)|清除 `deque` 末尾处的元素。|  
|[pop_front](#deque__pop_front)|清除 `deque` 开头处的元素。|  
|[push_back](#deque__push_back)|将元素添加到 `deque` 的末尾。|  
|[push_front](#deque__push_front)|将元素添加到 `deque` 的开头。|  
|[rbegin](#deque__rbegin)|返回指向反向 `deque` 中的第一个元素的随机访问迭代器。|  
|[rend](#deque__rend)|返回指向刚超出反向 `deque` 中的最后一个元素位置的随机访问迭代器。|  
|[调整大小](#deque__resize)|为 `deque` 指定新的大小。|  
|[deque:: shrink_to_fit](#deque__shrink_to_fit)|放弃额外容量。|  
|[大小](#deque__size)|返回 `deque` 中的元素数量。|  
|[交换](#deque__swap)|交换两个 `deque` 的元素。|  
  
### <a name="operators"></a>运算符  
  
|||  
|-|-|  
|[运算符 &#91; &#93;](#deque__operator_at)|返回对指定位置的 `deque` 元素的引用。|  
|[deque:: operator =](#deque__operator_eq)|将 `deque` 的元素替换为另一个 `deque` 的副本。|  
  
## <a name="requirements"></a>要求  
 **标头**: \< q u e>  
  
##  <a name="a-namedequeallocatortypea-dequeallocatortype"></a><a name="deque__allocator_type"></a>  deque:: allocator_type  
 表示 e q u e 对象的分配器类的类型。  
  
```  
typedef Allocator allocator_type;  
```  
  
### <a name="remarks"></a>备注  
 **allocator_type** 是模板参数的同义词 **分配器**。  
  
### <a name="example"></a>示例  
  请参阅示例 [get_allocator](#deque__get_allocator)。  
  
##  <a name="a-namedequeassigna-dequeassign"></a><a name="deque__assign"></a>  deque:: assign  
 将元素从 deque 擦除并将一组新的元素复制到目标 e q u e。  
  
```  
template <class InputIterator>  
void assign(
    InputIterator First,  
    InputIterator Last);

void assign(
    size_type Count,  
    const Type& Val);

void assign(
    initializer_list<Type>  
IList);
```  
  
### <a name="parameters"></a>参数  
 `First`  
 要从参数 deque 复制的元素范围中第一个元素的位置。  
  
 `Last`  
 要从参数 deque 复制的元素范围以外的第一个元素的位置。  
  
 `Count`  
 要插入到 e q u e 元素的副本数。  
  
 `Val`  
 要插入到 e q u e 元素的值。  
  
 `IList`  
 要插入到 e q u e initializer_list。  
  
### <a name="remarks"></a>备注  
 目标 deque 中的任何现有元素会被清除之后， `assign` 插入指定的元素范围从原始 deque 或某些其他 e q u e 目标 e q u e，或指定的值的新元素的副本插入到目标 e q u e。  
  
### <a name="example"></a>示例  
  
```  
// deque_assign.cpp  
// compile with: /EHsc  
#include <deque>  
#include <iostream>  
#include <initializer_list>  
  
int main()  
{  
    using namespace std;  
    deque <int> c1, c2;  
    deque <int>::const_iterator cIter;  
  
    c1.push_back(10);  
    c1.push_back(20);  
    c1.push_back(30);  
    c2.push_back(40);  
    c2.push_back(50);  
    c2.push_back(60);  
  
    deque<int> d1{ 1, 2, 3, 4 };  
    initializer_list<int> iList{ 5, 6, 7, 8 };  
    d1.assign(iList);  
  
    cout << "d1 = ";  
    for (int i : d1)  
        cout << i;  
    cout << endl;  
  
    cout << "c1 =";  
    for (int i : c1)  
        cout << i;  
    cout << endl;  
  
    c1.assign(++c2.begin(), c2.end());  
    cout << "c1 =";  
    for (int i : c1)  
        cout << i;  
    cout << endl;  
  
    c1.assign(7, 4);  
    cout << "c1 =";  
    for (int i : c1)  
        cout << i;  
    cout << endl;  
  
}  
  
```  
  
```Output  
d1 = 5678c1 =102030c1 =5060c1 =4444444  
```  
  
##  <a name="a-namedequeata-dequeat"></a><a name="deque__at"></a>  deque:: at  
 在 e q u e 返回对指定位置处的元素的引用。  
  
```  
reference at(size_type _Pos);

const_reference at(size_type _Pos) const;
```  
  
### <a name="parameters"></a>参数  
 `_Pos`  
 下标 （或位置编号） 的元素在 e q u e 中引用。  
  
### <a name="return-value"></a>返回值  
 如果 `_Pos` 大于 e q u e，大小 **在** 将引发异常。  
  
### <a name="return-value"></a>返回值  
 如果返回值为 **在** 分配给 `const_reference`, ，e q u e 对象不能修改。 如果返回值为 **在** 分配给 **引用**, ，可以修改 e q u e 对象。  
  
### <a name="example"></a>示例  
  
```  
// deque_at.cpp  
// compile with: /EHsc  
#include <deque>  
#include <iostream>  
  
int main( )   
{  
   using namespace std;  
   deque <int> c1;  
  
   c1.push_back( 10 );  
   c1.push_back( 20 );  
  
   const int& i = c1.at( 0 );  
   int& j = c1.at( 1 );  
   cout << "The first element is " << i << endl;  
   cout << "The second element is " << j << endl;  
}  
```  
  
```Output  
The first element is 10  
The second element is 20  
```  
  
##  <a name="a-namedequebacka-dequeback"></a><a name="deque__back"></a>  deque:: back  
 返回到 e q u e 的最后一个元素的引用。  
  
```  
reference back();

const_reference back() const;
```  
  
### <a name="return-value"></a>返回值  
 E q u e 最后一个元素。 如果 e q u e 是空的则返回值不确定。  
  
### <a name="remarks"></a>备注  
 如果返回值为 **回** 分配给 `const_reference`, ，e q u e 对象不能修改。 如果返回值为 **回** 分配给 **引用**, ，可以修改 e q u e 对象。  
  
 在使用 _SECURE_SCL 1 编译时，如果试图访问空 deque 中的元素，将发生运行时错误。  有关更多信息，请参见 [Checked Iterators](../standard-library/checked-iterators.md) 。  
  
### <a name="example"></a>示例  
  
```  
// deque_back.cpp  
// compile with: /EHsc  
#include <deque>  
#include <iostream>  
  
int main( )   
{  
   using namespace std;  
   deque <int> c1;  
  
   c1.push_back( 10 );  
   c1.push_back( 11 );  
  
   int& i = c1.back( );  
   const int& ii = c1.front( );  
  
   cout << "The last integer of c1 is " << i << endl;  
   i--;  
   cout << "The next-to-last integer of c1 is " << ii << endl;  
}  
```  
  
```Output  
The last integer of c1 is 11  
The next-to-last integer of c1 is 10  
```  
  
##  <a name="a-namedequebegina-dequebegin"></a><a name="deque__begin"></a>  deque:: begin  
 返回发现 e q u e 的第一个元素的迭代器。  
  
```  
const_iterator begin() const;

iterator begin();
```  
  
### <a name="return-value"></a>返回值  
 发现第一个元素 q u e 中或之后空 e q u e 的位置的随机访问迭代器。  
  
### <a name="remarks"></a>备注  
 如果返回值为 **开始** 分配给 `const_iterator`, ，e q u e 对象不能修改。 如果返回值为 **开始** 分配给 **迭代器**, ，可以修改 e q u e 对象。  
  
### <a name="example"></a>示例  
  
```  
// deque_begin.cpp  
// compile with: /EHsc  
#include <deque>  
#include <iostream>  
  
int main( )   
{  
   using namespace std;  
   deque <int> c1;  
   deque <int>::iterator c1_Iter;  
   deque <int>::const_iterator c1_cIter;  
  
   c1.push_back( 1 );  
   c1.push_back( 2 );  
  
   c1_Iter = c1.begin( );  
   cout << "The first element of c1 is " << *c1_Iter << endl;  
  
 *c1_Iter = 20;  
   c1_Iter = c1.begin( );  
   cout << "The first element of c1 is now " << *c1_Iter << endl;  
  
   // The following line would be an error because iterator is const  
   // *c1_cIter = 200;  
}  
```  
  
```Output  
The first element of c1 is 1  
The first element of c1 is now 20  
```  
  
##  <a name="a-namedequecbegina-dequecbegin"></a><a name="deque__cbegin"></a>  deque:: cbegin  
 返回确定范围中第一个元素地址的 `const` 迭代器。  
  
```  
const_iterator cbegin() const;
```  
  
### <a name="return-value"></a>返回值  
 `const` 随机访问迭代器，指向范围的第一个元素，或刚超出空范围末尾的位置（对于空范围，`cbegin() == cend()`）。  
  
### <a name="remarks"></a>备注  
 由于使用 `cbegin` 的返回值，因此不能修改范围中的元素。  
  
 可以使用此成员函数替代 `begin()` 成员函数，以保证返回值为 `const_iterator`。 通常情况下，结合使用 [自动](../cpp/auto-cpp.md) 类型推导关键字，如下面的示例中所示。 在示例中，请考虑 `Container` 的可修改 (非 `const`) 容器支持任何种类的 `begin()` 和 `cbegin()`。  
  
```cpp  
 
auto i1 = Container.begin();
// i1 is Container<T>::iterator   
auto i2 = Container.cbegin();

// i2 is Container<T>::const_iterator  
```  
  
##  <a name="a-namedequecenda-dequecend"></a><a name="deque__cend"></a>  deque:: cend  
 返回一个 `const` 迭代器，此迭代器用于发现刚超出范围中最后一个元素的位置。  
  
```  
const_iterator cend() const;
```  
  
### <a name="return-value"></a>返回值  
 指向刚超出范围末尾的位置的随机访问迭代器。  
  
### <a name="remarks"></a>备注  
 `cend` 用于测试迭代器是否超过了其范围的末尾。  
  
 可以使用此成员函数替代 `end()` 成员函数，以保证返回值为 `const_iterator`。 通常情况下，结合使用 [自动](../cpp/auto-cpp.md) 类型推导关键字，如下面的示例中所示。 在示例中，请考虑 `Container` 的可修改 (非 `const`) 容器支持任何种类的 `end()` 和 `cend()`。  
  
```cpp  
 
auto i1 = Container.end();
// i1 is Container<T>::iterator   
auto i2 = Container.cend();

// i2 is Container<T>::const_iterator  
```  
  
 不应对 `cend` 返回的值取消引用。  
  
##  <a name="a-namedequecleara-dequeclear"></a><a name="deque__clear"></a>  deque:: clear  
 清除 e q u e 的全部的元素。  
  
```  
void clear();
```  
  
### <a name="example"></a>示例  
  
```  
// deque_clear.cpp  
// compile with: /EHsc  
#include <deque>  
#include <iostream>  
  
int main( )   
{  
   using namespace std;  
   deque <int> c1;  
  
   c1.push_back( 10 );  
   c1.push_back( 20 );  
   c1.push_back( 30 );  
  
   cout << "The size of the deque is initially " << c1.size( ) << endl;  
   c1.clear( );  
   cout << "The size of the deque after clearing is " << c1.size( ) << endl;  
}  
```  
  
```Output  
The size of the deque is initially 3  
The size of the deque after clearing is 0  
```  
  
##  <a name="a-namedequeconstiteratora-dequeconstiterator"></a><a name="deque__const_iterator"></a>  deque:: const_iterator  
 提供的随机访问迭代器的类型可访问和读取 **const** e q u e 中的元素。  
  
```  
typedef implementation-defined const_iterator;  
```  
  
### <a name="remarks"></a>备注  
 `const_iterator` 类型不能用于修改元素的值。  
  
### <a name="example"></a>示例  
  请参阅示例 [回](#deque__back)。  
  
##  <a name="a-namedequeconstpointera-dequeconstpointer"></a><a name="deque__const_pointer"></a>  deque:: const_pointer  
 提供指向 deque 中 `const` 元素的指针。  
  
```unstlib  
typedef typename Allocator::const_pointer const_pointer;  
```  
  
### <a name="remarks"></a>备注  
 `const_pointer` 类型不能用于修改元素的值。  [迭代器](#deque__iterator) 更常用于访问 deque 元素。  
  
##  <a name="a-namedequeconstreferencea-dequeconstreference"></a><a name="deque__const_reference"></a>  deque:: const_reference  
 提供对引用的类型 **const** 元素存储在用于读取和执行 deque **const** 操作。  
  
```  
typedef typename Allocator::const_reference const_reference;  
```  
  
### <a name="remarks"></a>备注  
 `const_reference` 类型不能用于修改元素的值。  
  
### <a name="example"></a>示例  
  
```  
// deque_const_ref.cpp  
// compile with: /EHsc  
#include <deque>  
#include <iostream>  
  
int main( )   
{  
   using namespace std;  
   deque <int> c1;  
  
   c1.push_back( 10 );  
   c1.push_back( 20 );  
  
   const deque <int> c2 = c1;  
   const int &i = c2.front( );  
   const int &j = c2.back( );  
   cout << "The first element is " << i << endl;  
   cout << "The second element is " << j << endl;  
  
   // The following line would cause an error as c2 is const  
   // c2.push_back( 30 );  
}  
```  
  
```Output  
The first element is 10  
The second element is 20  
```  
  
##  <a name="a-namedequeconstreverseiteratora-dequeconstreverseiterator"></a><a name="deque__const_reverse_iterator"></a>  deque:: const_reverse_iterator  
 一种提供随机访问迭代器可读取任何 **const** e q u e 中的元素。  
  
```  
typedef std::reverse_iterator<const_iterator> const_reverse_iterator;  
```  
  
### <a name="remarks"></a>备注  
 一种类型 `const_reverse_iterator` 无法修改元素的值，用于循环访问 e q u e 按相反的顺序。  
  
### <a name="example"></a>示例  
  请参阅示例 [rbegin](#deque__rbegin) 以举例说明如何声明和使用迭代器。  
  
##  <a name="a-namedequecrbegina-dequecrbegin"></a><a name="deque__crbegin"></a>  deque:: crbegin  
 返回发现反向 deque 中的第一个元素的常量迭代器。  
  
```  
const_reverse_iterator crbegin() const;
```  
  
### <a name="return-value"></a>返回值  
 一个常量反向随机访问迭代器定址反向的第一个元素 [e q u e](../standard-library/deque-class.md) 或发现曾是非反向的最后一个元素 `deque`。  
  
### <a name="remarks"></a>备注  
 返回值为 `crbegin` 时，无法修改 `deque` 对象。  
  
### <a name="example"></a>示例  
  
```  
// deque_crbegin.cpp  
// compile with: /EHsc  
#include <deque>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;     
   deque <int> v1;  
   deque <int>::iterator v1_Iter;  
   deque <int>::const_reverse_iterator v1_rIter;  
  
   v1.push_back( 1 );  
   v1.push_back( 2 );  
  
   v1_Iter = v1.begin( );  
   cout << "The first element of deque is "  
        << *v1_Iter << "." << endl;  
  
   v1_rIter = v1.crbegin( );  
   cout << "The first element of the reversed deque is "  
        << *v1_rIter << "." << endl;  
}  
```  
  
```Output  
The first element of deque is 1.  
The first element of the reversed deque is 2.  
```  
  
##  <a name="a-namedequecrenda-dequecrend"></a><a name="deque__crend"></a>  deque:: crend  
 返回发现反向 deque 中的最后一个元素之后的位置的常量迭代器。  
  
```  
const_reverse_iterator crend() const;
```  
  
### <a name="return-value"></a>返回值  
 一个常量反向随机访问迭代器，此迭代中发现反向最后一个元素之后的位置 [e q u e](../standard-library/deque-class.md) （非反向 deque 中的第一个元素之前的位置）。  
  
### <a name="remarks"></a>备注  
 `crend` 使用与反向 `deque` 就像 [array::cend](../standard-library/array-class-stl.md#array__cend) 与使用 `deque`。  
  
 返回值为 `crend` （适当递减）， `deque` 对象不能修改。  
  
 `crend` 可以用于测试反向迭代器是否已到达其 e q u e 的末尾。  
  
 不应对 `crend` 返回的值取消引用。  
  
### <a name="example"></a>示例  
  
```  
// deque_crend.cpp  
// compile with: /EHsc  
#include <deque>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;     
   deque <int> v1;  
   deque <int>::const_reverse_iterator v1_rIter;  
  
   v1.push_back( 1 );  
   v1.push_back( 2 );  
  
   for ( v1_rIter = v1.rbegin( ) ; v1_rIter != v1.rend( ) ; v1_rIter++ )  
      cout << *v1_rIter << endl;  
}  
```  
  
```Output  
2  
1  
```  
  
##  <a name="a-namedequedequea-dequedeque"></a><a name="deque__deque"></a>  deque:: deque  
 构造，它具有特定大小或它的元素具有特定值或具有特定分配器，或作为的全部或部分副本的某些其他 e q u e d e q。  
  
```  
deque();

explicit deque(
    const Allocator& Al);

explicit deque(
    size_type Count);

deque(
    size_type Count,  
    const Type& Val);

deque(
    size_type Count,  
    const Type& Val,  
    const Allocator& Al);

deque(
    const deque& Right);

template <class InputIterator>  
deque(
 InputIterator First,  
    InputIterator Last);

template <class InputIterator>  
deque(
 InputIterator First,  
    InputIterator Last,  
    const Allocator& Al);

deque(
    initializer_list<value_type>  
IList,  
    const Allocator& Al);
```  
  
### <a name="parameters"></a>参数  
  
|||  
|-|-|  
|参数|描述|  
|`Al`|要用于此对象的分配器类。|  
|`Count`|构造 deque 中的元素数。|  
|`Val`|在构造 deque 元素的值。|  
|`Right`|E q u e 构造的 deque 的要成为副本。|  
|`First`|要复制的元素范围内的第一个元素的位置。|  
|`Last`|要复制的元素范围外的第一个元素的位置。|  
|`IList`|要复制 initializer_list。|  
  
### <a name="remarks"></a>备注  
 所有构造函数都会存储一个分配器对象 ( `Al`) 并初始化 e q u e。  
  
 前两个构造函数指定空的初始 deque;第二个还指定分配器类型 ( `_Al`) 使用。  
  
 第三个构造函数指定的指定数量的重复 ( ` count`) 的元素的默认值为类 `Type`。  
  
 第四个和第五个构造函数指定的重复 ( `Count`) 值的元素 ` val`。  
  
 第六个构造函数指定一份 e q u e `Right`。  
  
 第七个和第八个构造函数复制范围 `[First, Last)` 的 e q u e。  
  
 第七个构造函数移动 e q u e `Right`。  
  
 第八个构造函数复制 initializer_list 的内容。  
  
 所有构造函数均不执行任何临时重新分配。  
  
### <a name="example"></a>示例  
  
```  
/ compile with: /EHsc  
#include <deque>  
#include <iostream>  
#include <forward_list>  
  
int main()  
{  
    using namespace std;  
  
    forward_list<int> f1{ 1, 2, 3, 4 };  
  
    f1.insert_after(f1.begin(), { 5, 6, 7, 8 });  
  
    deque <int>::iterator c1_Iter, c2_Iter, c3_Iter, c4_Iter, c5_Iter, c6_Iter;  
  
    // Create an empty deque c0  
    deque <int> c0;  
  
    // Create a deque c1 with 3 elements of default value 0  
    deque <int> c1(3);  
  
    // Create a deque c2 with 5 elements of value 2  
    deque <int> c2(5, 2);  
  
    // Create a deque c3 with 3 elements of value 1 and with the   
    // allocator of deque c2  
    deque <int> c3(3, 1, c2.get_allocator());  
  
    // Create a copy, deque c4, of deque c2  
    deque <int> c4(c2);  
  
    // Create a deque c5 by copying the range c4[ first,  last)  
    c4_Iter = c4.begin();  
    c4_Iter++;  
    c4_Iter++;  
    deque <int> c5(c4.begin(), c4_Iter);  
  
    // Create a deque c6 by copying the range c4[ first,  last) and   
    // c2 with the allocator of deque  
    c4_Iter = c4.begin();  
    c4_Iter++;  
    c4_Iter++;  
    c4_Iter++;  
    deque <int> c6(c4.begin(), c4_Iter, c2.get_allocator());  
  
    // Create a deque c8 by copying the contents of an initializer_list  
    // using brace initialization  
    deque<int> c8({ 1, 2, 3, 4 });  
  
    initializer_list<int> iList{ 5, 6, 7, 8 };  
    deque<int> c9( iList);  
  
    cout << "c1 = ";  
    for (int i : c1)  
        cout << i << " ";  
    cout << endl;  
  
    cout << "c2 = ";  
    for (int i : c2)  
        cout << i << " ";  
    cout << endl;  
  
    cout << "c3 = ";  
    for (int i : c3)  
        cout << i << " ";  
    cout << endl;  
  
    cout << "c4 = ";  
    for (int i : c4)  
        cout << i << " ";  
    cout << endl;  
  
    cout << "c5 = ";  
    for (int i : c5)  
        cout << i << " ";  
    cout << endl;  
  
    cout << "c6 = ";  
    for (int i : c6)  
        cout << i << " ";  
    cout << endl;  
  
    // Move deque c6 to deque c7  
    deque <int> c7(move(c6));  
    deque <int>::iterator c7_Iter;  
  
    cout << "c7 =";  
    for (int i : c7)  
        cout << i << " ";  
    cout << endl;  
  
    cout << "c8 = ";  
    for (int i : c8)  
        cout << i << " ";  
    cout << endl;  
  
    cout << "c9 = ";  
    for (int i : c9)  
        cout << i << " ";  
    cout << endl;  
  
    int x = 3;  
}  
// deque_deque.cpp  
// compile with: /EHsc  
#include <deque>  
#include <iostream>  
  
int main( )   
{  
    using namespace std;  
   deque <int>::iterator c1_Iter, c2_Iter, c3_Iter, c4_Iter, c5_Iter, c6_Iter;  
  
    // Create an empty deque c0  
    deque <int> c0;  
  
    // Create a deque c1 with 3 elements of default value 0  
    deque <int> c1( 3 );  
  
    // Create a deque c2 with 5 elements of value 2  
    deque <int> c2( 5, 2 );  
  
    // Create a deque c3 with 3 elements of value 1 and with the   
    // allocator of deque c2  
    deque <int> c3( 3, 1, c2.get_allocator( ) );  
  
    // Create a copy, deque c4, of deque c2  
    deque <int> c4( c2 );  
  
    // Create a deque c5 by copying the range c4[ first,  last)  
    c4_Iter = c4.begin( );  
    c4_Iter++;  
    c4_Iter++;  
    deque <int> c5( c4.begin( ), c4_Iter );  
  
    // Create a deque c6 by copying the range c4[ first,  last) and   
    // c2 with the allocator of deque  
    c4_Iter = c4.begin( );  
   c4_Iter++;  
   c4_Iter++;  
   c4_Iter++;  
   deque <int> c6( c4.begin( ), c4_Iter, c2.get_allocator( ) );  
  
    // Create a deque c8 by copying the contents of an initializer_list  
    // using brace initialization  
    deque<int> c8({ 1, 2, 3, 4 });  
  
        initializer_list<int> iList{ 5, 6, 7, 8 };  
    deque<int> c9( iList);  
  
    cout << "c1 = ";  
    for ( c1_Iter = c1.begin( ); c1_Iter != c1.end( ); c1_Iter++ )  
        cout << *c1_Iter << " ";  
    cout << endl;  
  
    cout << "c2 = ";  
    for ( c2_Iter = c2.begin( ); c2_Iter != c2.end( ); c2_Iter++ )  
        cout << *c2_Iter << " ";  
    cout << endl;  
  
    cout << "c3 = ";  
    for ( c3_Iter = c3.begin( ); c3_Iter != c3.end( ); c3_Iter++ )  
        cout << *c3_Iter << " ";  
    cout << endl;  
  
    cout << "c4 = ";  
    for ( c4_Iter = c4.begin( ); c4_Iter != c4.end( ); c4_Iter++ )  
        cout << *c4_Iter << " ";  
    cout << endl;  
  
    cout << "c5 = ";  
    for ( c5_Iter = c5.begin( ); c5_Iter != c5.end( ); c5_Iter++ )  
        cout << *c5_Iter << " ";  
    cout << endl;  
  
    cout << "c6 = ";  
    for ( c6_Iter = c6.begin( ); c6_Iter != c6.end( ); c6_Iter++ )  
        cout << *c6_Iter << " ";  
    cout << endl;  
  
    // Move deque c6 to deque c7  
    deque <int> c7( move(c6) );  
    deque <int>::iterator c7_Iter;  
  
    cout << "c7 =" ;  
    for ( c7_Iter = c7.begin( ) ; c7_Iter != c7.end( ) ; c7_Iter++ )  
        cout << " " << *c7_Iter;  
    cout << endl;  
  
    cout << "c8 = ";  
    for (int i : c8)  
        cout << i << " ";  
    cout << endl;  
  
    cout << "c9 = ";  
    or (int i : c9)  
        cout << i << " ";  
    cout << endl;  
}  
```  
  
##  <a name="a-namedequedifferencetypea-dequedifferencetype"></a><a name="deque__difference_type"></a>  deque:: difference_type  
 提供引用同一 deque 中的元素的两个迭代之间的差异的类型。  
  
```  
typedef typename Allocator::difference_type difference_type;  
```  
  
### <a name="remarks"></a>备注  
 `difference_type` 也可以被描述为两个指针之间的元素数目。  
  
### <a name="example"></a>示例  
  
```  
// deque_diff_type.cpp  
// compile with: /EHsc  
#include <iostream>  
#include <deque>  
#include <algorithm>  
  
int main( )   
{  
   using namespace std;  
  
   deque <int> c1;  
   deque <int>::iterator c1_Iter, c2_Iter;  
  
   c1.push_back( 30 );  
   c1.push_back( 20 );  
   c1.push_back( 30 );  
   c1.push_back( 10 );  
   c1.push_back( 30 );  
   c1.push_back( 20 );  
  
   c1_Iter = c1.begin( );  
   c2_Iter = c1.end( );  
  
   deque <int>::difference_type df_typ1, df_typ2, df_typ3;  
  
   df_typ1 = count( c1_Iter, c2_Iter, 10 );  
   df_typ2 = count( c1_Iter, c2_Iter, 20 );  
   df_typ3 = count( c1_Iter, c2_Iter, 30 );  
   cout << "The number '10' is in c1 collection " << df_typ1 << " times.\n";  
   cout << "The number '20' is in c1 collection " << df_typ2 << " times.\n";  
   cout << "The number '30' is in c1 collection " << df_typ3 << " times.\n";  
}  
```  
  
```Output  
The number '10' is in c1 collection 1 times.  
The number '20' is in c1 collection 2 times.  
The number '30' is in c1 collection 3 times.  
```  
  
##  <a name="a-namedequeemplacea-dequeemplace"></a><a name="deque__emplace"></a>  deque:: emplace  
 插入到指定位置处 deque 就地构造的元素。  
  
```  
iterator emplace(
    const_iterator _Where,  
    Type&& val);
```  
  
### <a name="parameters"></a>参数  
  
|||  
|-|-|  
|参数|描述|  
|`_Where`|中的位置 [e q u e](../standard-library/deque-class.md) 插入的第一个元素的位置。|  
|` val`|插入到 `deque` 中的元素的值。|  
  
### <a name="return-value"></a>返回值  
 该函数将返回一个迭代器，指向将新元素插入 e q u e 处的位置。  
  
### <a name="remarks"></a>备注  
 任何插入操作可以产生巨额费用，请参阅 `deque` 有关的讨论 `deque` 性能。  
  
### <a name="example"></a>示例  
  
```  
// deque_emplace.cpp  
// compile with: /EHsc  
#include <deque>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;     
   deque <int> v1;  
   deque <int>::iterator Iter;  
  
   v1.push_back( 10 );  
   v1.push_back( 20 );  
   v1.push_back( 30 );  
  
   cout << "v1 =" ;  
   for ( Iter = v1.begin( ) ; Iter != v1.end( ) ; Iter++ )  
      cout << " " << *Iter;  
   cout << endl;  
  
// initialize a deque of deques by moving v1  
   deque < deque <int> > vv1;  
  
   vv1.emplace( vv1.begin(), move( v1 ) );  
   if ( vv1.size( ) != 0 && vv1[0].size( ) != 0 )  
      {  
      cout << "vv1[0] =";  
      for (Iter = vv1[0].begin( ); Iter != vv1[0].end( ); Iter++ )  
         cout << " " << *Iter;  
      cout << endl;  
      }  
}  
```  
  
```Output  
v1 = 10 20 30  
vv1[0] = 10 20 30  
```  
  
##  <a name="a-namedequeemplacebacka-dequeemplaceback"></a><a name="deque__emplace_back"></a>  deque:: emplace_back  
 添加到 e q u e 末尾就地构造的元素。  
  
```  
void emplace_back(Type&& val);
```  
  
### <a name="parameters"></a>参数  
  
|||  
|-|-|  
|参数|描述|  
|` val`|添加到末尾的元素 [e q u e](../standard-library/deque-class.md)。|  
  
### <a name="example"></a>示例  
  
```  
// deque_emplace_back.cpp  
// compile with: /EHsc  
#include <deque>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;     
   deque <int> v1;  
  
   v1.push_back( 1 );  
   if ( v1.size( ) != 0 )  
      cout << "Last element: " << v1.back( ) << endl;  
  
   v1.push_back( 2 );  
   if ( v1.size( ) != 0 )  
      cout << "New last element: " << v1.back( ) << endl;  
  
// initialize a deque of deques by moving v1  
   deque < deque <int> > vv1;  
  
   vv1.emplace_back( move( v1 ) );  
   if ( vv1.size( ) != 0 && vv1[0].size( ) != 0 )  
      cout << "Moved last element: " << vv1[0].back( ) << endl;  
}  
```  
  
```Output  
Last element: 1  
New last element: 2  
Moved last element: 2  
```  
  
##  <a name="a-namedequeemplacefronta-dequeemplacefront"></a><a name="deque__emplace_front"></a>  deque:: emplace_front  
 添加到 e q u e 末尾就地构造的元素。  
  
```  
void emplace_front(Type&& val);
```  
  
### <a name="parameters"></a>参数  
  
|||  
|-|-|  
|参数|描述|  
|` val`|添加到开始处的元素 [e q u e](../standard-library/deque-class.md)。|  
  
### <a name="example"></a>示例  
  
```  
// deque_emplace_front.cpp  
// compile with: /EHsc  
#include <deque>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;     
   deque <int> v1;  
  
   v1.push_back( 1 );  
   if ( v1.size( ) != 0 )  
      cout << "Last element: " << v1.back( ) << endl;  
  
   v1.push_back( 2 );  
   if ( v1.size( ) != 0 )  
      cout << "New last element: " << v1.back( ) << endl;  
  
// initialize a deque of deques by moving v1  
   deque < deque <int> > vv1;  
  
   vv1.emplace_front( move( v1 ) );  
   if ( vv1.size( ) != 0 && vv1[0].size( ) != 0 )  
      cout << "Moved last element: " << vv1[0].back( ) << endl;  
}  
```  
  
```Output  
Last element: 1  
New last element: 2  
Moved last element: 2  
```  
  
##  <a name="a-namedequeemptya-dequeempty"></a><a name="deque__empty"></a>  deque:: empty  
 测试 e q u e 是否为空。  
  
```  
bool empty() const;
```  
  
### <a name="return-value"></a>返回值  
 **true** e q u e 是否为空; **false** e q u e 是否不为空。  
  
### <a name="example"></a>示例  
  
```  
// deque_empty.cpp  
// compile with: /EHsc  
#include <deque>  
#include <iostream>  
  
int main( )   
{  
   using namespace std;  
   deque <int> c1;  
  
   c1.push_back( 10 );  
   if ( c1.empty( ) )  
      cout << "The deque is empty." << endl;  
   else  
      cout << "The deque is not empty." << endl;  
}  
```  
  
```Output  
The deque is not empty.  
```  
  
##  <a name="a-namedequeenda-dequeend"></a><a name="deque__end"></a>  deque:: end  
 返回发现 deque 中的最后一个元素之后的位置的迭代器。  
  
```  
const_iterator end() const;

iterator end();
```  
  
### <a name="return-value"></a>返回值  
 用于 deque 中的最后一个元素之后的位置的随机访问迭代器。 如果 e q u e 为空，则 deque:: end = = deque:: begin。  
  
### <a name="remarks"></a>备注  
 **结束** 用于测试是否迭代器已到达其 e q u e 的末尾。  
  
### <a name="example"></a>示例  
  
```  
// deque_end.cpp  
// compile with: /EHsc  
#include <deque>  
#include <iostream>  
  
int main( )   
{  
   using namespace std;  
   deque <int> c1;  
   deque <int>::iterator c1_Iter;  
  
   c1.push_back( 10 );  
   c1.push_back( 20 );  
   c1.push_back( 30 );  
  
   c1_Iter = c1.end( );  
   c1_Iter--;  
   cout << "The last integer of c1 is " << *c1_Iter << endl;  
  
   c1_Iter--;  
 *c1_Iter = 400;  
   cout << "The new next-to-last integer of c1 is " << *c1_Iter << endl;  
  
   // If a const iterator had been declared instead with the line:  
   // deque <int>::const_iterator c1_Iter;  
   // an error would have resulted when inserting the 400  
  
   cout << "The deque is now:";  
   for ( c1_Iter = c1.begin( ); c1_Iter != c1.end( ); c1_Iter++ )  
      cout << " " << *c1_Iter;  
}  
```  
  
```Output  
The last integer of c1 is 30  
The new next-to-last integer of c1 is 400  
The deque is now: 10 400 30  
```  
  
##  <a name="a-namedequeerasea-dequeerase"></a><a name="deque__erase"></a>  deque:: erase  
 在 e q u e 的指定位置移除一个元素或一系列元素。  
  
```  
iterator erase(iterator _Where);

iterator erase(iterator first, iterator last);
```  
  
### <a name="parameters"></a>参数  
 `_Where`  
 要从 e q u e 中移除的元素的位置。  
  
 ` first`  
 从 e q u e 移除的第一个元素的位置。  
  
 ` last`  
 从 e q u e 移除的刚超出最后一个元素的位置。  
  
### <a name="return-value"></a>返回值  
 指定已移除，任何元素之外保留的第一个元素的随机访问迭代器或指向 deque 如果不存在此元素的末尾的指针。  
  
### <a name="remarks"></a>备注  
 有关详细信息 **擦除**, ，请参阅 [deque:: erase 和 deque:: clear](../misc/deque-erase-and-deque-clear.md)。  
  
 **擦除** 永远不会引发异常。  
  
### <a name="example"></a>示例  
  
```  
// deque_erase.cpp  
// compile with: /EHsc  
#include <deque>  
#include <iostream>  
  
int main( )   
{  
   using namespace std;  
   deque <int> c1;  
   deque <int>::iterator Iter;  
  
   c1.push_back( 10 );  
   c1.push_back( 20 );  
   c1.push_back( 30 );  
   c1.push_back( 40 );  
   c1.push_back( 50 );  
   cout << "The initial deque is: ";  
   for ( Iter = c1.begin( ); Iter != c1.end( ); Iter++ )  
      cout << *Iter << " ";  
   cout << endl;  
   c1.erase( c1.begin( ) );  
   cout << "After erasing the first element, the deque becomes:  ";  
   for ( Iter = c1.begin( ); Iter != c1.end( ); Iter++ )  
      cout << *Iter << " ";  
   cout << endl;  
   Iter = c1.begin( );  
   Iter++;  
   c1.erase( Iter, c1.end( ) );  
   cout << "After erasing all elements but the first, deque becomes: ";  
   for ( Iter = c1.begin( ); Iter != c1.end( ); Iter++ )  
      cout << *Iter << " ";  
   cout << endl;  
}  
```  
  
```Output  
The initial deque is: 10 20 30 40 50   
After erasing the first element, the deque becomes:  20 30 40 50   
After erasing all elements but the first, deque becomes: 20   
```  
  
##  <a name="a-namedequefronta-dequefront"></a><a name="deque__front"></a>  deque:: front  
 Deque 中返回的第一个元素的引用。  
  
```  
reference front();

const_reference front() const;
```  
  
### <a name="return-value"></a>返回值  
 如果 e q u e 为空，则返回值未定义。  
  
### <a name="remarks"></a>备注  
 如果返回值为 `front` 分配给 `const_reference`, ，e q u e 对象不能修改。 如果返回值为 `front` 分配给 **引用**, ，可以修改 e q u e 对象。  
  
 在使用 _SECURE_SCL 1 编译时，如果试图访问空 deque 中的元素，将发生运行时错误。  有关更多信息，请参见 [Checked Iterators](../standard-library/checked-iterators.md) 。  
  
### <a name="example"></a>示例  
  
```  
// deque_front.cpp  
// compile with: /EHsc  
#include <deque>  
#include <iostream>  
  
int main( )   
{  
   using namespace std;  
   deque <int> c1;  
  
   c1.push_back( 10 );  
   c1.push_back( 11 );  
  
   int& i = c1.front( );  
   const int& ii = c1.front( );  
  
   cout << "The first integer of c1 is " << i << endl;  
   i++;  
   cout << "The second integer of c1 is " << ii << endl;  
}  
```  
  
```Output  
The first integer of c1 is 10  
The second integer of c1 is 11  
```  
  
##  <a name="a-namedequegetallocatora-dequegetallocator"></a><a name="deque__get_allocator"></a>  deque:: get_allocator  
 返回用于构造 e q u e 的分配器对象的副本。  
  
```  
Allocator get_allocator() const;
```  
  
### <a name="return-value"></a>返回值  
 使用 e q u e 的分配器。  
  
### <a name="remarks"></a>备注  
 Deque 类的分配器指定类管理存储的方式。 STL 容器类提供的默认分配器足以满足大多编程需求。 编写和使用你自己的分配器类是高级 C++ 主题。  
  
### <a name="example"></a>示例  
  
```  
// deque_get_allocator.cpp  
// compile with: /EHsc  
#include <deque>  
#include <iostream>  
  
int main( )   
{  
   using namespace std;  
   // The following lines declare objects that use the default allocator.  
   deque <int> c1;  
   deque <int, allocator<int> > c2 = deque <int, allocator<int> >( allocator<int>( ) );  
  
   // c3 will use the same allocator class as c1  
   deque <int> c3( c1.get_allocator( ) );  
  
   deque <int>::allocator_type xlst = c1.get_allocator( );  
   // You can now call functions on the allocator class used by c1  
}  
```  
  
##  <a name="a-namedequeinserta-dequeinsert"></a><a name="deque__insert"></a>  deque:: insert  
 将一个元素或大量元素范围插入到 e q u e 中的指定位置。  
  
```  
iterator insert(
    const_iterator Where,  
    const Type& Val);

iterator insert(
    const_iterator Where,  
    Type&& Val);

void insert(
    iterator Where,  
    size_type Count,  
    const Type& Val);

template <class InputIterator>  
void insert(
    iterator Where,  
    InputIterator First,  
    InputIterator Last);

iterator insert(
    iterator Where,initializer_list<Type>  
IList);
```  
  
### <a name="parameters"></a>参数  
  
|||  
|-|-|  
|参数|描述|  
|`Where`|在目标 deque 其中插入的第一个元素的位置。|  
|`Val`|要插入到 e q u e 元素的值。|  
|`Count`|要插入到 e q u e 的元素数。|  
|`First`|中的参数 deque 要复制的元素范围的第一个元素的位置。|  
|`Last`|中参数 deque 要复制的元素范围以外的第一个元素的位置。|  
|`IList`|要插入元素的 initializer_list。|  
  
### <a name="return-value"></a>返回值  
 前两个插入函数返回的迭代器指向将新元素插入 e q u e 处的位置。  
  
### <a name="remarks"></a>备注  
 任何插入操作可能很昂贵。  
  
##  <a name="a-namedequeiteratora-dequeiterator"></a><a name="deque__iterator"></a>  deque:: iterator  
 提供可读取或修改 deque 中的任何元素的随机访问迭代器的类型。  
  
```  
typedef implementation-defined iterator;  
```  
  
### <a name="remarks"></a>备注  
 一种类型 **迭代器** 可以用于修改元素的值。  
  
### <a name="example"></a>示例  
  请参阅示例 [开始](#deque__begin)。  
  
##  <a name="a-namedequemaxsizea-dequemaxsize"></a><a name="deque__max_size"></a>  deque:: max_size  
 返回 e q u e 的最大长度。  
  
```  
size_type max_size() const;
```  
  
### <a name="return-value"></a>返回值  
 E q u e 最大可能长度。  
  
### <a name="example"></a>示例  
  
```  
// deque_max_size.cpp  
// compile with: /EHsc  
#include <deque>  
#include <iostream>  
  
int main( )   
{  
   using namespace std;  
   deque <int> c1;  
   deque <int>::size_type i;  
  
   i = c1.max_size( );  
   cout << "The maximum possible length of the deque is " << i << "." << endl;  
}  
```  
  
##  <a name="a-namedequeoperatorata-dequeoperator"></a><a name="deque__operator_at"></a>  deque:: operator]  
 返回对指定位置处的 e q u e 元素的引用。  
  
```  
reference operator[](size_type _Pos);

const_reference operator[](size_type _Pos) const;
```  
  
### <a name="parameters"></a>参数  
 `_Pos`  
 Deque 元素中引用的位置。  
  
### <a name="return-value"></a>返回值  
 对参数中指定其位置的元素的引用。 如果指定的位置大于 e q u e 的大小，则结果是未定义。  
  
### <a name="remarks"></a>备注  
 如果返回值为 `operator[]` 分配给 `const_reference`, ，e q u e 对象不能修改。 如果返回值为 `operator[]` 分配给 **引用**, ，可以修改 e q u e 对象。  
  
 在使用 _SECURE_SCL 1 编译时，将发生运行时错误，如果您尝试访问 e q u e 的边界以外的元素。  有关更多信息，请参见 [Checked Iterators](../standard-library/checked-iterators.md) 。  
  
### <a name="example"></a>示例  
  
```  
// deque_op_ref.cpp  
// compile with: /EHsc  
#include <deque>  
#include <iostream>  
  
int main( )   
{  
   using namespace std;  
   deque <int> c1;  
  
   c1.push_back( 10 );  
   c1.push_back( 20 );  
   cout << "The first integer of c1 is " << c1[0] << endl;  
   int& i = c1[1];  
   cout << "The second integer of c1 is " << i << endl;  
  
}  
```  
  
```Output  
The first integer of c1 is 10  
The second integer of c1 is 20  
```  
  
##  <a name="a-namedequeoperatoreqa-dequeoperator"></a><a name="deque__operator_eq"></a>  deque:: operator =  
 替换此 q u e 使用来自另一个 e q u e 中的元素的元素。  
  
```  
deque& operator=(const deque& right);

deque& operator=(deque&& right);
```  
  
### <a name="parameters"></a>参数  
  
|||  
|-|-|  
|参数|描述|  
|` right`|E q u e 提供新的内容。|  
  
### <a name="remarks"></a>备注  
 第一重写将元素复制到此 e q u e 从 ` right`, ，赋值的源。 第二个重写将元素移动到此 e q u e 从 ` right`。  
  
 移除该运算符在执行之前此 e q u e 中包含的元素。  
  
### <a name="example"></a>示例  
  
```  
// deque_operator_as.cpp  
// compile with: /EHsc  
#include <deque>  
#include <iostream>  
using namespace std;  
  
typedef deque<int> MyDeque;  
  
template<typename MyDeque> struct S;  
  
template<typename MyDeque> struct S<MyDeque&> {  
  static void show( MyDeque& d ) {  
    MyDeque::const_iterator iter;  
    for (iter = d.cbegin(); iter != d.cend(); iter++)  
       cout << *iter << " ";  
    cout << endl;  
  }  
};  
  
template<typename MyDeque> struct S<MyDeque&&> {  
  static void show( MyDeque&& d ) {  
    MyDeque::const_iterator iter;  
    for (iter = d.cbegin(); iter != d.cend(); iter++)  
       cout << *iter << " ";  
cout << " via unnamed rvalue reference " << endl;  
  }  
};  
  
int main( )  
{  
   MyDeque d1, d2;  
  
   d1.push_back(10);  
   d1.push_back(20);  
   d1.push_back(30);  
   d1.push_back(40);  
   d1.push_back(50);  
  
   cout << "d1 = " ;  
   S<MyDeque&>::show( d1 );  
  
   d2 = d1;  
   cout << "d2 = ";  
   S<MyDeque&>::show( d2 );  
  
   cout << "     ";  
   S<MyDeque&&>::show ( move< MyDeque& > (d1) );  
 }  
```  
  
##  <a name="a-namedequepointera-dequepointer"></a><a name="deque__pointer"></a>  deque:: pointer  
 提供指向中的元素的 [e q u e](../standard-library/deque-class.md)。  
  
```unstlib  
typedef typename Allocator::pointer pointer;  
```  
  
### <a name="remarks"></a>备注  
 一种类型 **指针** 可以用于修改元素的值。  [迭代器](#deque__iterator) 更常用于访问 deque 元素。  
  
##  <a name="a-namedequepopbacka-dequepopback"></a><a name="deque__pop_back"></a>  deque:: pop_back  
 删除 e q u e 末尾处的元素。  
  
```  
void pop_back();
```  
  
### <a name="remarks"></a>备注  
 最后一个元素不得为空。 `pop_back` 绝不会引发异常。  
  
### <a name="example"></a>示例  
  
```  
// deque_pop_back.cpp  
// compile with: /EHsc  
#include <deque>  
#include <iostream>  
  
int main( )   
{  
   using namespace std;  
   deque <int> c1;  
  
   c1.push_back( 1 );  
   c1.push_back( 2 );  
   cout << "The first element is: " << c1.front( ) << endl;  
   cout << "The last element is: " << c1.back( ) << endl;  
  
   c1.pop_back( );  
   cout << "After deleting the element at the end of the deque, the "  
      "last element is: " << c1.back( ) << endl;  
}  
```  
  
```Output  
The first element is: 1  
The last element is: 2  
After deleting the element at the end of the deque, the last element is: 1  
```  
  
##  <a name="a-namedequepopfronta-dequepopfront"></a><a name="deque__pop_front"></a>  deque:: pop_front  
 删除 e q u e 开头的元素。  
  
```  
void pop_front();
```  
  
### <a name="remarks"></a>备注  
 第一个元素不得为空。 `pop_front` 绝不会引发异常。  
  
### <a name="example"></a>示例  
  
```  
// deque_pop_front.cpp  
// compile with: /EHsc  
#include <deque>  
#include <iostream>  
  
int main( )   
{  
   using namespace std;  
   deque <int> c1;  
  
   c1.push_back( 1 );  
   c1.push_back( 2 );  
   cout << "The first element is: " << c1.front( ) << endl;  
   cout << "The second element is: " << c1.back( ) << endl;  
  
   c1.pop_front( );  
   cout << "After deleting the element at the beginning of the "  
      "deque, the first element is: " << c1.front( ) << endl;  
}  
```  
  
```Output  
The first element is: 1  
The second element is: 2  
After deleting the element at the beginning of the deque, the first element is: 2  
```  
  
##  <a name="a-namedequepushbacka-dequepushback"></a><a name="deque__push_back"></a>  deque:: push_back  
 将元素添加到 e q u e 的末尾。  
  
```  
void push_back(const Type& val);

void push_back(Type&& val);
```  
  
### <a name="parameters"></a>参数  
  
|||  
|-|-|  
|参数|描述|  
|` val`|添加到 e q u e 末尾的元素。|  
  
### <a name="remarks"></a>备注  
 如果引发异常，e q u e 将保持不变，重新引发该异常。  
  
##  <a name="a-namedequepushfronta-dequepushfront"></a><a name="deque__push_front"></a>  deque:: push_front  
 到 e q u e 的开头添加一个元素。  
  
```  
    void push_front(const Type& val);

void push_front(Type&& val);
```  
  
### <a name="parameters"></a>参数  
  
|||  
|-|-|  
|参数|描述|  
|` val`|添加到 e q u e 开头的元素。|  
  
### <a name="remarks"></a>备注  
 如果引发异常，e q u e 将保持不变，重新引发该异常。  
  
### <a name="example"></a>示例  
  
```  
// deque_push_front.cpp  
// compile with: /EHsc  
#include <deque>  
#include <iostream>  
#include <string>  
  
int main( )   
{  
   using namespace std;  
   deque <int> c1;  
  
   c1.push_front( 1 );  
   if ( c1.size( ) != 0 )  
      cout << "First element: " << c1.front( ) << endl;  
  
   c1.push_front( 2 );  
   if ( c1.size( ) != 0 )  
      cout << "New first element: " << c1.front( ) << endl;  
  
// move initialize a deque of strings  
   deque <string> c2;  
   string str("a");  
  
   c2.push_front( move( str ) );  
   cout << "Moved first element: " << c2.front( ) << endl;  
}  
```  
  
```Output  
First element: 1  
New first element: 2  
Moved first element: a  
```  
  
##  <a name="a-namedequerbegina-dequerbegin"></a><a name="deque__rbegin"></a>  deque:: rbegin  
 返回发现反向 deque 中的第一个元素的迭代器。  
  
```  
const_reverse_iterator rbegin() const;

reverse_iterator rbegin();
```  
  
### <a name="return-value"></a>返回值  
 反向随机访问迭代器寻址反向 deque 中的第一个元素或发现曾在非反向 deque 中的最后一个元素。  
  
### <a name="remarks"></a>备注  
 `rbegin` 用于发现反向 deque 就像 [开始](#deque__begin) 与 deque 一起使用。  
  
 如果返回值为 `rbegin` 分配给 `const_reverse_iterator`, ，e q u e 对象不能修改。 如果返回值为 `rbegin` 分配给 `reverse_iterator`, ，可以修改 e q u e 对象。  
  
 `rbegin` 可以用于向后循环访问 e q u e。  
  
### <a name="example"></a>示例  
  
```  
// deque_rbegin.cpp  
// compile with: /EHsc  
#include <deque>  
#include <iostream>  
  
int main( )   
{  
   using namespace std;  
   deque <int> c1;  
   deque <int>::iterator c1_Iter;  
   deque <int>::reverse_iterator c1_rIter;  
  
   // If the following line had replaced the line above, an error   
   // would have resulted in the line modifying an element   
   // (commented below) because the iterator would have been const  
   // deque <int>::const_reverse_iterator c1_rIter;  
  
   c1.push_back( 10 );  
   c1.push_back( 20 );  
   c1.push_back( 30 );  
  
   c1_rIter = c1.rbegin( );  
   cout << "Last element in the deque is " << *c1_rIter << "." << endl;  
  
   cout << "The deque contains the elements: ";  
   for ( c1_Iter = c1.begin( ); c1_Iter != c1.end( ); c1_Iter++ )  
      cout << *c1_Iter << " ";  
   cout << "in that order.";  
   cout << endl;  
  
   // rbegin can be used to iterate through a deque in reverse order  
   cout << "The reversed deque is: ";  
   for ( c1_rIter = c1.rbegin( ); c1_rIter != c1.rend( ); c1_rIter++ )  
      cout << *c1_rIter << " ";  
   cout << endl;  
  
   c1_rIter = c1.rbegin( );  
 *c1_rIter = 40;  // This would have caused an error if a   
                    // const_reverse iterator had been declared as   
                    // noted above  
   cout << "Last element in deque is now " << *c1_rIter << "." << endl;  
}  
```  
  
```Output  
Last element in the deque is 30.  
The deque contains the elements: 10 20 30 in that order.  
The reversed deque is: 30 20 10   
Last element in deque is now 40.  
```  
  
##  <a name="a-namedequereferencea-dequereference"></a><a name="deque__reference"></a>  deque:: reference  
 提供对 deque 中存储的元素的引用的类型。  
  
```  
typedef typename Allocator::reference reference;  
```  
  
### <a name="example"></a>示例  
  
```  
// deque_reference.cpp  
// compile with: /EHsc  
#include <deque>  
#include <iostream>  
  
int main( )   
{  
   using namespace std;  
   deque <int> c1;  
  
   c1.push_back( 10 );  
   c1.push_back( 20 );  
  
   const int &i = c1.front( );  
   int &j = c1.back( );  
   cout << "The first element is " << i << endl;  
   cout << "The second element is " << j << endl;  
}  
```  
  
```Output  
The first element is 10  
The second element is 20  
```  
  
##  <a name="a-namedequerenda-dequerend"></a><a name="deque__rend"></a>  deque:: rend  
 返回发现反向 deque 中的最后一个元素之后的位置的迭代器。  
  
```  
const_reverse_iterator rend() const;

reverse_iterator rend();
```  
  
### <a name="return-value"></a>返回值  
 一个反向随机访问迭代器，此迭代之后反向 deque （非反向 deque 中的第一个元素之前的位置） 中的最后一个元素的位置。  
  
### <a name="remarks"></a>备注  
 `rend` 用于发现反向 deque 就像 [结束](#deque__end) 与 deque 一起使用。  
  
 如果返回值为 `rend` 分配给 `const_reverse_iterator`, ，e q u e 对象不能修改。 如果返回值为 `rend` 分配给 `reverse_iterator`, ，可以修改 e q u e 对象。  
  
 `rend` 可以用于测试是否反向迭代器已到达其 e q u e 的末尾。  
  
 不应对 `rend` 返回的值取消引用。  
  
### <a name="example"></a>示例  
  
```  
// deque_rend.cpp  
// compile with: /EHsc  
#include <deque>  
#include <iostream>  
  
int main( )   
{  
   using namespace std;  
  
   deque <int> c1;  
   deque <int>::iterator c1_Iter;  
   deque <int>::reverse_iterator c1_rIter;  
   // If the following line had replaced the line above, an error  
   // would have resulted in the line modifying an element  
   // (commented below) because the iterator would have been const  
   // deque <int>::const_reverse_iterator c1_rIter;  
  
   c1.push_back( 10 );  
   c1.push_back( 20 );  
   c1.push_back( 30 );  
  
   c1_rIter = c1.rend( );  
   c1_rIter --; // Decrementing a reverse iterator moves it forward   
                // in the deque (to point to the first element here)  
   cout << "The first element in the deque is: " << *c1_rIter << endl;  
  
   cout << "The deque is: ";  
   for ( c1_Iter = c1.begin( ); c1_Iter != c1.end( ); c1_Iter++ )  
      cout << *c1_Iter << " ";  
   cout << endl;  
  
   // rend can be used to test if an iteration is through all of   
   // the elements of a reversed deque  
   cout << "The reversed deque is: ";  
   for ( c1_rIter = c1.rbegin( ); c1_rIter != c1.rend( ); c1_rIter++ )  
      cout << *c1_rIter << " ";  
   cout << endl;  
  
   c1_rIter = c1.rend( );  
   c1_rIter--; // Decrementing the reverse iterator moves it backward   
               // in the reversed deque (to the last element here)  
 *c1_rIter = 40; // This modification of the last element would   
                   // have caused an error if a const_reverse   
                   // iterator had been declared (as noted above)  
   cout << "The modified reversed deque is: ";  
   for ( c1_rIter = c1.rbegin( ); c1_rIter != c1.rend( ); c1_rIter++ )  
      cout << *c1_rIter << " ";  
   cout << endl;  
}  
```  
  
```Output  
The first element in the deque is: 10  
The deque is: 10 20 30   
The reversed deque is: 30 20 10   
The modified reversed deque is: 30 20 40   
```  
  
##  <a name="a-namedequeresizea-dequeresize"></a><a name="deque__resize"></a>  deque:: resize  
 指定的新大小来 e q u e。  
  
```  
void resize(size_type _Newsize);

void resize(size_type _Newsize, Type val);
```  
  
### <a name="parameters"></a>参数  
 `_Newsize`  
 E q u e 新大小。  
  
 ` val`  
 如果新大小大于将添加到 e q u e 的新元素的值的原始大小。 如果省略该值，则新元素被指定类的默认值。  
  
### <a name="remarks"></a>备注  
 如果 e q u e 的大小小于请求的大小， `_Newsize`, ，直至到达所请求的大小，元素被添加到 e q u e。  
  
 如果 e q u e 的大小大于请求的大小，接近 e q u e 末尾元素将被删除直到 e q u e 达到大小 `_Newsize`。  
  
 如果 e q u e 的当前大小与请求的大小相同，则不执行任何操作。  
  
 [大小](#deque__size) 反映 e q u e 的当前大小。  
  
### <a name="example"></a>示例  
  
```  
// deque_resize.cpp  
// compile with: /EHsc  
#include <deque>  
#include <iostream>  
  
int main( )   
{   
   using namespace std;  
   deque <int> c1;  
  
   c1.push_back( 10 );  
   c1.push_back( 20 );  
   c1.push_back( 30 );  
  
   c1.resize( 4,40 );  
   cout << "The size of c1 is: " << c1.size( ) << endl;  
   cout << "The value of the last element is " << c1.back( ) << endl;  
  
   c1.resize( 5 );  
   cout << "The size of c1 is now: " << c1.size( ) << endl;  
   cout << "The value of the last element is now " << c1.back( ) << endl;  
  
   c1.resize( 2 );  
   cout << "The reduced size of c1 is: " << c1.size( ) << endl;  
   cout << "The value of the last element is now " << c1.back( ) << endl;  
}  
```  
  
```Output  
The size of c1 is: 4  
The value of the last element is 40  
The size of c1 is now: 5  
The value of the last element is now 0  
The reduced size of c1 is: 2  
The value of the last element is now 20  
```  
  
##  <a name="a-namedequereverseiteratora-dequereverseiterator"></a><a name="deque__reverse_iterator"></a>  deque:: reverse_iterator  
 提供可读取或修改反向 deque 中的元素的随机访问迭代器的类型。  
  
```  
typedef std::reverse_iterator<iterator> reverse_iterator;  
```  
  
### <a name="remarks"></a>备注  
 一种类型 `reverse_iterator` 用于循环访问 e q u e。  
  
### <a name="example"></a>示例  
  请参阅 rbegin 的示例。  
  
##  <a name="a-namedequeshrinktofita-dequeshrinktofit"></a><a name="deque__shrink_to_fit"></a>  deque:: shrink_to_fit  
 放弃额外容量。  
  
```  
void shrink_to_fit();
```  
  
### <a name="remarks"></a>备注  
 没有可移植方法来确定是否 `shrink_to_fit` 可以减少使用的存储 [e q u e](../standard-library/deque-class.md)。  
  
### <a name="example"></a>示例  
  
```  
// deque_shrink_to_fit.cpp  
// compile with: /EHsc  
#include <deque>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;     
   deque <int> v1;  
   //deque <int>::iterator Iter;  
  
   v1.push_back( 1 );  
   v1.push_back( 2 );  
   cout << "Current size of v1 = "   
      << v1.size( ) << endl;  
   v1.shrink_to_fit();  
   cout << "Current size of v1 = "   
      << v1.size( ) << endl;  
}  
```  
  
```Output  
Current size of v1 = 1  
Current size of v1 = 1  
```  
  
##  <a name="a-namedequesizea-dequesize"></a><a name="deque__size"></a>  deque:: size  
 在 e q u e 中返回元素的数。  
  
```  
size_type size() const;
```  
  
### <a name="return-value"></a>返回值  
 E q u e 当前长度。  
  
### <a name="example"></a>示例  
  
```  
// deque_size.cpp  
// compile with: /EHsc  
#include <deque>  
#include <iostream>  
  
int main( )   
{  
   using namespace std;  
   deque <int> c1;  
   deque <int>::size_type i;  
  
   c1.push_back( 1 );  
   i = c1.size( );  
   cout << "The deque length is " << i << "." << endl;  
  
   c1.push_back( 2 );  
   i = c1.size( );  
   cout << "The deque length is now " << i << "." << endl;  
}  
```  
  
```Output  
The deque length is 1.  
The deque length is now 2.  
```  
  
##  <a name="a-namedequesizetypea-dequesizetype"></a><a name="deque__size_type"></a>  deque:: size_type  
 一种计算 e q u e 中的元素数。  
  
```  
typedef typename Allocator::size_type size_type;  
```  
  
### <a name="example"></a>示例  
  请参阅示例 [大小](#deque__size)。  
  
##  <a name="a-namedequeswapa-dequeswap"></a><a name="deque__swap"></a>  deque:: swap  
 交换两个 deque 的元素。  
  
```  
void swap(deque<Type, Allocator>& right);

friend void swap(deque<Type, Allocator>& left, deque<Type, Allocator>& right) template <class Type, class Allocator>  
void swap(deque<Type, Allocator>& left, deque<Type, Allocator>& right);
```  
  
### <a name="parameters"></a>参数  
 ` right`  
 Q u e 提供要交换的元素或其元素将要与那些 e q u e 交换的 deque ` left`。  
  
 ` left`  
 其元素将要与那些 e q u e 交换的 deque ` right`。  
  
### <a name="example"></a>示例  
  
```  
// deque_swap.cpp  
// compile with: /EHsc  
#include <deque>  
#include <iostream>  
  
int main( )   
{  
   using namespace std;  
   deque <int> c1, c2, c3;  
   deque <int>::iterator c1_Iter;  
  
   c1.push_back( 1 );  
   c1.push_back( 2 );  
   c1.push_back( 3 );  
   c2.push_back( 10 );  
   c2.push_back( 20 );  
   c3.push_back( 100 );  
  
   cout << "The original deque c1 is:";  
   for ( c1_Iter = c1.begin( ); c1_Iter != c1.end( ); c1_Iter++ )  
      cout << " " << *c1_Iter;  
   cout << endl;  
  
   c1.swap( c2 );  
  
   cout << "After swapping with c2, deque c1 is:";  
   for ( c1_Iter = c1.begin( ); c1_Iter != c1.end( ); c1_Iter++ )  
      cout << " " << *c1_Iter;  
   cout << endl;  
  
   swap( c1,c3 );  
  
   cout << "After swapping with c3, deque c1 is:";  
   for ( c1_Iter = c1.begin( ); c1_Iter != c1.end( ); c1_Iter++ )  
      cout << " " << *c1_Iter;  
   cout << endl;  
  
   swap<>(c1, c2);  
   cout << "After swapping with c2, deque c1 is:";  
   for ( c1_Iter = c1.begin( ); c1_Iter != c1.end( ); c1_Iter++ )  
      cout << " " << *c1_Iter;  
   cout << endl;  
}  
```  
  
```Output  
The original deque c1 is: 1 2 3  
After swapping with c2, deque c1 is: 10 20  
After swapping with c3, deque c1 is: 100  
After swapping with c2, deque c1 is: 1 2 3  
```  
  
##  <a name="a-namedequevaluetypea-dequevaluetype"></a><a name="deque__value_type"></a>  deque:: value_type  
 一种表示存储 deque 中的数据类型的类型。  
  
```  
typedef typename Allocator::value_type value_type;  
```  
  
### <a name="remarks"></a>备注  
 `value_type` 是模板参数的同义词 **类型**。  
  
### <a name="example"></a>示例  
  
```  
// deque_value_type.cpp  
// compile with: /EHsc  
#include <deque>  
#include <iostream>  
int main( )   
{  
   using namespace std;  
   deque<int>::value_type AnInt;  
   AnInt = 44;  
   cout << AnInt << endl;  
}  
```  
  
```Output  
44  
```  
  
## <a name="see-also"></a>另请参阅  
 [C + + 标准库中的线程安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)   
 [标准模板库](../misc/standard-template-library.md)


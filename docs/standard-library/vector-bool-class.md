---
title: "vector&lt;bool&gt; 类 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vector<bool>"
  - "std.vector<bool>"
  - "std::vector<bool>"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "vector < bool > 类"
ms.assetid: 8028c8ed-ac9c-4f06-aba1-5de45c00aafb
caps.latest.revision: 29
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 29
---
# vector&lt;bool&gt; 类
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

 `vector<bool>` 类是部分专用化 [向量](../standard-library/vector-class.md) 类型元素的 `bool`。 它包含由专用化使用的基础类型的分配器，此分配器通过每个位存储一个 `bool` 值的方式来提供空间优化。  
  
## <a name="syntax"></a>语法  
  
```  
template <class Allocator = allocator<bool>>  
class vector<bool, Allocator>  
```  
  
## <a name="remarks"></a>备注  
 此类模板专用化的行为类似，差别在于这篇文章中所述的向量。  
  
 处理 `bool` 类型的操作与容器存储中的值相对应。 `allocator_traits::construct` 不用于构造这些值。  
  
### <a name="typedefs"></a>Typedef  
  
|||  
|-|-|  
|[const_pointer](#vector_lt_bool_gt___const_pointer)|`const_iterator` 的 typedef，可用作指向 `vector<bool>` 的布尔值元素的常量指针。|  
|[const_reference](#vector_lt_bool_gt___const_reference)|`bool` 的 typedef。 初始化之后，它不观察对原始值的更新。|  
|[指针](#vector_lt_bool_gt___pointer)|`iterator` 的 typedef，可用作指向 `vector<bool>` 的布尔值元素的指针。|  
  
### <a name="member-functions"></a>成员函数  
  
|||  
|-|-|  
|[翻转](#vector_lt_bool_gt___flip)|反转 `vector<bool>` 中的所有位。|  
|[交换](#vector_lt_bool_gt___swap)|交换两个 `vector<bool>` 的元素。|  
|[运算符 &#91; &#93;](#vector_lt_bool_gt___operator_at)|返回对指定位置的 `vector<bool>` 元素的模拟引用。|  
|`at`|函数与非专用相同 [向量](../standard-library/vector-class.md):: 函数，只不过它使用代理类时 [向量 \< bool>:: 引用](#vector_lt_bool_gt___reference_class)。 另请参阅 [运算符 &#91; &#93;](#vector_lt_bool_gt___operator_at)。|  
|`front`|函数与非专用相同 [向量](../standard-library/vector-class.md):: front 函数，只不过它使用代理类 [向量 \< bool>:: 引用](#vector_lt_bool_gt___reference_class)。 另请参阅 [运算符 &#91; &#93;](#vector_lt_bool_gt___operator_at)。|  
|`back`|函数与非专用相同 [向量](../standard-library/vector-class.md):: 备份函数，只不过它使用代理类 [向量 \< bool>:: 引用](#vector_lt_bool_gt___reference_class)。 另请参阅 [运算符 &#91; &#93;](#vector_lt_bool_gt___operator_at)。|  
  
### <a name="proxy-class"></a>代理类  
  
|||  
|-|-|  
|[向量 \< bool> 引用类](#vector_lt_bool_gt___reference_class)|一种用做代理以模拟 `bool&` 行为的类，其对象可提供对 `vector<bool>` 对象中的元素（一位）的引用。|  
  
## <a name="requirements"></a>要求  
 **标头**: \< 矢量>  
  
 **命名空间：** std  
  
##  <a name="a-namevectorltboolgtconstpointera-vectorboolconstpointer"></a><a name="vector_lt_bool_gt___const_pointer"></a>  向量 \< bool>:: const_pointer  
 该类型描述可作为常量指针的对象，该指针指向 `vector<bool>` 对象所包含序列中的布尔元素。  
  
```  
typedef const_iterator const_pointer;  
```  
  
##  <a name="a-namevectorltboolgtconstreferencea-vectorboolconstreference"></a><a name="vector_lt_bool_gt___const_reference"></a>  向量 \< bool>:: const_reference  
 该类型描述可作为常量引用的对象，它引用 `vector<bool>` 对象所包含序列中的布尔元素。  
  
```  
typedef bool const_reference;  
```  
  
### <a name="remarks"></a>备注  
 有关详细信息和代码示例，请参阅 [向量&lt;bool&gt;:: reference::operator =](#vector_lt_bool_gt___reference_operator_eq)。  
  
##  <a name="a-namevectorltboolgtflipa-vectorboolflip"></a><a name="vector_lt_bool_gt___flip"></a>  向量 \< bool>:: flip  
 反转 `vector<bool>` 中的所有位。  
  
```  
void flip();
```  
  
### <a name="example"></a>示例  
  
```cpp  
// vector_bool_flip.cpp  
// compile with: /EHsc /W4  
#include <vector>  
#include <iostream>  
  
int main()  
{  
    using namespace std;  
    cout << boolalpha; // format output for subsequent code  
  
    vector<bool> vb = { true, false, false, true, true };  
    cout << "The vector is:" << endl << "    ";  
    for (const auto& b : vb) {  
        cout << b << " ";  
    }  
    cout << endl;  
  
    vb.flip();  
  
    cout << "The flipped vector is:" << endl << "    ";  
    for (const auto& b : vb) {  
        cout << b << " ";  
    }  
    cout << endl;  
}  
  
```  
  
##  <a name="a-namevectorltboolgtoperatorata-vectorbooloperator"></a><a name="vector_lt_bool_gt___operator_at"></a>  向量 \< bool>:: operator]  
 返回对指定位置的 `vector<bool>` 元素的模拟引用。  
  
```  
vector<bool>::reference operator[](size_type Pos);

vector&<bool&>::const_reference operator[](size_type Pos) const;
```  
  
### <a name="parameters"></a>参数  
  
|||  
|-|-|  
|参数|描述|  
|`Pos`|`vector<bool>` 元素的位置。|  
  
### <a name="return-value"></a>返回值  
 一个 [向量 \< bool>:: 引用](#vector_lt_bool_gt___reference_class) 或 [向量 \< bool>:: const_reference](#vector_lt_bool_gt___const_reference) 对象，它包含索引的元素的值。  
  
 如果指定的位置大于或等于容器大小，则结果为 undefined。  
  
### <a name="remarks"></a>备注  
 在使用 `_ITERATOR_DEBUG_LEVEL` 集进行编译时，如果你尝试访问矢量边界以外的元素，则将发生运行时错误。  有关更多信息，请参见 [Checked Iterators](../standard-library/checked-iterators.md)。  
  
### <a name="example"></a>示例  
  此代码示例演示如何正确使用 `vector<bool>::operator[]` 以及两种常见编码错误（已被注释掉）。 这两种编码错误将导致错误，因为无法使用 `vector<bool>::reference` 返回的 `vector<bool>::operator[]` 对象的地址。  
  
```cpp  
  
// cl.exe /EHsc /nologo /W4 /MTd   
#include <vector>  
#include <iostream>  
  
int main()  
{  
    using namespace std;  
    cout << boolalpha;  
    vector<bool> vb;  
  
    vb.push_back(true);  
    vb.push_back(false);  
  
    //    bool* pb = &vb[1]; // conversion error -                         do not use  
    //    bool& refb = vb[1];   // conversion error -                         do not use  
    bool hold = vb[1];  
    cout << "The second element of vb is " << vb[1] << endl;  
    cout << "The held value from the second element of vb is " << hold << endl;  
  
    // Note this doesn't modify hold.  
    vb[1] = true;  
    cout << "The second element of vb is " << vb[1] << endl;  
    cout << "The held value from the second element of vb is " << hold << endl;  
}  
  
```  
  
##  <a name="a-namevectorltboolgtpointera-vectorboolpointer"></a><a name="vector_lt_bool_gt___pointer"></a>  向量 \< bool>:: 指针  
 一种类型，用于描述一个对象来充当指针，以便指向 `vector<bool>` 对象所包含序列的布尔元素。  
  
```  
typedef iterator pointer;  
```  
  
##  <a name="a-namevectorltboolgtreferenceclassa-vectorboolreference-class"></a><a name="vector_lt_bool_gt___reference_class"></a>  向量 \< bool>:: reference 类  
  `vector<bool>::reference` 类是由一个代理类 [向量 \< bool> 类](../standard-library/vector-bool-class.md) 来模拟 `bool&`。  
  
### <a name="remarks"></a>备注  
 必须使用模拟引用，因为 C++ 不允许直接引用位。 `vector<bool>` 每个元素只使用一个位，这可以使用此代理类来引用。 但是，引用模拟不会完成，原因是某些赋值无效。 例如，因为的地址 `vector<bool>::reference` 不能提取对象，使用下面的代码 [向量 \< bool>:: 运算符 &#91; &#93;](#vector_lt_bool_gt___operator_at) 不正确︰  
  
```cpp  
    vector<bool> vb;  
...  
    bool* pb = &vb[1]; // conversion error -         do not use  
    bool& refb = vb[1];   // conversion error -         do not use  
```  
  
###  <a name="a-namevectorltboolgtreferenceflipa-vectorboolreferenceflip"></a><a name="vector_lt_bool_gt___reference_flip"></a>  向量 \< bool>:: reference:: flip  
 反转引用的布尔值 [向量 \< bool>](../standard-library/vector-bool-class.md) 元素。  
  
```  
void flip();
```  
  
#### <a name="remarks"></a>备注  
  
#### <a name="example"></a>示例  
  
```cpp  
// vector_bool_ref_flip.cpp  
// compile with: /EHsc /W4  
#include <vector>  
#include <iostream>  
  
int main()  
{  
    using namespace std;  
    cout << boolalpha;  
  
    vector<bool> vb = { true, false, false, true, true };  
  
    cout << "The vector is: " << endl << "    ";  
    for (const auto& b : vb) {  
        cout << b << " ";  
    }  
    cout << endl;  
  
    vector<bool>::reference vbref = vb.front();  
    vbref.flip();  
  
    cout << "The vector with first element flipped is: " << endl << "    ";  
    for (const auto& b : vb) {  
        cout << b << " ";  
    }  
    cout << endl;  
}  
/* Output:  
The vector is:  
    true false false true true  
The vector with first element flipped is:  
    false false false true true  
    */  
  
```  
  
###  <a name="a-namevectorltboolgtreferenceoperatorboola-vectorboolreferenceoperator-bool"></a><a name="vector_lt_bool_gt___reference_operator_bool"></a>  向量 \< bool>:: operator bool  
 提供从 `vector<bool>::reference` 到 `bool` 的隐式转换。  
  
'' 运算符 bool() const;
```  
  
#### Return Value  
 The Boolean value of the element of the vector<bool\> object.  
  
#### Remarks  
 The `vector<bool>` object cannot be modified by this operator.  
  
###  <a name="vector_lt_bool_gt___reference_operator_eq"></a>  vector<bool\>::reference::operator=  
 Assigns a Boolean value to a bit, or the value held by a referenced element to a bit.  
  
```  
运算符 & 引用 = （常量引用和右）;

运算符 & 引用 =(bool Val);
```  
  
#### Parameters  
 `Right`  
 The element reference whose value is to be assigned to the bit.  
  
 `Val`  
 The Boolean value to be assigned to the bit.  
  
#### Example  
  
```cpp  
// vector_bool_ref_op_assign.cpp  
// compile with: /EHsc  
#include <vector>  
#include <iostream>  
#include <string>  
  
using namespace std;  
  
template <typename C> void print(const string& s, const C& c) {  
    cout << s;  
  
    for (const auto& e : c) {  
        cout << e << " ";  
    }  
  
    cout << endl;  
}  
  
int main()  
{  
    cout << boolalpha;  
  
    vector<bool> vb = { true, false, false, true, true };  
  
    print("The vector is: ", vb);  
  
    // Invoke vector<bool>::reference::operator=()  
    vector<bool>::reference refelem1 = vb[0];  
    vector<bool>::reference refelem2 = vb[1];  
    vector<bool>::reference refelem3 = vb[2];  
  
    bool b1 = refelem1;  
    bool b2 = refelem2;  
    bool b3 = refelem3;  
    cout << "The original value of the 1st element stored in a bool: " << b1 << endl;  
    cout << "The original value of the 2nd element stored in a bool: " << b2 << endl;  
    cout << "The original value of the 3rd element stored in a bool: " << b3 << endl;  
    cout << endl;  
  
    refelem2 = refelem1;  
  
    print("The vector after assigning refelem1 to refelem2 is now: ", vb);  
  
    refelem3 = true;  
  
    print("The vector after assigning false to refelem1 is now: ", vb);  
  
    // The initial values are still stored in the bool variables and remained unchanged  
    cout << "The original value of the 1st element still stored in a bool: " << b1 << endl;  
    cout << "The original value of the 2nd element still stored in a bool: " << b2 << endl;  
    cout << "The original value of the 3rd element still stored in a bool: " << b3 << endl;  
    cout << endl;  
}  
/* Output:  
The vector is: true false false true true  
The original value of the 1st element stored in a bool: true  
The original value of the 2nd element stored in a bool: false  
The original value of the 3rd element stored in a bool: false  
  
The vector after assigning refelem1 to refelem2 is now: true true false true true  
The vector after assigning false to refelem1 is now: true true true true true  
The original value of the 1st element still stored in a bool: true  
The original value of the 2nd element still stored in a bool: false  
The original value of the 3rd element still stored in a bool: false  
*/  
  
```  
  
##  <a name="a-namevectorltboolgtswapa-vectorboolswap"></a><a name="vector_lt_bool_gt___swap"></a>  向量 \< bool>:: swap  
 交换布尔矢量的两个元素的静态成员函数 ( `vector<bool>`) 使用的代理类 [向量 \< bool>:: 引用](#vector_lt_bool_gt___reference_class)。  
  
```  
 
static void swap(
    reference Left,  
    reference Right);
```  
  
### <a name="parameters"></a>参数  
 `Left`  
 将与 `Right` 元素交换的元素。  
  
 `Right`  
 将与 `Left` 元素交换的元素。  
  
### <a name="remarks"></a>备注  
 此重载支持 `vector<bool>` 的特殊代理要求。 [向量](../standard-library/vector-class.md):: swap 具有相同的功能的单参数重载 `vector<bool>::swap()`。  
  
## <a name="see-also"></a>另请参阅  
 [C + + 标准库中的线程安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)   
 [标准模板库](../misc/standard-template-library.md)


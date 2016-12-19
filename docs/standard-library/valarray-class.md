---
title: "valarray 类 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "valarray"
  - "std.valarray"
  - "std::valarray"
  - "valarray/std::valarray"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "valarray 类"
ms.assetid: 19b862f9-5d09-4003-8844-6ddd02c1a3a7
caps.latest.revision: 23
caps.handback.revision: 23
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# valarray 类
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

此模板类描述一个对象，用于控制类型的元素的序列 **类型** ，存储为数组、 执行高速的数学运算，设计和优化的计算性能。  
  
## <a name="remarks"></a>备注  
 此类是一组有序值的数学概念表示形式，元素从 0 开始按顺序编号。 类被描述为接近的容器，因为它支持一些，但并非所有功能的第一类序列容器，如 [向量](../standard-library/vector-class.md), ，支持。 它在以下两个重要方面不同于模板类矢量：  
  
-   它定义了大量的相应元素之间的算术运算 **数值数组 \< 类型>** 对象的指针相同的类型和长度，如 *xarr* = cos ( *yarr*) + sin ( *zarr*)。  
  
-   它定义了各种有趣的方式为下标 **数值数组 \< 类型>** 对象，通过重载 [运算符 &#91; &#93;](#valarray__operator_at)。  
  
 类的对象 **类型**:  
  
-   具有公共默认构造函数、析构函数、复制构造函数、赋值运算符和常规行为。  
  
-   根据需要，定义适用于浮点类型的算术运算符、数学函数和常规行为。  
  
 具体而言，复制构造和后跟分配的默认构造之间可能不存在任何细微的差异。 无类的对象上的操作 **类型** 可能会引发异常。  
  
### <a name="constructors"></a>构造函数  
  
|||  
|-|-|  
|[数值数组](#valarray__valarray)|构造一个 `valarray`，其具有特定大小、包含特定值的元素、作为另一个 `valarray` 的副本或另一个 `valarray` 的子集。|  
  
### <a name="typedefs"></a>Typedef  
  
|||  
|-|-|  
|[value_type](#valarray__value_type)|一种类型，表示存储在 `valarray` 中的元素的类型。|  
  
### <a name="member-functions"></a>成员函数  
  
|||  
|-|-|  
|[应用](#valarray__apply)|将指定函数应用到 `valarray` 的每个元素。|  
|[cshift](#valarray__cshift)|将 `valarray` 中的所有元素循环移动指定数目的位置。|  
|[释放](#valarray__free)|释放 `valarray` 使用的内存。|  
|[最大值](#valarray__max)|查找 `valarray` 中的最大元素。|  
|[最小值](#valarray__min)|查找 `valarray` 中的最小元素。|  
|[调整大小](#valarray__resize)|将 `valarray` 中元素的数量更改为指定数量，根据需要添加或删除元素。|  
|[按住 shift](#valarray__shift)|将 `valarray` 的所有元素移动指定数目的位置。|  
|[大小](#valarray__size)|查找 `valarray` 中的元素数目。|  
|[sum](#valarray__sum)|确定长度不为零的 `valarray` 中的所有元素的总和。|  
|[交换](#valarray__swap)||  
  
### <a name="operators"></a>运算符  
  
|||  
|-|-|  
|[运算符 ！](#valarray__operator_not)|一个一元运算符，它用于获取 `valarray` 中每个元素的逻辑 `NOT` 值。|  
|[operator %=](#valarray__operator_mod_eq)|获取用指定 `valarray` 或元素类型的值对数组元素进行点除所得的余数。|  
|[运算符 & =](#valarray__operator_amp__eq)|获取数组中元素的按位 `AND`，该数组具有指定 `valarray` 中的对应元素或具有元素类型的值。|  
|[运算符 >> =](#valarray__operator_gt__gt__eq)|将 `valarray` 操作数中的每个元素向右移动指定数目的位置，或者按第二个 `valarray` 指定的点算数右移。|  
|[运算符 << =](#valarray__operator_lt__lt__eq)|将 `valarray` 操作数中的每个元素向左移动指定数目的位置，或者按第二个 `valarray` 指定的点算数左移。|  
|[运算符 * =](#valarray__operator_star_eq)|将指定 `valarray` 的元素或元素类型的值与操作数 `valarray` 进行点乘。|  
|[operator +](#valarray__operator_add)|一个一元运算符，该运算符将 `valarray` 中的所有元素相加。|  
|[operator + =](#valarray__operator_add_eq)|将指定 `valarray` 的元素或元素类型的值与操作数 `valarray` 进行点加。|  
|[operator-](#valarray__operator-)|一个一元运算符，该运算符将 `valarray` 中的所有元素相减。|  
|[运算符 =](#valarray__operator-_eq)|将指定 `valarray` 的元素或元素类型的值与操作数 `valarray` 进行点减。|  
|[/ = 运算符](#valarray__operator__eq)|将操作数 `valarray` 与指定 `valarray` 的元素或元素类型的值进行点除。|  
|[运算符 =](#valarray__operator_eq)|将元素分配给 `valarray`，其值可以直接指定，也可以作为一些其他 `valarray` 的一部分指定，或由 `slice_array`、`gslice_array`、`mask_array` 或 `indirect_array` 指定。|  
|[运算符 &#91; &#93;](#valarray__operator_at)|返回对指定索引或指定子集处的元素或其值的引用。|  
|[运算符 ^ =](#valarray__operator_xor_eq)|获取逻辑的逐元素集异或运算符 ( `XOR`) 的具有指定的数值数组或元素类型的值的数组。|  
|[运算符 &#124; =](#valarray__operator_or_eq)|获取数组中元素的按位 `OR`，该数组具有指定 `valarray` 中的对应元素或具有元素类型的值。|  
|[运算符 ~](#valarray__operator_dtor)|一个一元运算符，该运算符获取 `valarray` 中每个元素的按位 `NOT` 值。|  
  
## <a name="requirements"></a>要求  
 **标头︰** \< 数值数组>  
  
 **命名空间：** std  
  
##  <a name="a-namevalarrayapplya-valarrayapply"></a><a name="valarray__apply"></a>  valarray:: apply  
 将指定的函数应用于数值数组的每个元素。  
  
```  
valarray<Type> apply(Type _Func(Type)) const;

valarray<Type> apply(Type _Func(constType&)) const;
```  
  
### <a name="parameters"></a>参数  
 *_Func(Type)*  
 要应用于操作数数值数组的每个元素的函数对象。  
  
 *_Func(const Type&)*  
 Const 要应用于操作数数值数组的每个元素的的函数对象。  
  
### <a name="return-value"></a>返回值  
 数值数组的元素已经 `_Func` element-wise 应用于操作数数值数组的元素。  
  
### <a name="remarks"></a>备注  
 成员函数将返回类的对象 [valarray](../standard-library/valarray-class.md)**\< 类型>**, ，长度为 [大小](#valarray__size), ，其元素的每个 `I` 是 **func**(( **\*这**) [ `I`])。  
  
### <a name="example"></a>示例  
  
```  
// valarray_apply.cpp  
// compile with: /EHsc  
#include <valarray>  
#include <iostream>  
  
using namespace std;  
  
int __cdecl MyApplyFunc( int n )  
{  
   return n*2;  
}  
  
int main( int argc, char* argv[] )  
{  
   valarray<int> vaR(10), vaApplied(10);  
   int i;  
  
   for ( i = 0; i < 10; i += 3 )  
      vaR[i] = i;  
  
   for ( i = 1; i < 10; i += 3 )  
      vaR[i] = 0;  
  
   for ( i = 2; i < 10; i += 3 )  
      vaR[i] = -i;  
  
   cout << "The initial Right valarray is: (";  
   for   ( i=0; i < 10; ++i )  
      cout << " " << vaR[i];  
   cout << " )" << endl;  
  
   vaApplied = vaR.apply( MyApplyFunc );  
  
   cout << "The element-by-element result of "  
       << "applying MyApplyFunc to vaR is the\nvalarray: ( ";  
   for ( i = 0; i < 10; ++i )  
      cout << " " << vaApplied[i];  
   cout << " )" << endl;  
}  
\* Output:   
The initial Right valarray is: ( 0 0 -2 3 0 -5 6 0 -8 9 )  
The element-by-element result of applying MyApplyFunc to vaR is the  
valarray: (  0 0 -4 6 0 -10 12 0 -16 18 )  
*\  
```  
  
##  <a name="a-namevalarraycshifta-valarraycshift"></a><a name="valarray__cshift"></a>  valarray:: cshift  
 循环方式将指定数量的位置上数值数组中的所有元素。  
  
```  
valarray<Type> cshift(int count) const;
```  
  
### <a name="parameters"></a>参数  
 ` count`  
 数字的位数的元素将向前移动。  
  
### <a name="return-value"></a>返回值  
 新数值数组中所有元素已被都移 ` count` 循环方式向前面的数值数组，左操作数数值数组中的位置相对的位置。  
  
### <a name="remarks"></a>备注  
 正值的 ` count` 将元素循环方式向左位移 ` count` 放置。  
  
 值为负 ` count` 将元素循环右位移 ` count` 放置。  
  
### <a name="example"></a>示例  
  
```  
// valarray_cshift.cpp  
// compile with: /EHsc  
  
#include <valarray>  
#include <iostream>  
  
int main()  
{  
    using namespace std;  
    int i;  
  
    valarray<int> va1(10), va2(10);  
    for (i = 0; i < 10; i+=1)  
        va1[i] = i;  
    for (i = 0; i < 10; i+=1)  
        va2[i] = 10 - i;  
  
    cout << "The operand valarray va1 is: (";  
    for (i = 0; i < 10; i++)  
        cout << " " << va1[i];  
    cout << ")" << endl;  
  
    // A positive parameter shifts elements right  
    va1 = va1.cshift(4);  
    cout << "The cyclically shifted valarray va1 is:\nva1.cshift (4) = (";  
    for (i = 0; i < 10; i++)  
        cout << " " << va1[i];  
    cout << ")" << endl;  
  
    cout << "The operand valarray va2 is: (";  
    for (i = 0; i < 10; i++)  
        cout << " " << va2[i];  
    cout << ")" << endl;  
  
    // A negative parameter shifts elements left  
    va2 = va2.cshift(-4);  
    cout << "The cyclically shifted valarray va2 is:\nva2.shift (-4) = (";  
    for (i = 0; i < 10; i++)  
        cout << " " << va2[i];  
    cout << ")" << endl;  
}  
\* Output:   
The operand valarray va1 is: ( 0 1 2 3 4 5 6 7 8 9)  
The cyclically shifted valarray va1 is:  
va1.cshift (4) = ( 4 5 6 7 8 9 0 1 2 3)  
The operand valarray va2 is: ( 10 9 8 7 6 5 4 3 2 1)  
The cyclically shifted valarray va2 is:  
va2.shift (-4) = ( 4 3 2 1 10 9 8 7 6 5)  
*\  
```  
  
##  <a name="a-namevalarrayfreea-valarrayfree"></a><a name="valarray__free"></a>  valarray:: free  
 释放使用的数值数组的内存。  
  
```  
void free();
```  
  
### <a name="remarks"></a>备注  
 此非标准函数等效于指定的数值数组为空。 例如:   
  
```  
valarray<T> v;  
v = valarray<T>();

// equivalent to v.free()  
```  
  
##  <a name="a-namevalarraymaxa-valarraymax"></a><a name="valarray__max"></a>  valarray:: max  
 在数值数组中查找最大的元素。  
  
```  
Type max() const;
```  
  
### <a name="return-value"></a>返回值  
 中的操作数数值数组的元素的最大值。  
  
### <a name="remarks"></a>备注  
 成员函数将值进行比较通过应用 **运算符 \<** 或 **运算符 >** 对类的元素之间 **类型**, ，对于哪些运算符必须提供为该元素 **类型**。  
  
### <a name="example"></a>示例  
  
```  
// valarray_max.cpp  
// compile with: /EHsc  
#include <valarray>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   int i, MaxValue;  
  
   valarray<int> vaR ( 10 );  
   for ( i = 0 ; i < 10 ; i += 3 )  
      vaR [ i ] =  i;  
   for ( i = 1 ; i < 10 ; i += 3 )  
      vaR [ i ] =  2*i - 1;  
   for ( i = 2 ; i < 10 ; i += 3 )  
      vaR [ i ] =  10 - i;  
  
   cout << "The operand valarray is: ( ";  
      for (i = 0 ; i < 10 ; i++ )  
         cout << vaR [ i ] << " ";  
   cout << ")." << endl;  
  
   MaxValue = vaR.max (  );  
   cout << "The largest element in the valarray is: "  
        << MaxValue  << "." << endl;  
}  
\* Output:   
The operand valarray is: ( 0 1 8 3 7 5 6 13 2 9 ).  
The largest element in the valarray is: 13.  
*\  
```  
  
##  <a name="a-namevalarraymina-valarraymin"></a><a name="valarray__min"></a>  valarray:: min  
 在数值数组中查找最小元素。  
  
```  
Type min() const;
```  
  
### <a name="return-value"></a>返回值  
 中的操作数数值数组的元素的最小值。  
  
### <a name="remarks"></a>备注  
 成员函数将值进行比较通过应用 **运算符 \<** 或 **运算符 >** 对类的元素之间 **类型**, ，对于哪些运算符必须提供为该元素 **类型**。  
  
### <a name="example"></a>示例  
  
```  
// valarray_min.cpp  
// compile with: /EHsc  
#include <valarray>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   int i, MinValue;  
  
   valarray<int> vaR ( 10 );  
   for ( i = 0 ; i < 10 ; i += 3 )  
      vaR [ i ] =  -i;  
   for ( i = 1 ; i < 10 ; i += 3 )  
      vaR [ i ] =  2*i;  
   for ( i = 2 ; i < 10 ; i += 3 )  
      vaR [ i ] =  5 - i;  
  
   cout << "The operand valarray is: ( ";  
      for ( i = 0 ; i < 10 ; i++ )  
         cout << vaR [ i ] << " ";  
   cout << ")." << endl;  
  
   MinValue = vaR.min ( );  
   cout << "The smallest element in the valarray is: "  
        << MinValue  << "." << endl;  
}  
\* Output:   
The operand valarray is: ( 0 2 3 -3 8 0 -6 14 -3 -9 ).  
The smallest element in the valarray is: -9.  
*\  
```  
  
##  <a name="a-namevalarrayoperatornota-valarrayoperator"></a><a name="valarray__operator_not"></a>  valarray:: operator ！  
 一元运算符，它获取的逻辑 **不** 数值数组中每个元素的值。  
  
```  
valarray<bool> operator!() const;
```  
  
### <a name="return-value"></a>返回值  
 操作数数值数组的元素的值求反运算的布尔值的数值数组。  
  
### <a name="remarks"></a>备注  
 逻辑操作 **不** 对元素求反，因为它将转换为全零转换并将与所有非零值并将它们转换为零。 返回数值数组的布尔值是大小的与操作数数值数组相同。  
  
 另外，还有按位 **不**[valarray:: operator ~](#valarray__operator_dtor) ，求反的单个位进行运算的二进制表示形式中的级别 `char` 和 `int` 数值数组元素。  
  
### <a name="example"></a>示例  
  
```  
// valarray_op_lognot.cpp  
// compile with: /EHsc  
#include <valarray>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   int i;  
  
   valarray<int> vaL ( 10 );  
   valarray<bool> vaNOT ( 10 );  
   for ( i = 0 ; i < 10 ; i += 2 )  
      vaL [ i ] =  0;  
   for ( i = 1 ; i < 10 ; i += 2 )  
      vaL [ i ] =  i-1;  
  
   cout << "The initial valarray is:  ( ";  
      for (i = 0 ; i < 10 ; i++ )  
         cout << vaL [ i ] << " ";  
   cout << ")." << endl;  
  
   vaNOT = !vaL;  
   cout << "The element-by-element result of "  
        << "the logical NOT operator! is the\n valarray: ( ";  
      for ( i = 0 ; i < 10 ; i++ )  
         cout << vaNOT [ i ] << " ";  
   cout << ")." << endl;  
}  
\* Output:   
The initial valarray is:  ( 0 0 0 2 0 4 0 6 0 8 ).  
The element-by-element result of the logical NOT operator! is the  
 valarray: ( 1 1 1 0 1 0 1 0 1 0 ).  
*\  
```  
  
##  <a name="a-namevalarrayoperatormodeqa-valarrayoperator"></a><a name="valarray__operator_mod_eq"></a>  valarray:: operator %=  
 获取指定的数值数组或元素类型的值 element-wise 除以数组的元素的余数。  
  
```  
valarray<Type>& operator%=(const valarray<Type>& right);

valarray<Type>& operator%=(const Type& right);
```  
  
### <a name="parameters"></a>参数  
 ` right`  
 数值数组或等于是除、 element-wise，操作数数值数组的操作数数值数组的元素类型的值。  
  
### <a name="return-value"></a>返回值  
 其元素是操作数数值数组的逐元素集除法运算的余数的数值数组的 ` right.`  
  
### <a name="example"></a>示例  
  
```  
// valarray_class_op_rem.cpp  
// compile with: /EHsc  
#include <valarray>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   int i;  
  
   valarray<int> vaL ( 6 ), vaR ( 6 );  
   for ( i = 0 ; i < 6 ; i += 2 )  
      vaL [ i ] =  53;  
   for ( i = 1 ; i < 6 ; i += 2 )  
      vaL [ i ] =  -67;  
   for ( i = 0 ; i < 6 ; i++ )  
      vaR [ i ] =  3*i+1;  
  
   cout << "The initial valarray is: ( ";  
      for ( i = 0 ; i < 6 ; i++ )  
         cout << vaL [ i ] << " ";  
   cout << ")." << endl;  
  
   cout << "The initial  right valarray is: ( ";  
      for ( i = 0 ; i < 6 ; i++ )  
         cout << vaR [ i ] << " ";  
   cout << ")." << endl;  
  
   vaL %= vaR;  
   cout << "The remainders from the element-by-element "  
        << "division is the\n valarray: ( ";  
      for ( i = 0 ; i < 6 ; i++ )  
         cout << vaL [ i ] << " ";  
   cout << ")." << endl;  
}  
\* Output:   
The initial valarray is: ( 53 -67 53 -67 53 -67 ).  
The initial  right valarray is: ( 1 4 7 10 13 16 ).  
The remainders from the element-by-element division is the  
 valarray: ( 0 -3 4 -7 1 -3 ).  
*\  
```  
  
##  <a name="a-namevalarrayoperatorampeqa-valarrayoperatoramp"></a><a name="valarray__operator_amp__eq"></a>  valarray::&amp;=  
 获取按位 **AND** 数组中的元素中指定的数值数组的相应元素或元素类型的值。  
  
```  
valarray<Type>& operator&=(const valarray<Type>& right);

valarray<Type>& operator&=(const Type& right);
```  
  
### <a name="parameters"></a>参数  
 ` right`  
 数值数组或值的元素类型与相同的是组合在一起的操作数数值数组、 逐元素集，通过逻辑 **AND** 与操作数数值数组。  
  
### <a name="return-value"></a>返回值  
 其元素是逐元素集 valarray 逻辑 **AND** 通过的操作数数值数组 ` right.`  
  
### <a name="remarks"></a>备注  
 按位运算仅可用于操作中的位 `char` 和 `int` 数据类型和变体，不在 **float**, ，**double**, ，**longdouble**, ，`void`, ，`bool`, ，或其他更复杂的数据类型。  
  
 按位与具有与逻辑相同的事实表 **AND** 但也适用于单个位进行运算的级别上的数据类型。 指定 bits *b*1 和 *b*2， *b*1 **AND** *b*2 是 **true** 两个位均为 true; 如果 **false** 如果至少一个为 false。  
  
### <a name="example"></a>示例  
  
```  
// valarray_class_op_bitand.cpp  
// compile with: /EHsc  
#include <valarray>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   int i;  
  
   valarray<int> vaL ( 10 ), vaR ( 10 );  
   for ( i = 0 ; i < 10 ; i += 2 )  
      vaL [ i ] =  0;  
   for ( i = 1 ; i < 10 ; i += 2 )  
      vaL [ i ] =  i-1;  
   for ( i = 0 ; i < 10 ; i++ )  
      vaR [ i ] =  i;  
  
   cout << "The initial valarray is:  ( ";  
      for ( i = 0 ; i < 10 ; i++ )  
         cout << vaL [ i ] << " ";  
   cout << ")." << endl;  
  
   cout << "The initial Right valarray is: ( ";  
      for ( i = 0 ; i < 10 ; i++ )  
         cout << vaR [ i ] << " ";  
   cout << ")." << endl;  
  
   vaL &= vaR;  
   cout << "The element-by-element result of "  
        << "the logical AND operator&= is the\n valarray: ( ";  
      for ( i = 0 ; i < 10 ; i++ )  
         cout << vaL [ i ] << " ";  
   cout << ")." << endl;  
}  
\* Output:   
The initial valarray is:  ( 0 0 0 2 0 4 0 6 0 8 ).  
The initial Right valarray is: ( 0 1 2 3 4 5 6 7 8 9 ).  
The element-by-element result of the logical AND operator&= is the  
 valarray: ( 0 0 0 2 0 4 0 6 0 8 ).  
*\  
```  
  
##  <a name="a-namevalarrayoperatorgtgteqa-valarrayoperatorgtgt"></a><a name="valarray__operator_gt__gt__eq"></a>  valarray::&gt;&gt;=  
 右移位的位的数值数组操作数指定数量的位置或第二个数值数组所指定的量逐元素集的每个元素。  
  
```  
valarray<Type>& operator>>=(const valarray<Type>& right);

valarray<Type>& operator>>=(const Type& right);
```  
  
### <a name="parameters"></a>参数  
 ` right`  
 用于指示右移位时或其元素指示右移位运算的逐元素集数量的数值数组的量的值。  
  
### <a name="return-value"></a>返回值  
 数值数组，其元素已向右位移中指定的金额 ` right`。  
  
### <a name="remarks"></a>备注  
 有符号的数字必须保留其符号。  
  
### <a name="example"></a>示例  
  
```  
// valarray_class_op_rs.cpp  
// compile with: /EHsc  
#include <valarray>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   int i;  
  
   valarray<int> vaL ( 8 ), vaR ( 8 );  
   for ( i = 0 ; i < 8 ; i += 2 )  
      vaL [ i ] =  64;  
   for ( i = 1 ; i < 8 ; i += 2 )  
      vaL [ i ] =  -64;  
   for ( i = 0 ; i < 8 ; i++ )  
      vaR [ i ] =  i;  
  
   cout << "The initial operand valarray is: ( ";  
      for ( i = 0 ; i < 8 ; i++ )  
         cout << vaL [ i ] << " ";  
   cout << ")." << endl;  
  
   cout << "The  right valarray is: ( ";  
      for ( i = 0 ; i < 8 ; i++ )  
         cout << vaR [ i ] << " ";  
   cout << ")." << endl;  
  
   vaL >>= vaR;  
   cout << "The element-by-element result of "  
        << "the right shift is the\n valarray: ( ";  
      for ( i = 0 ; i < 8 ; i++ )  
         cout << vaL [ i ] << " ";  
   cout << ")." << endl;  
}  
\* Output:   
The initial operand valarray is: ( 64 -64 64 -64 64 -64 64 -64 ).  
The  right valarray is: ( 0 1 2 3 4 5 6 7 ).  
The element-by-element result of the right shift is the  
 valarray: ( 64 -32 16 -8 4 -2 1 -1 ).  
*\  
```  
  
##  <a name="a-namevalarrayoperatorltlteqa-valarrayoperatorltlt"></a><a name="valarray__operator_lt__lt__eq"></a>  valarray::&lt;&lt;=  
 左移位的位的数值数组操作数指定数量的位置或第二个数值数组所指定的量逐元素集的每个元素。  
  
```  
valarray<Type>& operator<<=(const valarray<Type>& right);

valarray<Type>& operator<<=(const Type& right);
```  
  
### <a name="parameters"></a>参数  
 ` right`  
 用于指示左的移或其元素指示左移位运算的逐元素集数量的数值数组的量的值。  
  
### <a name="return-value"></a>返回值  
 已移动的元素数值数组保留中指定的金额 ` right`。  
  
### <a name="remarks"></a>备注  
 有符号的数字必须保留其符号。  
  
### <a name="example"></a>示例  
  
```  
// valarray_class_op_ls.cpp  
// compile with: /EHsc  
#include <valarray>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   int i;  
  
   valarray<int> vaL ( 8 ), vaR ( 8 );  
   for ( i = 0 ; i < 8 ; i += 2 )  
      vaL [ i ] =  1;  
   for ( i = 1 ; i < 8 ; i += 2 )  
      vaL [ i ] =  -1;  
   for ( i = 0 ; i < 8 ; i++ )  
      vaR [ i ] =  i;  
  
   cout << "The initial operand valarray is: ( ";  
      for ( i = 0 ; i < 8 ; i++ )  
         cout << vaL [ i ] << " ";  
   cout << ")." << endl;  
  
   cout << "The  right valarray is: ( ";  
      for ( i = 0 ; i < 8 ; i++ )  
         cout << vaR [ i ] << " ";  
   cout << ")." << endl;  
  
   vaL <<= vaR;  
   cout << "The element-by-element result of "  
        << "the left shift\n on the operand array is the valarray:\n ( ";  
      for ( i = 0 ; i < 8 ; i++ )  
         cout << vaL [ i ] << " ";  
   cout << ")." << endl;  
}  
\* Output:   
The initial operand valarray is: ( 1 -1 1 -1 1 -1 1 -1 ).  
The  right valarray is: ( 0 1 2 3 4 5 6 7 ).  
The element-by-element result of the left shift  
 on the operand array is the valarray:  
 ( 1 -2 4 -8 16 -32 64 -128 ).  
*\  
```  
  
##  <a name="a-namevalarrayoperatorstareqa-valarrayoperator"></a><a name="valarray__operator_star_eq"></a>  valarray:: operator * =  
 到操作数 valarray element-wise，乘以指定的数值数组的元素或元素类型的值。  
  
```  
valarray<Type>& operator*=(const valarray<Type>& right);

valarray<Type>& operator*=(const Type& right);
```  
  
### <a name="parameters"></a>参数  
 ` right`  
 数值数组或等于是执行乘，element-wise，操作数数值数组的操作数数值数组的元素类型的值。  
  
### <a name="return-value"></a>返回值  
 其元素是操作数数值数组的逐元素集乘积的数值数组和 ` right.`  
  
### <a name="example"></a>示例  
  
```  
// valarray_op_emult.cpp  
// compile with: /EHsc  
#include <valarray>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   int i;  
  
   valarray<int> vaL ( 8 ), vaR ( 8 );  
   for ( i = 0 ; i < 8 ; i += 2 )  
      vaL [ i ] =  2;  
   for ( i = 1 ; i < 8 ; i += 2 )  
      vaL [ i ] =  -1;  
   for ( i = 0 ; i < 8 ; i++ )  
      vaR [ i ] =  i;  
  
   cout << "The initial valarray is: ( ";  
      for ( i = 0 ; i < 8 ; i++ )  
         cout << vaL [ i ] << " ";  
   cout << ")." << endl;  
  
   cout << "The initial Right valarray is: ( ";  
      for ( i = 0 ; i < 8 ; i++ )  
         cout << vaR [ i ] << " ";  
   cout << ")." << endl;  
  
   vaL *= vaR;  
   cout << "The element-by-element result of "  
        << "the multiplication is the\n valarray: ( ";  
      for ( i = 0 ; i < 8 ; i++ )  
         cout << vaL [ i ] << " ";  
   cout << ")." << endl;  
}  
\* Output:   
The initial valarray is: ( 2 -1 2 -1 2 -1 2 -1 ).  
The initial Right valarray is: ( 0 1 2 3 4 5 6 7 ).  
The element-by-element result of the multiplication is the  
 valarray: ( 0 -1 4 -3 8 -5 12 -7 ).  
*\  
```  
  
##  <a name="a-namevalarrayoperatoradda-valarrayoperator"></a><a name="valarray__operator_add"></a>  valarray:: operator +  
 一元运算符应用于数值数组中每个元素的加号。  
  
```  
valarray<Type> operator+() const;
```  
  
### <a name="return-value"></a>返回值  
 其元素是以及操作数数组的数值数组。  
  
### <a name="example"></a>示例  
  
```  
// valarray_op_eplus.cpp  
// compile with: /EHsc  
#include <valarray>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   int i;  
  
   valarray<int> vaL ( 10 );  
   valarray<int> vaPLUS ( 10 );  
   for ( i = 0 ; i < 10 ; i += 2 )  
      vaL [ i ] =  -i;  
   for ( i = 1 ; i < 10 ; i += 2 )  
      vaL [ i ] =  i-1;  
  
   cout << "The initial valarray is:  ( ";  
      for ( i = 0 ; i < 10 ; i++ )  
         cout << vaL [ i ] << " ";  
   cout << ")." << endl;  
  
   vaPLUS = +vaL;  
   cout << "The element-by-element result of "  
        << "the operator+ is the\n valarray: ( ";  
      for ( i = 0 ; i < 10 ; i++ )  
         cout << vaPLUS [ i ] << " ";  
   cout << ")." << endl;  
}  
\* Output:   
The initial valarray is:  ( 0 0 -2 2 -4 4 -6 6 -8 8 ).  
The element-by-element result of the operator+ is the  
 valarray: ( 0 0 -2 2 -4 4 -6 6 -8 8 ).  
*\  
```  
  
##  <a name="a-namevalarrayoperatoraddeqa-valarrayoperator"></a><a name="valarray__operator_add_eq"></a>  valarray:: operator + =  
 将指定的数值数组的元素或元素类型的值 element-wise，添加到操作数数值数组。  
  
```  
valarray<Type>& operator+=(const valarray<Type>& right);

valarray<Type>& operator+=(const Type& right);
```  
  
### <a name="parameters"></a>参数  
 ` right`  
 数值数组或与相同的是要添加，element-wise，到操作数数值数组的操作数数值数组的元素类型的值。  
  
### <a name="return-value"></a>返回值  
 其元素是逐元素集的操作数数值数组的总和数值数组和 ` right.`  
  
### <a name="example"></a>示例  
  
```  
// valarray_op_eadd.cpp  
// compile with: /EHsc  
#include <valarray>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   int i;  
  
   valarray<int> vaL ( 8 ), vaR ( 8 );  
   for ( i = 0 ; i < 8 ; i += 2 )  
      vaL [ i ] =  2;  
   for ( i = 1 ; i < 8 ; i += 2 )  
      vaL [ i ] =  -1;  
   for ( i = 0 ; i < 8 ; i++ )  
      vaR [ i ] =  i;  
  
   cout << "The initial valarray is: ( ";  
      for (i = 0 ; i < 8 ; i++ )  
         cout << vaL [ i ] << " ";  
   cout << ")." << endl;  
  
   cout << "The initial  right valarray is: ( ";  
      for (i = 0 ; i < 8 ; i++ )  
         cout << vaR [ i ] << " ";  
   cout << ")." << endl;  
  
   vaL += vaR;  
   cout << "The element-by-element result of "  
        << "the sum is the\n valarray: ( ";  
      for (i = 0 ; i < 8 ; i++ )  
         cout << vaL [ i ] << " ";  
   cout << ")." << endl;  
}  
\* Output:   
The initial valarray is: ( 2 -1 2 -1 2 -1 2 -1 ).  
The initial  right valarray is: ( 0 1 2 3 4 5 6 7 ).  
The element-by-element result of the sum is the  
 valarray: ( 2 0 4 2 6 4 8 6 ).  
*\  
```  
  
##  <a name="a-namevalarrayoperator-a-valarrayoperator-"></a><a name="valarray__operator-"></a>  valarray:: operator-  
 一元运算符应用于数值数组中每个元素的减号。  
  
```  
valarray<Type> operator-() const;
```  
  
### <a name="return-value"></a>返回值  
 其元素是减去操作数数组的数值数组。  
  
### <a name="example"></a>示例  
  
```  
// valarray_op_eminus.cpp  
// compile with: /EHsc  
#include <valarray>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   int i;  
  
   valarray<int> vaL ( 10 );  
   valarray<int> vaMINUS ( 10 );  
   for ( i = 0 ; i < 10 ; i += 2 )  
      vaL [ i ] =  -i;  
   for ( i = 1 ; i < 10 ; i += 2 )  
      vaL [ i ] =  i-1;  
  
   cout << "The initial valarray is:  ( ";  
      for ( i = 0 ; i < 10 ; i++ )  
         cout << vaL [ i ] << " ";  
   cout << ")." << endl;  
  
   vaMINUS = -vaL;  
   cout << "The element-by-element result of "  
        << "the operator+ is the\n valarray: ( ";  
      for ( i = 0 ; i < 10 ; i++ )  
         cout << vaMINUS [ i ] << " ";  
   cout << ")." << endl;  
}  
\* Output:   
The initial valarray is:  ( 0 0 -2 2 -4 4 -6 6 -8 8 ).  
The element-by-element result of the operator+ is the  
 valarray: ( 0 0 2 -2 4 -4 6 -6 8 -8 ).  
*\  
```  
  
##  <a name="a-namevalarrayoperator-eqa-valarrayoperator-"></a><a name="valarray__operator-_eq"></a>  valarray:: operator =  
 从数组的操作数数值 element-wise，减去指定的数值数组的元素或元素类型的值。  
  
```  
valarray<Type>& operator-=(const valarray<Type>& right);

valarray<Type>& operator-=(const Type& right);
```  
  
### <a name="parameters"></a>参数  
 ` right`  
 数值数组或等于是被减数，element-wise，操作数数值数组的操作数数值数组的元素类型的值。  
  
### <a name="return-value"></a>返回值  
 数值数组，其元素是操作数数值数组的逐元素集差异和 ` right.`  
  
### <a name="example"></a>示例  
  
```  
// valarray_op_esub.cpp  
// compile with: /EHsc  
#include <valarray>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   int i;  
  
   valarray<int> vaL ( 8 ), vaR ( 8 );  
   for ( i = 0 ; i < 8 ; i += 2 )  
      vaL [ i ] =  10;  
   for ( i = 1 ; i < 8 ; i += 2 )  
      vaL [ i ] =  0;  
   for ( i = 0 ; i < 8 ; i++ )  
      vaR [ i ] =  i;  
  
   cout << "The initial valarray is: ( ";  
      for (i = 0 ; i < 8 ; i++ )  
         cout << vaL [ i ] << " ";  
   cout << ")." << endl;  
  
   cout << "The initial  right valarray is: ( ";  
      for ( i = 0 ; i < 8 ; i++ )  
         cout << vaR [ i ] << " ";  
   cout << ")." << endl;  
  
   vaL -= vaR;  
   cout << "The element-by-element result of "  
        << "the difference is the\n valarray: ( ";  
      for ( i = 0 ; i < 8 ; i++ )  
         cout << vaL [ i ] << " ";  
   cout << ")." << endl;  
}  
\* Output:   
The initial valarray is: ( 10 0 10 0 10 0 10 0 ).  
The initial  right valarray is: ( 0 1 2 3 4 5 6 7 ).  
The element-by-element result of the difference is the  
 valarray: ( 10 -1 8 -3 6 -5 4 -7 ).  
*\  
```  
  
##  <a name="a-namevalarrayoperatoreqa-valarrayoperator"></a><a name="valarray__operator__eq"></a>  valarray:: operator / =  
 除以的数值数组操作数 element-wise 指定的数值数组的元素或元素类型的值。  
  
```  
valarray<Type>& operator/=(const valarray<Type>& right);

valarray<Type>& operator/=(const Type& right);
```  
  
### <a name="parameters"></a>参数  
 ` right`  
 数值数组或与相同的是要作为被除数，element-wise，到操作数数值数组的操作数数值数组的元素类型的值。  
  
### <a name="return-value"></a>返回值  
 其元素是操作数数值数组的逐元素集商数值除以 ` right.`  
  
### <a name="example"></a>示例  
  
```  
// valarray_op_ediv.cpp  
// compile with: /EHsc  
#include <valarray>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   int i;  
  
   valarray<double> vaL ( 6 ), vaR ( 6 );  
   for ( i = 0 ; i < 6 ; i += 2 )  
      vaL [ i ] =  100;  
   for ( i = 1 ; i < 6 ; i += 2 )  
      vaL [ i ] =  -100;  
   for ( i = 0 ; i < 6 ; i++ )  
      vaR [ i ] =  2*i;  
  
   cout << "The initial valarray is: ( ";  
      for (i = 0 ; i < 6 ; i++ )  
         cout << vaL [ i ] << " ";  
   cout << ")." << endl;  
  
   cout << "The initial Right valarray is: ( ";  
      for (i = 0 ; i < 6 ; i++ )  
         cout << vaR [ i ] << " ";  
   cout << ")." << endl;  
  
   vaL /= vaR;  
   cout << "The element-by-element result of "  
        << "the quotient is the\n valarray: ( ";  
      for (i = 0 ; i < 6 ; i++ )  
         cout << vaL [ i ] << " ";  
   cout << ")." << endl;  
}  
\* Output:   
The initial valarray is: ( 100 -100 100 -100 100 -100 ).  
The initial Right valarray is: ( 0 2 4 6 8 10 ).  
The element-by-element result of the quotient is the  
 valarray: ( 1.#INF -50 25 -16.6667 12.5 -10 ).  
*\  
```  
  
##  <a name="a-namevalarrayoperatoreqa-valarrayoperator"></a><a name="valarray__operator_eq"></a>  valarray:: operator =  
 将元素分配给直接或作为某些其他数值数组或 slice_array、 gslice_array、 mask_array 或 indirect_array 的一部分，其值未指定数值数组。  
  
```  
valarray<Type>& operator=(const valarray<Type>& right);

valarray<Type>& operator=(valarray<Type>&& right);

valarray<Type>& operator=(const Type& val);

valarray<Type>& operator=(const slice_array<Type>& _Slicearray);

valarray<Type>& operator=(const gslice_array<Type>& _Gslicearray);

valarray<Type>& operator=(const mask_array<Type>& _Maskarray);

valarray<Type>& operator=(const indirect_array<Type>& _Indarray);
```  
  
### <a name="parameters"></a>参数  
 ` right`  
 数值数组要复制到的操作数数值数组。  
  
 ` val`  
 要分配给操作数数值数组的元素的值。  
  
 `_Slicearray`  
 要被复制到操作数 valarray slice_array。  
  
 `_Gslicearray`  
 要被复制到操作数 valarray gslice_array。  
  
 `_Maskarray`  
 要被复制到操作数 valarray mask_array。  
  
 `_Indarray`  
 要被复制到操作数 valarray indirect_array。  
  
### <a name="return-value"></a>返回值  
 第一个成员运算符所控制序列的副本替换受控的序列 ` right`。  
  
 第二个成员运算符是与第一个，但它具有相同 [Rvalue 引用声明符︰ & &](../cpp/rvalue-reference-declarator-amp-amp.md)。  
  
 第三个成员运算符替换一份受控序列的每个元素 ` val`。  
  
 其余的成员的指针运算符替换由其参数，仅可由生成所选的受控序列的那些元素 [运算符 &#91; &#93;](#valarray__operator_at)。  
  
 如果替换控制序列中的值取决于初始的受控序列中的成员，则结果是成员的未定义。  
  
### <a name="remarks"></a>备注  
 如果受控序列的长度发生更改，则结果是通常未定义。 在此实现中，但是，效果是只是要使之无效的任何指针或对受控序列中的元素的引用。  
  
### <a name="example"></a>示例  
  
```  
// valarray_op_assign.cpp  
// compile with: /EHsc  
#include <valarray>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   int i;  
  
   valarray<int> va ( 10 ), vaR ( 10 );  
   for ( i = 0 ; i < 10 ; i += 1 )  
      va [ i ] = i;  
   for ( i = 0 ; i < 10 ; i+=1 )  
      vaR [ i ] = 10 -  i;  
  
   cout << "The operand valarray va is:";  
   for ( i = 0 ; i < 10 ; i++ )  
      cout << " " << va [ i ];  
   cout << endl;  
  
   cout << "The operand valarray vaR is:";  
      for ( i = 0 ; i < 10 ; i++ )  
         cout << " " << vaR [ i ];  
   cout << endl;  
  
   // Assigning vaR to va with the first member functon  
   va = vaR;  
   cout << "The reassigned valarray va is:";  
   for ( i = 0 ; i < 10 ; i++ )  
      cout << " " << va [ i ];  
   cout << endl;  
  
   // Assigning elements of value 10 to va  
   // with the second member functon  
   va = 10;  
   cout << "The reassigned valarray va is:";  
      for ( i = 0 ; i < 10 ; i++ )  
         cout << " " << va [ i ];  
   cout << endl;  
}  
\* Output:   
The operand valarray va is: 0 1 2 3 4 5 6 7 8 9  
The operand valarray vaR is: 10 9 8 7 6 5 4 3 2 1  
The reassigned valarray va is: 10 9 8 7 6 5 4 3 2 1  
The reassigned valarray va is: 10 10 10 10 10 10 10 10 10 10  
*\  
```  
  
##  <a name="a-namevalarrayoperatorata-valarrayoperator"></a><a name="valarray__operator_at"></a>  valarray:: operator]  
 返回对指定索引或指定子集处的元素或其值的引用。  
  
```  
Type& operator[](size_t _Off);

slice_array<Type> operator[](slice _Slicearray);

gslice_array<Type> operator[](const gslice& _Gslicearray);

mask_array<Type> operator[](const valarray<bool>& _Boolarray);

indirect_array<Type> operator[](const valarray<size_t>& _Indarray);

Type operator[](size_t _Off) const;

 
valarray<Type> operator[](slice _Slice) const;

 
valarray<Type> operator[](const gslice& _Gslicearray) const;

 
valarray<Type> operator[](const valarray<bool>& _Boolarray) const;

 
valarray<Type> operator[](const valarray<size_t>& _Indarray) const;
```  
  
### <a name="parameters"></a>参数  
 `_Off`  
 要将值分配到的元素的索引。  
  
 `_Slicearray`  
 指定要选择或返回到新的数值数组的子集的数值数组的 slice_array。  
  
 `_Gslicearray`  
 指定要选择或返回到新的数值数组的子集的数值数组的 gslice_array。  
  
 *_Boolarray*  
 指定要选择或返回到新的数值数组的子集的数值数组 bool_array。  
  
 `_Indarray`  
 指定要选择或返回到新的数值数组的子集的数值数组的 indirect_array。  
  
### <a name="return-value"></a>返回值  
 对一个元素或其值在指定的索引或指定的子集的引用。  
  
### <a name="remarks"></a>备注  
 成员运算符将被重载以提供了多种方法来选择序列的元素从那些由 *\****这**。 第一组五个成员的指针运算符配合使用的各种重载 [运算符 =](#valarray__operator_eq) （和其他分配运算符） 以允许选择性替换受控序列的 （切片）。 所选的元素必须存在。  
  
 在使用 _SECURE_SCL 1 编译时，如果您尝试访问的数值数组的边界以外的元素，将发生运行时错误。  有关更多信息，请参见 [Checked Iterators](../standard-library/checked-iterators.md) 。  
  
### <a name="example"></a>示例  
  请参阅示例 [slice:: slice](../standard-library/slice-class.md#slice__slice) 和 [gslice:: gslice](../standard-library/gslice-class.md#gslice__gslice) 以举例说明如何声明和使用运算符。  
  
##  <a name="a-namevalarrayoperatorxoreqa-valarrayoperator"></a><a name="valarray__operator_xor_eq"></a>  valarray:: operator ^ =  
 获取逻辑的逐元素集异或运算符 ( **异或**) 的具有指定的数值数组或元素类型的值的数组。  
  
```  
valarray<Type>& operator|=(const valarray<Type>& right);

valarray<Type>& operator|=(const Type& right);
```  
  
### <a name="parameters"></a>参数  
 ` right`  
 数值数组或值的元素类型与相同的是组合在一起的操作数数值数组、 逐元素集，通过逻辑排他锁 **异或** 与操作数数值数组。  
  
### <a name="return-value"></a>返回值  
 其元素是逻辑的逐元素集，专用 valarray **异或** 操作数数值数组和 ` right.`  
  
### <a name="remarks"></a>备注  
 排他锁逻辑或，称为 **异或**, ，具有以下语义︰ 给定元素 *e*1 和 *e*2， *e*1 **异或** *e*2 是 **true** 恰好一个元素，则返回 true; 如果 **false** 如果这两个元素均为 false 或者这两个元素，则返回 true。  
  
### <a name="example"></a>示例  
  
```  
// valarray_op_exor.cpp  
// compile with: /EHsc  
#include <valarray>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   int i;  
  
   valarray<int> vaL ( 10 ), vaR ( 10 );  
   for ( i = 0 ; i < 10 ; i += 2 )  
      vaL [ i ] =  1;  
   for ( i = 1 ; i < 10 ; i += 2 )  
      vaL [ i ] =  0;  
   for ( i = 0 ; i < 10 ; i += 3 )  
      vaR [ i ] =  i;  
   for ( i = 1 ; i < 10 ; i += 3 )  
      vaR [ i ] =  i-1;  
   for ( i = 2 ; i < 10 ; i += 3 )  
      vaR [ i ] =  i-1;  
  
   cout << "The initial operand valarray is:  ( ";  
      for (i = 0 ; i < 10 ; i++ )  
         cout << vaL [ i ] << " ";  
   cout << ")." << endl;  
  
   cout << "The  right valarray is: ( ";  
      for ( i = 0 ; i < 10 ; i++ )  
         cout << vaR [ i ] << " ";  
   cout << ")." << endl;  
  
   vaL ^= vaR;  
   cout << "The element-by-element result of "  
        << "the bitwise XOR operator^= is the\n valarray: ( ";  
      for (i = 0 ; i < 10 ; i++ )  
         cout << vaL [ i ] << " ";  
   cout << ")." << endl;  
}  
\* Output:   
The initial operand valarray is:  ( 1 0 1 0 1 0 1 0 1 0 ).  
The  right valarray is: ( 0 0 1 3 3 4 6 6 7 9 ).  
The element-by-element result of the bitwise XOR operator^= is the  
 valarray: ( 1 0 0 3 2 4 7 6 6 9 ).  
*\  
```  
  
##  <a name="a-namevalarrayoperatororeqa-valarrayoperator124"></a><a name="valarray__operator_or_eq"></a>  valarray:: operator &#124; =  
 获取按位 `OR` 数组中的元素中指定的数值数组的相应元素或元素类型的值。  
  
```  
valarray<Type>& operator|=(const valarray<Type>& right);

valarray<Type>& operator|=(const Type& right);
```  
  
### <a name="parameters"></a>参数  
 ` right`  
 数值数组或值的元素类型与相同的是组合在一起的操作数数值数组、 逐元素集，通过按位 `OR` 与操作数数值数组。  
  
### <a name="return-value"></a>返回值  
 其元素是逐元素集按位数值数组 `OR` 通过的操作数数值数组 ` right.`  
  
### <a name="remarks"></a>备注  
 按位运算仅可用于操作中的位 `char` 和 `int` 数据类型和变体，不在 **float**, ，**double**, ，**longdouble**, ，`void`, ，`bool`, ，或其他更复杂的数据类型。  
  
 按位 `OR` 有与逻辑相同的事实表 `OR` 但也适用于单个位进行运算的级别上的数据类型。 指定 bits *b*1 和 *b*2， *b*1 `OR` *b*2 是 **true** 至少一个位，则返回 true; 如果 **false** 如果两个位均为 false。  
  
### <a name="example"></a>示例  
  
```  
// valarray_class_op_bitor.cpp  
// compile with: /EHsc  
#include <valarray>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   int i;  
  
   valarray<int> vaL ( 10 ), vaR ( 10 );  
   for ( i = 0 ; i < 10 ; i += 2 )  
      vaL [ i ] =  1;  
   for ( i = 1 ; i < 10 ; i += 2 )  
      vaL [ i ] =  0;  
   for ( i = 0 ; i < 10 ; i += 3 )  
      vaR [ i ] =  i;  
   for ( i = 1 ; i < 10 ; i += 3 )  
      vaR [ i ] =  i-1;  
   for ( i = 2 ; i < 10 ; i += 3 )  
      vaR [ i ] =  i-1;  
  
   cout << "The initial operand valarray is:\n ( ";  
      for ( i = 0 ; i < 10 ; i++ )  
         cout << vaL [ i ] << " ";  
   cout << ")." << endl;  
  
   cout << "The  right valarray is:\n ( ";  
      for ( i = 0 ; i < 10 ; i++ )  
         cout << vaR [ i ] << " ";  
   cout << ")." << endl;  
  
   vaL |= vaR;  
   cout << "The element-by-element result of "  
        << "the logical OR\n operator|= is the valarray:\n ( ";  
      for (i = 0 ; i < 10 ; i++ )  
         cout << vaL [ i ] << " ";  
   cout << ")." << endl;  
}  
\* Output:   
The initial operand valarray is:  
 ( 1 0 1 0 1 0 1 0 1 0 ).  
The  right valarray is:  
 ( 0 0 1 3 3 4 6 6 7 9 ).  
The element-by-element result of the logical OR  
 operator|= is the valarray:  
 ( 1 0 1 3 3 4 7 6 7 9 ).  
*\  
```  
  
##  <a name="a-namevalarrayoperatordtora-valarrayoperator"></a><a name="valarray__operator_dtor"></a>  valarray:: operator ~  
 一元运算符，它获取的按位 **不** 数值数组中每个元素的值。  
  
```  
valarray<Type> operator~() const;
```  
  
### <a name="return-value"></a>返回值  
 按位的布尔值的数值数组 **不** 操作数数值数组的元素值。  
  
### <a name="remarks"></a>备注  
 按位运算仅可用于操作中的位 `char` 和 `int` 数据类型和变体，不在 **float**, ，**double**, ，**longdouble**, ，`void`, ，`bool` 或其他更复杂的数据类型。  
  
 按位 **不** 有与逻辑相同的事实表 **不** 但也适用于单个位进行运算的级别上的数据类型。 给定位 *b*, ，~ *b* 适用如果 *b* 为 false false 如果 *b* 为 true。 逻辑 **不**[运算符 ！](#valarray__operator_not) 计算所有非零值作为元素级上适用 **true**, ，并且结果为布尔值的数值数组。 按位 **NOToperator ~**, ，与此相反，可能会导致 0 或 1，具体取决于的按位运算的结果以外的值的数值数组。  
  
### <a name="example"></a>示例  
  
```  
// valarray_op_bitnot.cpp  
// compile with: /EHsc  
#include <valarray>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   int i;  
  
   valarray<unsigned short int> vaL1 ( 10 );  
   valarray<unsigned short int> vaNOT1 ( 10 );  
   for ( i = 0 ; i < 10 ; i += 2 )  
      vaL1 [ i ] =  i;  
   for ( i = 1 ; i < 10 ; i += 2 )  
      vaL1 [ i ] =  5*i;  
  
   cout << "The initial valarray <unsigned short int> is:  ( ";  
      for ( i = 0 ; i < 10 ; i++ )  
         cout << vaL1 [ i ] << " ";  
   cout << ")." << endl;  
  
   vaNOT1 = ~vaL1;  
   cout << "The element-by-element result of "  
        << "the bitwise NOT operator~ is the\n valarray: ( ";  
      for ( i = 0 ; i < 10 ; i++ )  
         cout << vaNOT1 [ i ] << " ";  
   cout << ")." << endl << endl;  
  
   valarray<int> vaL2 ( 10 );  
   valarray<int> vaNOT2 ( 10 );  
   for ( i = 0 ; i < 10 ; i += 2 )  
      vaL2 [ i ] =  i;  
   for ( i = 1 ; i < 10 ; i += 2 )  
      vaL2 [ i ] =  -2 * i;  
  
   cout << "The initial valarray <int> is:  ( ";  
      for ( i = 0 ; i < 10 ; i++ )  
         cout << vaL2 [ i ] << " ";  
   cout << ")." << endl;  
  
   vaNOT2 = ~vaL2;  
   cout << "The element-by-element result of "  
        << "the bitwise NOT operator~ is the\n valarray: ( ";  
      for ( i = 0 ; i < 10 ; i++ )  
         cout << vaNOT2 [ i ] << " ";  
   cout << ")." << endl;  
  
   // The negative numbers are represented using  
   // the two's complement approach, so adding one  
   // to the flipped bits returns the negative elements  
   vaNOT2 = vaNOT2 + 1;  
   cout << "The element-by-element result of "  
        << "adding one\n is the negative of the "  
        << "original elements the\n valarray: ( ";  
      for ( i = 0 ; i < 10 ; i++ )  
         cout << vaNOT2 [ i ] << " ";  
   cout << ")." << endl;  
}  
\* Output:   
The initial valarray <unsigned short int> is:  ( 0 5 2 15 4 25 6 35 8 45 ).  
The element-by-element result of the bitwise NOT operator~ is the  
 valarray: ( 65535 65530 65533 65520 65531 65510 65529 65500 65527 65490 ).  
  
The initial valarray <int> is:  ( 0 -2 2 -6 4 -10 6 -14 8 -18 ).  
The element-by-element result of the bitwise NOT operator~ is the  
 valarray: ( -1 1 -3 5 -5 9 -7 13 -9 17 ).  
The element-by-element result of adding one  
 is the negative of the original elements the  
 valarray: ( 0 2 -2 6 -4 10 -6 14 -8 18 ).  
*\  
```  
  
##  <a name="a-namevalarrayresizea-valarrayresize"></a><a name="valarray__resize"></a>  valarray:: resize  
 将 valarray 中的元素数更改为指定数量。  
  
```  
void resize(
    size_t _Newsize);

void resize(
    size_t _Newsize,   
    const Type val);
```  
  
### <a name="parameters"></a>参数  
 `_Newsize`  
 调整大小后的 valarray 中的元素数。  
  
 ` val`  
 要提供给调整大小后的 valarray 的元素的值。  
  
### <a name="remarks"></a>备注  
 第一个成员函数使用其默认构造函数初始化元素。  
  
 受控序列中元素的任何指针或引用都会失效。  
  
### <a name="example"></a>示例  
  下面的示例演示如何使用 valarray::resize 成员函数。  
  
```  
// valarray_resize.cpp  
// compile with: /EHsc  
#include <valarray>  
#include <iostream>  
  
int main()  
{  
    using namespace std;  
    int i;  
    size_t size1, sizeNew;  
  
    valarray<int> va1(10);  
    for (i = 0; i < 10; i+=1)  
        va1[i] = i;  
  
    cout << "The valarray contains ( ";  
        for (i = 0; i < 10; i++)  
            cout << va1[i] << " ";  
    cout << ")." << endl;  
  
    size1 = va1.size();  
    cout << "The number of elements in the valarray is: "  
         << size1  << "." <<endl << endl;  
  
    va1.resize(15, 10);  
  
    cout << "The valarray contains ( ";  
        for (i = 0; i < 15; i++)  
            cout << va1[i] << " ";  
    cout << ")." << endl;  
    sizeNew = va1.size();  
    cout << "The number of elements in the resized valarray is: "  
         << sizeNew  << "." <<endl << endl;  
}  
\* Output:   
The valarray contains ( 0 1 2 3 4 5 6 7 8 9 ).  
The number of elements in the valarray is: 10.  
  
The valarray contains ( 10 10 10 10 10 10 10 10 10 10 10 10 10 10 10 ).  
The number of elements in the resized valarray is: 15.  
*\  
```  
  
##  <a name="a-namevalarrayshifta-valarrayshift"></a><a name="valarray__shift"></a>  valarray:: shift  
 将指定数量的位数右移数值数组中的所有元素。  
  
```  
valarray<Type> shift(int count) const;
```  
  
### <a name="parameters"></a>参数  
 ` count`  
 数字的位数的元素将向前移动。  
  
### <a name="return-value"></a>返回值  
 新数值数组中所有元素已被都移 ` count` 到队的数值数组，左操作数数值数组中的位置相对的位置。  
  
### <a name="remarks"></a>备注  
 正值的 ` count` 将剩余元素位移 ` count` 地方，则用零填充。  
  
 值为负 ` count` 切换元素右 ` count` 地方，则用零填充。  
  
### <a name="example"></a>示例  
  
```  
// valarray_shift.cpp  
// compile with: /EHsc  
#include <valarray>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   int i;  
  
   valarray<int> va1 ( 10 ), va2 ( 10 );  
   for ( i = 0 ; i < 10 ; i += 1 )  
      va1 [ i ] =  i;  
   for ( i = 0 ; i < 10 ; i += 1 )  
      va2 [ i ] = 10 -  i;  
  
   cout << "The operand valarray va1(10) is: ( ";  
      for ( i = 0 ; i < 10 ; i++ )  
         cout << va1 [ i ] << " ";  
   cout << ")." << endl;  
  
   // A positive parameter shifts elements left  
   va1 = va1.shift ( 4 );  
   cout << "The shifted valarray va1 is: va1.shift (4) = ( ";  
      for ( i = 0 ; i < 10 ; i++ )  
         cout << va1 [ i ] << " ";  
   cout << ")." << endl;  
  
   cout << "The operand valarray va2(10) is: ( ";  
      for ( i = 0 ; i < 10 ; i++ )  
         cout << va2 [ i ] << " ";  
   cout << ")." << endl;  
  
   // A negative parameter shifts elements right  
   va2 = va2.shift ( - 4 );  
   cout << "The shifted valarray va2 is: va2.shift (-4) = ( ";  
      for ( i = 0 ; i < 10 ; i++ )  
         cout << va2 [ i ] << " ";  
   cout << ")." << endl;  
}  
\* Output:   
The operand valarray va1(10) is: ( 0 1 2 3 4 5 6 7 8 9 ).  
The shifted valarray va1 is: va1.shift (4) = ( 4 5 6 7 8 9 0 0 0 0 ).  
The operand valarray va2(10) is: ( 10 9 8 7 6 5 4 3 2 1 ).  
The shifted valarray va2 is: va2.shift (-4) = ( 0 0 0 0 10 9 8 7 6 5 ).  
*\  
```  
  
##  <a name="a-namevalarraysizea-valarraysize"></a><a name="valarray__size"></a>  valarray:: size  
 返回 valarray 中的元素数。  
  
```  
size_t size() const;
```  
  
### <a name="return-value"></a>返回值  
 操作数 valarray 中的元素数。  
  
### <a name="example"></a>示例  
  下面的示例演示如何使用 valarray::size 成员函数。  
  
```  
// valarray_size.cpp  
// compile with: /EHsc  
#include <valarray>  
#include <iostream>  
  
int main()  
{  
    using namespace std;  
    int i;  
    size_t size1, size2;  
  
    valarray<int> va1(10), va2(12);  
    for (i = 0; i < 10; i += 1)  
        va1[i] =  i;  
    for (i = 0; i < 10; i += 1)  
        va2[i] =  i;  
  
    cout << "The operand valarray va1(10) is: ( ";  
        for (i = 0; i < 10; i++)  
            cout << va1[i] << " ";  
    cout << ")." << endl;  
  
    size1 = va1.size();  
    cout << "The number of elements in the valarray va1 is: va1.size = "  
         << size1  << "." <<endl << endl;  
  
    cout << "The operand valarray va2(12) is: ( ";  
        for (i = 0; i < 10; i++)  
            cout << va2[i] << " ";  
    cout << ")." << endl;  
  
    size2 = va2.size();  
    cout << "The number of elements in the valarray va2 is: va2.size = "  
         << size2  << "." << endl << endl;  
  
    // Initializing two more elements to va2  
    va2[10] = 10;  
    va2[11] = 11;  
    cout << "After initializing two more elements,\n "  
         << "the operand valarray va2(12) is now: ( ";  
        for (i = 0; i < 12; i++)  
            cout << va2[i] << " ";  
    cout << ")." << endl;  
    cout << "The number of elements in the valarray va2 is still: "  
         << size2  << "." << endl;  
}  
\* Output:   
The operand valarray va1(10) is: ( 0 1 2 3 4 5 6 7 8 9 ).  
The number of elements in the valarray va1 is: va1.size = 10.  
  
The operand valarray va2(12) is: ( 0 1 2 3 4 5 6 7 8 9 ).  
The number of elements in the valarray va2 is: va2.size = 12.  
  
After initializing two more elements,  
 the operand valarray va2(12) is now: ( 0 1 2 3 4 5 6 7 8 9 10 11 ).  
The number of elements in the valarray va2 is still: 12.  
*\  
```  
  
##  <a name="a-namevalarraysuma-valarraysum"></a><a name="valarray__sum"></a>  valarray:: sum  
 确定为非零长度的数值数组中的所有元素的总和。  
  
```  
Type sum() const;
```  
  
### <a name="return-value"></a>返回值  
 操作数数值数组的元素的总和。  
  
### <a name="remarks"></a>备注  
 如果长度大于 1，成员函数将值添加到总和通过应用 `operator+=` 对类的元素之间 **类型**, ，因此，需要为类型的元素提供哪种运算符， **类型**。  
  
### <a name="example"></a>示例  
  
```  
// valarray_sum.cpp  
// compile with: /EHsc  
#include <valarray>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   int i;  
   int sumva = 0;  
  
   valarray<int> va ( 10 );  
   for ( i = 0 ; i < 10 ; i+=1 )  
      va [ i ] =  i;  
  
   cout << "The operand valarray va (10) is: ( ";  
      for ( i = 0 ; i < 10 ; i++ )  
         cout << va [ i ] << " ";  
   cout << ")." << endl;  
  
   sumva = va.sum ( );  
   cout << "The sum of elements in the valarray is: "  
        << sumva  << "." <<endl;  
}  
\* Output:   
The operand valarray va (10) is: ( 0 1 2 3 4 5 6 7 8 9 ).  
The sum of elements in the valarray is: 45.  
*\  
```  
  
##  <a name="a-namevalarrayswapa-valarrayswap"></a><a name="valarray__swap"></a>  valarray:: swap  
 交换两个 `valarray` 的元素。  
  
```  
void swap(valarray& right);
```  
  
### <a name="parameters"></a>参数  
  
|参数|描述|  
|---------------|-----------------|  
|` right`|一个 `valarray`，提供要交换的元素。|  
  
### <a name="remarks"></a>备注  
 成员函数交换 `*this` 和 ` right` 之间的受控序列。 它在固定时间内执行此操作，它不引发任何异常，不使任何引用、指针或指定两个受控序列中的元素的迭代器失效。  
  
##  <a name="a-namevalarrayvalarraya-valarrayvalarray"></a><a name="valarray__valarray"></a>  valarray:: valarray  
 构造特定大小的数值数组、带特定值的元素的数值数组、作为另一个数值数组的副本或另一个数值数组的子集的数值数组。  
  
```  
valarray();

explicit valarray(
    size_t Count);

valarray(
    const Type& Val,   
    size_t Count);

valarray(
    const Type* Ptr,   
    size_t Count);

valarray(
    const valarray<Type>& Right);

valarray(
    const slice_array<Type>& SliceArray);

valarray(
    const gslice_array<Type>& GsliceArray);

valarray(
    const mask_array<Type>& MaskArray);

valarray(
    const indirect_array<Type>& IndArray);

valarray(
    valarray<Type>&& Right);

valarray(
    initializer_list<Type> IList);
```  
  
### <a name="parameters"></a>参数  
 `Count`  
 数值数组要包含的元素的数目。  
  
 `Val`  
 要用于初始化数值数组中的元素的值。  
  
 `Ptr`  
 指向要用于初始化数值数组中的元素的值的指针。  
  
 `Right`  
 用于初始化新数值数组的现有数值数组。  
  
 `SliceArray`  
 其元素值要用于初始化要构造的数值数组的元素的 slice_array。  
  
 `GsliceArray`  
 其元素值要用于初始化要构造的数值数组的元素的 gslice_array。  
  
 `MaskArray`  
 其元素值要用于初始化要构造的数值数组的元素的 mask_array。  
  
 `IndArray`  
 其元素值要用于初始化要构造的数值数组的元素的 indirect_array。  
  
 `IList`  
 包含要复制的元素的 initializer_list。  
  
### <a name="remarks"></a>备注  
 第一个（默认）构造函数将对象初始化为空数组。 接下来的三个构造函数将对象初始化为 `Count` 元素的数组，如下所示：  
  
-   对于显式 `valarray(size_t Count)`，使用默认构造函数初始化每个元素。  
  
-   对于 `valarray(const Type& Val, Count)`，使用 `Val` 初始化每个元素。  
  
-   有关 `valarray(const Type* Ptr, Count)`, ，位置处的元素 `I` 使用初始化 `Ptr`[ `I`]。  
  
 每个保留的构造函数将对象初始化为数值数组 \< 类型> 参数中指定的子集确定的对象。  
  
 最后一个构造函数是到下一步相同最后一个元素，但与 [Rvalue 引用声明符︰ & &](../cpp/rvalue-reference-declarator-amp-amp.md)。  
  
### <a name="example"></a>示例  
  
```  
// valarray_ctor.cpp  
// compile with: /EHsc  
#include <valarray>  
#include <iostream>  
  
int main()  
{  
    using namespace std;  
    int i;  
  
    // The second member function  
    valarray<int> va(10);  
    for (auto i : va){  
        va[i] = 2 * (i + 1);  
    }  
  
    cout << "The operand valarray va is:\n(";  
    for (auto i : va) {  
        cout << " " << va[i];  
    }  
    cout << " )" << endl;  
  
    slice Slice(2, 4, 3);  
  
    // The fifth member function  
    valarray<int> vaSlice = va[Slice];  
  
    cout << "The new valarray initialized from the slice is vaSlice ="  
        << "\nva[slice( 2, 4, 3)] = (";  
    for (int i = 0; i < 3; i++) {  
        cout << " " << vaSlice[i];  
    }  
    cout << " )" << endl;  
  
    valarray<int> va2{{ 1, 2, 3, 4 }};  
    for (auto& v : va2){  
        cout << v << " ";  
    }  
    cout << endl;  
}  
  
```  
  
```Output  
The operand valarray va is:( 0 2 2 2 2 2 2 2 2 2 )The new valarray initialized from the slice is vaSlice =va[slice( 2, 4, 3)] = ( 0 0 0 )1 2 3 4  
```  
  
##  <a name="a-namevalarrayvaluetypea-valarrayvaluetype"></a><a name="valarray__value_type"></a>  valarray:: value_type  
 一种表示存储在数值数组中元素的类型的类型。  
  
```  
typedef Type value_type;  
```  
  
### <a name="remarks"></a>备注  
 类型是模板参数的同义词 **类型**。  
  
### <a name="example"></a>示例  
  
```  
// valarray_value_type.cpp  
// compile with: /EHsc  
#include <valarray>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   int i;  
   valarray<int> va ( 10 );  
   for ( i = 0 ; i < 10 ; i += 2 )  
      va [ i ] =  i;  
   for ( i = 1 ; i < 10 ; i += 2 )  
      va [ i ] =  -1;  
  
   cout << "The initial operand valarray is:  ( ";  
      for ( i = 0 ; i < 10 ; i++ )  
         cout << va [ i ] << " ";  
   cout << ")." << endl;  
  
   // value_type declaration and initialization:  
   valarray<int>::value_type Right = 10;  
  
   cout << "The decalared value_type Right is: "   
           << Right << endl;  
   va *= Right;  
   cout << "The resulting valarray is:  ( ";  
      for ( i = 0 ; i < 10 ; i++ )  
         cout << va [ i ] << " ";  
   cout << ")." << endl;  
}  
\* Output:   
The initial operand valarray is:  ( 0 -1 2 -1 4 -1 6 -1 8 -1 ).  
The decalared value_type Right is: 10  
The resulting valarray is:  ( 0 -10 20 -10 40 -10 60 -10 80 -10 ).  
*\  
```  
  
## <a name="see-also"></a>另请参阅  
 [C + + 标准库中的线程安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)


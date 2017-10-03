---
title: "slice 类 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- valarray/std::slice
- valarray/std::slice::size
- valarray/std::slice::start
- valarray/std::slice::stride
dev_langs:
- C++
helpviewer_keywords:
- std::slice [C++]
- std::slice [C++], size
- std::slice [C++], start
- std::slice [C++], stride
ms.assetid: 00f0b03d-d657-4b81-ba53-5a9034bb2bf2
caps.latest.revision: 23
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: MT
ms.sourcegitcommit: 65f4e356ad0d46333b0d443d0fd6ac0b9f2b6f58
ms.openlocfilehash: f2fdeb6f751fa40d74c2557341279529bca6a8d7
ms.contentlocale: zh-cn
ms.lasthandoff: 10/03/2017

---
# <a name="slice-class"></a>slice 类
valarray 的实用程序类，用于定义父级 valarray 的一维子集。 如果 valarray 被视为一个其所有元素都在一个数组中的二维矩阵，则切片会将一个维度中的向量从二维数组中提取出来。  
  
## <a name="remarks"></a>备注  
 该类存储了将 [slice_array](../standard-library/slice-array-class.md) 类型的对象特征化的参数。当类切片显示为 [valarray](../standard-library/valarray-class.md#op_at)**\<Type** 类的对象的自变量时，会间接构造 valarray 的子集。 存储的值（用于指定从父级 valarray 选择的子集）包括：  
  
-   valarray 中的起始索引。  
  
-   总长度或切片中的元素数目。  
  
-   跨距，或 valarray 中元素的后续索引之间的距离。  
  
 如果由切片定义的集为常量 valarray 的子集，则该切片将是新的 valarray。 如果由切片定义的集为非常量 valarray 的子集，则该切片将具有对原始 valarray 的引用语义。 非常量 valarray 的评估机制节省了时间和内存。  
  
 仅当由切片定义的源和目标子集都是不重复的并且所有索引都是有效的，才可以保证对 valarray 的操作。  
  
### <a name="constructors"></a>构造函数  
  
|||  
|-|-|  
|[slice](#slice)|定义 `valarray` 的一个子集，该 valarray 包含一些等距分隔的元素，并且在指定的元素开始。|  
  
### <a name="member-functions"></a>成员函数  
  
|||  
|-|-|  
|[size](#size)|查找 `valarray` 的切片中的元素数目。|  
|[start](#start)|查找 `valarray` 的切片的起始索引。|  
|[stride](#stride)|查找 `valarray` 的切片中元素之间的距离。|  
  
## <a name="requirements"></a>要求  
 **标头：**\<valarray>  
  
 **命名空间：** std  
  
##  <a name="size"></a>  slice::size  
 查找 valarray 切片中的元素数。  
  
```  
size_t size() const;
```  
  
### <a name="return-value"></a>返回值  
 valarray 切片中的元素数。  
  
### <a name="example"></a>示例  
  
```cpp  
// slice_size.cpp  
// compile with: /EHsc  
#include <valarray>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   int i;  
   size_t sizeVA, sizeVAR;  
  
   valarray<int> va ( 20 ), vaResult;  
   for ( i = 0 ; i < 20 ; i += 1 )  
      va [ i ] =  i+1;  
  
   cout << "The operand valarray va is:\n ( ";  
      for ( i = 0 ; i < 20 ; i++ )  
         cout << va [ i ] << " ";  
   cout << ")." << endl;  
  
   sizeVA = va.size ( );  
   cout << "The size of the valarray is: "  
        << sizeVA << "." << endl << endl;  
  
   slice vaSlice ( 3 , 6 , 3 );  
   vaResult = va [ vaSlice ];  
  
   cout << "The slice of valarray va is vaResult = "  
        << "va[slice( 3, 6, 3)] =\n ( ";  
      for ( i = 0 ; i < 6 ; i++ )  
         cout << vaResult [ i ] << " ";  
   cout << ")." << endl;  
  
   sizeVAR = vaSlice.size ( );  
   cout << "The size of slice vaSlice is: "  
        << sizeVAR << "." << endl;  
}  
```  
  
```Output  
The operand valarray va is:  
 ( 1 2 3 4 5 6 7 8 9 10 11 12 13 14 15 16 17 18 19 20 ).  
The size of the valarray is: 20.  
  
The slice of valarray va is vaResult = va[slice( 3, 6, 3)] =  
 ( 4 7 10 13 16 19 ).  
The size of slice vaSlice is: 6.  
```  
  
##  <a name="slice"></a>  slice::slice  
 定义 valarray 的一个子集，该 valarray 包含许多等距分隔的元素，并且从指定的元素开始。  
  
```  
slice();

slice(
    size_t _StartIndex,  
    size_t _Len,   
    size_t stride);
```  
  
### <a name="parameters"></a>参数  
 `_StartIndex`  
 子集中第一个元素的 valarray 索引。  
  
 `_Len`  
 子集中的元素数。  
  
 `stride`  
 子集中元素间的距离。  
  
### <a name="return-value"></a>返回值  
 默认构造函数对于起始索引、总长度和 stride 都存储为零。 第二个构造函数对于起始索引存储为 `_StartIndex`，对于总长度存储为 `_Len`，对于跨距存储为 `stride`。  
  
### <a name="remarks"></a>备注  
 跨距可为负数。  
  
### <a name="example"></a>示例  
  
```cpp  
// slice_ctor.cpp  
// compile with: /EHsc  
#include <valarray>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   int i;  
  
   valarray<int> va ( 20 ), vaResult;  
   for ( i = 0 ; i < 20 ; i+=1 )  
      va [ i ] =  2 * (i + 1 );  
  
   cout << "The operand valarray va is:\n( ";  
      for ( i = 0 ; i < 20 ; i++ )  
         cout << va [ i ] << " ";  
   cout << ")." << endl;  
  
   slice vaSlice ( 1 , 7 , 3 );  
   vaResult = va [ vaSlice ];  
  
   cout << "\nThe slice of valarray va is vaResult:"  
        << "\nva[slice( 1, 7, 3)] = ( ";  
      for ( i = 0 ; i < 7 ; i++ )  
         cout << vaResult [ i ] << " ";  
   cout << ")." << endl;  
}  
```  
  
```Output  
The operand valarray va is:  
( 2 4 6 8 10 12 14 16 18 20 22 24 26 28 30 32 34 36 38 40 ).  
  
The slice of valarray va is vaResult:  
va[slice( 1, 7, 3)] = ( 4 10 16 22 28 34 40 ).  
```  
  
##  <a name="start"></a>  slice::start  
 查找 valarray 切片的起始索引。  
  
```  
size_t start() const;
```  
  
### <a name="return-value"></a>返回值  
 valarray 切片的起始索引。  
  
### <a name="example"></a>示例  
  
```cpp  
// slice_start.cpp  
// compile with: /EHsc  
#include <valarray>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   int i;  
   size_t startVAR;  
  
   valarray<int> va ( 20 ), vaResult;  
   for ( i = 0 ; i < 20 ; i += 1 )  
      va [ i ] = i+1;  
  
   cout << "The operand valarray va is:\n ( ";  
      for ( i = 0 ; i < 20 ; i++ )  
         cout << va [ i ] << " ";  
   cout << ")." << endl;  
  
   slice vaSlice ( 3 , 6 , 3 );  
   vaResult = va [ vaSlice ];  
  
   cout << "The slice of valarray va is vaResult = "  
        << "va[slice( 3, 6, 3)] =\n ( ";  
      for ( i = 0 ; i < 6 ; i++ )  
         cout << vaResult [ i ] << " ";  
   cout << ")." << endl;  
  
   startVAR = vaSlice.start ( );  
   cout << "The start index of slice vaSlice is: "  
        << startVAR << "." << endl;  
}  
```  
  
```Output  
The operand valarray va is:  
 ( 1 2 3 4 5 6 7 8 9 10 11 12 13 14 15 16 17 18 19 20 ).  
The slice of valarray va is vaResult = va[slice( 3, 6, 3)] =  
 ( 4 7 10 13 16 19 ).  
The start index of slice vaSlice is: 3.  
```  
  
##  <a name="stride"></a>  slice::stride  
 查找 valarray 切片中元素之间的距离。  
  
```  
size_t stride() const;
```  
  
### <a name="return-value"></a>返回值  
 valarray 切片中元素之间的距离。  
  
### <a name="example"></a>示例  
  
```cpp  
// slice_stride.cpp  
// compile with: /EHsc  
#include <valarray>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   int i;  
   size_t strideVAR;  
  
   valarray<int> va ( 20 ), vaResult;  
   for ( i = 0 ; i < 20 ; i += 1 )  
      va [ i ] =  3 * ( i + 1 );  
  
   cout << "The operand valarray va is:\n ( ";  
      for ( i = 0 ; i < 20 ; i++ )  
         cout << va [ i ] << " ";  
   cout << ")." << endl;  
  
   slice vaSlice ( 4 , 5 , 3 );  
   vaResult = va [ vaSlice ];  
  
   cout << "The slice of valarray va is vaResult = "  
        << "va[slice( 4, 5, 3)] =\n ( ";  
      for ( i = 0 ; i < 5 ; i++ )  
         cout << vaResult [ i ] << " ";  
   cout << ")." << endl;  
  
   strideVAR = vaSlice.stride ( );  
   cout << "The stride of slice vaSlice is: "  
        << strideVAR << "." << endl;  
}  
```  
  
```Output  
The operand valarray va is:  
 ( 3 6 9 12 15 18 21 24 27 30 33 36 39 42 45 48 51 54 57 60 ).  
The slice of valarray va is vaResult = va[slice( 4, 5, 3)] =  
 ( 15 24 33 42 51 ).  
The stride of slice vaSlice is: 3.  
```  
  
## <a name="see-also"></a>另请参阅  
 [C++ 标准库中的线程安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)



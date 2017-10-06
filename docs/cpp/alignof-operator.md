---
title: "__alignof 运算符 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- alignas_cpp
- __alignof_cpp
- alignof_cpp
dev_langs:
- C++
helpviewer_keywords:
- alignas [C++]
- alignment of structures
- __alignof keyword [C++]
- alignof [C++]
- types [C++], alignment requirements
ms.assetid: acb1eed7-6398-40bd-b0c5-684ceb64afbc
caps.latest.revision: 11
author: mikeblome
ms.author: mblome
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
ms.translationtype: HT
ms.sourcegitcommit: 6ffef5f51e57cf36d5984bfc43d023abc8bc5c62
ms.openlocfilehash: 66ec7ff196a4f22aec043d8b76faf0189e05cd0f
ms.contentlocale: zh-cn
ms.lasthandoff: 09/25/2017

---
# <a name="alignof-operator"></a>__alignof 运算符
C++11 引入 `alignof` 运算符，该运算符返回指定类型的对齐方式（以字节为单位）。 为实现最大的可移植性，应使用 alignof 运算符，而不是特定于 Microsoft 的 __alignof 运算符。  
  
 **Microsoft 专用**  
  
 返回类型的值**size_t** ，它是类型的对齐要求。  
  
## <a name="syntax"></a>语法  
  
```  
  
      __alignof(   
   type    
)  
```  
  
## <a name="remarks"></a>备注  
 例如:   
  
|Expression|值|  
|----------------|-----------|  
|**__alignof (char)**|1|  
|**__alignof （短）**|2|  
|**__alignof (int)**|4|  
|**__alignof ( \__int64)**|8|  
|**__alignof (float)**|4|  
|**__alignof （双精度型）**|8|  
|**__alignof (char\* )**|4|  
  
 `__alignof` 值与基本类型的 `sizeof` 的值相同。 但是，请考虑该示例：  
  
```  
typedef struct { int a; double b; } S;  
// __alignof(S) == 8  
```  
  
 在该示例中，`__alignof` 值是结构中的最大元素的对齐要求。  
  
 同样，  
  
```  
typedef __declspec(align(32)) struct { int a; } S;  
```  
  
 `__alignof(S)` 等于 `32`。  
  
 `__alignof` 的用途之一是作为某个内存分配例程的参数。 例如，假定下面定义的结构 `S`，您可以调用名为 `aligned_malloc` 的内存分配例程以在特定对齐边界上分配内存。  
  
```  
typedef __declspec(align(32)) struct { int a; double b; } S;  
int n = 50; // array size  
S* p = (S*)aligned_malloc(n * sizeof(S), __alignof(S));  
```  
  
 有关修改对齐方式的详细信息，请参阅：  
  
-   [pack](../preprocessor/pack.md)  
  
-   [align](../cpp/align-cpp.md)  
  
-   [__unaligned](../cpp/unaligned.md)  
  
-   [/Zp （结构成员对齐）](../build/reference/zp-struct-member-alignment.md)  
  
-   [结构对齐示例](../build/examples-of-structure-alignment.md)(特定于 x64)  
  
 有关 x86 和 x64 代码中的对齐方式的差异的详细信息，请参阅：  
  
-   [与 x86 编译器冲突](../build/conflicts-with-the-x86-compiler.md)  
  
**结束 Microsoft 专用**  
  
## <a name="see-also"></a>另请参阅  
 [使用一元运算符的表达式](../cpp/expressions-with-unary-operators.md)   
 [关键字](../cpp/keywords-cpp.md)

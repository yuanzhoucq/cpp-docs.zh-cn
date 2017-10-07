---
title: "裸 （c + +） |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- naked_cpp
dev_langs:
- C++
helpviewer_keywords:
- __declspec keyword [C++], naked
- naked __declspec keyword
ms.assetid: 69723241-05e1-439b-868e-20a83a16ab6d
caps.latest.revision: 12
author: mikeblome
ms.author: mblome
manager: ghogen
ms.translationtype: HT
ms.sourcegitcommit: 6ffef5f51e57cf36d5984bfc43d023abc8bc5c62
ms.openlocfilehash: 8d22ae96facd89f16ebabb74ba46a9172cc4d2e9
ms.contentlocale: zh-cn
ms.lasthandoff: 09/25/2017

---
# <a name="naked-c"></a>naked (C++)
**Microsoft 专用**  
  
 函数声明与`naked`特性，因此编译器生成不带 prolog 和 epilog 代码。 利用此功能，可以使用内联汇编程序代码编写您自己的 prolog/epilog 代码序列。 裸函数对于编写虚拟设备驱动程序特别有用。  请注意，`naked` 特性仅在 x86 和 ARM 上有效，且不可用于 [!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)] 上。  
  
## <a name="syntax"></a>语法  
  
```  
__declspec(naked) declarator  
```  
  
## <a name="remarks"></a>备注  
 因为`naked`特性仅与函数定义相关且不是类型修饰符，裸函数必须使用扩展的特性语法和[__declspec](../cpp/declspec.md)关键字。  
  

 编译器无法生成使用裸特性，标记的函数的内联函数，即使此函数也标记与[__forceinline](inline-functions-cpp.md)关键字。  

  
 如果编译器将发出错误`naked`特性应用于非成员方法的定义之外的任何内容。  
  
## <a name="examples"></a>示例  
 此代码定义一个函数与`naked`属性：  
  
```  
__declspec( naked ) int func( formal_parameters ) {}  
```  
  
 或者，或者：  
  
```  
#define Naked __declspec( naked )  
Naked int func( formal_parameters ) {}  
```  
  
 `naked` 特性仅影响函数的 prolog 和 epilog 序列的编译器代码生成的性质。 它不影响为调用这些函数而生成的代码。 因此，`naked` 特性不被视为函数的类型的一部分，并且函数指针不能具有 `naked` 特性。 此外，`naked` 特性不能应用于数据定义。 例如，此代码示例将生成错误：  
  
```  
__declspec( naked ) int i;       // Error--naked attribute not  
                                 // permitted on data declarations.  
```  
  
 `naked` 特性仅与函数的定义相关，且无法在函数原型中指定。 例如，此声明将生成一个编译器错误：  
  
```  
__declspec( naked ) int func();  // Error--naked attribute not   
                                 // permitted on function declarations  
```  
  
 **结束 Microsoft 专用**  
  
## <a name="see-also"></a>另请参阅  
 [__declspec](../cpp/declspec.md)   
 [关键字](../cpp/keywords-cpp.md)   
 [Naked 函数调用](../cpp/naked-function-calls.md)

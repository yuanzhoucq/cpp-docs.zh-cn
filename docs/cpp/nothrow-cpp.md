---
title: "nothrow （c + +） |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- nothrow_cpp
dev_langs:
- C++
helpviewer_keywords:
- __declspec keyword [C++], nothrow
- nothrow __declspec keyword
ms.assetid: 0a475139-459c-4ec6-99e8-7ecd0d7f44a3
caps.latest.revision: 7
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
ms.openlocfilehash: c74490229e2ef54e7947f5e8fedda6057ecccb70
ms.contentlocale: zh-cn
ms.lasthandoff: 09/25/2017

---
# <a name="nothrow-c"></a>nothrow (C++)
**Microsoft 专用**  
  
 `__declspec` 扩展特性，可在函数声明中使用。  
  
## <a name="syntax"></a>语法  
  
```  
  
return-type __declspec(nothrow) [call-convention] function-name ([argument-list])  
```  
  
## <a name="remarks"></a>备注  
 此特性告知编译器，声明的函数及其调用的函数从不引发异常。 利用当前默认的同步异常处理模式，编译器可以消除跟踪此类函数中的某些不可展开的对象的生命周期的机制，从而显著减小代码大小。 在使用以下预处理器指令的情况下，下面的三个函数声明是等效的：  
  
```  
#define WINAPI __declspec(nothrow) __stdcall   
  
void WINAPI f1();  
void __declspec(nothrow) __stdcall f2();  
void __stdcall f3() throw();  
```  
  
 使用 `void __declspec(nothrow) __stdcall f2();` 有一个好处，即，您可以使用 API 定义（如 `#define` 语句阐释的定义）在一组函数上轻松指定 `nothrow`。 第三个声明 `, void __stdcall f3() throw();` 是由 C++ 标准定义的语法。  
  
  
 **结束 Microsoft 专用**  
  
## <a name="see-also"></a>另请参阅  
 [__declspec](../cpp/declspec.md)   
 [关键字](../cpp/keywords-cpp.md)

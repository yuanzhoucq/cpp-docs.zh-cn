---
title: "编译器警告 C4958 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- C4958
dev_langs:
- C++
helpviewer_keywords:
- C4958
ms.assetid: e79b9e9c-d572-4a3a-a3b6-60962b70864a
caps.latest.revision: 12
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Machine Translation
ms.sourcegitcommit: 0d9cbb01d1ad0f2ea65d59334cb88140ef18fce0
ms.openlocfilehash: 7deb92709adbb5a10148c092985e9a7c9f463c0c
ms.lasthandoff: 04/12/2017

---
# <a name="compiler-warning-c4958"></a>编译器警告 C4958
“operation”: 指针算法是不可验证的  
  
 使用指针算法将产生不可验证的映像。  
  
 有关详细信息，请参阅[纯代码和可验证代码 (C + + /cli CLI)](../../dotnet/pure-and-verifiable-code-cpp-cli.md)。  
  
 此警告作为错误发出，并且可以禁用，[警告](../../preprocessor/warning.md)杂注或[/wd](../../build/reference/compiler-option-warning-level.md)编译器选项。  
  
 下面的示例生成 C4958：  
  
```  
// C4958.cpp  
// compile with: /clr:safe  
// #pragma warning( disable : 4958 )  
using namespace System;  
  
int main( ) {  
   Int32 arr[] = new Int32[10];  
   Int32* p = &arr[0];  
   p++;   // C4958  
}  
```  
  
 编译器使用指针算法实现数组操作。 因此，不可验证本机数组；请改用 CLR 数组。 有关详细信息，请参阅[数组](../../windows/arrays-cpp-component-extensions.md)。  
  
 下面的示例生成 C4958：  
  
```  
// C4958b.cpp  
// compile with: /clr:safe  
// #pragma warning( disable : 4958 )  
  
int main() {  
   int array[5];  
   array[4] = 0;   // C4958  
}  
```

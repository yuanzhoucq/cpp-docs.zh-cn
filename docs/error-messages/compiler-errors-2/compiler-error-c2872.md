---
title: "编译器错误 C2872 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C2872
dev_langs:
- C++
helpviewer_keywords:
- C2872
ms.assetid: c619ef97-6e0e-41d7-867c-f8d28a07d553
caps.latest.revision: 11
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
translationtype: Machine Translation
ms.sourcegitcommit: 65e7a7bd56096fbeec61b651ab494d82edef9c90
ms.openlocfilehash: d53dbd9429ba3c1a525b85a3ef9f2e70152ddfa2
ms.lasthandoff: 02/24/2017

---
# <a name="compiler-error-c2872"></a>编译器错误 C2872
symbol︰ 不明确的符号  
  
编译器无法确定所引用的符号。  
  
如果标头文件包含，则会出现 C2872 [using 指令](../../cpp/namespaces-cpp.md#using_directives)，包含了一个后续的头文件，并包含在指定的命名空间中也是一种`using`指令。 指定`using`指令仅在所有标头文件指定与后`#include`。  
  
 有关 C2872 的详细信息，请参阅知识库文章[PRB︰ 编译器错误在您使用 #import 具有 Visual c + +.NET 中的 XML](http://support.microsoft.com/kb/316317)和["错误 C2872: 平台︰ 不明确的符号"Visual Studio 2013 中使用 Windows::Foundation::Metadata 命名空间时，错误消息](https://support.microsoft.com/kb/2890859)。  
  
## <a name="example"></a>示例  
 下面的示例生成 C2872:  
  
```cpp  
// C2872.cpp  
namespace A {  
   int i;  
}  
  
using namespace A;  
int i;  
int main() {  
   ::i++;   // ok  
   A::i++;   // ok  
   i++;   // C2872 ::i or A::i?  
}  
```

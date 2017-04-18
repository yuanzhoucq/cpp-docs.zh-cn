---
title: "编译器警告 （等级 3） C4792 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- C4792
dev_langs:
- C++
helpviewer_keywords:
- C4792
ms.assetid: c047ce69-a622-44e1-9425-d41aa9261c61
caps.latest.revision: 9
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
ms.openlocfilehash: 7886d2b28c9120e2e764dedd0ecc72265fe91be5
ms.lasthandoff: 04/12/2017

---
# <a name="compiler-warning-level-3-c4792"></a>编译器警告（等级 3）C4792
函数“function”使用 sysimport 声明并从本机代码引用；需要链接导入库  
  
 从非托管函数调用通过 DllImport 导入到程序中的本机函数。 因此，你必须链接到该 DLL 的导入库。  
  
 无法在代码中解决该警告，也无法通过改变编译方式来解决。 使用[警告](../../preprocessor/warning.md)杂注来禁用此警告。  
  
 以下示例生成 C4792：  
  
```  
// C4792.cpp  
// compile with: /clr /W3  
// C4792 expected  
using namespace System::Runtime::InteropServices;  
[DllImport("msvcrt")]  
extern "C" int __cdecl puts(const char *);  
int main() {}  
  
// Uncomment the following line to resolve.  
// #pragma warning(disable : 4792)  
#pragma unmanaged  
void func(void){  
   puts("test");  
}  
```

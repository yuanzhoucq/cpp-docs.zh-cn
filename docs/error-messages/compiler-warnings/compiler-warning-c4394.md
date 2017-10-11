---
title: "编译器警告 C4394 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C4394
dev_langs:
- C++
helpviewer_keywords:
- C4394
ms.assetid: 5de94de0-17e3-4e7c-92f4-5c3c1b825120
caps.latest.revision: 11
author: corob-msft
ms.author: corob
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 35b46e23aeb5f4dbfd2a0dd44b906389dd5bfc88
ms.openlocfilehash: 5b201b95a2ec9d43c904de35ca581efbf31b7526
ms.contentlocale: zh-cn
ms.lasthandoff: 10/10/2017

---
# <a name="compiler-warning-c4394"></a>编译器警告 C4394
function： 不应与 __declspec （dllexport） 标记为每个 appdomain 符号  
  
 使用标记的函数[appdomain](../../cpp/appdomain.md) `__declspec`修饰符编译为 MSIL （不，为本机） 和导出表 ([导出](../../windows/export.md)`__declspec`修饰符) 不支持对托管的函数。  
  
 您可以将托管函数声明为具有公共可访问性。 有关详细信息，请参阅[键入可见性](../../dotnet/how-to-define-and-consume-classes-and-structs-cpp-cli.md#BKMK_Type_visibility)和[成员的可见性](../../dotnet/how-to-define-and-consume-classes-and-structs-cpp-cli.md#BKMK_Member_visibility)。  
  
 C4394 始终作为错误发出。  你可以关闭此警告，其中包含`#pragma warning`或**/wd**; 请参阅[警告](../../preprocessor/warning.md)或[/w、 /w0 取消显示、 /W1、 /W2、 /W3、 /W4、 /w1、 /w2、 /w3、 /w4，/Wall、 /wd，/ 我们 /wo，/Wv，/WX （警告级别）](../../build/reference/compiler-option-warning-level.md)有关详细信息。  
  
## <a name="example"></a>示例  
 下面的示例生成 C4394。  
  
```  
// C4394.cpp  
// compile with: /clr /c  
__declspec(dllexport) __declspec(appdomain) int g1 = 0;   // C4394  
__declspec(dllexport) int g2 = 0;   // OK  
```

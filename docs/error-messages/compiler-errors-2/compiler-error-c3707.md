---
title: 编译器错误 C3707 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3707
dev_langs:
- C++
helpviewer_keywords:
- C3707
ms.assetid: ac63a5dd-7a4b-48d2-9f2a-be9cb090134c
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 7268f584d9f269b4f2f15b837379ec12ab0185d8
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33273720"
---
# <a name="compiler-error-c3707"></a>编译器错误 C3707
function： 调度接口方法必须具有一个 dispid  
  
 如果你使用`dispinterface`方法，你必须将其分配`dispid`。 若要修复此错误，分配`dispid`到`dispinterface`方法，例如，通过取消注释`id`在下面的示例方法的特性。 有关详细信息，请参阅属性[调度接口](../../windows/dispinterface.md)和[id](../../windows/id.md)。  
  
 下面的示例生成 C3707:  
  
```  
// C3707.cpp  
#include <atlbase.h>  
#include <atlcom.h>  
#include <atlctl.h>  
  
[module(name="xx")];  
[dispinterface]  
__interface IEvents : IDispatch  
{  
   HRESULT event1([in] int i);   // C3707  
   // try the following line instead  
   // [id(1)] HRESULT event1([in] int i);  
};  
  
int main() {  
}  
```
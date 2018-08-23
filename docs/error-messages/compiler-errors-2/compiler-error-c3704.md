---
title: 编译器错误 C3704 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3704
dev_langs:
- C++
helpviewer_keywords:
- C3704
ms.assetid: ee40ea35-a214-4dec-9489-d7f155dd0ac2
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 2b3b1f255852def5e04d75751b0a902fb7072545
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33264137"
---
# <a name="compiler-error-c3704"></a>编译器错误 C3704
function: vararg 方法不能激发事件  
  
 你尝试使用[__event](../../cpp/event.md) vararg 方法。 若要修复此错误，请替换`fireEvent(int i, ...)`调用`fireEvent(int i)`调用下面的代码示例中所示。  
  
 下面的示例生成 C3704:  
  
```  
// C3704.cpp  
[ event_source(native) ]  
class CEventSrc {  
   public:  
      __event void fireEvent(int i, ...);   // C3704  
      // try the following line instead:  
      // __event void fireEvent(int i);  
};  
  
int main() {  
}  
```
---
title: "编译器错误 C3295 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- C3295
dev_langs:
- C++
helpviewer_keywords:
- C3295
ms.assetid: 83f0aa4d-0e0a-4905-9f66-fcf9991fc07a
caps.latest.revision: 4
author: corob-msft
ms.author: corob
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 35b46e23aeb5f4dbfd2a0dd44b906389dd5bfc88
ms.openlocfilehash: b72e4839341006d2058c21a1523b0d7567f51696
ms.contentlocale: zh-cn
ms.lasthandoff: 10/10/2017

---
# <a name="compiler-error-c3295"></a>编译器错误 C3295
“#pragma pragma”只能在全局范围或命名空间范围上使用  
  
 部分杂注不能在函数中使用。  请参阅[杂注指令和 __Pragma 关键字](../../preprocessor/pragma-directives-and-the-pragma-keyword.md)有关详细信息。  
  
## <a name="example"></a>示例  
 以下示例生成 C3295。  
  
```  
// C3295.cpp  
int main() {  
   #pragma managed   // C3295  
}  
```

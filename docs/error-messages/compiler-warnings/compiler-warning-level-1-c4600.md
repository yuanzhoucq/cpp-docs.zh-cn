---
title: 编译器警告 （等级 1） C4600 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4600
dev_langs:
- C++
helpviewer_keywords:
- C4600
ms.assetid: f023a2a1-7fc4-463f-a434-dc93fcd3f4e9
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 7866268cffce31467e5306a969e981f310e91ace
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33287509"
---
# <a name="compiler-warning-level-1-c4600"></a>编译器警告（等级 1）C4600
\#杂注 macro name： 应为有效的非空字符串  
  
 推送或弹出使用宏名称时，不能指定空字符串[pop_macro](../../preprocessor/pop-macro.md)或[push_macro](../../preprocessor/push-macro.md)。  
  
 下面的示例生成 C4600:  
  
```  
// C4600.cpp  
// compile with: /W1  
int main()  
{  
   #pragma push_macro("")   // C4600 passing an empty string  
}  
```
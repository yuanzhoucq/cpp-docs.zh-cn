---
title: 编译器警告 （等级 4） C4032 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4032
dev_langs:
- C++
helpviewer_keywords:
- C4032
ms.assetid: 70dd0c85-0239-43f9-bb06-507f6a57d206
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: eb61588c12378972194305d979ecdd89140ac6f6
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33291682"
---
# <a name="compiler-warning-level-4-c4032"></a>编译器警告 （等级 4） C4032
形参数字具有不同的类型提升时  
  
 参数类型不兼容，通过默认提升，与以前的声明中的类型。  
  
 这是 ANSI C 中的错误 ([/Za](../../build/reference/za-ze-disable-language-extensions.md)) 和 Microsoft 扩展 (/Ze) 下的警告。  
  
## <a name="example"></a>示例  
  
```  
// C4032.c  
// compile with: /W4  
void func();  
void func(char);   // C4032, char promotes to int  
  
int main()  
{  
}  
```
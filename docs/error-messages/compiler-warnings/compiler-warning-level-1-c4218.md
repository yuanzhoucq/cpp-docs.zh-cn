---
title: 编译器警告 （等级 1） C4218 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4218
dev_langs:
- C++
helpviewer_keywords:
- C4218
ms.assetid: d6c3cd90-4518-49e9-ae86-4ba9e2761d98
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 88b27af84c390760274bb20665eec4452c8e7072
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33279745"
---
# <a name="compiler-warning-level-1-c4218"></a>编译器警告（等级 1）C4218
使用的非标准扩展： 必须指定至少一个存储类或类型  
  
 具有默认的 Microsoft 扩展 (/Ze) 中，可以声明一个变量，而不指定某个类型或存储类。 默认类型为 `int`。  
  
## <a name="example"></a>示例  
  
```  
// C4218.c  
// compile with: /W4  
i;  // C4218  
  
int main()  
{  
}  
```  
  
 此类声明是在 ANSI 兼容性无效 ([/Za](../../build/reference/za-ze-disable-language-extensions.md))。
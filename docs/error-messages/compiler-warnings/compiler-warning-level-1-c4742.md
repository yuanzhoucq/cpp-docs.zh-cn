---
title: 编译器警告 (等级 1) C4742 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4742
dev_langs:
- C++
helpviewer_keywords:
- C4742
ms.assetid: e520881d-1eeb-48b1-9df0-8017ee8ba076
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d9c5c891699e89b177f9a3c070a95f496e2c77ac
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33282075"
---
# <a name="compiler-warning-level-1-c4742"></a>编译器警告（等级 1）C4742
var 具有 file1 和 file2 中的不同对齐方式： 编号和编号  
  
 已在两个文件中定义或引用的外部变量，这些文件中具有不同的对齐方式。 当编译器发现时，发出此警告`__alignof`中为变量*file1*区别`__alignof`中为变量*file2*。 这可以通过在不同文件中声明变量时使用不兼容的类型或使用不匹配造成`#pragma pack`在不同的文件。  
  
 若要解决此警告，请使用相同的类型定义，或使用不同的变量名称。  
  
 有关详细信息，请参阅[包](../../preprocessor/pack.md)和[__alignof 运算符](../../cpp/alignof-operator.md)。  
  
## <a name="example"></a>示例  
 这是定义的类型的第一个文件。  
  
```  
// C4742a.c  
// compile with: /c  
struct X {  
   char x, y, z, w;  
} global;  
```  
  
## <a name="example"></a>示例  
 下面的示例生成 C4742。  
  
```  
// C4742b.c  
// compile with: C4742a.c /W1 /GL  
// C4742 expected  
extern struct X {  
   int a;  
} global;  
  
int main() {  
   global.a = 0;  
}  
```
---
title: 编译器警告 C4430 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4430
dev_langs:
- C++
helpviewer_keywords:
- C4430
ms.assetid: 12efbfff-aa58-4a86-a7d6-2c6a12d01dd3
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 311c75ed1fcacdf8b40f096a759d669c9331c2ca
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-warning-c4430"></a>编译器警告 C4430
缺少类型说明符 - 假定为 int。 注意： c + + 不支持默认的 int  
  
 此错误可能来自于为 Visual c + + 2005年执行的编译器一致性工作： 所有声明必须显式都指定的类型;不再假定 int。  
  
 C4430 始终作为错误发出。  你可以关闭此警告，其中包含`#pragma warning`或 **/wd**; 请参阅[警告](../../preprocessor/warning.md)或[/w、 /w0 取消显示、 /W1、 /W2、 /W3、 /W4、 /w1、 /w2、 /w3、 /w4，/Wall、 /wd，/ 我们 /wo，/Wv，/WX （警告级别）](../../build/reference/compiler-option-warning-level.md)有关详细信息。  
  
## <a name="example"></a>示例  
 下面的示例生成 C4430。  
  
```  
// C4430.cpp  
// compile with: /c  
struct CMyClass {  
   CUndeclared m_myClass;  // C4430  
   int m_myClass;  // OK  
};  
  
typedef struct {  
   POINT();   // C4430  
   // try the following line instead  
   // int POINT();  
   unsigned x;  
   unsigned y;  
} POINT;  
```
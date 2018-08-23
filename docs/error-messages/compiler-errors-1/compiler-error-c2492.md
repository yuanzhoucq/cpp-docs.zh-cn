---
title: 编译器错误 C2492 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2492
dev_langs:
- C++
helpviewer_keywords:
- C2492
ms.assetid: 8c44c9bb-c366-4fe5-a0ab-882e38608aaa
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 68b3d769c5b86be172a0a27828fb1dc3905959d5
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33197359"
---
# <a name="compiler-error-c2492"></a>编译器错误 C2492
*变量*： 具有线程存储持续时间的数据可能没有 dll 接口    
  
 变量声明与[线程](../../cpp/thread.md)属性，并使用的 DLL 接口。 地址`thread`变量之前运行时，不进行已知，以便它不能链接到 DLL 导入或导出。  
  
 下面的示例生成 C2492:  
  
```  
// C2492.cpp  
// compile with: /c  
class C {  
public:  
   char   ch;  
};  
  
__declspec(dllexport) __declspec(thread) C c_1;   // C2492  
__declspec(thread) C c_1;   // OK  
```
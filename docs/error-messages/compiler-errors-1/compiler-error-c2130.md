---
title: 编译器错误 C2130 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2130
dev_langs:
- C++
helpviewer_keywords:
- C2130
ms.assetid: c6fd5a7e-8f28-4f67-99d1-95a13b0dff90
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 4484d183def04f764ae75faaa503449e7bdf9984
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33172071"
---
# <a name="compiler-error-c2130"></a>编译器错误 C2130
\#行应包含文件名，却找到 token 的字符串  
  
 在 [#line](../../preprocessor/hash-line-directive-c-cpp.md) `linenumber` 后面的可选文件名标记必须是字符串。  
  
 以下示例生成 C2130:  
  
```  
// C2130.cpp  
int main() {  
   #line 1000 test   // C2130  
   #line 1000 "test"   // OK  
}  
```
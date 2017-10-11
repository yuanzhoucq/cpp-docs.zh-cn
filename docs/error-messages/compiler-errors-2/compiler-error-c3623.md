---
title: "编译器错误 C3623 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C3623
dev_langs:
- C++
helpviewer_keywords:
- C3623
ms.assetid: a0341b45-062a-4f67-beb9-ba74201ed1ed
caps.latest.revision: 11
author: corob-msft
ms.author: corob
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 35b46e23aeb5f4dbfd2a0dd44b906389dd5bfc88
ms.openlocfilehash: df590a7883266f34c749e1aaae2f7f0b8a1f0243
ms.contentlocale: zh-cn
ms.lasthandoff: 10/10/2017

---
# <a name="compiler-error-c3623"></a>编译器错误 C3623
“variable”: 托管或 WinRT 类型中不支持位域  
  
 不允许在托管或 WinRT 类的变量上使用位域。  
  
 以下示例生成 C3623：  
  
```  
// C3623.cpp  
// compile with: /clr  
using namespace System;  
ref class CMyClass {  
public:  
   int i : 1;   // C3623  
};  
  
int main() {  
   CMyClass^ pMyClass = gcnew CMyClass();  
   pMyClass->i = 3;  
   Console::Out->WriteLine(pMyClass->i);  
}  
```  


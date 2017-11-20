---
title: "编译器错误 C3192 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C3192
dev_langs: C++
helpviewer_keywords: C3192
ms.assetid: 8b0083d4-706f-46f6-858a-e1d9af464cf8
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 0f4b1dabfa305bc7d25daab60270ef07579bcf17
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c3192"></a>编译器错误 C3192
语法错误: ^ 不是一个前缀运算符 (您的意思 ' *'？)  
  
 句柄不能用作取消引用运算符。  
  
 下面的示例生成 C3192:  
  
```  
// C3192.cpp  
// compile with: /clr  
using namespace System;  
  
ref class MyClass {  
public:  
   MyClass () {}  
   MyClass(MyClass%) {}  
};  
  
int main() {  
   MyClass ^ s = gcnew MyClass;   
   MyClass b = ^s;   // C3192  
  
   // OK  
   MyClass b2 = *s;  
}  
```
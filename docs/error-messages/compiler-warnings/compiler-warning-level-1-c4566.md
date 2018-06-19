---
title: 编译器警告 （等级 1） C4566 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4566
dev_langs:
- C++
helpviewer_keywords:
- C4566
ms.assetid: 65f40730-e86f-447c-b37b-16caadcfe311
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: e8044df3a37e54585f7f3b495b99314e258934f1
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33284220"
---
# <a name="compiler-warning-level-1-c4566"></a>编译器警告（等级 1）C4566
通用字符名称 char 所表示的字符不能表示在当前代码页 （页）  
  
 可在你当前的 ANSI 代码页表示不是每个 Unicode 字符。  
  
 窄字符串 （单字节字符） 转换为多字节字符，而不是宽字符串 （双字节字符）。  
  
 下面的示例生成 C4566:  
  
```  
// C4566.cpp  
// compile with: /W1  
int main() {  
   char c1 = '\u03a0';   // C4566  
   char c2 = '\u0642';   // C4566  
  
   wchar_t c3 = L'\u03a0';   // OK  
   wchar_t c4 = L'\u0642';   // OK  
}  
```
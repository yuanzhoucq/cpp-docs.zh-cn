---
title: "编译器错误 C3172 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C3172
dev_langs:
- C++
helpviewer_keywords:
- C3172
ms.assetid: 1834e2fd-6036-4c33-aff2-b51bc7c99441
caps.latest.revision: 8
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: a82768750e6a7837bb81edd8a51847f83c294c20
ms.openlocfilehash: a53e7bc0b8543813e5745773f6a7548eb9a83442
ms.contentlocale: zh-cn
ms.lasthandoff: 04/04/2017

---
# <a name="compiler-error-c3172"></a>编译器错误 C3172
模块名︰ 不能在项目中指定不同 idl_module 特性  
  
 [idl_module](../../windows/idl-module.md)属性具有相同名称但不同`dllname`或`version`中一次编译中的文件的两个找到的参数。 只有一个唯一`idl_module`属性可以指定每次编译。  
  
 相同`idl_module`属性可以指定多个源代码文件中。  
  
 例如，如果以下`idl_module`找属性︰  
  
```  
// C3172.cpp  
[module(name="MyMod")];  
[ idl_module(name="x", dllname="file.dll", version="1.1") ];  
int main() {}  
```  
  
 然后，  
  
```  
// C3172b.cpp  
// compile with: C3172.cpp  
// C3172 expected  
[ idl_module(name="x", dllname="file.dll", version="1.0") ];  
```  
  
 编译器将生成 C3172 （请注意不同的版本值）。

---
title: "编译器错误 C3628 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C3628
dev_langs:
- C++
helpviewer_keywords:
- C3628
ms.assetid: 0ff5a4a4-fcc9-47a0-a4d8-8af9cf2815f6
caps.latest.revision: 10
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
translationtype: Machine Translation
ms.sourcegitcommit: c243063a9770542f137d5950e8a269f771960f74
ms.openlocfilehash: e8723f85289d1094a6969d2bf26c30a85ccf382b
ms.lasthandoff: 02/24/2017

---
# <a name="compiler-error-c3628"></a>编译器错误 C3628
base class︰ 托管或 WinRTclasses 只支持公共继承  
  
尝试使用托管或 WinRT 类用作[专用](../../cpp/private-cpp.md)或[保护](../../cpp/protected-cpp.md)基类。 托管或 WinRT 类只能用作基类，其[公共](../../cpp/public-cpp.md)访问。  
  
下面的示例生成 C3628，并演示如何修复此错误：  
  
```  
// C3628a.cpp  
// compile with: /clr  
ref class B {  
};  
  
ref class D : private B {   // C3628  
  
// The following line resolves the error.  
// ref class D : public B {  
};  
  
int main() {  
}  
```  


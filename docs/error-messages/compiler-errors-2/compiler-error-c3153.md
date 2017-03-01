---
title: "编译器错误 C3153 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C3153
dev_langs:
- C++
helpviewer_keywords:
- C3153
ms.assetid: d775d97e-2480-484f-81f1-88406b10f947
caps.latest.revision: 9
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
ms.openlocfilehash: e7755c5924af2d2266fdf5e97a76eac3d229aa79
ms.lasthandoff: 02/24/2017

---
# <a name="compiler-error-c3153"></a>编译器错误 C3153
接口︰ 无法创建接口的实例  
  
 无法实例化接口。 若要使用接口的成员，从接口派生类，实现接口成员，然后使用这些成员。  
  
 下面的示例生成 C3153:  
  
```  
// C3153.cpp  
// compile with: /clr  
interface class A {  
};  
  
int main() {  
   A^ a = gcnew A;   // C3153  
}  
```  


---
title: "编译器错误 C3903 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C3903
dev_langs: C++
helpviewer_keywords: C3903
ms.assetid: cf47d7ad-a3bd-4f75-a253-71586e7a3be6
caps.latest.revision: "9"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 181a0d7f4e8b69c660dc995d9368c882ec96957e
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c3903"></a>编译器错误 C3903
property： 未不具有 set 或 get 方法  
  
 属性必须具有至少一个`get`或`set`方法。 有关详细信息，请参阅 [property](../../windows/property-cpp-component-extensions.md)。  
  
 下面的示例生成 C3903:  
  
```  
// C3903.cpp  
// compile with: /clr  
ref class X {  
   property int P {  
      void f(int){}  
      // Add one or both of the following lines.  
      // void set(int){}  
      // int get(){return 0;}  
   };   // C3903  
  
   property double Q[,,,,] {  
      void f(){}  
      // Add one or both of the following lines.  
      // void set(int, char, int, char, double, double){}  
      // double get(int, char, int, char, double){return 1.1;}  
   }   // C3903  
};  
```
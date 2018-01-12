---
title: "编译器警告 （等级 4） C4266 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C4266
dev_langs: C++
helpviewer_keywords: C4266
ms.assetid: 90ec5f5b-3451-4c16-bb1b-c30a626bdaa0
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: e7d94cc47d6df61a286d97f5a6d3a382ad3820cb
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-warning-level-4-c4266"></a>编译器警告（等级 4）C4266
function： 不重写的基 type; 的虚拟成员函数函数将被隐藏  
  
 派生的类未重写虚函数的所有重载。  
  
 默认情况下，此警告处于关闭状态。  请参阅 [默认情况下处于关闭状态的编译器警告](../../preprocessor/compiler-warnings-that-are-off-by-default.md) 了解详细信息。  
  
 下面的示例生成 C4266:  
  
```  
// C4266.cpp  
// compile with: /W4 /c  
#pragma warning (default : 4266)  
class Engine {  
public:  
   virtual void OnException(int&,int);  
   virtual void OnException(int&,int&,int);  
};  
  
class LocalBinding : private Engine {  
   virtual void OnException(int&,int);  
};   // C4266  
```  
  
 可能的解决方法：  
  
```  
// C4266b.cpp  
// compile with: /W4 /c  
#pragma warning (default : 4266)  
class Engine {  
public:  
   virtual void OnException(int&,int);  
   virtual void OnException(int&,int&,int);  
};  
  
class LocalBinding : private Engine {  
   virtual void OnException(int&,int);  
   virtual void OnException(int&, int&, int);  
};  
```
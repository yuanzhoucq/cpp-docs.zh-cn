---
title: "编译器错误 C3223 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: C3223
dev_langs: C++
helpviewer_keywords: C3223
ms.assetid: 1f4380b4-0413-40db-a868-62f97babaf78
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 40d433c600dd560a4642aac1832fe94b60917fa0
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c3223"></a>编译器错误 C3223
“property”：不能将“typeid”应用于属性  
  
 不能将 [typeid](../../windows/typeid-cpp-component-extensions.md) 应用于属性。  
  
## <a name="example"></a>示例  
 以下示例生成 C3223。  
  
```  
// C3223.cpp  
// compile with: /clr  
ref class R {  
public:  
   property int myprop;  
};  
  
int main() {  
   System::Type^ type2 = R::myprop::typeid;   // C3223  
}  
```
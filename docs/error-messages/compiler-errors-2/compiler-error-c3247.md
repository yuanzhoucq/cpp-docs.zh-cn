---
title: "编译器错误 C3247 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: C3247
dev_langs: C++
helpviewer_keywords: C3247
ms.assetid: f9a2bbb5-3fce-40bf-9fd3-835a5f164dbb
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: fc07da3d6fa994bfba9588b1169287da8c0d738b
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c3247"></a>编译器错误 C3247
“class1”：组件类不能继承自另一个组件类“class2”  
  
 [coclass](../../windows/coclass.md) 特性标记的类不能继承自 `coclass` 特性标记的另一个类。  
  
 以下示例生成 C3247：  
  
```  
// C3247.cpp  
[module(name="MyLib")];  
[coclass]  
class a {  
};  
  
[coclass]  
class b : public a {   // C3247  
};  
int main() {  
}  
```
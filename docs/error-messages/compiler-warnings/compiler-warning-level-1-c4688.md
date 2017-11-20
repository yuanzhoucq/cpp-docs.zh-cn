---
title: "编译器警告 （等级 1） C4688 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: C4688
dev_langs: C++
helpviewer_keywords: C4688
ms.assetid: a027df3c-b2b8-4c49-8539-c2bc42db74e8
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: fb1ff3dfba0b3f3fb2d3fedc94c3724cc0ac446e
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-warning-level-1-c4688"></a>编译器警告（等级 1）C4688
“constraint”：约束列表包含程序集私有类型“type”  
  
 约束列表中有程序集私有类型，这意味着从程序集外部访问类型时，它将不可用。 有关详细信息，请参阅[泛型](../../windows/generics-cpp-component-extensions.md)。  
  
## <a name="example"></a>示例  
 以下示例生成 C4688。  
  
```  
// C4688.cpp  
// compile with: /clr /c /W1  
ref struct A {};   // private type  
public ref struct B {};  
  
// Delete the following 3 lines to resolve.  
generic <class T>   
where T : A   // C4688  
public ref struct M {};  
  
generic <class T>   
where T : B  
public ref struct N {};  
```
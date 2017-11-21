---
title: "编译器警告 （等级 1） C4364 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C4364
dev_langs: C++
helpviewer_keywords: C4364
ms.assetid: 1477634c-d60f-4570-ad16-1aaeae24ac7f
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 94004ea52d76d39657da1fdb79e0b61777524d47
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-warning-level-1-c4364"></a>编译器警告（等级 1）C4364
\#使用适用于程序集在不具有 as_friend 属性; location(line_number) 以前看到的 fileas_friend 不应用  
  
 A`#using`指令重复对于给定的元数据文件，但`as_friend`第一个匹配项中未使用过限定符; 编译器将忽略第二个`as_friend`。  
  
 有关详细信息，请参阅[友元程序集 （c + +）](../../dotnet/friend-assemblies-cpp.md)。  
  
## <a name="example"></a>示例  
 下面的示例创建一个组件。  
  
```  
// C4364.cpp  
// compile with: /clr /LD  
ref class A {};  
```  
  
## <a name="example"></a>示例  
 下面的示例生成 C4364。  
  
```  
// C4364_b.cpp  
// compile with: /clr /W1 /c  
#using " C4364.dll"  
#using " C4364.dll" as_friend   // C4364  
```
---
title: "编译器警告 （等级 1） C4377 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C4377
dev_langs:
- C++
helpviewer_keywords:
- C4377
ms.assetid: a1c797b8-cd5e-4a56-b430-d07932e811cf
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: b2cf61aa35bcfc40a40febb9e066caba6decd682
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-warning-level-1-c4377"></a>编译器警告（等级 1）C4377
本机类型是私有的默认设置;-d1PrivateNativeTypes 已弃用  
  
 在以前版本中，在程序集中的本机类型也是公共的默认情况下和一个内部、 未记录的编译器选项 (**/d1PrivateNativeTypes**) 用于设置为专用。  
  
 所有类型，本机和 CLR，现在是私有默认情况下，在程序集中，因此**/d1PrivateNativeTypes**不再需要。  
  
## <a name="example"></a>示例  
 下面的示例生成 C4377。  
  
```  
// C4377.cpp  
// compile with: /clr /d1PrivateNativeTypes /W1  
// C4377 warning expected  
int main() {}  
```
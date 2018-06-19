---
title: 编译器警告 （等级 1） C4075 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4075
dev_langs:
- C++
helpviewer_keywords:
- C4075
ms.assetid: 19a700b6-f210-4b9d-a2f2-76cfe39ab178
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: c9a0d9fb3808af9ed05454b5b07d471303abc654
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33282878"
---
# <a name="compiler-warning-level-1-c4075"></a>编译器警告（等级 1） C4075
初始值设定项放置在无法识别的初始化区域中  
  
 [#pragma init_seg](../../preprocessor/init-seg.md) 使用无法识别的节名称。 编译器忽略 **pragma** 命令。  
  
 以下示例生成 C4075：  
  
```  
// C4075.cpp  
// compile with: /W1  
#pragma init_seg("mysegg")   // C4075  
  
// try..  
// #pragma init_seg(user)  
  
int main() {  
}  
```
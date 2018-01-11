---
title: "编译器错误 C3748 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C3748
dev_langs: C++
helpviewer_keywords: C3748
ms.assetid: 6fe71a0a-dd93-4ce6-9729-b9616360cf34
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 653a732b28f68d201c1ded7a03b5582d3dba11a5
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c3748"></a>编译器错误 C3748
interface： 托管的接口可能不会激发事件  
  
 [__Event](../../cpp/event.md)关键字不能出现在接口内。  
  
 下面的示例生成 C3748:  
  
```  
// C3748.cpp  
__interface I {  
// try the following line instead  
// struct I {  
   __event void f();   // C3748  
};  
  
int main() {  
}  
```
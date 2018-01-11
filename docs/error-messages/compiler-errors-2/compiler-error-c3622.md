---
title: "编译器错误 C3622 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C3622
dev_langs: C++
helpviewer_keywords: C3622
ms.assetid: 02836f78-0cf2-4947-b87e-710187d81014
caps.latest.revision: "11"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 75d853b01f4f88fbf5e435b3b1f7a86fed0c8388
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c3622"></a>编译器错误 C3622
class: 类声明为 keyword 不能实例化  
  
尝试实例化类标记为[抽象](../../windows/abstract-cpp-component-extensions.md)。 一个类标记为`abstract`可以是基类，但它不能实例化。  
  
## <a name="example"></a>示例  
下面的示例生成 C3622。  
  
```  
// C3622.cpp  
// compile with: /clr  
ref class a abstract {};  
  
int main() {  
   a aa;   // C3622  
}  
```  

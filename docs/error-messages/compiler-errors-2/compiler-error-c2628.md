---
title: "编译器错误 C2628 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C2628
dev_langs: C++
helpviewer_keywords: C2628
ms.assetid: 19a25e77-d5be-4107-88d5-0745b6281f98
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 60fd4e45b19423e32b7a5973b8bdfad34b75bcc6
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c2628"></a>编译器错误 C2628
type1 跟 type2 是非法 (是否忘记了;？)  
  
 分号可能会丢失。  
  
 下面的示例生成 C2628:  
  
```  
// C2628.cpp  
class CMyClass {}  
int main(){}   // C2628 error  
```  
  
 可能的解决方法：  
  
```  
// C2628b.cpp  
class CMyClass {};  
int main(){}  
```
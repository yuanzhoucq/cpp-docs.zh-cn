---
title: "编译器错误 C2046 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: C2046
dev_langs: C++
helpviewer_keywords: C2046
ms.assetid: f0c8f9dd-dbd7-4c4a-8838-fde54208ec71
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 39f85239298b554e62fd525c8020f65c0e94a831
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c2046"></a>编译器错误 C2046
非法的 case  
  
 关键字 `case` 仅出现在 `switch` 语句中。  
  
 以下示例生成 C2046：  
  
```  
// C2046.cpp  
int main() {  
   case 0:   // C2046  
}  
```  
  
 可能的解决方法：  
  
```  
// C2046b.cpp  
int main() {  
   int i = 0;  
  
   switch(i) {  
      case 0:  
      break;  
  
      default:  
      break;  
   }  
}  
```
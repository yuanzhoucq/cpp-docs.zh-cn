---
title: "浮点协处理器和调用约定 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- floating-point numbers [C++]
- floating-point coprocessor
ms.assetid: 3cc6615a-b308-4cf7-9570-83e192a832b3
caps.latest.revision: 7
author: mikeblome
ms.author: mblome
manager: ghogen
ms.translationtype: HT
ms.sourcegitcommit: 6ffef5f51e57cf36d5984bfc43d023abc8bc5c62
ms.openlocfilehash: 6d14f7f445064316c83b31e9b4cdc421d68d7255
ms.contentlocale: zh-cn
ms.lasthandoff: 09/25/2017

---
# <a name="floating-point-coprocessor-and-calling-conventions"></a>浮点协处理器和调用约定
如果要为浮点例程点协处理器编写程序集，你必须保留浮点控制字和清理协处理器堆栈，除非您在返回**float**或**double**值 （您的函数应返回 ST(0)) 中。  
  
## <a name="see-also"></a>另请参阅  
 [调用约定](../cpp/calling-conventions.md)

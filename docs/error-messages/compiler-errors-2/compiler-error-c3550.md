---
title: "编译器错误 C3550 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C3550
dev_langs:
- C++
helpviewer_keywords:
- C3550
ms.assetid: 9f2d5ffc-e429-41a1-89e3-7acc4fd47e14
caps.latest.revision: 6
author: corob-msft
ms.author: corob
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 35b46e23aeb5f4dbfd2a0dd44b906389dd5bfc88
ms.openlocfilehash: 52b3e3323bac9ad55ff10481b3504e4e054ba874
ms.contentlocale: zh-cn
ms.lasthandoff: 10/10/2017

---
# <a name="compiler-error-c3550"></a>编译器错误 C3550
此上下文只允许纯“decltype(auto)”  
  
 如果 `decltype(auto)` 用作函数的返回类型的占位符，则它必须被其自身使用。 它无法用作指针声明 (`decltype(auto*)`)、引用声明 (`decltype(auto&)`) 或其他此类限定的一部分。  
  
## <a name="see-also"></a>另请参阅  
 [auto](../../cpp/auto-cpp.md)

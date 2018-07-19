---
title: 编译器错误 C3550 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3550
dev_langs:
- C++
helpviewer_keywords:
- C3550
ms.assetid: 9f2d5ffc-e429-41a1-89e3-7acc4fd47e14
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 91003af2069ba32083caefa8f5a79cbe0e7cd9c9
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33252889"
---
# <a name="compiler-error-c3550"></a>编译器错误 C3550
此上下文只允许纯“decltype(auto)”  
  
 如果 `decltype(auto)` 用作函数的返回类型的占位符，则它必须被其自身使用。 它无法用作指针声明 (`decltype(auto*)`)、引用声明 (`decltype(auto&)`) 或其他此类限定的一部分。  
  
## <a name="see-also"></a>请参阅  
 [auto](../../cpp/auto-cpp.md)
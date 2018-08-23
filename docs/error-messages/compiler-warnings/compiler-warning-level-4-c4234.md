---
title: 编译器警告 （等级 4） C4234 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4234
dev_langs:
- C++
helpviewer_keywords:
- C4234
ms.assetid: f7fecd5c-8248-4fde-8446-502aedc357ca
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b8d5b7a2999b77c0b34ee925f5dd85a0a27c63f5
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33293512"
---
# <a name="compiler-warning-level-4-c4234"></a>编译器警告（等级 4）C4234
使用的非标准扩展： 保留供将来使用的关键字 keyword  
  
 编译器不尚未实现您使用的关键字。  
  
 此警告将自动提升为错误。 如果你想要修改此行为，使用[#pragma 警告](../../preprocessor/warning.md)。 例如，若要使一个级别 4 警告问题，C4234  
  
```  
#pragma warning(2:4234)  
```  
  
 在你的源代码文件。
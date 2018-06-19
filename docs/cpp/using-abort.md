---
title: 使用 abort |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- Abort
dev_langs:
- C++
helpviewer_keywords:
- abort function
ms.assetid: 3ba39b78-ef74-4a8d-8dee-2d62442de174
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 7231339ba4884445d7ad6b0161c6cff793c6db8a
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
ms.locfileid: "32421843"
---
# <a name="using-abort"></a>使用 abort
调用[中止](../c-runtime-library/reference/abort.md)函数导致立即终止。 它绕过初始化的全局静态对象的一般析构过程。 它还绕过使用 `atexit` 函数指定的任何特殊处理。  
  
## <a name="see-also"></a>请参阅  
 [附加终止注意事项](../cpp/additional-termination-considerations.md)
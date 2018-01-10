---
title: "使用 abort |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: Abort
dev_langs: C++
helpviewer_keywords: abort function
ms.assetid: 3ba39b78-ef74-4a8d-8dee-2d62442de174
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 88f7d2319fd238fbc7bf573d304245ca74696720
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="using-abort"></a>使用 abort
调用[中止](../c-runtime-library/reference/abort.md)函数导致立即终止。 它绕过初始化的全局静态对象的一般析构过程。 它还绕过使用 `atexit` 函数指定的任何特殊处理。  
  
## <a name="see-also"></a>请参阅  
 [附加终止注意事项](../cpp/additional-termination-considerations.md)
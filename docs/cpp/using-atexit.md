---
title: 使用 atexit |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- atexit
dev_langs:
- C++
helpviewer_keywords:
- atexit function
ms.assetid: d28fda17-c3d4-4af6-ba44-f44886bbb237
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: f4acd81a5420f9fe2685e7570f26fea61691b845
ms.sourcegitcommit: 51f804005b8d921468775a0316de52ad39b77c3e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/02/2018
ms.locfileid: "39467399"
---
# <a name="using-atexit"></a>使用 atexit
与[atexit](../c-runtime-library/reference/atexit.md)函数，可以指定在程序终止之前执行 exit-processing 函数。 初始化之前调用了任何全局静态对象**atexit**在执行 exit-processing 函数之前销毁。  
  
## <a name="see-also"></a>请参阅  
 [附加终止注意事项](../cpp/additional-termination-considerations.md)
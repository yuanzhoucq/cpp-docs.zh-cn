---
title: "使用 atexit |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- atexit
dev_langs:
- C++
helpviewer_keywords:
- atexit function
ms.assetid: d28fda17-c3d4-4af6-ba44-f44886bbb237
caps.latest.revision: 8
author: mikeblome
ms.author: mblome
manager: ghogen
ms.translationtype: HT
ms.sourcegitcommit: 6ffef5f51e57cf36d5984bfc43d023abc8bc5c62
ms.openlocfilehash: 4093bf14422fb6598f53d298aa8958a506103fb2
ms.contentlocale: zh-cn
ms.lasthandoff: 09/25/2017

---
# <a name="using-atexit"></a>使用 atexit
与[atexit](../c-runtime-library/reference/atexit.md)函数，您可以指定在程序终止之前执行的 exit-processing 函数。 在执行 exit-processing 函数之前不会销毁在调用 `atexit` 之前初始化的任何全局静态对象。  
  
## <a name="see-also"></a>另请参阅  
 [附加终止注意事项](../cpp/additional-termination-considerations.md)

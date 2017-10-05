---
title: "使用 abort |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- Abort
dev_langs:
- C++
helpviewer_keywords:
- abort function
ms.assetid: 3ba39b78-ef74-4a8d-8dee-2d62442de174
caps.latest.revision: 8
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: HT
ms.sourcegitcommit: 6ffef5f51e57cf36d5984bfc43d023abc8bc5c62
ms.openlocfilehash: 690e76eb3b83844e0fed81bf8d7bbd4c395abb14
ms.contentlocale: zh-cn
ms.lasthandoff: 09/25/2017

---
# <a name="using-abort"></a>使用 abort
调用[中止](../c-runtime-library/reference/abort.md)函数导致立即终止。 它绕过初始化的全局静态对象的一般析构过程。 它还绕过使用 `atexit` 函数指定的任何特殊处理。  
  
## <a name="see-also"></a>另请参阅  
 [附加终止注意事项](../cpp/additional-termination-considerations.md)

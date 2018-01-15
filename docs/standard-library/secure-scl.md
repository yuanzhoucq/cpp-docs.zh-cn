---
title: _SECURE_SCL |Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: _SECURE_SCL
dev_langs: C++
helpviewer_keywords: _SECURE_SCL
ms.assetid: 4ffbc788-cc12-4c6a-8cd7-490081675086
caps.latest.revision: "10"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 6f32a4ebfd9aec0cfbdcc03098f6aa0a23b8ecff
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="securescl"></a>_SECURE_SCL
  
被 [_ITERATOR_DEBUG_LEVEL](../standard-library/iterator-debug-level.md) 所取代，此宏可定义是否已启用[经过检查的迭代器](../standard-library/checked-iterators.md)。 默认情况下，经过检查的迭代器在调试版本中处于启用状态，在零售版本中处于禁用状态。  
  
> [!IMPORTANT]
> 已弃用直接使用宏 `_SECURE_SCL`。 而改用 `_ITERATOR_DEBUG_LEVEL` 来控制经过检查的迭代器设置。 有关详细信息，请参阅 [_ITERATOR_DEBUG_LEVEL](../standard-library/iterator-debug-level.md)。  
  
## <a name="remarks"></a>备注  
  
启用经过检查的迭代器时，使用不安全的迭代器会导致运行时错误并终止程序。 若要启用经过检查的迭代器，请将 `_ITERATOR_DEBUG_LEVEL` 设置为 1 或 2。 这相当于 `_SECURE_SCL` 设置为 1 或已启用：  
  
```  
#define _ITERATOR_DEBUG_LEVEL 1  
```  
  
若要禁用经过检查的迭代器，请将 `_ITERATOR_DEBUG_LEVEL` 设置为 0。 这相当于 `_SECURE_SCL` 设置为 0 或已禁用：  
  
```  
#define _ITERATOR_DEBUG_LEVEL 0  
```  
  
有关如何禁用经过检查的迭代器的警告信息，请参阅 [_SCL_SECURE_NO_WARNINGS](../standard-library/scl-secure-no-warnings.md)。  
  
## <a name="see-also"></a>请参阅  
[_ITERATOR_DEBUG_LEVEL](../standard-library/iterator-debug-level.md)   
[经过检查的迭代器](../standard-library/checked-iterators.md)   
[调试迭代器支持](../standard-library/debug-iterator-support.md)   
[安全库：C++ 标准库](../standard-library/safe-libraries-cpp-standard-library.md)


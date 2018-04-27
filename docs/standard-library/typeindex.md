---
title: '&lt;typeindex&gt; | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- <typeindex>
dev_langs:
- C++
ms.assetid: a9551137-f74b-4f02-af64-ff00214cea1f
caps.latest.revision: 14
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 63eae51554003a2c12caf2522a912adc9b96ec02
ms.sourcegitcommit: dd1a509526fa8bb18e97ab7bc7b91cbdb3ec7059
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/26/2018
---
# <a name="lttypeindexgt"></a>&lt;typeindex&gt;

包括标准标头 \<typeindex>，以定义支持类 [type_info](../cpp/type-info-class.md) 的对象索引的类和函数。

## <a name="syntax"></a>语法

```cpp
#include <typeindex>
```

## <a name="remarks"></a>备注

[hash 结构](../standard-library/hash-structure.md)可定义适合将 [type_index](../standard-library/type-index-class.md) 类型的值映射到索引值的分布的 `hash function`。

`type_index` 类包装指向 `type_info` 对象的指针，以便辅助编写索引。

## <a name="see-also"></a>请参阅

[头文件引用](../standard-library/cpp-standard-library-header-files.md)<br/>
[C++ 标准库中的线程安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
[C++ 标准库参考](../standard-library/cpp-standard-library-reference.md)<br/>

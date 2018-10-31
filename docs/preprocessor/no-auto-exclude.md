---
title: no_auto_exclude |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- no_auto_exclude
dev_langs:
- C++
helpviewer_keywords:
- no_auto_exclude attribute
ms.assetid: 3241ef9c-758a-4e86-bdc5-37da6072430f
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 0673a7216bc00fb13cb0c99e0f9b74accabe33b0
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/25/2018
ms.locfileid: "50074955"
---
# <a name="noautoexclude"></a>no_auto_exclude
**C + + 专用**

禁用自动排除。

## <a name="syntax"></a>语法

```
no_auto_exclude
```

## <a name="remarks"></a>备注

类型库可能包含在系统标头文件或其他类型库中定义的项的定义。 `#import` 尝试通过自动排除此类项来避免多个定义错误。 完成此操作后，[编译器警告 （等级 3） C4192](../error-messages/compiler-warnings/compiler-warning-level-3-c4192.md)为每个要排除的项，将发出。 您可以使用此特性来禁用此自动排除。

**结束 c + + 专用**

## <a name="see-also"></a>请参阅

[#import 属性](../preprocessor/hash-import-attributes-cpp.md)<br/>
[#import 指令](../preprocessor/hash-import-directive-cpp.md)
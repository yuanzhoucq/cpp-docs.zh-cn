---
title: no_implementation
ms.date: 11/04/2016
f1_keywords:
- no_implementation
helpviewer_keywords:
- no_implementation attribute
ms.assetid: bdc67785-e131-409c-87bc-f4d2f4abb07b
ms.openlocfilehash: d4e55d06bef823d28c5deb3467654bc530a3853e
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50456779"
---
# <a name="noimplementation"></a>no_implementation
**C + + 专用**

取消生成 .tli 标头，它包含包装器成员函数的实现。

## <a name="syntax"></a>语法

```
no_implementation
```

## <a name="remarks"></a>备注

如果指定此特性，则将生成 .tlh 标头（带用于公开类型库项的声明），而无需用于包含 .tli 标头文件的 `#include` 语句。

结合使用此特性[implementation_only](../preprocessor/implementation-only.md)。

**结束 c + + 专用**

## <a name="see-also"></a>请参阅

[#import 属性](../preprocessor/hash-import-attributes-cpp.md)<br/>
[#import 指令](../preprocessor/hash-import-directive-cpp.md)
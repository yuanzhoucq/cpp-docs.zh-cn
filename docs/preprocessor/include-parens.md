---
title: include()
ms.date: 10/18/2018
f1_keywords:
- include()
helpviewer_keywords:
- include() attribute
ms.assetid: 86c9dcb2-d9e0-4fd5-97d7-0bb3e23d6ecc
ms.openlocfilehash: 1208f14a9f6b3724dd5353df57213baa3910d07f
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/18/2019
ms.locfileid: "59040922"
---
# <a name="include"></a>include()

**C++特定**

禁用自动排除。

## <a name="syntax"></a>语法

```
include("Name1"[,"Name2", ...])
```

### <a name="parameters"></a>参数

*Name1*<br/>
要强制包含的第一项。

*Name2*<br/>
要强行包含的第二项（如果需要）。

## <a name="remarks"></a>备注

类型库可能包含在系统标头文件或其他类型库中定义的项的定义。 `#import` 尝试通过自动排除此类项来避免多个定义错误。 如果已排除项，如所示[编译器警告 （等级 3） C4192](../error-messages/compiler-warnings/compiler-warning-level-3-c4192.md)，因此它们不应具有已，此属性可用于禁用自动排除。 此特性可采用任意数量的自变量，每个自变量都是要包含的类型库项的名称。

**结束C++特定**

## <a name="see-also"></a>请参阅

[#import 属性](../preprocessor/hash-import-attributes-cpp.md)<br/>
[#import 指令](../preprocessor/hash-import-directive-cpp.md)
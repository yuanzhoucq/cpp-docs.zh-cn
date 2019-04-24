---
title: exclude (#import)
ms.date: 10/18/2018
f1_keywords:
- exclude
helpviewer_keywords:
- exclude attribute
ms.assetid: 0883248a-d4bf-420e-9848-807b28fa976e
ms.openlocfilehash: d6a320089d5954b2cf1d0d96ae1f37656f2ddd58
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/18/2019
ms.locfileid: "59032383"
---
# <a name="exclude-import"></a>排除 (\#导入)

**C++特定**

从要生成的类型库标头文件中排除项。

## <a name="syntax"></a>语法

```
exclude("Name1"[, "Name2",...])
```

### <a name="parameters"></a>参数

*Name1*<br/>
要排除的第一项。

*Name2*<br/>
要排除的第二项（如果需要）。

## <a name="remarks"></a>备注

类型库可能包含在系统标头文件或其他类型库中定义的项的定义。 此特性可以采用任意数量的参数，每个参数都是要排除的顶级类型库项。

**结束C++特定**

## <a name="see-also"></a>请参阅

[#import 属性](../preprocessor/hash-import-attributes-cpp.md)<br/>
[#import 指令](../preprocessor/hash-import-directive-cpp.md)
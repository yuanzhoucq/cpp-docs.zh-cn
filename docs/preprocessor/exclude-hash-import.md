---
title: exclude (#import)
ms.date: 10/18/2018
f1_keywords:
- exclude
helpviewer_keywords:
- exclude attribute
ms.assetid: 0883248a-d4bf-420e-9848-807b28fa976e
ms.openlocfilehash: 1de1376fbe80147bc9fe01ea83bad81912431310
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50498249"
---
# <a name="exclude-import"></a>排除 (\#导入)

**C + + 专用**

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

类型库可能包含在系统标头文件或其他类型库中定义的项的定义。 此特性可以采用任意数量的自变量，每个自变量都是要排除的顶级类型库项。

**结束 c + + 专用**

## <a name="see-also"></a>请参阅

[#import 属性](../preprocessor/hash-import-attributes-cpp.md)<br/>
[#import 指令](../preprocessor/hash-import-directive-cpp.md)
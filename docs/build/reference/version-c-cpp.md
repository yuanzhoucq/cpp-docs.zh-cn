---
title: VERSION (C/C++)
ms.date: 11/04/2016
f1_keywords:
- VERSION
helpviewer_keywords:
- VERSION .def file statement
ms.assetid: 3533b97c-5183-45f9-9ca8-4e63462b5d26
ms.openlocfilehash: abc0b751440d09dcaad7e449d7b151b479c51911
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62316816"
---
# <a name="version-cc"></a>VERSION (C/C++)

会通知链接将数字放入的.exe 文件的标头中或 DLL。

```
VERSION major[.minor]
```

## <a name="remarks"></a>备注

*主要*并*次要*参数是十进制数字 0 到 65,535 范围内的。 默认值为版本 0.0。

指定的版本号的等效方法是使用[版本信息](version-version-information.md)(/ 版本) 选项。

## <a name="see-also"></a>请参阅

[模块定义语句的规则](rules-for-module-definition-statements.md)

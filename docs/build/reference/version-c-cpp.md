---
title: VERSION (C/C++)
ms.date: 11/04/2016
f1_keywords:
- VERSION
helpviewer_keywords:
- VERSION .def file statement
ms.assetid: 3533b97c-5183-45f9-9ca8-4e63462b5d26
ms.openlocfilehash: 6d275e1e191e0550143dd5e7a828b734bba0fc96
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/05/2019
ms.locfileid: "57414052"
---
# <a name="version-cc"></a>VERSION (C/C++)

会通知链接将数字放入的.exe 文件的标头中或 DLL。

```
VERSION major[.minor]
```

## <a name="remarks"></a>备注

*主要*并*次要*参数是十进制数字 0 到 65,535 范围内的。 默认值为版本 0.0。

指定的版本号的等效方法是使用[版本信息](../../build/reference/version-version-information.md)(/ 版本) 选项。

## <a name="see-also"></a>请参阅

[模块定义语句的规则](../../build/reference/rules-for-module-definition-statements.md)

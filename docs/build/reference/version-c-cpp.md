---
title: 版本 （C/C + +） |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- VERSION
dev_langs:
- C++
helpviewer_keywords:
- VERSION .def file statement
ms.assetid: 3533b97c-5183-45f9-9ca8-4e63462b5d26
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 7330d979e841d952f7e800e52ae762256ede6808
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/17/2018
ms.locfileid: "45718297"
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
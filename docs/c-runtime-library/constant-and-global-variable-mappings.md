---
title: 常量和全局变量映射 | Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: conceptual
f1_keywords:
- _tenviron
- _TEOF
- _tfinddata_t
dev_langs:
- C++
helpviewer_keywords:
- tfinddatat function
- tenviron function
- TEOF type
- _TEOF type
- generic-text mappings
- _tenviron function
- _tfinddata_t function
ms.assetid: 3af4fd3e-9ed5-4ed9-96fd-7031e5126fd1
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 94cee77f82f850560cc5fe50e13b85c58b7187ad
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46077838"
---
# <a name="constant-and-global-variable-mappings"></a>常量和全局变量映射

TCHAR.H 中定义了这些一般文本常量、全局变量和标准类型映射，具体取决于程序中是否定义了常量 `_UNICODE` 或 `_MBCS`。

### <a name="generic-text-constant-and-global-variable-mappings"></a>一般文本常量和全局变量映射

|一般文本 - 对象名称|SBCS（未定义的 _UNICODE 和 _MBCS）|已定义 _MBCS|已定义 _UNICODE|
|----------------------------------|--------------------------------------------|--------------------|-----------------------|
|`_TEOF`|`EOF`|`EOF`|`WEOF`|
|`_tenviron`|`_environ`|`_environ`|`_wenviron`|
|`_tpgmptr`|`_pgmptr`|`_pgmptr`|`_wpgmptr`|

## <a name="see-also"></a>请参阅

[一般文本映射](../c-runtime-library/generic-text-mappings.md)<br/>
[数据类型映射](../c-runtime-library/data-type-mappings.md)<br/>
[例程映射](../c-runtime-library/routine-mappings.md)<br/>
[示例一般文本程序](../c-runtime-library/a-sample-generic-text-program.md)<br/>
[使用一般文本映射](../c-runtime-library/using-generic-text-mappings.md)
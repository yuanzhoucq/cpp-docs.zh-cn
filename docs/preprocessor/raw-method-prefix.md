---
title: raw_method_prefix
ms.date: 10/18/2018
f1_keywords:
- raw_method_prefix
helpviewer_keywords:
- raw_method_prefix attribute
ms.assetid: 71490313-af78-4bb2-b28a-eee67950d30b
ms.openlocfilehash: 4169b4e23049bf1cf2c61eaefba619169e0ce377
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50467753"
---
# <a name="rawmethodprefix"></a>raw_method_prefix

**C + + 专用**

指定不同的前缀以避免名称冲突。

## <a name="syntax"></a>语法

```
raw_method_prefix("Prefix")
```

### <a name="parameters"></a>参数

Prefix<br/>
要使用的前缀。

## <a name="remarks"></a>备注

使用默认前缀的命名的成员函数公开低级别的属性和方法**raw_** 以避免与高级错误处理成员函数的名称冲突。

> [!NOTE]
> 效果**raw_method_prefix**属性将不会更改由存在[raw_interfaces_only](#_predir_raw_interfaces_only)属性。 **Raw_method_prefix**始终优先于`raw_interfaces_only`中指定前缀。 如果这两个属性使用在同一`#import`语句，然后指定的前缀**raw_method_prefix**使用属性。

**结束 c + + 专用**

## <a name="see-also"></a>请参阅

[#import 属性](../preprocessor/hash-import-attributes-cpp.md)<br/>
[#import 指令](../preprocessor/hash-import-directive-cpp.md)
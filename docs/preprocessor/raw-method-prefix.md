---
title: raw_method_prefix |Microsoft Docs
ms.custom: ''
ms.date: 10/18/2018
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- raw_method_prefix
dev_langs:
- C++
helpviewer_keywords:
- raw_method_prefix attribute
ms.assetid: 71490313-af78-4bb2-b28a-eee67950d30b
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 78094053c963f5d836646e91857e171625c447c9
ms.sourcegitcommit: 0164af5615389ffb1452ccc432eb55f6dc931047
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/23/2018
ms.locfileid: "49808545"
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
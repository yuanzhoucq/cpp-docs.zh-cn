---
title: raw_interfaces_only
ms.date: 11/04/2016
f1_keywords:
- raw_interfaces_only
helpviewer_keywords:
- raw_interfaces_only attribute
ms.assetid: 87056c6d-3f34-4248-af58-f5775a35bfb7
ms.openlocfilehash: 48133b85ccb5ddb8de8e6cb614d41cde22dac66b
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62179784"
---
# <a name="rawinterfacesonly"></a>raw_interfaces_only
**C++特定**

取消生成的错误处理的包装函数和[属性](../cpp/property-cpp.md)使用这些包装器函数的声明。

## <a name="syntax"></a>语法

```
raw_interfaces_only
```

## <a name="remarks"></a>备注

**Raw_interfaces_only**属性还会导致命名要删除的非属性函数中使用的默认前缀。 通常情况下，该前缀是**raw_**。 如果指定了此特性，函数名将直接来自类型库。

利用此特性，您可以只公开类型库的低级别内容。

**结束C++特定**

## <a name="see-also"></a>请参阅

[#import 属性](../preprocessor/hash-import-attributes-cpp.md)<br/>
[#import 指令](../preprocessor/hash-import-directive-cpp.md)
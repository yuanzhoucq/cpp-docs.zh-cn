---
title: tlbid
ms.date: 10/18/2018
f1_keywords:
- tlbid
helpviewer_keywords:
- tlbid attribute
ms.assetid: 54b06785-191b-4e77-a9a5-485f2b4acb09
ms.openlocfilehash: ae79ce9245bb1c0425c3e9b92dd27b52fa443dba
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/05/2019
ms.locfileid: "59037925"
---
# <a name="tlbid"></a>tlbid

**C++ 专用**

允许加载主类型库之外的库。

## <a name="syntax"></a>语法

```
tlbid(number)
```

### <a name="parameters"></a>参数

*数值*<br/>
`filename` 中的类型库的编号。

## <a name="remarks"></a>备注

如果多个类型库内置于一个 dll，它可以加载非主类型库使用**tlbid**。

例如：

```cpp
#import <MyResource.dll> tlbid(2)
```

等效于：

```cpp
LoadTypeLib("MyResource.dll\\2");
```

**结束 C++ 专用**

## <a name="see-also"></a>请参阅

[#import 特性](../preprocessor/hash-import-attributes-cpp.md)<br/>
[#import 指令](../preprocessor/hash-import-directive-cpp.md)
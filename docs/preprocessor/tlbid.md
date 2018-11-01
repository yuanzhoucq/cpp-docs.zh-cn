---
title: tlbid
ms.date: 10/18/2018
f1_keywords:
- tlbid
helpviewer_keywords:
- tlbid attribute
ms.assetid: 54b06785-191b-4e77-a9a5-485f2b4acb09
ms.openlocfilehash: 31b71f7c195a7e2ee649b40197551e4ff5efda2c
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50584505"
---
# <a name="tlbid"></a>tlbid

**C + + 专用**

允许加载主类型库之外的库。

## <a name="syntax"></a>语法

```
tlbid(number)
```

### <a name="parameters"></a>参数

*数量*<br/>
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

**结束 c + + 专用**

## <a name="see-also"></a>请参阅

[#import 属性](../preprocessor/hash-import-attributes-cpp.md)<br/>
[#import 指令](../preprocessor/hash-import-directive-cpp.md)
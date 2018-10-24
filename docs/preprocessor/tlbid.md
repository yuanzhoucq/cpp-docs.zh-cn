---
title: tlbid |Microsoft Docs
ms.custom: ''
ms.date: 10/18/2018
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- tlbid
dev_langs:
- C++
helpviewer_keywords:
- tlbid attribute
ms.assetid: 54b06785-191b-4e77-a9a5-485f2b4acb09
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 6324ec9a64a0d1c47dab8d1beee021f6c8752a96
ms.sourcegitcommit: 0164af5615389ffb1452ccc432eb55f6dc931047
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/23/2018
ms.locfileid: "49807973"
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
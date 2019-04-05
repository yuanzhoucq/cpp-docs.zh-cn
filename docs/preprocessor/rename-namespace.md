---
title: rename_namespace
ms.date: 10/18/2018
f1_keywords:
- rename_namespace
helpviewer_keywords:
- rename_namespace attribute
ms.assetid: 45006d2b-36cd-4bec-98b9-3b8ec45299e3
ms.openlocfilehash: 7b3917a7114ca44d092f10a7831bb35bc64e9387
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/05/2019
ms.locfileid: "59039867"
---
# <a name="renamenamespace"></a>rename_namespace

**C++ 专用**

重命名包含类型库内容的命名空间。

## <a name="syntax"></a>语法

```
rename_namespace("NewName")
```

### <a name="parameters"></a>参数

*NewName*<br/>
命名空间的新名称。

## <a name="remarks"></a>备注

它采用一个参数， *NewName*，它指定命名空间的新名称。

若要删除命名空间，请使用[no_namespace](../preprocessor/no-namespace.md)特性。

**结束 C++ 专用**

## <a name="see-also"></a>请参阅

[#import 特性](../preprocessor/hash-import-attributes-cpp.md)<br/>
[#import 指令](../preprocessor/hash-import-directive-cpp.md)
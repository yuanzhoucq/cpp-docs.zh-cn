---
title: rename_namespace
ms.date: 10/18/2018
f1_keywords:
- rename_namespace
helpviewer_keywords:
- rename_namespace attribute
ms.assetid: 45006d2b-36cd-4bec-98b9-3b8ec45299e3
ms.openlocfilehash: 7b3917a7114ca44d092f10a7831bb35bc64e9387
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/18/2019
ms.locfileid: "59039867"
---
# <a name="renamenamespace"></a>rename_namespace

**C++特定**

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

**结束C++特定**

## <a name="see-also"></a>请参阅

[#import 属性](../preprocessor/hash-import-attributes-cpp.md)<br/>
[#import 指令](../preprocessor/hash-import-directive-cpp.md)
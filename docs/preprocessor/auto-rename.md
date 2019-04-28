---
title: auto_rename
ms.date: 11/04/2016
f1_keywords:
- auto_rename
helpviewer_keywords:
- auto_rename attribute
ms.assetid: 1075f3ab-f6fc-4e04-8e22-ebe02695a567
ms.openlocfilehash: ba07b8532ba64c99f835e59d7c71aac8e3f2b03d
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62336681"
---
# <a name="autorename"></a>auto_rename

**C++特定**

通过将两个下划线 (__) 追加到变量名称来重命名 C++ 保留字，从而解决可能的名称冲突。

## <a name="syntax"></a>语法

```
auto_rename
```

## <a name="remarks"></a>备注

当导入将一个或多个 C++ 保留字（关键字或宏）用作变量名称的类型库时，使用此特性。

**结束C++特定**

## <a name="see-also"></a>请参阅

[#import 属性](../preprocessor/hash-import-attributes-cpp.md)<br/>
[#import 指令](../preprocessor/hash-import-directive-cpp.md)
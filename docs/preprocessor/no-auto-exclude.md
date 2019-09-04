---
title: no_auto_exclude 导入属性
ms.date: 08/29/2019
f1_keywords:
- no_auto_exclude
helpviewer_keywords:
- no_auto_exclude attribute
ms.assetid: 3241ef9c-758a-4e86-bdc5-37da6072430f
ms.openlocfilehash: 530c2b2adf24e964cb0a512371f4430a61bf8b11
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/03/2019
ms.locfileid: "70216076"
---
# <a name="no_auto_exclude-import-attribute"></a>no_auto_exclude 导入属性

**C++相关**

禁用自动排除。

## <a name="syntax"></a>语法

> **#import***类型库***no_auto_exclude**

## <a name="remarks"></a>备注

类型库可能包含在系统标头文件或其他类型库中定义的项的定义。 `#import` 尝试通过自动排除此类项来避免多个定义错误。 这会导致为要排除的每个项发出[编译器警告 (等级 3) C4192](../error-messages/compiler-warnings/compiler-warning-level-3-c4192.md) 。 您可以使用此属性禁用自动排除。

**结束C++特定**

## <a name="see-also"></a>请参阅

[#import 特性](../preprocessor/hash-import-attributes-cpp.md)\
[#import 指令](../preprocessor/hash-import-directive-cpp.md)

---
title: rename_namespace 导入属性
ms.date: 08/29/2019
f1_keywords:
- rename_namespace
helpviewer_keywords:
- rename_namespace attribute
ms.assetid: 45006d2b-36cd-4bec-98b9-3b8ec45299e3
ms.openlocfilehash: d319d7390e7c7dce070a35be44aad37c7a34e1a0
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/03/2019
ms.locfileid: "70216652"
---
# <a name="rename_namespace-import-attribute"></a>rename_namespace 导入属性

**C++相关**

重命名包含类型库内容的命名空间。

## <a name="syntax"></a>语法

> **#import***类型库***rename_namespace (** "*NewName*" **)**

### <a name="parameters"></a>参数

*NewName*\
命名空间的新名称。

## <a name="remarks"></a>备注

**Rename_namespace**属性采用单个自变量, 它指定命名空间的新名称。

若要删除命名空间, 请改为使用[no_namespace](../preprocessor/no-namespace.md)特性。

**结束C++特定**

## <a name="see-also"></a>请参阅

[#import 特性](../preprocessor/hash-import-attributes-cpp.md)\
[#import 指令](../preprocessor/hash-import-directive-cpp.md)

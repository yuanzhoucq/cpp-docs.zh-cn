---
title: no_registry 导入属性
ms.date: 08/29/2019
f1_keywords:
- no_registry
helpviewer_keywords:
- no_registry attribute
ms.assetid: d30de4e2-551c-428c-98fd-951330d578d3
ms.openlocfilehash: 7c81cc2f570cb9ac4e977dac6d55cb69e491d3b2
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/03/2019
ms.locfileid: "70220722"
---
# <a name="no_registry-import-attribute"></a>no_registry 导入属性

**no_registry**告知编译器不要在注册表中搜索导入的`#import`类型库。

## <a name="syntax"></a>语法

> **#import***类型库***no_registry**

### <a name="parameters"></a>参数

*类型库*\
类型库。

## <a name="remarks"></a>备注

如果在 include 目录中找不到引用的类型库, 则即使类型库位于注册表中, 编译也会失败。  **no_registry**传播到用隐式导入的`auto_search`其他类型库。

编译器决不会在注册表中搜索由文件名指定并直接传递到`#import`的类型库。

指定`auto_search`时, 将使用初始`#import` `#import`的**no_registry**设置生成其他指令。 如果初始`#import`指令为`auto_search` **no_registry**, 则生成`#import`的也是**no_registry**。

如果要导入交叉引用的类型库, 则**no_registry**非常有用。 它使编译器无法在注册表中查找文件的较旧版本。 如果未注册类型库, **no_registry**也很有用。

## <a name="see-also"></a>请参阅

[#import 特性](../preprocessor/hash-import-attributes-cpp.md)\
[#import 指令](../preprocessor/hash-import-directive-cpp.md)

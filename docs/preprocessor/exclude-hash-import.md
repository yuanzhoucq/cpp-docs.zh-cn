---
title: 排除 import 特性
ms.date: 08/29/2019
f1_keywords:
- exclude
helpviewer_keywords:
- exclude attribute
ms.assetid: 0883248a-d4bf-420e-9848-807b28fa976e
ms.openlocfilehash: 6a3625ee0dd44f3e2731e1240fea5f3dd4ed109e
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/03/2019
ms.locfileid: "70218716"
---
# <a name="exclude-import-attribute"></a>排除 import 特性

**C++相关**

从要生成的类型库标头文件中排除项。

## <a name="syntax"></a>语法

> **#import***类型库***exclude (** "*Name1*" [ **,** "*Name2*" ...] **)**

### <a name="parameters"></a>参数

*Name1*\
要排除的第一项。

*Name2*\
可有可无要排除的第二个和更高版本的项目 (如有必要)。

## <a name="remarks"></a>备注

类型库可能包含在系统标头文件或其他类型库中定义的项的定义。 此特性可以采用任意数量的参数, 其中每个参数都是要排除的顶级类型库项。

**结束C++特定**

## <a name="see-also"></a>请参阅

[#import 特性](../preprocessor/hash-import-attributes-cpp.md)\
[#import 指令](../preprocessor/hash-import-directive-cpp.md)

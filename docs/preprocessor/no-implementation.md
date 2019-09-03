---
title: no_implementation 导入属性
ms.date: 08/29/2019
f1_keywords:
- no_implementation
helpviewer_keywords:
- no_implementation attribute
ms.assetid: bdc67785-e131-409c-87bc-f4d2f4abb07b
ms.openlocfilehash: 8f0a7454fdbedc1959b665ccb2a23748d21c342d
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/03/2019
ms.locfileid: "70220771"
---
# <a name="no_implementation-import-attribute"></a>no_implementation 导入属性

**C++相关**

取消了`.tli`标头的生成, 其中包含包装成员函数的实现。

## <a name="syntax"></a>语法

> **#import***类型库***no_implementation**

## <a name="remarks"></a>备注

如果指定此特性, 则将`.tlh`在`#include`不包含`.tli`头文件的语句的情况下生成带有公开类型库项的声明的标头。

此属性与[implementation_only](../preprocessor/implementation-only.md)结合使用。

**结束C++特定**

## <a name="see-also"></a>请参阅

[#import 特性](../preprocessor/hash-import-attributes-cpp.md)\
[#import 指令](../preprocessor/hash-import-directive-cpp.md)

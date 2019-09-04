---
title: raw_interfaces_only 导入属性
ms.date: 08/29/2019
f1_keywords:
- raw_interfaces_only
helpviewer_keywords:
- raw_interfaces_only attribute
ms.assetid: 87056c6d-3f34-4248-af58-f5775a35bfb7
ms.openlocfilehash: 4b79aa4dbafa204d84f4d6ed7ec78fdec1b81fa7
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/03/2019
ms.locfileid: "70216206"
---
# <a name="raw_interfaces_only-import-attribute"></a>raw_interfaces_only 导入属性

**C++相关**

禁止生成错误处理包装函数, 以及使用这些包装函数的[属性](../cpp/property-cpp.md)声明。

## <a name="syntax"></a>语法

> **#import***类型库***raw_interfaces_only**

## <a name="remarks"></a>备注

**Raw_interfaces_only**属性还会导致删除用于命名非属性函数的默认前缀。 通常, 前缀是`raw_`。 如果指定此特性, 则将从类型库中直接获取函数名称。

利用此特性，您可以只公开类型库的低级别内容。

**结束C++特定**

## <a name="see-also"></a>请参阅

[#import 特性](../preprocessor/hash-import-attributes-cpp.md)\
[#import 指令](../preprocessor/hash-import-directive-cpp.md)

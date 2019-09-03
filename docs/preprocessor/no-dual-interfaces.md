---
title: no_dual_interfaces 导入属性
ms.date: 08/29/2019
f1_keywords:
- no_dual_interfaces
helpviewer_keywords:
- no_dual_interfaces attribute
ms.assetid: 9acd5d9d-4a49-4cdc-9470-73a2c23cf512
ms.openlocfilehash: 6270888f0d31e4fbe18fb3364995be8c73426b83
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/03/2019
ms.locfileid: "70220762"
---
# <a name="no_dual_interfaces-import-attribute"></a>no_dual_interfaces 导入属性

**C++相关**

更改编译器为双重接口方法生成包装器函数的方式。

## <a name="syntax"></a>语法

> **#import***类型库***no_dual_interfaces**

## <a name="remarks"></a>备注

通常, 包装器通过接口的虚拟函数表调用方法。 对于**no_dual_interfaces**, 包装将调用`IDispatch::Invoke`来调用方法。

**结束C++特定**

## <a name="see-also"></a>请参阅

[#import 特性](../preprocessor/hash-import-attributes-cpp.md)\
[#import 指令](../preprocessor/hash-import-directive-cpp.md)

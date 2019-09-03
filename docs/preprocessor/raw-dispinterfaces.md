---
title: raw_dispinterfaces 导入属性
ms.date: 08/29/2019
f1_keywords:
- raw_dispinterfaces
helpviewer_keywords:
- raw_dispinterfaces attribute
ms.assetid: f762864d-29bf-445b-825a-ba7b29a95409
ms.openlocfilehash: 73c58b72b27de8dcf96e8ab9464d0fb6bce12b66
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/03/2019
ms.locfileid: "70216229"
---
# <a name="raw_dispinterfaces-import-attribute"></a>raw_dispinterfaces 导入属性

**C++相关**

通知编译器为调度接口方法生成低级别包装函数, 并通知调用`IDispatch::Invoke`并返回 HRESULT 错误代码的属性。

## <a name="syntax"></a>语法

> **#import***类型库***raw_dispinterfaces**

## <a name="remarks"></a>备注

如果未指定此特性, 则仅生成高级包装, 这会在失败C++时引发异常。

**结束C++特定**

## <a name="see-also"></a>请参阅

[#import 特性](../preprocessor/hash-import-attributes-cpp.md)\
[#import 指令](../preprocessor/hash-import-directive-cpp.md)

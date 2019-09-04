---
title: raw_method_prefix
ms.date: 08/29/2019
f1_keywords:
- raw_method_prefix
helpviewer_keywords:
- raw_method_prefix attribute
ms.assetid: 71490313-af78-4bb2-b28a-eee67950d30b
ms.openlocfilehash: b1bc536507716e5c117718ec825bf7fe76c84b61
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/03/2019
ms.locfileid: "70216143"
---
# <a name="raw_method_prefix"></a>raw_method_prefix

**C++相关**

指定不同的前缀以避免名称冲突。

## <a name="syntax"></a>语法

> **#import***类型库***raw_method_prefix (** "*prefix*" **)**

### <a name="parameters"></a>参数

*作为*\
要使用的前缀。

## <a name="remarks"></a>备注

低级别属性和方法由使用默认前缀**raw_** 命名的成员函数公开, 以避免与高级错误处理成员函数发生名称冲突。

> [!NOTE]
> **Raw_method_prefix**属性的效果在出现[raw_interfaces_only](raw-interfaces-only.md)属性时保持不变。 在指定前缀时, raw_method_prefix `raw_interfaces_only`始终优先于。 如果在同一`#import`语句中同时使用这两个属性, 则使用**raw_method_prefix**属性指定的前缀。

**结束C++特定**

## <a name="see-also"></a>请参阅

[#import 特性](../preprocessor/hash-import-attributes-cpp.md)\
[#import 指令](../preprocessor/hash-import-directive-cpp.md)

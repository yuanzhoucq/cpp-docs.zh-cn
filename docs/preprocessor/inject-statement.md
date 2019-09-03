---
title: inject_statement 导入属性
ms.date: 08/29/2019
f1_keywords:
- inject_statement
helpviewer_keywords:
- inject_statement attribute
ms.assetid: 07d6f0f4-d9fb-4e18-aa62-f235f142ff5e
ms.openlocfilehash: 25dee621ff8af2c9a39e605b9da2c29d80f9570a
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/03/2019
ms.locfileid: "70220991"
---
# <a name="inject_statement-import-attribute"></a>inject_statement 导入属性

**C++相关**

将其自变量作为源文本插入类型库标头。

## <a name="syntax"></a>语法

> **#import***类型库***inject_statement (** "*源文本*" **)**

### <a name="parameters"></a>参数

*源-文本*\
要插入类型库标头文件的源文本。

## <a name="remarks"></a>备注

文本位于命名空间声明的开头, 该声明在标头文件中包装*类型库*内容。

**结束C++特定**

## <a name="see-also"></a>请参阅

[#import 特性](../preprocessor/hash-import-attributes-cpp.md)\
[#import 指令](../preprocessor/hash-import-directive-cpp.md)

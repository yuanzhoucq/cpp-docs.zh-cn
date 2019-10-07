---
title: high_property_prefixes 导入属性
ms.date: 08/29/2019
f1_keywords:
- high_property_prefixes
helpviewer_keywords:
- high_property_prefixes attribute
ms.assetid: 91c6cc2b-19b6-4aba-8831-d9e5cccb58b5
ms.openlocfilehash: 9e44f6f1afae479f803f4c6d866ef3ee38744561
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/03/2019
ms.locfileid: "70218999"
---
# <a name="high_property_prefixes-import-attribute"></a>high_property_prefixes 导入属性

**C++相关**

指定用于三个属性方法的备用前缀。

## <a name="syntax"></a>语法

> **#import***类型库***high_property_prefixes (** "*GetPrefix*" **,** "*PutPrefix*" **,** "*PutRefPrefix*" **)**

### <a name="parameters"></a>参数

*GetPrefix*\
要用于`propget`方法的前缀。

*PutPrefix*\
要用于`propput`方法的前缀。

*PutRefPrefix*\
要用于`propputref`方法的前缀。

## <a name="remarks"></a>备注

默认情况下, 高级错误处理`propget`、 `propput`和`propputref`方法由名为前缀`Get`、 `Put`和`PutRef`的成员函数公开。

**结束C++特定**

## <a name="see-also"></a>请参阅

[#import 特性](../preprocessor/hash-import-attributes-cpp.md)\
[#import 指令](../preprocessor/hash-import-directive-cpp.md)

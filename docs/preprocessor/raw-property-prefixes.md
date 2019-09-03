---
title: raw_property_prefixes 导入属性
ms.date: 08/29/2019
f1_keywords:
- raw_property_prefixes
helpviewer_keywords:
- raw_property_prefixes attribute
ms.assetid: 03a0f48c-c460-4175-a762-9f7f8d84b12f
ms.openlocfilehash: d4d91470781e7c5f673fd228c24904322d1db8b3
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/03/2019
ms.locfileid: "70216037"
---
# <a name="raw_property_prefixes-import-attribute"></a>raw_property_prefixes 导入属性

**C++相关**

指定用于三个属性方法的备用前缀。

## <a name="syntax"></a>语法

> **#import***类型库***raw_property_prefixes (** "*GetPrefix*" **,** "*PutPrefix*" **,** "*PutRefPrefix*" **)**

### <a name="parameters"></a>参数

*GetPrefix*\
`propget`用于方法的前缀。

*PutPrefix*\
`propput`用于方法的前缀。

*PutRefPrefix*\
`propputref`用于方法的前缀。

## <a name="remarks"></a>备注

默认情况下, 低级别`propget`、 `propput`和`propputref`方法通过分别使用、 `put_`和`putref_`的`get_`前缀进行命名的成员函数公开。 这些前缀与在 MIDL 生成的标头文件中使用的名称兼容。

**结束C++特定**

## <a name="see-also"></a>请参阅

[#import 特性](../preprocessor/hash-import-attributes-cpp.md)\
[#import 指令](../preprocessor/hash-import-directive-cpp.md)

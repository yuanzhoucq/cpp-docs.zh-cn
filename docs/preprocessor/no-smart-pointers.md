---
title: no_smart_pointers 导入属性
ms.date: 08/29/2019
f1_keywords:
- no_smart_pointers
helpviewer_keywords:
- no_smart_pointers attribute
ms.assetid: d69dd71e-08a8-4446-a3d0-a062dc29cb17
ms.openlocfilehash: 1fca3eb486ff3cfc7403c38e91855b799a698782
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/03/2019
ms.locfileid: "70220697"
---
# <a name="no_smart_pointers-import-attribute"></a>no_smart_pointers 导入属性

**C++相关**

取消对类型库中所有接口的智能指针的创建。

## <a name="syntax"></a>语法

> **#import***类型库***no_smart_pointers**

## <a name="remarks"></a>备注

默认情况下，当使用 `#import` 时，您将获得针对类型库中的所有接口的智能指针声明。 这些智能指针的类型为[_com_ptr_t](../cpp/com-ptr-t-class.md)。

**结束C++特定**

## <a name="see-also"></a>请参阅

[#import 特性](../preprocessor/hash-import-attributes-cpp.md)\
[#import 指令](../preprocessor/hash-import-directive-cpp.md)

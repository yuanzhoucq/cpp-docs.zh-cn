---
title: __RTDynamicCast | Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: conceptual
apiname:
- __RTDynamicCast
apilocation:
- msvcr90.dll
- msvcr110.dll
- msvcr120.dll
- msvcrt.dll
- msvcr100.dll
- msvcr80.dll
- msvcr110_clr0400.dll
apitype: DLLExport
f1_keywords:
- __RTDynamicCast
dev_langs:
- C++
helpviewer_keywords:
- __RTDynamicCast
ms.assetid: 56aa2d7a-aa47-46ef-830d-e37175611239
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 90c68ed56b52b57deb234717b3b95ec197d26318
ms.sourcegitcommit: 6e3cf8df676d59119ce88bf5321d063cf479108c
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/22/2018
ms.locfileid: "34450929"
---
# <a name="rtdynamiccast"></a>__RTDynamicCast
[dynamic_cast](../cpp/dynamic-cast-operator.md) 运算符的运行时实现。  
  
## <a name="syntax"></a>语法  
  
```cpp  
PVOID __RTDynamicCast (  
   PVOID inptr,   
   LONG VfDelta,  
   PVOID SrcType,  
   PVOID TargetType,   
   BOOL isReference  
   ) throw(...)  
```  
  
#### <a name="parameters"></a>参数  
 `inptr`  
 指向多态对象的指针。  
  
 `VfDelta`  
 对象中的虚函数指针的偏移量。  
  
 `SrcType`  
 由 `inptr` 参数指向的对象的静态类型。  
  
 `TargetType`  
 转换的预期结果。  
  
 `isReference`  
 如果输入是引用，则为 `true`；如果输入是指针，则为 `false`。  
  
## <a name="return-value"></a>返回值  
 如果成功，则为指向适当的子对象的指针；否则为 NULL。  
  
## <a name="exceptions"></a>异常  
 如果 `bad_cast()` 的输入为引用并且转换失败，则为 `dynamic_cast<>`。  
  
## <a name="remarks"></a>备注  
 将 `inptr` 转换为 `TargetType` 类型的对象。 如果 `TargetType` 是指针，则 `inptr` 类型必须为指针，或者如果 `TargetType` 是引用，则为左值。 `TargetType` 必须是针对以前定义的类类型的指针或引用，或者是指向 void 的指针。  
  
## <a name="requirements"></a>惠?  
  
|例程所返回的值|必需的标头|  
|-------------|---------------------|  
|__RTDynamicCast|rtti.h|
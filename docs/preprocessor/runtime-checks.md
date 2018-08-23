---
title: runtime_checks |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- vc-pragma.runtime_checks
- runtime_checks_CPP
dev_langs:
- C++
helpviewer_keywords:
- runtime_checks pragma
- pragmas, runtime_checks
ms.assetid: ae50b43f-f88d-47ad-a2db-3389e9e7df5b
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b20ea9dd12bfe4daff8e2e440c96a41c220aa742
ms.sourcegitcommit: d4c803bd3a684d7951bf88dcecf1f14af43ae411
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/10/2018
ms.locfileid: "42541356"
---
# <a name="runtimechecks"></a>runtime_checks
禁用或还原 [/RTC](../build/reference/rtc-run-time-error-checks.md) 设置。  
  
## <a name="syntax"></a>语法  
  
```  
#pragma runtime_checks( "[runtime_checks]", {restore | off} )  
```  
  
## <a name="remarks"></a>备注  
 
不能启用未使用编译器选项启用的运行时检查。 例如，如果未指定`/RTCs`，并指定`#pragma runtime_checks( "s", restore)`将不会启用堆栈帧验证。  
  
**runtime_checks** 杂注必须显示在函数的外部，并在杂注显示后定义的第一个函数处生效。 *还原*并*off*参数打开选项中指定**runtime_checks**打开或关闭。  
  
**Runtime_checks**可以是零个或多个表所示的参数。  
  
### <a name="parameters-of-the-runtimechecks-pragma"></a>runtime_checks 杂注的参数  
  
|参数|运行时检查的类型|  
|--------------------|-----------------------------|  
|*s*|启用堆栈（帧）验证。|  
|*c*|报告何时向较小的数据类型赋值会导致数据丢失。|  
|*u*|报告何时在定义变量前先使用变量。|  
  
这些是与一起使用的相同字母`/RTC`编译器选项。 例如：  
  
```  
#pragma runtime_checks( "sc", restore )  
```  
  
将 **runtime_checks** 杂注和空字符串 (**""**) 一起使用是该指令的特殊形式：  
  
- 当你使用*关闭*参数，它会关闭上述表中列出的运行时错误检查。  
  
- 当你使用*还原*参数，它会重置的运行时错误检查为使用指定的`/RTC`编译器选项。  
  
```  
#pragma runtime_checks( "", off )  
.  
.  
.  
#pragma runtime_checks( "", restore )   
```  
  
## <a name="see-also"></a>请参阅  
 
[Pragma 指令和 __Pragma 关键字](../preprocessor/pragma-directives-and-the-pragma-keyword.md)   
---
title: runtime_checks |Microsoft 文档
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
ms.openlocfilehash: 817afaff738b2528bd165e814517c8399cd8a151
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/07/2018
---
# <a name="runtimechecks"></a>runtime_checks
禁用或还原 [/RTC](../build/reference/rtc-run-time-error-checks.md) 设置。  
  
## <a name="syntax"></a>语法  
  
```  
  
#pragma runtime_checks( "[runtime_checks]", {restore | off} )  
```  
  
## <a name="remarks"></a>备注  
 不能启用未使用编译器选项启用的运行时检查。 例如，如果您未指定 /RTC，则指定 `#pragma runtime_checks( "s", restore)` 将不会启用堆栈帧验证。  
  
 **runtime_checks** 杂注必须显示在函数的外部，并在杂注显示后定义的第一个函数处生效。 **restore** 和 **off** 参数打开或关闭 *runtime_checks* 中指定的选项。  
  
 *runtime_checks* 可以为下表中显示的零个或多个参数。  
  
### <a name="parameters-of-the-runtimechecks-pragma"></a>runtime_checks 杂注的参数  
  
|参数|运行时检查的类型|  
|--------------------|-----------------------------|  
|**秒**|启用堆栈（帧）验证。|  
|**c**|报告何时向较小的数据类型赋值会导致数据丢失。|  
|**u**|报告何时在定义变量前先使用变量。|  
  
 这些是用于 /RTC 编译器选项的相同字母。 例如：  
  
```  
#pragma runtime_checks( "sc", restore )  
```  
  
 将 **runtime_checks** 杂注和空字符串 (**""**) 一起使用是该指令的特殊形式：  
  
-   使用 **off** 参数时，会禁用上表中列出的运行时错误检查。  
  
-   使用 **restore** 参数时，它会将运行时错误检查重置为使用 /RTC 编译器选项指定的检查。  
  
```  
#pragma runtime_checks( "", off )  
.  
.  
.  
#pragma runtime_checks( "", restore )   
```  
  
## <a name="see-also"></a>请参阅  
 [Pragma 指令和 __Pragma 关键字](../preprocessor/pragma-directives-and-the-pragma-keyword.md)   

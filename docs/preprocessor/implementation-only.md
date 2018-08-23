---
title: implementation_only |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- implementation_only
dev_langs:
- C++
helpviewer_keywords:
- implementation_only attribute
ms.assetid: d8cabc86-4425-45a0-9587-d57536980088
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 2e7f0f40ad5d01b647f1f3273dc9a55d7cfa7564
ms.sourcegitcommit: d4c803bd3a684d7951bf88dcecf1f14af43ae411
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/10/2018
ms.locfileid: "42540548"
---
# <a name="implementationonly"></a>implementation_only
**C + + 专用**  
  
取消生成 .tlh 头文件（主要头文件）。  
  
## <a name="syntax"></a>语法  
  
```  
implementation_only  
```  
  
## <a name="remarks"></a>备注  
 
此文件包含用于公开类型库内容的所有声明。 具有包装器成员函数的实现的 .tli 头文件将会生成并包含在编译中。  
  
指定此特性后，.tli 标头的内容将位于通常在 .tlh 标头中使用的同一命名空间中。 此外，成员函数未声明为内联。  
  
**Implementation_only**属性适合使用结合[no_implementation](../preprocessor/no-implementation.md)属性作为一种方法将实现保持预编译标头 (PCH) 文件。 将在用于创建 PCH 的源区域中放置具有 `#import` 特性的 `no_implementation` 语句。 生成的 PCH 由很多源文件使用。 `#import`语句**implementation_only**然后 PCH 区域外使用属性。 您需要在源文件之一中仅使用此语句一次。 这将生成所有必需的包装器成员函数，而不会额外重新编译每个源文件。  
  
> [!NOTE]
> **Implementation_only**属性中某个`#import`语句必须是与另一种结合使用`#import`语句的相同类型库的具有`no_implementation`属性。 否则，将生成编译器错误。 这是因为生成的包装器类定义`#import`语句`no_implementation`编译生成的实现所需属性是**implementation_only**属性。  
  
**结束 c + + 专用**  
  
## <a name="see-also"></a>请参阅  
 
[#import 属性](../preprocessor/hash-import-attributes-cpp.md)   
[#import 指令](../preprocessor/hash-import-directive-cpp.md)
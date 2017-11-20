---
title: "implementation_only |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: implementation_only
dev_langs: C++
helpviewer_keywords: implementation_only attribute
ms.assetid: d8cabc86-4425-45a0-9587-d57536980088
caps.latest.revision: "4"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 673fb22feaf53ec4fa018a45c88073e1c04f6c71
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
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
  
 `implementation_only`属性供结合使用[no_implementation](../preprocessor/no-implementation.md)作为一种预编译标头 (PCH) 文件中保持实现的属性。 将在用于创建 PCH 的源区域中放置具有 `#import` 特性的 `no_implementation` 语句。 生成的 PCH 由很多源文件使用。 之后将在 PCH 区域外使用具有 `#import` 特性的 `implementation_only` 语句。 您需要在源文件之一中仅使用此语句一次。 这将生成所有必需的包装器成员函数，而不会额外重新编译每个源文件。  
  
> [!NOTE]
>  一个 `implementation_only` 语句中的 `#import` 特性必须与同一类型库的具有 `#import` 特性的另一个 `no_implementation` 语句结合使用。 否则，将生成编译器错误。 这是因为编译 `#import` 特性生成的实现需要具有 `no_implementation` 特性的 `implementation_only` 语句生成的包装器类定义。  
  
 **结束 c + + 专用**  
  
## <a name="see-also"></a>另请参阅  
 [#import 属性](../preprocessor/hash-import-attributes-cpp.md)   
 [#import 指令](../preprocessor/hash-import-directive-cpp.md)
---
title: no_namespace |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- no_namespace
dev_langs:
- C++
helpviewer_keywords:
- no_namespace attribute
ms.assetid: 5d81b741-a558-451b-b493-1f3b18967337
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a02919e1e96717c1accc6343ecff32a66968cbcc
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/19/2018
ms.locfileid: "46378809"
---
# <a name="nonamespace"></a>no_namespace
**C + + 专用**  
  
指定命名空间的名称不由编译器生成。  
  
## <a name="syntax"></a>语法  
  
```  
no_namespace  
```  
  
## <a name="remarks"></a>备注  
 
`#import` 标头文件中的类型库内容通常在命名空间中定义。 中指定的命名空间名称`library`语句的原始 IDL 文件。 如果**no_namespace**指定属性，则编译器不生成此命名空间。  
  
如果你想要使用不同的命名空间名称，然后使用[rename_namespace](../preprocessor/rename-namespace.md)特性。  
  
**结束 c + + 专用**  
  
## <a name="see-also"></a>请参阅  
 
[#import 属性](../preprocessor/hash-import-attributes-cpp.md)<br/>
[#import 指令](../preprocessor/hash-import-directive-cpp.md)
---
title: no_auto_exclude |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- no_auto_exclude
dev_langs:
- C++
helpviewer_keywords:
- no_auto_exclude attribute
ms.assetid: 3241ef9c-758a-4e86-bdc5-37da6072430f
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 67d077ca620661ffda2e8664b2a4fb9ef5ea7168
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/19/2018
ms.locfileid: "46408253"
---
# <a name="noautoexclude"></a>no_auto_exclude
**C + + 专用**  
  
禁用自动排除。  
  
## <a name="syntax"></a>语法  
  
```  
no_auto_exclude  
```  
  
## <a name="remarks"></a>备注  
 
类型库可能包含在系统标头文件或其他类型库中定义的项的定义。 `#import` 尝试通过自动排除此类项来避免多个定义错误。 完成此操作后，[编译器警告 （等级 3） C4192](../error-messages/compiler-warnings/compiler-warning-level-3-c4192.md)为每个要排除的项，将发出。 您可以使用此特性来禁用此自动排除。  
  
**结束 c + + 专用**  
  
## <a name="see-also"></a>请参阅  
 
[#import 属性](../preprocessor/hash-import-attributes-cpp.md)<br/>
[#import 指令](../preprocessor/hash-import-directive-cpp.md)
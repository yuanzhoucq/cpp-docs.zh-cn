---
title: no_dual_interfaces |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- no_dual_interfaces
dev_langs:
- C++
helpviewer_keywords:
- no_dual_interfaces attribute
ms.assetid: 9acd5d9d-4a49-4cdc-9470-73a2c23cf512
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 4eb26790a46f46638e4a4180ee2209efefda201c
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/19/2018
ms.locfileid: "46432212"
---
# <a name="nodualinterfaces"></a>no_dual_interfaces
**C + + 专用**  
  
更改编译器为双重接口方法生成包装器函数的方式。  
  
## <a name="syntax"></a>语法  
  
```  
no_dual_interfaces  
```  
  
## <a name="remarks"></a>备注  
 
通常，该包装器将通过接口的虚函数表调用方法。 与**no_dual_interfaces**，而是调用包装器`IDispatch::Invoke`来调用该方法。  
  
**结束 c + + 专用**  
  
## <a name="see-also"></a>请参阅  
 
[#import 属性](../preprocessor/hash-import-attributes-cpp.md)<br/>
[#import 指令](../preprocessor/hash-import-directive-cpp.md)
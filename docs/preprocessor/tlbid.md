---
title: tlbid |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- tlbid
dev_langs:
- C++
helpviewer_keywords:
- tlbid attribute
ms.assetid: 54b06785-191b-4e77-a9a5-485f2b4acb09
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 9d651546733f42b1a714ac7a39992fa2d392c8fa
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/07/2018
---
# <a name="tlbid"></a>tlbid
**C + + 专用**  
  
 允许加载主类型库之外的库。  
  
## <a name="syntax"></a>语法  
  
```  
tlbid(number)  
```  
  
#### <a name="parameters"></a>参数  
 `number`  
 `filename` 中的类型库的编号。  
  
## <a name="remarks"></a>备注  
 如果将多个类型库内置于一个 DLL，则可以使用 `tlbid` 来加载非主类型库。  
  
 例如：  
  
```  
#import <MyResource.dll> tlbid(2)  
```  
  
 等效于：  
  
```  
LoadTypeLib("MyResource.dll\\2");  
```  
  
 **结束 c + + 专用**  
  
## <a name="see-also"></a>请参阅  
 [#import 属性](../preprocessor/hash-import-attributes-cpp.md)   
 [#import 指令](../preprocessor/hash-import-directive-cpp.md)
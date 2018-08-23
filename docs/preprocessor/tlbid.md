---
title: tlbid |Microsoft Docs
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
ms.openlocfilehash: 1ec0150e63209728cf2f02c854fe03702b8a45b4
ms.sourcegitcommit: d4c803bd3a684d7951bf88dcecf1f14af43ae411
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/10/2018
ms.locfileid: "42540547"
---
# <a name="tlbid"></a>tlbid
**C + + 专用**  
  
允许加载主类型库之外的库。  
  
## <a name="syntax"></a>语法  
  
```  
tlbid(number)  
```  
  
### <a name="parameters"></a>参数  
*数量*  
`filename` 中的类型库的编号。  
  
## <a name="remarks"></a>备注  
 
如果多个类型库内置于一个 dll，它可以加载非主类型库使用**tlbid**。  
  
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
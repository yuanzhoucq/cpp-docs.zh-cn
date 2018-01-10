---
title: "tlbid |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: tlbid
dev_langs: C++
helpviewer_keywords: tlbid attribute
ms.assetid: 54b06785-191b-4e77-a9a5-485f2b4acb09
caps.latest.revision: "4"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 812b105fc02782b611b3f55061e448062dcd07c7
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
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
  
 例如:  
  
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
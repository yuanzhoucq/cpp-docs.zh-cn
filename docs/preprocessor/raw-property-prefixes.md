---
title: "raw_property_prefixes |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- raw_property_prefixes
dev_langs:
- C++
helpviewer_keywords:
- raw_property_prefixes attribute
ms.assetid: 03a0f48c-c460-4175-a762-9f7f8d84b12f
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 9c38541d720a9b2bc857a4121c2d0e33ec4fc5b9
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/23/2018
---
# <a name="rawpropertyprefixes"></a>raw_property_prefixes
**C + + 专用**  
  
 指定用于三个属性方法的备用前缀。  
  
## <a name="syntax"></a>语法  
  
```  
raw_property_prefixes("GetPrefix","PutPrefix","PutRefPrefix")  
```  
  
#### <a name="parameters"></a>参数  
 `GetPrefix`  
 前缀用于**propget**方法。  
  
 `PutPrefix`  
 前缀用于**propput**方法。  
  
 `PutRefPrefix`  
 前缀用于**propputref**方法。  
  
## <a name="remarks"></a>备注  
 默认情况下，低级别**propget**， **propput**，和**propputref**方法公开的成员函数使用前缀名为**get_**， **put_**，和**putref_**分别。 这些前缀与在 MIDL 生成的标头文件中使用的名称兼容。  
  
 **结束 c + + 专用**  
  
## <a name="see-also"></a>请参阅  
 [#import 属性](../preprocessor/hash-import-attributes-cpp.md)   
 [#import 指令](../preprocessor/hash-import-directive-cpp.md)
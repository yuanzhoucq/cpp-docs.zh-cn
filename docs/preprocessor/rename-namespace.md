---
title: rename_namespace |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- rename_namespace
dev_langs:
- C++
helpviewer_keywords:
- rename_namespace attribute
ms.assetid: 45006d2b-36cd-4bec-98b9-3b8ec45299e3
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 0876aed966db79b23d506bffd9247dd68d4a3935
ms.sourcegitcommit: d4c803bd3a684d7951bf88dcecf1f14af43ae411
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/10/2018
ms.locfileid: "42540546"
---
# <a name="renamenamespace"></a>rename_namespace
**C + + 专用**  
  
重命名包含类型库内容的命名空间。  
  
## <a name="syntax"></a>语法  
  
```  
rename_namespace("NewName")  
```  
  
### <a name="parameters"></a>参数  
*新名称*  
命名空间的新名称。  
  
## <a name="remarks"></a>备注  
 
它采用一个参数， *NewName*，它指定命名空间的新名称。  
  
若要删除命名空间，请使用[no_namespace](../preprocessor/no-namespace.md)特性。  
  
**结束 c + + 专用**  
  
## <a name="see-also"></a>请参阅  
 
[#import 属性](../preprocessor/hash-import-attributes-cpp.md)   
[#import 指令](../preprocessor/hash-import-directive-cpp.md)
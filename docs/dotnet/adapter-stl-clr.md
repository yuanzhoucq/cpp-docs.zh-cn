---
title: "适配器 (STL/CLR) |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: <cliext/adapter>
dev_langs: C++
helpviewer_keywords:
- <adapter> header [STL/CLR]
- adapter [STL/CLR]
- <cliext/adapter> header [STL/CLR]
ms.assetid: 71ce7e51-42b6-4f70-9595-303791a97677
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: fc5480896ed931fffdd4087eb5f39cfd8bbe67aa
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="adapter-stlclr"></a>adapter (STL/CLR)
STL/CLR 标头`<cliext/adapter>`指定两个模板类 (`collection_adapter`和`range_adapter`)，该模板函数`make_collection`。  
  
## <a name="syntax"></a>语法  
  
```  
#include <cliext/adapter>  
```  
  
## <a name="remarks"></a>备注  
  
|类|描述|  
|-----------|-----------------|  
|[collection_adapter (STL/CLR)](../dotnet/collection-adapter-stl-clr.md)|包装为一个范围的基类库 (BCL) 集合。|  
|[range_adapter (STL/CLR)](../dotnet/range-adapter-stl-clr.md)|包装为 BCL 集合的范围。|  
  
|函数|描述|  
|--------------|-----------------|  
|[make_collection (STL/CLR)](../dotnet/make-collection-stl-clr.md)|创建范围适配器使用的迭代器对。|  
  
## <a name="requirements"></a>要求  
 **标头：** \<cliext/适配器 >  
  
 **Namespace:** cliext  
  
## <a name="see-also"></a>另请参阅  
 [STL/CLR 库参考](../dotnet/stl-clr-library-reference.md)
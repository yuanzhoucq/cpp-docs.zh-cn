---
title: "ATL 全局变量 |Microsoft 文档"
ms.custom: 
ms.date: 12/06/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- ATLBASE/_pAtlModule
dev_langs:
- C++
helpviewer_keywords:
- global variables, ATL
- _pAtlModule
ms.assetid: e881a319-99ca-4f5d-8a0b-34b3dcd0f37f
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: bcf9a88e57d351a3fb6647f6deea3eccbad33bf8
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="atl-global-variables"></a>ATL 全局变量

## <a name="patlmodule"></a>_pAtlModule  
存储指向当前模块的全局变量。  

```cpp  
__declspec(selectany) CAtlModule * _pAtlModule  
```  
### <a name="remarks"></a>备注  
在此全局变量的方法可以用于提供 （现已过时） 类 CComModule 提供在 Visual c + + 6.0 中的功能。

### <a name="example"></a>示例  

```cpp  
LONG lLocks = _pAtlModule->GetLockCount();  
```  
### <a name="requirements"></a>惠?  
 **标头：** atlbase.h  


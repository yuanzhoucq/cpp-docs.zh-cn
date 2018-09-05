---
title: ATL 全局变量 |Microsoft Docs
ms.custom: ''
ms.date: 12/06/2017
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- ATLBASE/_pAtlModule
dev_langs:
- C++
helpviewer_keywords:
- global variables, ATL
- _pAtlModule
ms.assetid: e881a319-99ca-4f5d-8a0b-34b3dcd0f37f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 55844390b872cb0d94ff991ab79b8519388d009f
ms.sourcegitcommit: 92dbc4b9bf82fda96da80846c9cfcdba524035af
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/05/2018
ms.locfileid: "43762455"
---
# <a name="atl-global-variables"></a>ATL 全局变量

## <a name="patlmodule"></a>_pAtlModule

存储指向当前模块的全局变量。  

```cpp  
__declspec(selectany) CAtlModule * _pAtlModule  
```  
### <a name="remarks"></a>备注

此全局变量的方法可以用于提供 （现在已过时） 类 CComModule Visual c + + 6.0 中提供的功能。

### <a name="example"></a>示例

```cpp  
LONG lLocks = _pAtlModule->GetLockCount();  
```  
### <a name="requirements"></a>要求

**标头：** atlbase.h  


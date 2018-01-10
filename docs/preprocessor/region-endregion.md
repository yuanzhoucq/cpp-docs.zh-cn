---
title: "地区、 endregion |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vc-pragma.endregion
- endregion_CPP
- region_CPP
- vc-pragma.region
dev_langs: C++
helpviewer_keywords:
- pragmas, region
- pragmas, endregion
- endregion pragma
- region pragma
ms.assetid: c697f807-622f-4796-851b-68a42bbecd84
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: ad2eb3d094447ae3ae35b0dbe9dc0fef2fe06710
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="region-endregion"></a>region、endregion
**#pragma 区域**允许你指定的可以展开或折叠时使用的代码块[大纲显示功能](/visualstudio/ide/outlining)的 Visual Studio 代码编辑器中。  
  
## <a name="syntax"></a>语法  
  
```  
#pragma region name  
#pragma endregion comment  
```  
  
#### <a name="parameters"></a>参数  
 `comment`（可选）  
 将在代码编辑器中显示的注释。  
  
 *名称*（可选）  
 区域的名称。  此名称将显示在代码编辑器中。  
  
## <a name="remarks"></a>备注  
 **#pragma endregion**标记的结束**#pragma 区域**块。  
  
 A`#region`块必须终止与**#pragma endregion**。  
  
## <a name="example"></a>示例  
  
```  
// pragma_directives_region.cpp  
#pragma region Region_1  
void Test() {}  
void Test2() {}  
void Test3() {}  
#pragma endregion Region_1  
  
int main() {}  
```  
  
## <a name="see-also"></a>请参阅  
 [Pragma 指令和 __Pragma 关键字](../preprocessor/pragma-directives-and-the-pragma-keyword.md)
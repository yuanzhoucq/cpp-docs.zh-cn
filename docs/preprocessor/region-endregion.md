---
title: 区域、 endregion |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- vc-pragma.endregion
- endregion_CPP
- region_CPP
- vc-pragma.region
dev_langs:
- C++
helpviewer_keywords:
- pragmas, region
- pragmas, endregion
- endregion pragma
- region pragma
ms.assetid: c697f807-622f-4796-851b-68a42bbecd84
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 9e6ec22be873dcec06f224913eb905a2779e4efd
ms.sourcegitcommit: d4c803bd3a684d7951bf88dcecf1f14af43ae411
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/10/2018
ms.locfileid: "42538207"
---
# <a name="region-endregion"></a>region、endregion
`#pragma region` 允许您指定的可以展开或折叠时使用的代码块[大纲功能](/visualstudio/ide/outlining)的 Visual Studio 代码编辑器中。  
  
## <a name="syntax"></a>语法  
  
```  
#pragma region name  
#pragma endregion comment  
```  
  
### <a name="parameters"></a>参数  
*注释*（可选）  
将在代码编辑器中显示的注释。  
  
 名称（可选）  
区域的名称。  此名称将显示在代码编辑器中。  
  
## <a name="remarks"></a>备注  
 
`#pragma endregion` 标记的末尾`#pragma region`块。  
  
一个`#region`块必须终止与`#pragma endregion`。  
  
## <a name="example"></a>示例  
  
```cpp  
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
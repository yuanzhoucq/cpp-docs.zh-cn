---
title: 区域、 endregion |Microsoft Docs
ms.custom: ''
ms.date: 10/18/2018
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
ms.openlocfilehash: 2e360009eb9126604d4466daed2445c7dfc582d4
ms.sourcegitcommit: 0164af5615389ffb1452ccc432eb55f6dc931047
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/23/2018
ms.locfileid: "49808064"
---
# <a name="region-endregion"></a>region、endregion

`#pragma region` 允许您指定的可以展开或折叠时使用的代码块[大纲功能](/visualstudio/ide/outlining)的 Visual Studio 代码编辑器中。

## <a name="syntax"></a>语法

```
#pragma region name
#pragma endregion comment
```

### <a name="parameters"></a>参数

*comment*<br/>
（可选）在代码编辑器中将显示注释。

*name*<br/>
（可选）区域的名称。  此名称将显示在代码编辑器中。

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
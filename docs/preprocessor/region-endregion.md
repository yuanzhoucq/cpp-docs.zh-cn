---
title: region、endregion 杂注
ms.date: 08/29/2019
f1_keywords:
- vc-pragma.endregion
- endregion_CPP
- region_CPP
- vc-pragma.region
helpviewer_keywords:
- pragmas, region
- pragmas, endregion
- endregion pragma
- region pragma
ms.assetid: c697f807-622f-4796-851b-68a42bbecd84
ms.openlocfilehash: 4a01e04582ac81d678aa0702945c62ee974a4428
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/03/2019
ms.locfileid: "70222374"
---
# <a name="region-endregion-pragmas"></a>region、endregion 杂注

`#pragma region`允许你指定一个代码块, 当使用 Visual Studio Code 编辑器的[大纲显示功能](/visualstudio/ide/outlining)时, 可以展开或折叠该代码块。

## <a name="syntax"></a>语法

> **#pragma 区域** *名称*\
> **#pragma endregion** *注释*

### <a name="parameters"></a>参数

*条*\
可有可无要在代码编辑器中显示的注释。

*路径名*\
可有可无区域的名称。 此名称显示在代码编辑器中。

## <a name="remarks"></a>备注

`#pragma endregion`标记`#pragma region`块的结尾。

`#region`块必须`#pragma endregion`由指令终止。

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

[Pragma 指令和 __pragma 关键字](../preprocessor/pragma-directives-and-the-pragma-keyword.md)

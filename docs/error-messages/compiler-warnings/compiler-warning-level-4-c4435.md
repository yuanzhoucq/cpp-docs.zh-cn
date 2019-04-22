---
title: 编译器警告（等级 4）C4435
ms.date: 11/04/2016
ms.assetid: a04524af-2b71-4ff9-9729-d9d1d1904ed7
ms.openlocfilehash: 43c13c484d6e9accee7c4d2c58b72a4539a75c4c
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/18/2019
ms.locfileid: "59041223"
---
# <a name="compiler-warning-level-4-c4435"></a>编译器警告（等级 4）C4435

class1:/ Vd2 下的对象布局将因虚拟基 class2 而更改

默认情况下，此警告处于关闭状态。 请参阅 [默认情况下处于关闭状态的编译器警告](../../preprocessor/compiler-warnings-that-are-off-by-default.md) 了解详细信息。

在 /vd1 的默认编译选项下，派生类没有指示的虚拟基的 `vtordisp` 字段。  如果 /vd2 或 `#pragma vtordisp(2)` 有效，`vtordisp` 字段将存在，并更改对象布局。  如果使用不同的 `vtordisp` 设置编译交互的模块，这可能导致二进制兼容性问题。

## <a name="example"></a>示例

下面的示例生成 C4435。

```cpp
// C4435.cpp
// compile with: /c /W4
#pragma warning(default : 4435)
class A
{
public:
    virtual ~A() {}
};

class B : public virtual A  // C4435
{};
```

## <a name="see-also"></a>请参阅

[vtordisp](../../preprocessor/vtordisp.md)<br/>
[/vd（禁用构造置换）](../../build/reference/vd-disable-construction-displacements.md)
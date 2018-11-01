---
title: 编译器警告（等级 4）C4435
ms.date: 11/04/2016
ms.assetid: a04524af-2b71-4ff9-9729-d9d1d1904ed7
ms.openlocfilehash: 7db1d483f571289c5b890c223ba1e59ba3d1f41e
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50572323"
---
# <a name="compiler-warning-level-4-c4435"></a>编译器警告（等级 4）C4435

“class1”: /vd2 下的对象布局将因虚拟基“class2”而更改

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
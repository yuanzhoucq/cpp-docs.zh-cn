---
title: vtordisp 杂注
ms.date: 08/29/2019
f1_keywords:
- vc-pragma.vtordisp
- vtordisp_CPP
helpviewer_keywords:
- pragmas, vtordisp
- vtordisp pragma
ms.assetid: 05b7d73c-43fa-4b62-8c8a-170a9e427391
ms.openlocfilehash: a6ffc5c0323389d812e659ff68555a8c8c993126
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87219360"
---
# <a name="vtordisp-pragma"></a>vtordisp 杂注

**C++ 专用**

控制隐藏的 `vtordisp` 构造/析构置换成员的添加。

## <a name="syntax"></a>语法

> **#pragma vtordisp （** [ **push，** ] *n* **）**\
> **#pragma vtordisp （pop）**\
> **#pragma vtordisp （）**\
> **#pragma vtordisp （** [**推送，** ] { **on**  |  **off** } **）**

### <a name="parameters"></a>参数

**请求**\
推送 `vtordisp` 内部编译器堆栈上的当前设置，并将新设置设置 `vtordisp` 为*n*。  如果未指定*n* ，则当前 `vtordisp` 设置保持不变。

**弹出**\
从内部编译器堆栈中移除顶部记录，并将设置还原 `vtordisp` 为删除的值。

*北*\
指定设置的新值 `vtordisp` 。 可能的值为0、1或2，对应于 `/vd0` 、 `/vd1` 和 `/vd2` 编译器选项。 有关详细信息，请参阅[/vd （禁用构造置换）](../build/reference/vd-disable-construction-displacements.md)。

**基于**\
等效于 `#pragma vtordisp(1)`。

**非**\
等效于 `#pragma vtordisp(0)`。

## <a name="remarks"></a>备注

**Vtordisp**杂注仅适用于使用虚拟库的代码。 如果派生类重写它从虚拟基类继承的虚函数，并且派生类的构造函数或析构函数使用指向该虚拟基类的指针调用该函数，则编译器可能将其他隐藏的 `vtordisp` 字段引入具有虚拟基的类。

**Vtordisp**杂注影响其后的类的布局。 `/vd0`、 `/vd1` 和 `/vd2` 选项为完整模块指定相同的行为。 指定0或**off**会禁止显示隐藏 `vtordisp` 成员。 仅当**vtordisp**该类的构造函数和析构函数不能在指针指向的对象上调用虚函数时，才会关闭 vtordisp **`this`** 。

指定 "1" 或 "**开**" 时，默认情况下，将在必要时启用隐藏 `vtordisp` 成员。

如果指定2，则将 `vtordisp` 为所有具有虚函数的虚拟基启用隐藏成员。  `#pragma vtordisp(2)`可能需要确保 **`dynamic_cast`** 在部分构造的对象上的性能正确。 有关详细信息，请参阅[编译器警告（等级1） C4436](../error-messages/compiler-warnings/compiler-warning-level-1-c4436.md)。

`#pragma vtordisp()`无参数的情况下，会将 `vtordisp` 设置还原为其初始设置。

```cpp
#pragma vtordisp(push, 2)
class GetReal : virtual public VBase { ... };
#pragma vtordisp(pop)
```

**结束 C++ 专用**

## <a name="see-also"></a>另请参阅

[Pragma 指令和 __pragma 关键字](../preprocessor/pragma-directives-and-the-pragma-keyword.md)

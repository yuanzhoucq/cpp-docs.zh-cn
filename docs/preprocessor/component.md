---
title: 组件
ms.date: 04/08/2019
f1_keywords:
- vc-pragma.component
- component_CPP
helpviewer_keywords:
- component pragma
- pragmas, component
ms.assetid: 7b66355e-3201-4c14-8190-f4a2a81a604a
ms.openlocfilehash: 4870860650a39d27639ad18100ba37ba14aa15c0
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/18/2019
ms.locfileid: "59424061"
---
# <a name="component"></a>组件

控件的浏览信息或从源文件中的依赖关系信息的集合。

## <a name="syntax"></a>语法

> **#pragma component( browser,** { **on** | **off** }[**,** **references** [**,** *name* ]] **)** \
> **#pragma 组件 (minrebuild 上** | **关闭)** \
> **#pragma 组件 (mintypeinfo 上** | **关闭)**

## <a name="remarks"></a>备注

### <a name="browser"></a>浏览者

您可以打开或关闭收集，也可以指定在收集信息时忽略特定名称。

使用打开或关闭来控制对之前的杂注中的浏览信息的收集。 例如：

```cpp
#pragma component(browser, off)
```

停止编译器收集浏览信息。

> [!NOTE]
> 若要启用的带此杂注的浏览信息的收集[必须先启用浏览信息](../build/reference/building-browse-information-files-overview.md)。

`references`可以使用选项，带或不带*名称*参数。 使用`references`而无需*名称*打开或关闭的引用的收集 （其他浏览信息仍是收集，但是）。 例如：

```cpp
#pragma component(browser, off, references)
```

停止编译器收集引用信息。

使用`references`与*名称*并`off`可防止对引用*名称*使其不显示浏览信息窗口。 使用此语法可忽略您不感兴趣的名称和类型，并减小浏览信息文件的大小。 例如：

```cpp
#pragma component(browser, off, references, DWORD)
```

将忽略对 DWORD 从该时间点的引用。 您可以启用对 DWORD 的引用重新使用收集的`on`:

```cpp
#pragma component(browser, on, references, DWORD)
```

这是唯一的方法，若要恢复到引用的收集*名称*; 你必须显式打开任何*名称*已处于关闭状态。

若要防止预处理器扩展*名称*（例如 0 到展开为 NULL），加上双引号它：

```cpp
#pragma component(browser, off, references, "NULL")
```

### <a name="minimal-rebuild"></a>最小重新生成

已弃用[/Gm （启用最小重新生成）](../build/reference/gm-enable-minimal-rebuild.md)功能要求编译器创建并存储C++类依赖关系信息，将占用磁盘空间。 若要节省磁盘空间，可以使用`#pragma component( minrebuild, off )`时不需要收集依赖关系信息，例如，不变的标头文件中。 插入`#pragma component(minrebuild, on)`后重新启用依赖项收集不变的类。

### <a name="reduce-type-information"></a>减少类型信息

`mintypeinfo`选项可减少指定的区域的调试信息。 此信息的量相当大，会影响 .pdb 和 .obj 文件。 您不能在 mintypeinfo 区域中调试类和结构。 使用 mintypeinfo 选项可帮助避免以下警告：

```cmd
LINK : warning LNK4018: too many type indexes in PDB "filename", discarding subsequent type information
```

有关详细信息，请参阅[/Gm （启用最小重新生成）](../build/reference/gm-enable-minimal-rebuild.md)编译器选项。

## <a name="see-also"></a>请参阅

[Pragma 指令和 __Pragma 关键字](../preprocessor/pragma-directives-and-the-pragma-keyword.md)
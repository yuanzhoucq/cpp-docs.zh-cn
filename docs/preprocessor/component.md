---
title: component 杂注
ms.date: 08/29/2019
f1_keywords:
- vc-pragma.component
- component_CPP
helpviewer_keywords:
- component pragma
- pragmas, component
ms.assetid: 7b66355e-3201-4c14-8190-f4a2a81a604a
ms.openlocfilehash: 578c590bdb4223f173e0249c18d0eea4e78a18db
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/03/2019
ms.locfileid: "70220480"
---
# <a name="component-pragma"></a>component 杂注

控制源文件内浏览信息或依赖项信息的集合。

## <a name="syntax"></a>语法

> **#pragma 组件 (浏览器,** { **on** | **off** } [ **,** **引用**[ **,** *名称*]] **)**  \
> **#pragma 组件 (minrebuild** ) |  \
> **#pragma 组件 (mintypeinfo** ) | 

## <a name="remarks"></a>备注

### <a name="browser"></a>浏览者

您可以打开或关闭收集，也可以指定在收集信息时忽略特定名称。

使用打开或关闭来控制对之前的杂注中的浏览信息的收集。 例如：

```cpp
#pragma component(browser, off)
```

停止编译器收集浏览信息。

> [!NOTE]
> 若要启用通过此杂注收集浏览信息,[必须先启用浏览信息](../build/reference/building-browse-information-files-overview.md)。

**引用**选项可与或不带*name*参数一起使用。 使用不带*名称*的**引用**将打开或关闭引用的收集 (但仍会收集其他浏览信息)。 例如:

```cpp
#pragma component(browser, off, references)
```

停止编译器收集引用信息。

使用*名称*和**off** **引用**可防止在 "浏览信息" 窗口中显示*名称*引用。 使用此语法可忽略您不感兴趣的名称和类型，并减小浏览信息文件的大小。 例如：

```cpp
#pragma component(browser, off, references, DWORD)
```

忽略从该点开始对 DWORD 值的引用。 可以通过使用**在**上打开对 DWORD 的引用的收集:

```cpp
#pragma component(browser, on, references, DWORD)
```

这是继续收集*名称*引用的唯一方法;您必须显式打开已关闭的任何*名称*。

若要防止预处理器扩展*名称*(如将 NULL 扩展到 0), 请在其两侧加上引号:

```cpp
#pragma component(browser, off, references, "NULL")
```

### <a name="minimal-rebuild"></a>最小重新生成

弃用的[/gm (启用最小重新生成)](../build/reference/gm-enable-minimal-rebuild.md)功能要求编译器创建并存储C++类依赖关系信息, 这会占用磁盘空间。 若要节省磁盘空间, 可以在`#pragma component( minrebuild, off )`不需要收集依赖项信息时使用, 例如, 在不变的标头文件中。 在`#pragma component( minrebuild, on )`不变的类后插入, 以重新打开依赖项集合。

### <a name="reduce-type-information"></a>减小类型信息

`mintypeinfo`选项可减少指定区域的调试信息。 此信息的量相当大，会影响 .pdb 和 .obj 文件。 您不能在 mintypeinfo 区域中调试类和结构。 使用 mintypeinfo 选项可帮助避免以下警告：

```cmd
LINK : warning LNK4018: too many type indexes in PDB "filename", discarding subsequent type information
```

有关详细信息, 请参阅[/gm (启用最小重新生成)](../build/reference/gm-enable-minimal-rebuild.md)编译器选项。

## <a name="see-also"></a>请参阅

[Pragma 指令和 __pragma 关键字](../preprocessor/pragma-directives-and-the-pragma-keyword.md)

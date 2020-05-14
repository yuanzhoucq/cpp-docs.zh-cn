---
title: PgoAutoSweep
ms.date: 07/02/2019
f1_keywords:
- PgoAutoSweep
- PogoAutoSweepA
- PogoAutoSweepW
ms.openlocfilehash: 57bcd1b2e9f0a3312867c4373fd1e50bcf91576e
ms.sourcegitcommit: 9b904e490b1e262293a602bd1291a8f3045e755b
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/03/2019
ms.locfileid: "67552246"
---
# <a name="pgoautosweep"></a>PgoAutoSweep

`PgoAutoSweep` 将当前配置文件计数器信息保存到文件，然后重置计数器。 在按配置优化训练期间使用函数将所有配置文件数据从正在运行的程序写入到 `.pgc` 文件，以便以后在优化生成中使用。

## <a name="syntax"></a>语法

```cpp
void PgoAutoSweep(const char* name);    // ANSI/MBCS
void PgoAutoSweep(const wchar_t* name); // UNICODE
```

### <a name="parameters"></a>参数

*name*<br/>
保存的 `.pgc` 文件的标识字符串。

## <a name="remarks"></a>备注

可以从应用程序调用 `PgoAutoSweep`，以在应用程序执行期间的任何点保存和重置配置文件数据。 在检测生成中，`PgoAutoSweep` 会捕获当前分析数据，将它保存在文件中，然后重置配置文件计数器。 它相当于在可执行文件中的特定点调用 [pgosweep](pgosweep.md) 命令。 在优化生成中，`PgoAutoSweep` 不执行任何操作。

保存的配置文件计数器数据会放置在一个名为 base_name-name!value.pgc    的文件中，其中 base_name  是可执行文件的基名称，name  是传递给 `PgoAutoSweep` 的参数，value  是唯一值，通常为单调递增的数字，用于防止文件名冲突。

`PgoAutoSweep` 创建的 `.pgc` 文件必须合并到用于创建优化可执行文件的 `.pgd` 文件中。 可以使用 [pgomgr](pgomgr.md) 命令执行合并。

通过对 [/USEPROFILE](reference/useprofile.md) 链接器选项使用 PGD=  filename  参数，或是使用已弃用的 /PGD  链接器选项，可以在优化生成期间将合并的 `.pgd` 文件的名称传递给链接器。 如果将 `.pgc` 文件合并到名为 base_name  .pgd 的文件中，则无需在命令行上指定文件名，因为默认情况下，链接器会选取此文件名。

`PgoAutoSweep` 函数会维护在创建检测生成时指定的线程安全设置。 如果使用默认设置或是对 [/GENPROFILE 或 /FASTGENPROFILE](reference/genprofile-fastgenprofile-generate-profiling-instrumented-build.md) 链接器选项指定 NOEXACT  参数，则对 `PgoAutoSweep` 的调用不是线程安全的。 EXACT  参数可创建线程安全且更精确，但速度较慢的检测可执行文件。

## <a name="requirements"></a>要求

|例程所返回的值|必需的标头|
|-------------|---------------------|
|`PgoAutoSweep`|\<pgobootrun.h>|

可执行文件必须包含链接库中的 pgobootrun.lib 文件。 此文件包含在 Visual Studio 安装中（位于每个受支持体系结构的 VC 库目录）。

## <a name="example"></a>示例

下面的示例使用 `PgoAutoSweep` 在执行过程中的不同点创建两个 `.pgc` 文件。 第一个文件包含描述运行时行为的数据，直到 `count` 等于 3，第二个文件包含此点之后收集的数据，直到应用程序终止之前。

```cpp
// pgoautosweep.cpp
// Compile by using: cl /c /GL /W4 /EHsc /O2 pgoautosweep.cpp
// Link to instrument: link /LTCG /genprofile pgobootrun.lib pgoautosweep.obj
// Run to generate data: pgoautosweep
// Merge data by using command line pgomgr tool:
// pgomgr /merge pgoautosweep-func1!1.pgc pgoautosweep-func2!1.pgc pgoautosweep.pgd
// Link to optimize: link /LTCG /useprofile pgobootrun.lib pgoautosweep.obj

#include <iostream>
#include <windows.h>
#include <pgobootrun.h>

void func2(int count)
{
    std::cout << "hello from func2 " << count << std::endl;
    Sleep(2000);
}

void func1(int count)
{
    std::cout << "hello from func1 " << count << std::endl;
    Sleep(2000);
}

int main()
{
    int count = 10;
    while (count--)
    {
        if (count < 3)
            func2(count);
        else
        {
            func1(count);
            if (count == 3)
            {
                PgoAutoSweep("func1");
            }
        }
    }
    PgoAutoSweep("func2");
}
```

在开发人员命令提示处，使用以下命令将代码编译为对象文件：

`cl /c /GL /W4 /EHsc /O2 pgoautosweep.cpp`

然后使用以下命令生成用于训练的检测生成：

`link /LTCG /genprofile pgobootrun.lib pgoautosweep.obj`

运行检测可执行文件以捕获训练数据。 调用 `PgoAutoSweep` 的数据输出保存在名为 pgoautosweep-func1!1.pgc 和 pgoautosweep-func2!1.pgc 的文件中。 程序在运行时的输出应如下所示：

```Output
hello from func1 9
hello from func1 8
hello from func1 7
hello from func1 6
hello from func1 5
hello from func1 4
hello from func1 3
hello from func2 2
hello from func2 1
hello from func2 0
```

通过运行 pgomgr  命令将保存的数据合并到配置文件训练数据库中：

`pgoautosweep-func1!1.pgc pgoautosweep-func2!1.pgc`

此命令的输出如下所示：

```Output
Microsoft (R) Profile Guided Optimization Manager 14.13.26128.0
Copyright (C) Microsoft Corporation. All rights reserved.

Merging pgoautosweep-func1!1.pgc
pgoautosweep-func1!1.pgc: Used  3.8% (22304 / 589824) of total space reserved.  0.0% of the counts were dropped due to overflow.
Merging pgoautosweep-func2!1.pgc
pgoautosweep-func2!1.pgc: Used  3.8% (22424 / 589824) of total space reserved.  0.0% of the counts were dropped due to overflow.
```

现在可以使用此训练数据生成优化生成。 使用以下命令生成优化可执行文件：

`link /LTCG /useprofile pgobootrun.lib pgoautosweep.obj`

```Output
Microsoft (R) Incremental Linker Version 14.13.26128.0
Copyright (C) Microsoft Corporation.  All rights reserved.

Merging pgoautosweep!1.pgc
pgoautosweep!1.pgc: Used  3.9% (22904 / 589824) of total space reserved.  0.0% of the counts were dropped due to overflow.
  Reading PGD file 1: pgoautosweep.pgd
Generating code

0 of 0 ( 0.0%) original invalid call sites were matched.
0 new call sites were added.
294 of 294 (100.00%) profiled functions will be compiled for speed
348 of 1239 inline instances were from dead/cold paths
294 of 294 functions (100.0%) were optimized using profile data
16870 of 16870 instructions (100.0%) were optimized using profile data
Finished generating code
```

## <a name="see-also"></a>请参阅

[按配置优化](profile-guided-optimizations.md)<br/>
[pgosweep](pgosweep.md)<br/>

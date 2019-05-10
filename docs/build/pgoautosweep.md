---
title: PgoAutoSweep
ms.date: 03/14/2018
f1_keywords:
- PgoAutoSweep
- PogoAutoSweepA
- PogoAutoSweepW
ms.openlocfilehash: 2d9804e5ce90663d44ac389ab4f71d10290e6470
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62295319"
---
# <a name="pgoautosweep"></a>PgoAutoSweep

`PgoAutoSweep` 将当前的配置文件计数器信息保存到一个文件，然后将重置计数器。 在培训，以将所有配置文件数据从正在运行的程序写入到在优化生成中的更高版本使用的.pgc 文件按配置优化过程中使用该函数。

## <a name="syntax"></a>语法

```cpp
void PgoAutoSweep(const char* name);    // ANSI/MBCS
void PgoAutoSweep(const wchar_t* name); // UNICODE
```

### <a name="parameters"></a>参数

*name*<br/>
已保存的.pgc 文件标识字符串。

## <a name="remarks"></a>备注

您可以调用`PgoAutoSweep`从你的应用程序，以保存并在应用程序执行期间重置任何位置的配置文件数据。 中的被检测生成`PgoAutoSweep`捕获当前分析数据、 将其保存在文件中，并将配置文件计数器重置。 它相当于调用[pgosweep](pgosweep.md)命令时可执行文件中的特定点。 在优化的生成，`PgoAutoSweep`不是执行任何操作。

保存的配置文件计数器数据放置在名为的文件中*base_name*-*名称*！*值*.pgc，其中*base_name*是可执行文件的基名称*名称*参数传递给`PgoAutoSweep`，以及*值*是唯一的值，通常单调递增的数字，以避免文件名称冲突。

创建的.pgc 文件`PgoAutoSweep`必须合并到要用于创建优化的可执行文件的.pgd 文件。 可以使用[pgomgr](pgomgr.md)命令来执行合并。

您可以合并的.pgd 文件的名称使用传递到链接器优化生成期间**PGD =**_filename_参数[/USEPROFILE](reference/useprofile.md)链接器选项，或通过使用已弃用 **/PGD**链接器选项。 如果你合并的.pgc 文件到名为的文件*base_name*.pgd，您不必在命令行上指定文件名因为链接器默认情况下选取此文件的名称。

`PgoAutoSweep`函数维护创建检测的生成时指定的线程安全设置。 如果使用默认设置或指定了**NOEXACT**自变量[/GENPROFILE 或 /FASTGENPROFILE]()链接器选项，调用`PgoAutoSweep`不是线程安全。 **EXACT**参数创建一个线程安全、 更准确，但速度较慢且经过检测的可执行文件。

## <a name="requirements"></a>要求

|例程所返回的值|必需的标头|
|-------------|---------------------|
|`PgoAutoSweep`|\<pgobootrun.h>|

可执行文件必须 pgobootrun.lib 文件包含链接的库。 此文件包含在 Visual Studio 安装，每个受支持的体系结构的 VC 库目录中。

## <a name="example"></a>示例

下面的示例使用`PgoAutoSweep`创建两个。在执行期间不同点的 PGC 文件。 第一个包含数据，用于描述直到运行时行为`count`等于 3，并且第二个包含之前只是应用程序终止前此点后收集的数据。

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

在开发人员命令提示符中，使用以下命令编译对象文件的代码：

`cl /c /GL /W4 /EHsc /O2 pgoautosweep.cpp`

然后使用以下命令，生成用于定型的被检测的生成：

`link /LTCG /genprofile pgobootrun.lib pgoautosweep.obj`

运行已检测的可执行文件，以捕获定型数据。 由调用的数据输出`PgoAutoSweep`保存在名为 pgoautosweep func1 文件 ！ 1.pgc 和 pgoautosweep func2 ！ 1.pgc。 程序的输出应如下所示运行：

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

通过运行已保存的数据合并到配置文件训练数据库**pgomgr**命令：

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

现在可以使用此训练数据来生成优化的生成。 使用以下命令来生成优化的可执行文件：

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

[按配置文件优化](profile-guided-optimizations.md)<br/>
[pgosweep](pgosweep.md)<br/>

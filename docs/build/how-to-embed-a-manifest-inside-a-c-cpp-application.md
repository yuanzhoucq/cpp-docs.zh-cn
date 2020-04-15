---
title: 如何：将清单嵌入到 C/C++ 应用程序
ms.date: 05/06/2019
helpviewer_keywords:
- manifests [C++]
- embedding manifests
- makefiles, updating to embed manifest
ms.assetid: ec0bac69-2fdc-466c-ab0d-710a22974e5d
ms.openlocfilehash: 2f125ee445d4ee9efdf21c37134d4c5adbca256d
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81322978"
---
# <a name="how-to-embed-a-manifest-inside-a-cc-application"></a>如何：将清单嵌入到 C/C++ 应用程序

我们建议您将应用程序或库的清单嵌入到最终二进制文件中，因为这保证了在大多数情况下正确的运行时行为。 默认情况下，Visual Studio 尝试在生成项目时嵌入清单。 有关详细信息，请参阅[可视化工作室中的"清单生成](manifest-generation-in-visual-studio.md)"。 但是，如果使用 nmake 构建应用程序，则必须对 makefile 进行一些更改。 本节演示如何更改 makefile，以便它自动将清单嵌入到最终二进制文件中。

## <a name="two-approaches"></a>两种方法

有两种方法可以将清单嵌入到应用程序或库中。

- 如果不执行增量生成，则可以使用类似于以下内容的命令行直接嵌入清单作为生成后步骤：

   ```cmd
   mt.exe -manifest MyApp.exe.manifest -outputresource:MyApp.exe;1
   ```

   or

   ```cmd
   mt.exe -manifest MyLibrary.dll.manifest -outputresource:MyLibrary.dll;2
   ```

   EXE 使用 1，对 DLL 使用 2。

- 如果要执行增量生成，请使用以下步骤：

  - 链接二进制文件以生成 MyApp.exe.manifest 文件。

  - 将清单转换为资源文件。

  - 重新链接（增量）以将清单资源嵌入到二进制文件中。

以下示例演示如何更改 makefile 以合并这两种技术。

## <a name="makefiles-before"></a>制作文件（之前）

请考虑 MyApp.exe 的 nmake 脚本，这是一个从一个文件构建的简单应用程序：

```
# build MyApp.exe
!if "$(DEBUG)" == "1"
CPPFLAGS=$(CPPFLAGS) /MDd
LFLAGS=$(LFLAGS) /INCREMENTAL
!else
CPPFLAGS=$(CPPFLAGS) /MD
!endif

MyApp.exe : MyApp.obj
    link $** /out:$@ $(LFLAGS)

MyApp.obj : MyApp.cpp

clean :
    del MyApp.obj MyApp.exe
```

如果此脚本在 Visual Studio 下运行不变，则已成功创建 MyApp.exe。 它还创建外部清单文件 MyApp.exe.manifest，供操作系统在运行时加载从属程序集。

MyLibrary.dll 的 nmake 脚本看起来非常类似：

```
# build MyLibrary.dll
!if "$(DEBUG)" == "1"
CPPFLAGS=$(CPPFLAGS) /MDd
LFLAGS=$(LFLAGS) /DLL /INCREMENTAL

!else
CPPFLAGS=$(CPPFLAGS) /MD
LFLAGS=$(LFLAGS) /DLL

!endif

MyLibrary.dll : MyLibrary.obj
    link $** /out:$@ $(LFLAGS)

MyLibrary.obj : MyLibrary.cpp

clean :
    del MyLibrary.obj MyLibrary.dll
```

## <a name="makefiles-after"></a>制作文件（之后）

要使用嵌入的清单构建，您必须对原始 makefile 进行四个小更改。 对于 MyApp.exe 制作文件：

```
# build MyApp.exe
!include makefile.inc
#^^^^^^^^^^^^^^^^^^^^ Change #1. (Add full path if necessary.)

!if "$(DEBUG)" == "1"
CPPFLAGS=$(CPPFLAGS) /MDd
LFLAGS=$(LFLAGS) /INCREMENTAL
!else
CPPFLAGS=$(CPPFLAGS) /MD
!endif

MyApp.exe : MyApp.obj
    link $** /out:$@ $(LFLAGS)
    $(_VC_MANIFEST_EMBED_EXE)
#^^^^^^^^^^^^^^^^^^^^^^^^^^^^ Change #2

MyApp.obj : MyApp.cpp

clean :
    del MyApp.obj MyApp.exe
    $(_VC_MANIFEST_CLEAN)
#^^^^^^^^^^^^^^^^^^^^^^^^ Change #3

!include makefile.targ.inc
#^^^^^^^^^^^^^^^^^^^^^^^^^ Change #4. (Add full path if necessary.)
```

对于 MyLibrary.dll 制作文件：

```
# build MyLibrary.dll
!include makefile.inc
#^^^^^^^^^^^^^^^^^^^^ Change #1. (Add full path if necessary.)

!if "$(DEBUG)" == "1"
CPPFLAGS=$(CPPFLAGS) /MDd
LFLAGS=$(LFLAGS) /DLL /INCREMENTAL

!else
CPPFLAGS=$(CPPFLAGS) /MD
LFLAGS=$(LFLAGS) /DLL

!endif

MyLibrary.dll : MyLibrary.obj
    link $** /out:$@ $(LFLAGS)
    $(_VC_MANIFEST_EMBED_DLL)
#^^^^^^^^^^^^^^^^^^^^^^^^^^^^ Change #2.

MyLibrary.obj : MyLibrary.cpp

clean :
    del MyLibrary.obj MyLibrary.dll
    $(_VC_MANIFEST_CLEAN)
#^^^^^^^^^^^^^^^^^^^^^^^^ Change #3.

!include makefile.targ.inc
#^^^^^^^^^^^^^^^^^^^^^^^^^ Change #4. (Add full path if necessary.)
```

makefile 现在包括两个文件，做真正的工作， 使file.inc 和 makefile.targ.inc.

创建 makefile.inc 并将其复制到其中：

```
# makefile.inc -- Include this file into existing makefile at the very top.

# _VC_MANIFEST_INC specifies whether build is incremental (1 - incremental).
# _VC_MANIFEST_BASENAME specifies name of a temporary resource file.

!if "$(DEBUG)" == "1"
CPPFLAGS=$(CPPFLAGS) /MDd
LFLAGS=$(LFLAGS) /INCREMENTAL
_VC_MANIFEST_INC=1
_VC_MANIFEST_BASENAME=__VC90.Debug

!else
CPPFLAGS=$(CPPFLAGS) /MD
_VC_MANIFEST_INC=0
_VC_MANIFEST_BASENAME=__VC90

!endif

####################################################
# Specifying name of temporary resource file used only in incremental builds:

!if "$(_VC_MANIFEST_INC)" == "1"
_VC_MANIFEST_AUTO_RES=$(_VC_MANIFEST_BASENAME).auto.res
!else
_VC_MANIFEST_AUTO_RES=
!endif

####################################################
# _VC_MANIFEST_EMBED_EXE - command to embed manifest in EXE:

!if "$(_VC_MANIFEST_INC)" == "1"

#MT_SPECIAL_RETURN=1090650113
#MT_SPECIAL_SWITCH=-notify_resource_update
MT_SPECIAL_RETURN=0
MT_SPECIAL_SWITCH=
_VC_MANIFEST_EMBED_EXE= \
if exist $@.manifest mt.exe -manifest $@.manifest -out:$(_VC_MANIFEST_BASENAME).auto.manifest $(MT_SPECIAL_SWITCH) & \
if "%ERRORLEVEL%" == "$(MT_SPECIAL_RETURN)" \
rc /r $(_VC_MANIFEST_BASENAME).auto.rc & \
link $** /out:$@ $(LFLAGS)

!else

_VC_MANIFEST_EMBED_EXE= \
if exist $@.manifest mt.exe -manifest $@.manifest -outputresource:$@;1

!endif

####################################################
# _VC_MANIFEST_CLEAN - command to clean resources files generated temporarily:

!if "$(_VC_MANIFEST_INC)" == "1"

_VC_MANIFEST_CLEAN=-del $(_VC_MANIFEST_BASENAME).auto.res \
    $(_VC_MANIFEST_BASENAME).auto.rc \
    $(_VC_MANIFEST_BASENAME).auto.manifest

!else

_VC_MANIFEST_CLEAN=

!endif

# End of makefile.inc
####################################################
```

现在创建**makefile.targ.inc**并将其复制到其中：

```
# makefile.targ.inc - include this at the very bottom of the existing makefile

####################################################
# Commands to generate initial empty manifest file and the RC file
# that references it, and for generating the .res file:

$(_VC_MANIFEST_BASENAME).auto.res : $(_VC_MANIFEST_BASENAME).auto.rc

$(_VC_MANIFEST_BASENAME).auto.rc : $(_VC_MANIFEST_BASENAME).auto.manifest
    type <<$@
#include <winuser.h>
1RT_MANIFEST"$(_VC_MANIFEST_BASENAME).auto.manifest"
<< KEEP

$(_VC_MANIFEST_BASENAME).auto.manifest :
    type <<$@
<?xml version='1.0' encoding='UTF-8' standalone='yes'?>
<assembly xmlns='urn:schemas-microsoft-com:asm.v1' manifestVersion='1.0'>
</assembly>
<< KEEP

# end of makefile.targ.inc
```

## <a name="see-also"></a>另请参阅

[了解 C/C++ 程序的清单生成](understanding-manifest-generation-for-c-cpp-programs.md)

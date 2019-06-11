---
title: Visual Studio 2015 和 Visual Studio 2019 之间的 C++ 二进制兼容性
ms.date: 05/03/2019
helpviewer_keywords:
- binary compatibility, Visual C++
ms.assetid: 591580f6-3181-4bbe-8ac3-f4fbaca949e6
ms.openlocfilehash: 052874eb9273ee9a9ce1695ffdadedd9911673e1
ms.sourcegitcommit: 7d64c5f226f925642a25e07498567df8bebb00d4
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/08/2019
ms.locfileid: "65449048"
---
# <a name="c-binary-compatibility-between-visual-studio-2015-and-visual-studio-2019"></a>Visual Studio 2015 和 Visual Studio 2019 之间的 C++ 二进制兼容性

在 Visual Studio 2013 及更低版本中，不能保证使用不同编译器工具集和运行时库版本生成的对象文件 (OBJ)、静态库 (LIB)、动态库 (DLL) 和可执行文件 (EXE) 之间的二进制兼容性。 

在 Visual Studio 2015 及更高版本中，C++ 工具集的主版本号是 14（Visual Studio 2015 是 v140，Visual Studio 2017 是 v141，Visual Studio 2019 是 v142）。 这反映了这样的事实：使用这两个版本之一的编译器编译的运行时库和应用程序是二进制兼容的。 这意味着，如果拥有使用 Visual Studio 2015 生成的第三方库，则无需对其进行重新编译即可通过使用 Visual Studio 2017 或 Visual Studio 2019 生成的应用程序使用该库。

此规则的唯一例外是，使用 `/GL` 编译器开关编译的静态库或对象文件不是二进制兼容的。 

混合使用通过 MSVC 工具集的不同受支持版本生成的二进制文件时，应用程序在其上运行的 Visual C++ 可再发行组件的版本不能低于用于生成应用或其使用的任何库的任何工具集版本。 

## <a name="see-also"></a>请参阅

[Visual C++ 更改历史记录](../porting/visual-cpp-change-history-2003-2015.md)

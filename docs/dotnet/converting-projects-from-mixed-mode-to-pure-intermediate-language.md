---
title: 将项目从混合模式转换为纯中间语言项目
ms.date: 08/19/2019
helpviewer_keywords:
- intermediate language, mixed-mode applications
- mixed-mode applications
- mixed-mode applications, intermediate language
- projects [C++], converting to intermediate language
ms.assetid: 855f9e3c-4f09-4bfe-8eab-a45f68292be9
ms.openlocfilehash: 05ece23e6d79fc399085099deebcde0aa4a92c64
ms.sourcegitcommit: 9d4ffb8e6e0d70520a1e1a77805785878d445b8a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/20/2019
ms.locfileid: "79544734"
---
# <a name="converting-projects-from-mixed-mode-to-pure-intermediate-language"></a>将项目从混合模式转换为纯中间语言项目

默认情况C++下，所有 Visual CLR 项目都链接到 C 运行时库。 因此，这些项目归类为混合模式应用程序，因为它们将本机代码与面向公共语言运行时（托管代码）的代码组合在一起。 编译时，它们将编译为中间语言（IL），也称为 Microsoft 中间语言（MSIL）。

> [!IMPORTANT]
> Visual Studio 2015 已弃用，Visual Studio 2017 不再支持为 CLR 应用程序创建 **/clr： pure**或 **/clr： safe**代码。 如果需要纯程序集或安全程序集，建议将应用程序转换C#为。

如果你使用的是早期版本的支持C++ **/clr： pure**或 **/clr： safe**的 Microsoft 编译器工具集，则可以使用此过程将代码转换为纯 MSIL：

### <a name="to-convert-your-mixed-mode-application-into-pure-intermediate-language"></a>将混合模式应用程序转换为纯中间语言

1. 删除指向[C 运行时库](../c-runtime-library/crt-library-features.md)（CRT）的链接：

   1. 在定义应用程序的入口点的 .cpp 文件中，将入口点更改为 `Main()`。 使用 `Main()` 指示项目未链接到 CRT。

   2. 在解决方案资源管理器中，右键单击项目，然后在快捷菜单上选择 "**属性**" 以打开应用程序的属性页。

   3. 在**链接器**的 "**高级**项目" 属性页中，选择**入口点**，然后在此字段中输入**Main** 。

   4. 对于控制台应用程序，在**链接器**的 "**系统**项目" 属性页中，选择 "**子系统**" 字段并将其更改为**控制台（/SUBSYSTEM： console）** 。

      > [!NOTE]
      > 您不必为 Windows 窗体应用程序设置此属性，因为默认情况下**子系统**字段设置为**Windows （/SUBSYSTEM： windows）** 。

   5. 在*stdafx.h*中，注释掉所有 `#include` 语句。 例如，在控制台应用程序中：

      ```cpp
      // #include <iostream>
      // #include <tchar.h>
      ```

       -或-

       例如，在 Windows 窗体应用程序中：

      ```cpp
      // #include <stdlib.h>
      // #include <malloc.h>
      // #include <memory.h>
      // #include <tchar.h>
      ```

   6. 对于 Windows 窗体应用程序，请在 Form1 中注释掉引用 Windows 的 `#include` 语句。 例如：

      ```cpp
      // #include <windows.h>
      ```

2. 将以下代码添加到*stdafx.h*：

   ```cpp
   #ifndef __FLTUSED__
   #define __FLTUSED__
      extern "C" __declspec(selectany) int _fltused=1;
   #endif
   ```

3. 删除所有非托管类型：

   在适当的位置，将非托管类型替换为来自[系统](/dotnet/api/system)命名空间的结构的引用。 下表列出了常见的托管类型：

   |结构|说明|
   |---------------|-----------------|
   |[布尔值](/dotnet/api/system.boolean)|表示布尔值。|
   |[Byte](/dotnet/api/system.byte)|表示一个 8 位无符号整数。|
   |[Char](/dotnet/api/system.char)|表示一个 Unicode 字符。|
   |[DateTime](/dotnet/api/system.datetime)|表示时间上的一刻，通常以日期和当天的时间表示。|
   |[小数](/dotnet/api/system.decimal)|表示十进制数。|
   |[双精度](/dotnet/api/system.double)|表示一个双精度浮点数。|
   |[Guid](/dotnet/api/system.guid)|表示全局唯一标识符 (GUID)。|
   |[Int16](/dotnet/api/system.int16)|表示 16 位有符号整数。|
   |[Int32](/dotnet/api/system.int32)|表示 32 位带符号整数。|
   |[Int64](/dotnet/api/system.int64)|表示 64 位有符号整数。|
   |[IntPtr](/dotnet/api/system.intptr)|用于表示指针或句柄的平台特定类型。|
   |[SByte](/dotnet/api/system.byte)|表示 8 位有符号整数。|
   |[Single](/dotnet/api/system.single)|表示一个单精度浮点数。|
   |[TimeSpan](/dotnet/api/system.timespan)|表示一个时间间隔。|
   |[UInt16](/dotnet/api/system.uint16)|表示 16 位无符号整数。|
   |[UInt32](/dotnet/api/system.uint32)|表示 32 位无符号整数。|
   |[UInt64](/dotnet/api/system.uint64)|表示 64 位无符号整数。|
   |[UIntPtr](/dotnet/api/system.uintptr)|用于表示指针或句柄的平台特定类型。|
   |[导致](/dotnet/api/system.void)|表示不返回值的方法;也就是说，该方法具有 void 返回类型。|
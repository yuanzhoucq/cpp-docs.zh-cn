---
title: 将项目从混合模式转换为纯中间语言项目
ms.date: 11/04/2016
helpviewer_keywords:
- intermediate language, mixed-mode applications
- mixed-mode applications
- mixed-mode applications, intermediate language
- projects [C++], converting to intermediate language
ms.assetid: 855f9e3c-4f09-4bfe-8eab-a45f68292be9
ms.openlocfilehash: 2f63b6860157e315d44f7c050812a7f0b97f2726
ms.sourcegitcommit: 7d64c5f226f925642a25e07498567df8bebb00d4
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/08/2019
ms.locfileid: "65448053"
---
# <a name="converting-projects-from-mixed-mode-to-pure-intermediate-language"></a>将项目从混合模式转换为纯中间语言

所有 Visual C++ CLR 项目链接到 C 运行时库，默认情况下。 因此，这些项目归类为混合模式应用程序，因为它们结合了具有面向公共语言运行时 （托管代码） 的代码的本机代码。 在编译时在编译为中间语言 (IL)，也称为 Microsoft 中间语言 (MSIL)。

> [!IMPORTANT]
> 不推荐使用 visual Studio 2015 和 Visual Studio 2017 不再支持创建 **/clr: pure**或 **/clr: safe** CLR 应用程序代码。 如果您需要纯或安全程序集，我们建议将转换为 C# 应用程序。

使用早期版本的 MicrosoftC++支持的编译器工具集 **/clr: pure**或 **/clr: safe**，可以使用此过程将转换为纯 MSIL 的代码：

### <a name="to-convert-your-mixed-mode-application-into-pure-intermediate-language"></a>将混合模式应用程序转换为纯中间语言

1. 删除指向[C 运行时库](../c-runtime-library/crt-library-features.md)(CRT):

   1. 在.cpp 文件中定义的应用程序的入口点更改的入口点`Main()`。 使用`Main()`指示你的项目不会链接到 CRT。

   2. 在解决方案资源管理器，右键单击项目并选择**属性**快捷菜单，打开你的应用程序的属性页上。

   3. 在中**高级**项目属性页**链接器**，选择**入口点**，然后输入**Main**此字段中。

   4. 对于控制台应用程序，在**系统**项目属性页**链接器**，选择**子系统**字段，该选项更改为**控制台 （/SUBSYSTEM:CONSOLE)**。

      > [!NOTE]
      > 不需要设置此属性对于 Windows 窗体应用程序，因为**子系统**字段设置为**Windows (/ 子系统： WINDOWS)** 默认情况下。

   5. 在 stdafx.h 中，注释掉所有`#include`语句。 例如，在控制台应用程序：

      ```cpp
      // #include <iostream>
      // #include <tchar.h>
      ```

       或

       例如，在 Windows 窗体应用程序：

      ```cpp
      // #include <stdlib.h>
      // #include <malloc.h>
      // #include <memory.h>
      // #include <tchar.h>
      ```

   6. 对于 Windows 窗体应用程序，在 Form1.cpp，注释掉`#include`引用 windows.h 的语句。 例如：

      ```cpp
      // #include <windows.h>
      ```

2. 将以下代码添加到 stdafx.h 中：

   ```cpp
   #ifndef __FLTUSED__
   #define __FLTUSED__
      extern "C" __declspec(selectany) int _fltused=1;
   #endif
   ```

3. 删除所有非托管的类型：

   在适当情况下，则会将非托管的类型替换到结构中的引用[系统](/dotnet/api/system)命名空间。 下表中列出了常见的托管的类型：

   |结构|描述|
   |---------------|-----------------|
   |[Boolean](/dotnet/api/system.boolean)|表示布尔值。|
   |[Byte](/dotnet/api/system.byte)|表示一个 8 位无符号整数。|
   |[Char](/dotnet/api/system.char)|表示一个 Unicode 字符。|
   |[DateTime](/dotnet/api/system.datetime)|表示时间上的一刻，通常以日期和当天的时间表示。|
   |[小数](/dotnet/api/system.decimal)|表示十进制数。|
   |[Double](/dotnet/api/system.double)|表示一个双精度浮点数。|
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
   |[Void](/dotnet/api/system.void)|指示不会返回一个值; 的方法也就是说，该方法具有 void 返回类型。|
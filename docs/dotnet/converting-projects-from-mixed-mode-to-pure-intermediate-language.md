---
title: 转换项目从混合模式为纯中间语言 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- intermediate language, mixed-mode applications
- mixed-mode applications
- mixed-mode applications, intermediate language
- projects [C++], converting to intermediate language
ms.assetid: 855f9e3c-4f09-4bfe-8eab-a45f68292be9
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 263a90710d2103c4ea97e6c56da67d676ba7366b
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/29/2018
ms.locfileid: "43222075"
---
# <a name="converting-projects-from-mixed-mode-to-pure-intermediate-language"></a>将项目从混合模式转换为纯中间语言

默认情况下，所有 Visual c + + CLR 项目链接到 C 运行时库。 因此，这些项目归类为混合模式应用程序，因为它们结合了具有面向公共语言运行时 （托管代码） 的代码的本机代码。 在编译时在编译为中间语言 (IL)，也称为 Microsoft 中间语言 (MSIL)。

> [!IMPORTANT]
> 不推荐使用 visual Studio 2015 和 Visual Studio 2017 不再支持创建 **/clr: pure**或 **/clr: safe** CLR 应用程序代码。 如果您需要纯或安全程序集，我们建议将转换为 C# 应用程序。

如果使用早期版本的支持的 Visual c + + 编译器工具集 **/clr: pure**或 **/clr: safe**，可以使用此过程将转换为纯 MSIL 的代码：

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

   在适当情况下，则会将非托管的类型替换到结构中的引用[系统](https://msdn.microsoft.com/library/system.appdomainmanager.appdomainmanager.aspx)命名空间。 下表中列出了常见的托管的类型：

   |结构|描述|
   |---------------|-----------------|
   |[布尔值](https://msdn.microsoft.com/library/system.boolean\(v=vs.140\).aspx)|表示布尔值。|
   |[Byte](https://msdn.microsoft.com/library/system.byte\(v=vs.140\).aspx)|表示一个 8 位无符号整数。|
   |[Char](https://msdn.microsoft.com/library/system.char\(v=vs.140\).aspx)|表示一个 Unicode 字符。|
   |[DateTime](https://msdn.microsoft.com/library/system.datetime.datetime.aspx)|表示时间上的一刻，通常以日期和当天的时间表示。|
   |[小数](https://msdn.microsoft.com/library/system.decimal\(v=vs.140\).aspx)|表示十进制数。|
   |[双精度](https://msdn.microsoft.com/library/system.double\(v=vs.140\).aspx)|表示一个双精度浮点数。|
   |[Guid](https://msdn.microsoft.com/library/system.guid\(v=vs.140\).aspx)|表示全局唯一标识符 (GUID)。|
   |[Int16](https://msdn.microsoft.com/library/system.int16\(v=vs.140\).aspx)|表示 16 位有符号整数。|
   |[Int32](https://msdn.microsoft.com/library/system.int32\(v=vs.140\).aspx)|表示 32 位带符号整数。|
   |[Int64](https://msdn.microsoft.com/library/system.int64\(v=vs.140\).aspx)|表示 64 位有符号整数。|
   |[IntPtr](https://msdn.microsoft.com/library/system.intptr\(v=vs.140\).aspx)|用于表示指针或句柄的平台特定类型。|
   |[SByte](https://msdn.microsoft.com/library/system.byte.aspx)|表示 8 位有符号整数。|
   |[单精度](https://msdn.microsoft.com/library/system.single.aspx)|表示一个单精度浮点数。|
   |[TimeSpan](https://msdn.microsoft.com/library/system.timespan\(v=vs.140\).aspx)|表示一个时间间隔。|
   |[UInt16](https://msdn.microsoft.com/library/system.uint16\(v=vs.140\).aspx)|表示 16 位无符号整数。|
   |[UInt32](https://msdn.microsoft.com/library/system.uint32\(v=vs.140\).aspx)|表示 32 位无符号整数。|
   |[UInt64](https://msdn.microsoft.com/library/system.uint64\(v=vs.140\).aspx)|表示 64 位无符号整数。|
   |[UIntPtr](https://msdn.microsoft.com/library/system.uintptr\(v=vs.140\).aspx)|用于表示指针或句柄的平台特定类型。|
   |[Void](https://msdn.microsoft.com/library/system.void\(v=vs.140\).aspx)|指示不会返回一个值; 的方法也就是说，该方法具有 void 返回类型。|
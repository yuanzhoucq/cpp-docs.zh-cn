---
title: 如何： 使用 PInvoke 从托管代码调用本机 Dll |Microsoft Docs
ms.custom: get-started-article
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- platform invoke [C++], calling native DLLs
- interop [C++], calling native DLLs
- marshaling [C++], calling native DLLs
- data marshaling [C++], calling native DLLs
ms.assetid: 3273eb4b-38d1-4619-92a6-71bda542be72
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: f849d2d9c3fd4a2d50d652ad159e93442b4c7ff3
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/19/2018
ms.locfileid: "46404639"
---
# <a name="how-to-call-native-dlls-from-managed-code-using-pinvoke"></a>如何：使用 PInvoke 从托管代码调用本机 DLL

可以从使用平台调用 (P/Invoke) 功能的托管代码调用非托管 Dll 中实现的函数。 如果该 DLL 的源代码不可用，P/Invoke 是唯一的选项之间的互操作。 但是，与其他.NET 语言，Visual c + + 提供 P/Invoke 的替代方法。 有关详细信息，请参阅[使用 c + + 互操作 (隐式 PInvoke)](../dotnet/using-cpp-interop-implicit-pinvoke.md)。

## <a name="example"></a>示例

下面的代码示例使用 Win32 [GetSystemMetrics](/windows/desktop/api/winuser/nf-winuser-getsystemmetrics)函数以检索屏幕以像素为单位的当前分辨率。

对于仅使用内部类型作为参数和返回值的函数，没有额外的工作是必需的。 其他数据类型，如函数指针、 数组和结构，需要确保正确的数据封送处理的其他属性。

尽管不是必需的很好的做法使 P/Invoke 声明的值类的静态成员，以便它们不在全局命名空间，在此示例中所示。

```
// pinvoke_basic.cpp
// compile with: /clr
using namespace System;
using namespace System::Runtime::InteropServices;

value class Win32 {
public:
   [DllImport("User32.dll")]
   static int GetSystemMetrics(int);

   enum class SystemMetricIndex {
      // Same values as those defined in winuser.h.
      SM_CXSCREEN = 0,
      SM_CYSCREEN = 1
   };
};

int main() {
   int hRes = Win32::GetSystemMetrics( safe_cast<int>(Win32::SystemMetricIndex::SM_CXSCREEN) );
   int vRes = Win32::GetSystemMetrics( safe_cast<int>(Win32::SystemMetricIndex::SM_CYSCREEN) );
   Console::WriteLine("screen resolution: {0},{1}", hRes, vRes);
}
```

## <a name="see-also"></a>请参阅

[在 C++ 中使用显式 PInvoke（DllImport 特性）](../dotnet/using-explicit-pinvoke-in-cpp-dllimport-attribute.md)
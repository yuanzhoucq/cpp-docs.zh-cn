---
title: 编译器警告（等级1） C4397
ms.date: 11/04/2016
f1_keywords:
- C4397
helpviewer_keywords:
- C4397
ms.assetid: 6346fdc2-dbbf-4fba-803a-32b0d0a707be
ms.openlocfilehash: fc13f83f79f8c8103184b4322a77866a78d149be
ms.sourcegitcommit: e5192a25c084eda9eabfa37626f3274507e026b3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/12/2019
ms.locfileid: "73964930"
---
# <a name="compiler-warning-level-1-c4397"></a>编译器警告（等级1） C4397

已忽略 DefaultCharSetAttribute

Microsoft C++编译器将忽略 <xref:System.Runtime.InteropServices.DefaultCharSetAttribute>。 若要为 DLL 指定字符集，请使用 DllImport 的字符集选项。 有关详细信息，请[参阅C++ Using 互操作（隐式 PInvoke）](../../dotnet/using-cpp-interop-implicit-pinvoke.md)。

## <a name="example"></a>示例

下面的示例生成 C4397。

```cpp
// C4397.cpp
// compile with: /W1 /c /clr
using namespace System;
using namespace System::Runtime::InteropServices;

[module:DefaultCharSetAttribute(CharSet::Unicode)];   // C4397

[DllImport("kernel32", EntryPoint="CloseHandle", CharSet=CharSet::Unicode)]   // OK
extern "C" bool ImportDefault(IntPtr hObject);

public ref class MySettingVC {
public:
   void method() {
      ImportDefault(IntPtr::Zero);
   }
};

[StructLayout(LayoutKind::Explicit)]
public ref struct StructDefault1{};

public ref class ClassDefault1{};
```
---
title: 编译器警告（等级 1）C4397
ms.date: 11/04/2016
f1_keywords:
- C4397
helpviewer_keywords:
- C4397
ms.assetid: 6346fdc2-dbbf-4fba-803a-32b0d0a707be
ms.openlocfilehash: 4ad690d78c1544adbe365a35ba3b5921c883631e
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50498759"
---
# <a name="compiler-warning-level-1-c4397"></a>编译器警告（等级 1）C4397

已忽略 DefaultCharSetAttribute

<xref:System.Runtime.InteropServices.DefaultCharSetAttribute> Visual c + + 编译器将忽略。 若要指定为 DLL 设置的字符，使用 DllImport 的 CharSet 选项。 有关详细信息，请参阅[使用 c + + 互操作 (隐式 PInvoke)](../../dotnet/using-cpp-interop-implicit-pinvoke.md)。

## <a name="example"></a>示例

下面的示例生成 C4397。

```
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
---
title: 编译器警告（等级 3）C4792
ms.date: 11/04/2016
f1_keywords:
- C4792
helpviewer_keywords:
- C4792
ms.assetid: c047ce69-a622-44e1-9425-d41aa9261c61
ms.openlocfilehash: f0efed41fad2648d7e681fa4e5575e7f36fb6aeb
ms.sourcegitcommit: 573b36b52b0de7be5cae309d45b68ac7ecf9a6d8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/10/2019
ms.locfileid: "74991673"
---
# <a name="compiler-warning-level-3-c4792"></a>编译器警告（等级 3）C4792

函数“function”使用 sysimport 声明并从本机代码引用；需要链接导入库

从非托管函数调用通过 DllImport 导入到程序中的本机函数。 因此，你必须链接到该 DLL 的导入库。

无法在代码中解决该警告，也无法通过改变编译方式来解决。 请使用 [警告](../../preprocessor/warning.md) 杂注禁用此警告。

以下示例生成 C4792：

```cpp
// C4792.cpp
// compile with: /clr /W3
// C4792 expected
using namespace System::Runtime::InteropServices;
[DllImport("msvcrt")]
extern "C" int __cdecl puts(const char *);
int main() {}

// Uncomment the following line to resolve.
// #pragma warning(disable : 4792)
#pragma unmanaged
void func(void){
   puts("test");
}
```

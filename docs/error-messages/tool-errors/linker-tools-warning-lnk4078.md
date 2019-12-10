---
title: 链接器工具警告 LNK4078
ms.date: 11/04/2016
f1_keywords:
- LNK4078
helpviewer_keywords:
- LNK4078
ms.assetid: 5a16796d-6caf-42d9-8f65-b042843eafb8
ms.openlocfilehash: 9ce72f476aa85434acd5277d0307ffc61e0a0214
ms.sourcegitcommit: 573b36b52b0de7be5cae309d45b68ac7ecf9a6d8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/10/2019
ms.locfileid: "74990998"
---
# <a name="linker-tools-warning-lnk4078"></a>链接器工具警告 LNK4078

找到多个具有不同特性的 "节名" 部分

LINK 找到了两个或多个同名但属性不同的节。

此警告可能是由早期版本的 LINK 或 LIB 创建的导入库或导出文件引起的。

重新创建文件并重新链接。

## <a name="example"></a>示例

LNK4078 也可能由重大更改引起： x86 上[init_seg](../../preprocessor/init-seg.md)命名的部分是读/写的，它现在为只读。

下面的示例生成 LNK4078。

```cpp
// LNK4078.cpp
// compile with: /W1
// LNK4078 expected
#include <stdio.h>
#pragma warning(disable : 4075)
typedef void (__cdecl *PF)(void);
int cxpf = 0;   // number of destructors to call
PF pfx[200];   // pointers to destructors.

struct A { A() {} };

int myexit (PF pf) { return 0; }

#pragma section(".mine$a", read, write)
// try the following line instead
// #pragma section(".mine$a", read)
__declspec(allocate(".mine$a")) int ii = 1;

#pragma section(".mine$z", read, write)
// try the following line instead
// #pragma section(".mine$z", read)
__declspec(allocate(".mine$z")) int i = 1;

#pragma data_seg()
#pragma init_seg(".mine$m", myexit)
A bbbb;
A cccc;
int main() {}
```

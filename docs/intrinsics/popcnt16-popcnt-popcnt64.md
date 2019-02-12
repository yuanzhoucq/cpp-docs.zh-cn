---
title: __popcnt16, __popcnt, __popcnt64
ms.date: 11/04/2016
f1_keywords:
- __popcnt64
- __popcnt
- __popcnt16
helpviewer_keywords:
- popcnt instruction
- __popcnt16
- __popcnt64
- __popcnt
ms.assetid: e525b236-adc8-42df-9b9b-8b7d8c245d3b
ms.openlocfilehash: a6424f3414d9da17e52c0a9f78290497f5e5e01e
ms.sourcegitcommit: f4be868c0d1d78e550fba105d4d3c993743a1f4b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/12/2019
ms.locfileid: "56146887"
---
# <a name="popcnt16-popcnt-popcnt64"></a>__popcnt16, __popcnt, __popcnt64

**Microsoft 专用**

计数的一个 16 位、 32 位或 64 位无符号的整数中的位 （填充计数）。

## <a name="syntax"></a>语法

```
unsigned short __popcnt16(
   unsigned short value
);
unsigned int __popcnt(
   unsigned int value
);
unsigned __int64 __popcnt64(
   unsigned __int64 value
);
```

#### <a name="parameters"></a>参数

*值*<br/>
[in]16 位、 32 或 64 位无符号的整数，我们需要填充计数。

## <a name="return-value"></a>返回值

中的一个比特数`value`参数。

## <a name="requirements"></a>要求

|内部函数|体系结构|
|---------------|------------------|
|`__popcnt16`|高级的位操作|
|`__popcnt`|高级的位操作|
|`__popcnt64`|在 64 位模式下的高级的位操作。|

**标头文件** \<intrin.h >

## <a name="remarks"></a>备注

每个这些内部函数生成`popcnt`指令。 在 32 位模式下有任何 64 位的通用寄存器，因此不是 64 位`popcnt`。

若要确定的硬件支持`popcnt`指令，调用`__cpuid`与内部`InfoType=0x00000001`并检查位 23 的`CPUInfo[2] (ECX)`。 此位为否则如果支持该指令，则为 1 和 0。 如果你运行代码，使用此内部函数不支持的硬件上`popcnt`指令，则结果不可预知。

## <a name="example"></a>示例

```
#include <iostream>
#include <intrin.h>
using namespace std;

int main()
{
  unsigned short us[3] = {0, 0xFF, 0xFFFF};
  unsigned short usr;
  unsigned int   ui[4] = {0, 0xFF, 0xFFFF, 0xFFFFFFFF};
  unsigned int   uir;

  for (int i=0; i<3; i++) {
    usr = __popcnt16(us[i]);
    cout << "__popcnt16(0x" << hex << us[i] << ") = " << dec << usr << endl;
  }

  for (int i=0; i<4; i++) {
    uir = __popcnt(ui[i]);
    cout << "__popcnt(0x" << hex << ui[i] << ") = " << dec << uir << endl;
  }
}
```

```Output
__popcnt16(0x0) = 0
__popcnt16(0xff) = 8
__popcnt16(0xffff) = 16
__popcnt(0x0) = 0
__popcnt(0xff) = 8
__popcnt(0xffff) = 16
__popcnt(0xffffffff) = 32
```

**结束 Microsoft 专用**

高级微设备，inc.版权所有 2007保留所有权利。 重新生成具有高级微设备，inc.的权限

## <a name="see-also"></a>请参阅

[编译器内部函数](../intrinsics/compiler-intrinsics.md)

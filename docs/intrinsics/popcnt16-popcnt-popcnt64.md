---
title: __popcnt16, __popcnt, __popcnt64
ms.date: 09/02/2019
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
ms.openlocfilehash: 3e5ae7f897500775671f8bd2563028874579a627
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/03/2019
ms.locfileid: "70221356"
---
# <a name="__popcnt16-__popcnt-__popcnt64"></a>__popcnt16, __popcnt, __popcnt64

**Microsoft 专用**

计算16、32 `1`或64位无符号整数中的位数 (人口数)。

## <a name="syntax"></a>语法

```C
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

### <a name="parameters"></a>参数

*value*\
中要填充计数的16、32或64位无符号整数。

## <a name="return-value"></a>返回值

值参数中`1`的位数。

## <a name="requirements"></a>要求

|内部函数|体系结构|
|---------------|------------------|
|`__popcnt16`|高级位操作|
|`__popcnt`|高级位操作|
|`__popcnt64`|64位模式下的高级位操作。|

**标头文件**\<intrin.h >

## <a name="remarks"></a>备注

每个内部函数都会生成`popcnt`指令。 在32位模式下, 没有任何64位通用寄存器, 因此不支持64位`popcnt` 。

若要确定`popcnt`指令的硬件支持, 请`__cpuid`调用内部`InfoType=0x00000001` , 并检查的`CPUInfo[2] (ECX)`位23。 如果支持指令, 则此位为 1; 否则为0。 如果在不支持`popcnt`指令的硬件上运行使用这些内部函数的代码, 则结果是不可预知的。

## <a name="example"></a>示例

```cpp
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

部分版权 2007, 由高级微设备, Inc。保留所有权利。 从高级微设备, Inc. 的权限重现。

## <a name="see-also"></a>请参阅

[编译器内部函数](../intrinsics/compiler-intrinsics.md)

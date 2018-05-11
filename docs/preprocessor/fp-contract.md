---
title: fp_contract |Microsoft 文档
ms.custom: ''
ms.date: 03/12/2018
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- vc-pragma.fp_contract
- fp_contract_CPP
dev_langs:
- C++
helpviewer_keywords:
- pragmas, fp_contract
- fp_contract pragma
ms.assetid: 15b97338-6680-4287-ba2a-2dccc5b2ccf5
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 514b4708129d625ea7880e4c61be22c4b1ac2db5
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/08/2018
---
# <a name="fpcontract"></a>fp_contract

确定浮点缩写式是否发生。 浮点缩写式是一个指令，如 FMA （Fused Multiply-添加），它将合并两个单独浮点运算成一条指令。 因为而不是每次操作后的舍入，处理器可能舍入一次在这两个操作后，这些指令的使用可能会影响浮点精度。

## <a name="syntax"></a>语法

> **#pragma fp_contract (** {**上** | **关闭**} **)**  

## <a name="remarks"></a>备注  

默认情况下， **fp_contract**是**上**。 这将告知编译器尽可能使用浮点缩写式说明。 设置**fp_contract**到**关闭**保留单独的浮点指令。

浮点行为的详细信息，请参阅[/fp （指定浮点行为）](../build/reference/fp-specify-floating-point-behavior.md)。

其他浮点杂注包括：

- [fenv_access](../preprocessor/fenv-access.md)

- [float_control](../preprocessor/float-control.md)

## <a name="example"></a>示例

此示例从生成的代码不使用 fused multiply-添加指令，即使它是在目标处理器上可用。 如果注释掉`#pragma fp_contract (off)`，生成的代码可能使用 fused multiply-添加指令，如果可用。  
  
```cpp
// pragma_directive_fp_contract.cpp
// on x86 and x64 compile with: /O2 /fp:fast /arch:AVX2
// other platforms compile with: /O2

#include <stdio.h>

// remove the following line to enable FP contractions
#pragma fp_contract (off)

int main() {
   double z, b, t;

   for (int i = 0; i < 10; i++) {
      b = i * 5.5;
      t = i * 56.025;

      z = t * i + b;
      printf("out = %.15e\n", z);
   }
}
```

```Output
out = 0.000000000000000e+00
out = 6.152500000000000e+01
out = 2.351000000000000e+02
out = 5.207249999999999e+02
out = 9.184000000000000e+02
out = 1.428125000000000e+03
out = 2.049900000000000e+03
out = 2.783725000000000e+03
out = 3.629600000000000e+03
out = 4.587525000000000e+03
```

## <a name="see-also"></a>请参阅

[Pragma 指令和 __Pragma 关键字](../preprocessor/pragma-directives-and-the-pragma-keyword.md)

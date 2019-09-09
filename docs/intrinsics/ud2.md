---
title: __ud2
ms.date: 09/02/2019
f1_keywords:
- __ud2
helpviewer_keywords:
- UD2 instruction
- __ud2 intrinsic
ms.assetid: 0831cd5a-8b65-402e-bb57-11e1d5d7ffd2
ms.openlocfilehash: b5aa20804099af4d75dcc62a5e62ccc0d4a09566
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/03/2019
ms.locfileid: "70219753"
---
# <a name="__ud2"></a>__ud2

**Microsoft 专用**

生成未定义的指令。

## <a name="syntax"></a>语法

```C
void __ud2();
```

## <a name="remarks"></a>备注

如果执行未定义的指令，处理器将引发无效的操作码异常。

`__ud2`函数等效`UD2`于计算机指令，仅在内核模式下可用。 有关详细信息，请搜索文档 "Intel 体系结构软件开发人员手册，第2卷：说明集[参考 "。](https://software.intel.com/articles/intel-sdm)

## <a name="requirements"></a>要求

|内部函数|体系结构|
|---------------|------------------|
|`__ud2`|x86、x64|

**标头文件**\<intrin.h >

**结束 Microsoft 专用**

## <a name="example"></a>示例

下面的示例执行未定义的指令，这会引发异常。 然后，异常处理程序将返回代码从0更改为1。

```cpp
// __ud2_intrinsic.cpp
#include <stdio.h>
#include <intrin.h>
#include <excpt.h>
// compile with /EHa

int main() {

// Initialize the return code to 0.
int ret = 0;

// Attempt to execute an undefined instruction.
  printf("Before __ud2(). Return code = %d.\n", ret);
  __try {
  __ud2();
  }

// Catch any exceptions and set the return code to 1.
  __except(EXCEPTION_EXECUTE_HANDLER){
  printf("  In the exception handler.\n");
  ret = 1;
  }

// Report the value of the return code.
  printf("After __ud2().  Return code = %d.\n", ret);
  return ret;
}
```

```Output
Before __ud2(). Return code = 0.
  In the exception handler.
After __ud2().  Return code = 1.
```

## <a name="see-also"></a>请参阅

[编译器内部函数](../intrinsics/compiler-intrinsics.md)

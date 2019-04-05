---
title: __ud2
ms.date: 11/04/2016
f1_keywords:
- __ud2
helpviewer_keywords:
- UD2 instruction
- __ud2 intrinsic
ms.assetid: 0831cd5a-8b65-402e-bb57-11e1d5d7ffd2
ms.openlocfilehash: a36ab5c25ac9138b2a4d6810cc2a339e534f1695
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/05/2019
ms.locfileid: "59029397"
---
# <a name="ud2"></a>__ud2

**Microsoft 专用**

生成未定义的指令。

## <a name="syntax"></a>语法

```
void __ud2();
```

## <a name="remarks"></a>备注

如果您执行未定义的指令，处理器将引发无效操作码异常。

`__ud2`函数等同于`UD2`机器指令，并且仅在内核模式下可用。 有关详细信息，搜索文档中，"Intel 体系结构软件开发人员手册，卷 2:指令设置参考，"在[Intel Corporation](https://software.intel.com/articles/intel-sdm)站点。

## <a name="requirements"></a>要求

|内部函数|体系结构|
|---------------|------------------|
|`__ud2`|x86、x64|

**标头文件** \<intrin.h >

**结束 Microsoft 专用**

## <a name="example"></a>示例

以下示例将执行未定义的指令，会引发异常。 然后，异常处理程序从零到其中一个更改返回代码。

```
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
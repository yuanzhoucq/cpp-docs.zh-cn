---
title: __svm_invlpga
ms.date: 09/02/2019
f1_keywords:
- __svm_invlpga
helpviewer_keywords:
- __svm_invlpga intrinsic
- INVLPGA instruction
ms.assetid: aa6578ce-8278-464b-8815-a0fc45330915
ms.openlocfilehash: e0f8ef02efdb64f70bb65f6f017449fcc03beca1
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/03/2019
ms.locfileid: "70219888"
---
# <a name="__svm_invlpga"></a>__svm_invlpga

**Microsoft 专用**

使计算机的翻译外观缓冲区中的地址映射条目失效。 参数指定要使其无效的页的虚拟地址和地址空间标识符。

## <a name="syntax"></a>语法

```C
void __svm_invlpga(void *Vaddr, int as_id);
```

### <a name="parameters"></a>参数

*Vaddr*\
中要使其无效的页的虚拟地址。

*as_id*\
中要使其无效的页的地址空间标识符 (ASID)。

## <a name="remarks"></a>备注

`__svm_invlpga` 函数等同于 `INVLPGA` 计算机指令。 此函数支持主机的虚拟机监视器与来宾操作系统及其应用程序进行交互。 有关详细信息, 请搜索文档 "AMD64 体系结构程序员手册卷 2:系统编程, "文档编号 24593, 修订版 3.11, 位于[AMD corporation](https://developer.amd.com/resources/developer-guides-manuals/)站点。

## <a name="requirements"></a>要求

|内部函数|体系结构|
|---------------|------------------|
|`__svm_invlpga`|x86、x64|

**标头文件**\<intrin.h >

**结束 Microsoft 专用**

## <a name="see-also"></a>请参阅

[编译器内部函数](../intrinsics/compiler-intrinsics.md)

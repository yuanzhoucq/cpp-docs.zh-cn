---
title: __svm_vmsave
ms.date: 09/02/2019
f1_keywords:
- __svm_vmsave
helpviewer_keywords:
- VMSAVE instruction
- __svm_vmsave intrinsic
ms.assetid: 617a60bd-8514-4ba1-8066-bcf4dd481030
ms.openlocfilehash: f91efa7116a8a8e9ebe27c7e5e4e64c4f1533e9d
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/03/2019
ms.locfileid: "70219791"
---
# <a name="__svm_vmsave"></a>__svm_vmsave

**Microsoft 专用**

将处理器状态的子集存储在指定的虚拟机控制块 (VMCB) 中。

## <a name="syntax"></a>语法

```C
void __svm_vmsave(
   size_t VmcbPhysicalAddress
);
```

### <a name="parameters"></a>参数

*VmcbPhysicalAddress*\
中VMCB 的物理地址。

## <a name="remarks"></a>备注

`__svm_vmsave` 函数等同于 `VMSAVE` 计算机指令。 此函数支持主机的虚拟机监视器与来宾操作系统及其应用程序进行交互。 有关详细信息, 请搜索文档 "AMD64 体系结构程序员手册卷 2:系统编程, "文档编号 24593, 修订版3.11 或更高版本, 位于[AMD Corporation](https://developer.amd.com/resources/developer-guides-manuals/)站点。

## <a name="requirements"></a>要求

|内部函数|体系结构|
|---------------|------------------|
|`__svm_vmsave`|x86、x64|

**标头文件**\<intrin.h >

**结束 Microsoft 专用**

## <a name="see-also"></a>请参阅

[编译器内部函数](../intrinsics/compiler-intrinsics.md)\
[__svm_vmrun](../intrinsics/svm-vmrun.md)\
[__svm_vmload](../intrinsics/svm-vmload.md)

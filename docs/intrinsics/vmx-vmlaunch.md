---
title: __vmx_vmlaunch
ms.date: 09/02/2019
f1_keywords:
- __vmx_vmlaunch
helpviewer_keywords:
- VMLAUNCH instruction
- __vmx_vmlaunch intrinsic
ms.assetid: 708f7c38-b7c1-4ee7-bfc4-0daeb9cc9360
ms.openlocfilehash: 8d78e5181fdd43e10431e12d0cf540c8c9c2e719
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/03/2019
ms.locfileid: "70219547"
---
# <a name="__vmx_vmlaunch"></a>__vmx_vmlaunch

**Microsoft 专用**

使用当前虚拟机控制结构 (VMCS) 将调用应用程序置于 .VMX 非根操作状态 (VM 输入)。

## <a name="syntax"></a>语法

```C
unsigned char __vmx_vmlaunch(void);
```

## <a name="return-value"></a>返回值

|值|含义|
|-----------|-------------|
|0|操作成功。|
|1|操作失败，当前 VMCS 的 `VM-instruction error field` 中提供了扩展状态。|
|2|操作失败，无可用状态。|

## <a name="remarks"></a>备注

应用程序可以使用[__vmx_vmlaunch](../intrinsics/vmx-vmlaunch.md)或[__VMX_VMRESUME](../intrinsics/vmx-vmresume.md)函数执行 VM 输入操作。 [__Vmx_vmlaunch](../intrinsics/vmx-vmlaunch.md)函数只能用于其启动状态为`Clear`的 VMCS, 而[__vmx_vmresume](../intrinsics/vmx-vmresume.md)函数只能与启动状态为`Launched`的 VMCS 一起使用。 因此, 使用[__vmx_vmclear](../intrinsics/vmx-vmclear.md)函数将 VMCS 的启动状态设置为`Clear`, 然后对第一个 vm 输入操作使用[__vmx_vmlaunch](../intrinsics/vmx-vmlaunch.md)函数, 并对后续 vm 使用[__vmx_vmresume](../intrinsics/vmx-vmresume.md)函数-enter运算符.

`__vmx_vmlaunch` 函数等同于 `VMLAUNCH` 计算机指令。 此函数支持主机的虚拟机监视器与来宾操作系统及其应用程序进行交互。 有关详细信息, 请在[Intel Corporation](https://software.intel.com/articles/intel-sdm)站点搜索文档 "适用于 IA-32 Intel 体系结构的 Intel 虚拟化技术规范" 文档编号 C97063-002。

## <a name="requirements"></a>要求

|内部函数|体系结构|
|---------------|------------------|
|`__vmx_vmlaunch`|X64|

**标头文件**\<intrin.h >

**结束 Microsoft 专用**

## <a name="see-also"></a>请参阅

[编译器内部函数](../intrinsics/compiler-intrinsics.md)\
[__vmx_vmresume](../intrinsics/vmx-vmresume.md)\
[__vmx_vmclear](../intrinsics/vmx-vmclear.md)

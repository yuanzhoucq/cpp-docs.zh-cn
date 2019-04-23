---
title: __vmx_vmclear
ms.date: 11/04/2016
f1_keywords:
- __vmx_vmclear
helpviewer_keywords:
- VMCLEAR instruction
- __vmx_vmclear intrinsic
ms.assetid: e3eb98e4-50fc-4c93-9bac-340fd1f0a466
ms.openlocfilehash: 17e3e5c91a58894b25fc6b2a72f7d0056fa88119
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/18/2019
ms.locfileid: "59036532"
---
# <a name="vmxvmclear"></a>__vmx_vmclear

**Microsoft 专用**

初始化指定的虚拟机控件结构 (VMCS) 并将其启动状态设置为`Clear`。

## <a name="syntax"></a>语法

```
unsigned char __vmx_vmclear(
   unsigned __int64 *VmcsPhysicalAddress
);
```

#### <a name="parameters"></a>参数

|参数|描述|
|---------------|-----------------|
|*VmcsPhysicalAddress*|[in]指向包含的物理地址的 VMCS，若要清除的 64 位内存位置的指针。|

## <a name="return-value"></a>返回值

|“值”|含义|
|-----------|-------------|
|0|操作成功。|
|1|操作失败，当前 VMCS 的 `VM-instruction error field` 中提供了扩展状态。|
|2|操作失败，无可用状态。|

## <a name="remarks"></a>备注

应用程序可以通过使用执行 VM 输入操作[__vmx_vmlaunch](../intrinsics/vmx-vmlaunch.md)或[__vmx_vmresume](../intrinsics/vmx-vmresume.md)函数。 [__Vmx_vmlaunch](../intrinsics/vmx-vmlaunch.md)函数可以仅可用于启动状态是将 VMCS `Clear`，和[__vmx_vmresume](../intrinsics/vmx-vmresume.md)函数可以仅可用于将 VMCS 的启动状态是`Launched`。 因此，使用[__vmx_vmclear](../intrinsics/vmx-vmclear.md)函数设置为将 VMCS 的启动状态`Clear`。 使用[__vmx_vmlaunch](../intrinsics/vmx-vmlaunch.md)函数对第一个 VM 输入操作与[__vmx_vmresume](../intrinsics/vmx-vmresume.md)对后续 VM 输入操作的函数。

`__vmx_vmclear` 函数等同于 `VMCLEAR` 计算机指令。 此函数支持主机的虚拟机监视器与来宾操作系统及其应用程序进行交互。 有关详细信息，搜索"Intel 虚拟化技术规范的 IA-32 Intel 体系结构，"文档在文档数字 C97063 002 [Intel Corporation](https://software.intel.com/articles/intel-sdm)站点。

## <a name="requirements"></a>要求

|内部函数|体系结构|
|---------------|------------------|
|`__vmx_vmclear`|X64|

**标头文件** \<intrin.h >

**结束 Microsoft 专用**

## <a name="see-also"></a>请参阅

[编译器内部函数](../intrinsics/compiler-intrinsics.md)<br/>
[__vmx_vmlaunch](../intrinsics/vmx-vmlaunch.md)<br/>
[__vmx_vmresume](../intrinsics/vmx-vmresume.md)
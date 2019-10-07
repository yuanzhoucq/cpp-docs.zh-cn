---
title: __vmx_on
ms.date: 09/02/2019
f1_keywords:
- __vmx_on
helpviewer_keywords:
- VMXON instruction
- __vmx_on intrinsic
ms.assetid: 16804991-6a75-4adf-8ec2-bc95acfa4801
ms.openlocfilehash: b6041711d9b6806362b856475151f2c4f63750cb
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/03/2019
ms.locfileid: "70219572"
---
# <a name="__vmx_on"></a>__vmx_on

**Microsoft 专用**

在处理器中激活虚拟机扩展 (.VMX) 操作。

## <a name="syntax"></a>语法

```C
unsigned char __vmx_on(
   unsigned __int64 *VmsSupportPhysicalAddress
);
```

### <a name="parameters"></a>参数

*VmsSupportPhysicalAddress*\
中指向指向虚拟机控制结构 (VMCS) 的64位物理地址的指针。

## <a name="return-value"></a>返回值

|值|含义|
|-----------|-------------|
|0|操作成功。|
|1|操作失败，当前 VMCS 的 `VM-instruction error field` 中提供了扩展状态。|
|2|操作失败，无可用状态。|

## <a name="remarks"></a>备注

该`__vmx_on`函数对应`VMXON`于计算机指令。 此函数支持主机的虚拟机监视器与来宾操作系统及其应用程序进行交互。 有关详细信息, 请在[Intel Corporation](https://software.intel.com/articles/intel-sdm)站点搜索文档 "适用于 IA-32 Intel 体系结构的 Intel 虚拟化技术规范" 文档编号 C97063-002。

## <a name="requirements"></a>要求

|内部函数|体系结构|
|---------------|------------------|
|`__vmx_on`|X64|

**标头文件**\<intrin.h >

**结束 Microsoft 专用**

## <a name="see-also"></a>请参阅

[编译器内部函数](../intrinsics/compiler-intrinsics.md)

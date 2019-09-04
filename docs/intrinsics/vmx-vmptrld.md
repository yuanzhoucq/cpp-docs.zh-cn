---
title: __vmx_vmptrld
ms.date: 09/02/2019
f1_keywords:
- __vmx_vmptrld
helpviewer_keywords:
- __vmx_vmptrld intrinsic
- VMPTRLD instruction
ms.assetid: 95c9ec5b-1a81-41ba-983e-327bd6a65fcb
ms.openlocfilehash: 79b5a8b34b652ae1f011e89c793a7157c9e435ee
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/03/2019
ms.locfileid: "70219503"
---
# <a name="__vmx_vmptrld"></a>__vmx_vmptrld

**Microsoft 专用**

从指定的地址将指针加载到当前的虚拟机控制结构 (VMCS)。

## <a name="syntax"></a>语法

```C
int __vmx_vmptrld(
   unsigned __int64 *VmcsPhysicalAddress
);
```

### <a name="parameters"></a>参数

*VmcsPhysicalAddress*\
中存储 VMCS 指针的地址。

## <a name="return-value"></a>返回值

0
操作成功。

2
操作失败，当前 VMCS 的 `VM-instruction error field` 中提供了扩展状态。

pps-2
操作失败，无可用状态。

## <a name="remarks"></a>备注

VMCS 指针是一个64位的物理地址。

`__vmx_vmptrld` 函数等同于 `VMPTRLD` 计算机指令。 此函数支持主机的虚拟机监视器与来宾操作系统及其应用程序进行交互。 有关详细信息, 请在[Intel Corporation](https://software.intel.com/articles/intel-sdm)站点搜索文档 "适用于 IA-32 Intel 体系结构的 Intel 虚拟化技术规范" 文档编号 C97063-002。

## <a name="requirements"></a>要求

|内部函数|体系结构|
|---------------|------------------|
|`__vmx_vmptrld`|X64|

**标头文件**\<intrin.h >

**结束 Microsoft 专用**

## <a name="see-also"></a>请参阅

[编译器内部函数](../intrinsics/compiler-intrinsics.md)\
[__vmx_vmptrst](../intrinsics/vmx-vmptrst.md)

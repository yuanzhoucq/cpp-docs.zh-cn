---
title: __vmx_vmread
ms.date: 09/02/2019
f1_keywords:
- __vmx_vmread
helpviewer_keywords:
- VMREAD instruction
- __vmx_vmread intrinsic
ms.assetid: 08bdd7a0-6435-4ea6-b9a0-f592d870e5aa
ms.openlocfilehash: 409835ac29d6f2e839de62291cc5b142166a465c
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/03/2019
ms.locfileid: "70219429"
---
# <a name="__vmx_vmread"></a>__vmx_vmread

**Microsoft 专用**

从当前虚拟机控制结构 (VMCS) 读取指定字段, 并将其放在指定位置。

## <a name="syntax"></a>语法

```C
unsigned char __vmx_vmread(
   size_t Field,
   size_t *FieldValue
);
```

### <a name="parameters"></a>参数

*定义域*\
中要读取的 VMCS 字段。

*FieldValue*\
中一个指针, 指向用于存储从`Field`参数指定的 VMCS 字段中读取的值的位置。

## <a name="return-value"></a>返回值

|值|含义|
|-----------|-------------|
|0|操作成功。|
|1|操作失败，当前 VMCS 的 `VM-instruction error field` 中提供了扩展状态。|
|2|操作失败，无可用状态。|

## <a name="remarks"></a>备注

`__vmx_vmread` 函数等同于 `VMREAD` 计算机指令。 `Field`参数的值是一个编码的字段索引, 在 Intel 文档中进行了介绍。 有关详细信息, 请在[Intel Corporation](https://software.intel.com/articles/intel-sdm)站点搜索 "适用于 IA-32 Intel 体系结构的 Intel 虚拟化技术规范" 的附录 C。

## <a name="requirements"></a>要求

|内部函数|体系结构|
|---------------|------------------|
|`__vmx_vmread`|X64|

**标头文件**\<intrin.h >

**结束 Microsoft 专用**

## <a name="see-also"></a>请参阅

[编译器内部函数](../intrinsics/compiler-intrinsics.md)\
[__vmx_vmwrite](../intrinsics/vmx-vmwrite.md)

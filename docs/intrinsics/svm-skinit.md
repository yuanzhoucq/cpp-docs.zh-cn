---
title: __svm_skinit |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- __svm_skinit
dev_langs:
- C++
helpviewer_keywords:
- SKINIT instruction
- __svm_skinit intrinsic
ms.assetid: 787ec781-4cf2-40a2-aa20-5192334b131a
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 1fa468fddd24bd622d839bb1882af99d393a3d99
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/19/2018
ms.locfileid: "46426128"
---
# <a name="svmskinit"></a>__svm_skinit

**Microsoft 专用**

启动加载的可验证安全软件，如虚拟机监视器。

## <a name="syntax"></a>语法

```
void __svm_skinit(
   int SLB
);
```

#### <a name="parameters"></a>参数

|参数|描述|
|---------------|-----------------|
|`SLB`|32 位物理地址的 64k 字节安全加载程序块 (SLB)。|

## <a name="remarks"></a>备注

`__svm_skinit`函数等同于`SKINIT`计算机指令。 此函数是使用处理器和受信任平台模块 (TPM) 来验证并加载名为安全内核 (SK) 受信任的软件安全系统的一部分。 虚拟机监视器是安全内核的示例。 安全系统将验证程序组件初始化过程中加载，并防止篡改被中断，设备的访问或另一个程序，如果计算机是多处理器组件。

`SLB`参数指定的内存中，调用 64k 块的物理地址*安全加载程序块*(SLB)。 SLB 包含一个名为建立操作环境的计算机，并随后将加载安全内核安全加载程序程序。

此函数支持主机的虚拟机监视器与来宾操作系统及其应用程序进行交互。 有关详细信息，搜索文档中，"AMD64 体系结构编程人员手动卷 2： 系统编程中，"文档数 24593，修订 3.11， [AMD corporation](https://developer.amd.com/resources/developer-guides-manuals/)站点。

## <a name="requirements"></a>要求

|内部函数|体系结构|
|---------------|------------------|
|`__svm_skinit`|x86、x64|

**标头文件** \<intrin.h >

**结束 Microsoft 专用**

## <a name="see-also"></a>请参阅

[编译器内部函数](../intrinsics/compiler-intrinsics.md)
---
title: __svm_vmrun | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- __svm_vmrun
dev_langs:
- C++
helpviewer_keywords:
- __svm_vmrun intrinsic
- VMRUN instruction
ms.assetid: ae98a781-fc17-47b2-b40f-86fcebf1867b
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 4711238c45955ee7067e3e418212bcdb0fae09ca
ms.sourcegitcommit: a41c4d096afca1e9b619bbbce045b77135d32ae2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/14/2018
ms.locfileid: "42539173"
---
# <a name="svmvmrun"></a>__svm_vmrun
**Microsoft 专用**  
  
 启动虚拟机来宾代码对应于指定的虚拟机控制块 (VMCB) 的执行。  
  
## <a name="syntax"></a>语法  
  
```  
void __svm_vmrun(  
   size_t VmcbPhysicalAddress  
);  
```  
  
#### <a name="parameters"></a>参数  
  
|参数|描述|  
|---------------|-----------------|  
|[in] `VmcbPhysicalAddress`|VMCB 物理地址。|  
  
## <a name="remarks"></a>备注  
 `__svm_vmrun`函数使用在 VMCB 最少量的信息来开始执行虚拟机来宾代码。 使用[__svm_vmsave](../intrinsics/svm-vmsave.md)或[__svm_vmload](../intrinsics/svm-vmload.md)函数如果需要处理的复杂中断或切换到另一台来宾的详细信息。  
  
 `__svm_vmrun`函数等同于`VMRUN`计算机指令。 此函数支持主机的虚拟机监视器与来宾操作系统及其应用程序进行交互。 有关详细信息，搜索文档中，"AMD64 体系结构编程人员手动卷 2： 系统编程中，"文档编号 24593、 3.11 或更高版本，在修订[AMD corporation](http://go.microsoft.com/fwlink/p/?linkid=23746)站点。  
  
## <a name="requirements"></a>要求  
  
|内部函数|体系结构|  
|---------------|------------------|  
|`__svm_vmrun`|x86、x64|  
  
 **标头文件** \<intrin.h >  
  
**结束 Microsoft 专用**  
  
## <a name="see-also"></a>请参阅  
 [编译器内部函数](../intrinsics/compiler-intrinsics.md)   
 [__svm_vmsave](../intrinsics/svm-vmsave.md)   
 [__svm_vmload](../intrinsics/svm-vmload.md)
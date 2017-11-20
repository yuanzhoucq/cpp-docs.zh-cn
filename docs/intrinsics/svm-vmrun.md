---
title: "__svm_vmrun |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: __svm_vmrun
dev_langs: C++
helpviewer_keywords:
- __svm_vmrun intrinsic
- VMRUN instruction
ms.assetid: ae98a781-fc17-47b2-b40f-86fcebf1867b
caps.latest.revision: "5"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 04467cc1d6d13a5c7c983aae48d2208622a75683
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
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
  
|参数|说明|  
|---------------|-----------------|  
|[in] `VmcbPhysicalAddress`|VMCB 物理地址。|  
  
## <a name="remarks"></a>备注  
 `__svm_vmrun`函数使用 VMCB 中最少量的信息来开始执行虚拟机来宾代码。 使用[__svm_vmsave](../intrinsics/svm-vmsave.md)或[__svm_vmload](../intrinsics/svm-vmload.md)函数如果你需要以处理复杂的中断，或切换到另一个来宾的详细信息。  
  
 `__svm_vmrun`函数等同于`VMRUN`计算机指令。 此函数支持主机的虚拟机监视器与来宾操作系统及其应用程序进行交互。 有关详细信息，搜索文档中，"AMD64 体系结构程序员手动卷 2： 系统编程中，"文档编号 24593、 修订 3.11 或更高版本，在[AMD corporation](http://go.microsoft.com/fwlink/?LinkId=23746)站点。  
  
## <a name="requirements"></a>要求  
  
|内部函数|体系结构|  
|---------------|------------------|  
|`__svm_vmrun`|x86, [!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|  
  
 **标头文件** \<intrin.h >  
  
**结束 Microsoft 专用**  
  
## <a name="see-also"></a>另请参阅  
 [编译器内部函数](../intrinsics/compiler-intrinsics.md)   
 [__svm_vmsave](../intrinsics/svm-vmsave.md)   
 [__svm_vmload](../intrinsics/svm-vmload.md)
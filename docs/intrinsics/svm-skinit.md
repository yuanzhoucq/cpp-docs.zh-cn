---
title: "__svm_skinit |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: __svm_skinit
dev_langs: C++
helpviewer_keywords:
- SKINIT instruction
- __svm_skinit intrinsic
ms.assetid: 787ec781-4cf2-40a2-aa20-5192334b131a
caps.latest.revision: "5"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 63f58bed44dcea47c925f94b90e9438eb1082962
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
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
|`SLB`|64k 字节的 32 位物理地址安全加载程序块 (SLB)。|  
  
## <a name="remarks"></a>备注  
 `__svm_skinit`函数等同于`SKINIT`计算机指令。 此函数是使用的处理器和受信任平台模块 (TPM) 来验证并加载调用安全内核 (SK) 的受信任的软件安全系统的一部分。 虚拟机监视器是一种安全内核。 安全系统验证程序组件加载在初始化过程中，并且防止篡改由中断，设备的访问或另一个程序，如果计算机是多处理器组件。  
  
 `SLB`参数指定的内存称为 64k 块的物理地址*安全加载程序块*(SLB)。 SLB 包含一个名为安全加载程序建立操作环境的计算机，并随后加载安全内核程序。  
  
 此函数支持主机的虚拟机监视器与来宾操作系统及其应用程序进行交互。 有关详细信息，搜索文档中，"AMD64 体系结构程序员手动卷 2： 系统编程中，"在文档数 24593，修订 3.11， [AMD corporation](http://go.microsoft.com/fwlink/?LinkId=23746)站点。  
  
## <a name="requirements"></a>要求  
  
|内部函数|体系结构|  
|---------------|------------------|  
|`__svm_skinit`|x86, [!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|  
  
 **标头文件** \<intrin.h >  
  
**结束 Microsoft 专用**  
  
## <a name="see-also"></a>另请参阅  
 [编译器内部函数](../intrinsics/compiler-intrinsics.md)
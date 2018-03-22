---
title: VCPROFILE_PATH | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VCPROFILE_PATH
dev_langs:
- C++
helpviewer_keywords:
- VCPROFILE_PATH environment variable
ms.assetid: 25217aa4-7e86-4eba-854d-10b3c457e4df
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: ea682b70f4417ef49bfca530af5f12f21699a389
ms.sourcegitcommit: 5cd2e3e51ecc8d9fc0d889555b4bfa193ba1d6a5
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/21/2018
---
# <a name="vcprofilepath"></a>VCPROFILE_PATH
指定要创建对应的.pgc 文件的目录。  
  
## <a name="syntax"></a>语法  
  
```  
VCPROFILE_PATH=path  
```  
  
#### <a name="parameters"></a>参数  
 `path`  
 中的.pgc 文件将被添加至目录路径。  
  
## <a name="remarks"></a>备注  
 默认情况下，在所分析二进制文件所在的目录中创建对应的.pgc 文件。  但是，如果二进制文件的绝对路径不存在，可能出现此情况，在其中生成二进制文件已从其他计算机上运行配置文件方案时，你可以设置`VCPROFILE_PATH`到存在的路径。  
  
## <a name="example"></a>示例  
  
```  
set VCPROFILE_PATH=c:\  
```  
  
## <a name="see-also"></a>另请参阅  
 [用于按配置文件优化的环境变量](../../build/reference/environment-variables-for-profile-guided-optimizations.md)
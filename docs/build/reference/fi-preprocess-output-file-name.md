---
title: "-Fi （预处理输出文件名） |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- /Fi
dev_langs:
- C++
helpviewer_keywords:
- Fi compiler option (C++)
- -Fi compiler option (C++)
- /Fi compiler option (C++)
- preprocessing output files, file name
ms.assetid: 6d0ba983-a8b7-41ec-84f5-b4688ef8efee
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 9bc3076a529984358aed16902f509ceb01423f9e
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="fi-preprocess-output-file-name"></a>/Fi（预处理输出文件名）
指定到的输出文件的名称[/P （预处理到文件）](../../build/reference/p-preprocess-to-a-file.md)编译器选项将预处理的输出。  
  
## <a name="syntax"></a>语法  
  
```  
/Fipathname  
```  
  
#### <a name="parameters"></a>参数  
  
|参数|描述|  
|---------------|-----------------|  
|`pathname`|名称和输出文件的路径由**/P**编译器选项。|  
  
## <a name="remarks"></a>备注  
 使用**/Fi**编译器选项结合**/P**编译器选项。  
  
 如果你仅为指定路径`pathname`参数，源文件的基名称用作预处理的输出文件的基名称。 `pathname`参数不需要特定文件扩展名。 但是，如果你不指定文件扩展名，则使用".i"的扩展。  
  
## <a name="example"></a>示例  
 下面的命令行对进行预处理 PROGRAM.cpp，保留注释，添加[#line](../../preprocessor/hash-line-directive-c-cpp.md)指令，并将结果写入到 MYPROCESS.i 文件。  
  
```  
CL /P /FiMYPROCESS.I PROGRAM.CPP  
```  
  
## <a name="see-also"></a>请参阅  
 [编译器选项](../../build/reference/compiler-options.md)   
 [/P （预处理到文件）](../../build/reference/p-preprocess-to-a-file.md)   
 [指定路径名](../../build/reference/specifying-the-pathname.md)
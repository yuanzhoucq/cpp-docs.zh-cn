---
title: "-MANIFESTINPUT （指定清单输入） |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
ms.assetid: a0b0c21e-1f9b-4d8c-bb3f-178f57fa7f1b
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: e1eec78675845e3f738bb0b6b440b3a71f1fd572
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="manifestinput-specify-manifest-input"></a>/MANIFESTINPUT（指定清单输入）
指定要包含在映像中嵌入的清单中的清单输入的文件。  
  
## <a name="syntax"></a>语法  
  
```  
/MANIFESTINPUT:filename  
```  
  
#### <a name="parameters"></a>参数  
 `filename`  
 要在嵌入的清单中包含的清单文件。  
  
## <a name="remarks"></a>备注  
 **/MANIFESTINPUT**选项指定要用于在可执行映像中创建嵌入的清单输入文件的路径。 如果你有多个清单输入文件，请使用交换机多次 — 一次针对每个输入文件。 清单输入的文件合并，以创建嵌入的清单。 此选项需要**/manifest： 嵌入**选项。  
  
 不能直接在中设置此选项[!INCLUDE[vsprvs](../../assembler/masm/includes/vsprvs_md.md)]。 请改用**其他清单文件**项目来指定要包括的其他清单文件属性。 有关详细信息，请参阅[输入和输出、 清单工具、 配置属性\<项目名称 > 属性页对话框中](../../ide/input-and-output-manifest-tool.md)。  
  
## <a name="see-also"></a>请参阅  
 [设置链接器选项](../../build/reference/setting-linker-options.md)   
 [链接器选项](../../build/reference/linker-options.md)
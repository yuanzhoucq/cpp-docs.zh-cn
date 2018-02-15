---
title: "ICommandTextImpl 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- ICommandText
dev_langs:
- C++
helpviewer_keywords:
- ICommandText class
ms.assetid: 9c2715cc-1e55-4468-8327-85341617ed46
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 397f7b26d9f75813897309c99c40d5db94f06c53
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/14/2018
---
# <a name="icommandtextimpl-class"></a>ICommandTextImpl 类
提供的实现[ICommandText](https://msdn.microsoft.com/en-us/library/ms714914.aspx)接口。  
  
## <a name="syntax"></a>语法

```cpp
template <class T >  
class ATL_NO_VTABLE ICommandTextImpl   
   : public ICommandImpl<T, ICommandText>  
```  
  
#### <a name="parameters"></a>参数  
 `T`  
 命令类派生自**ICommandTextImpl**。  
  
## <a name="members"></a>成员  
  
### <a name="interface-methods"></a>接口方法  
  
|||  
|-|-|  
|[GetCommandText](../../data/oledb/icommandtextimpl-getcommandtext.md)|返回的文本命令集的最后一个调用[SetCommandText](../../data/oledb/icommandtextimpl-setcommandtext.md)。|  
|[SetCommandText](../../data/oledb/icommandtextimpl-setcommandtext.md)|设置替换现有的命令文本的命令文本。|  
  
### <a name="data-members"></a>数据成员  
  
|||  
|-|-|  
|[m_strCommandText](../../data/oledb/icommandtextimpl-m-strcommandtext.md)|将存储命令文本。|  
  
## <a name="remarks"></a>备注  
 命令上的必需接口。  
  
## <a name="requirements"></a>惠?  
 **标头：** altdb.h  
  
## <a name="see-also"></a>请参阅  
 [OLE DB 提供程序模板](../../data/oledb/ole-db-provider-templates-cpp.md)   
 [OLE DB 提供程序模板体系结构](../../data/oledb/ole-db-provider-template-architecture.md)
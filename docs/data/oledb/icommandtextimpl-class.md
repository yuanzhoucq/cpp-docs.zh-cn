---
title: ICommandTextImpl 类 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- ICommandText
- GetCommandText
- ICommandTextImpl.GetCommandText
- ICommandTextImpl::GetCommandText
- ATL::ICommandTextImpl::m_strCommandText
- ICommandTextImpl<T>::m_strCommandText
- m_strCommandText
- ICommandTextImpl.m_strCommandText
- ICommandTextImpl::m_strCommandText
- ATL::ICommandTextImpl<T>::m_strCommandText
- ATL.ICommandTextImpl.m_strCommandText
- ICommandTextImpl.SetCommandText
- ICommandTextImpl::SetCommandText
- SetCommandText
dev_langs:
- C++
helpviewer_keywords:
- ICommandText class
- GetCommandText method
- m_strCommandText
- SetCommandText method
ms.assetid: 9c2715cc-1e55-4468-8327-85341617ed46
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: b73111fe05a7c752edda0c95f1289a125828d4a5
ms.sourcegitcommit: 3a141cf07b5411d5f1fdf6cf67c4ce928cf389c3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/11/2018
ms.locfileid: "49082548"
---
# <a name="icommandtextimpl-class"></a>ICommandTextImpl 类

提供一个实现[ICommandText](/previous-versions/windows/desktop/ms714914)接口。  
  
## <a name="syntax"></a>语法

```cpp
template <class T >  
class ATL_NO_VTABLE ICommandTextImpl   
   : public ICommandImpl<T, ICommandText>  
```  
  
### <a name="parameters"></a>参数  

*T*<br/>
命令类派生自`ICommandTextImpl`。 

## <a name="requirements"></a>要求  

**标头：** altdb.h  
  
## <a name="members"></a>成员  
  
### <a name="interface-methods"></a>接口方法  
  
|||  
|-|-|  
|[GetCommandText](#getcommandtext)|返回到最后一次调用设置的文本命令[SetCommandText](../../data/oledb/icommandtextimpl-setcommandtext.md)。|  
|[SetCommandText](#setcommandtext)|设置替换现有命令文本的命令文本。|  
  
### <a name="data-members"></a>数据成员  
  
|||  
|-|-|  
|[m_strCommandText](#strcommandtext)|存储命令文本。|  
  
## <a name="remarks"></a>备注  

在命令上必需的接口。  
 
## <a name="getcommandtext"></a> Icommandtextimpl:: Getcommandtext

返回到最后一次调用设置的文本命令[SetCommandText](../../data/oledb/icommandtextimpl-setcommandtext.md)。  
  
### <a name="syntax"></a>语法  
  
```cpp
STDMETHOD(GetCommandText)(GUID * pguidDialect,   
   LPOLESTR * ppwszCommand);  
```  
  
#### <a name="parameters"></a>参数  

请参阅[ICommandText::GetCommandText](/previous-versions/windows/desktop/ms709825)中*OLE DB 程序员参考*。 *PguidDialect*默认情况下忽略参数。  

## <a name="setcommandtext"></a> Icommandtextimpl:: Setcommandtext

设置替换现有命令文本的命令文本。  
  
### <a name="syntax"></a>语法  
  
```cpp
STDMETHOD(SetCommandText)(REFGUID rguidDialect,   
   LPCOLESTR pwszCommand);  
```  
  
#### <a name="parameters"></a>参数  

请参阅[icommandtext:: Setcommandtext](/previous-versions/windows/desktop/ms709757)中*OLE DB 程序员参考*。 

## <a name="strcommandtext"></a> Icommandtextimpl:: M_strcommandtext

存储命令文本字符串。  
  
### <a name="syntax"></a>语法  
  
```cpp
CComBSTR m_strCommandText;  
```  
  
## <a name="see-also"></a>请参阅  

[OLE DB 提供程序模板](../../data/oledb/ole-db-provider-templates-cpp.md)<br/>
[OLE DB 提供程序模板体系结构](../../data/oledb/ole-db-provider-template-architecture.md)
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
ms.openlocfilehash: 2b54d0db22181089a8470c540ccd72f85c717fbe
ms.sourcegitcommit: 889a75be1232817150be1e0e8d4d7f48f5993af2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/30/2018
ms.locfileid: "39340288"
---
# <a name="icommandtextimpl-class"></a>ICommandTextImpl 类
提供一个实现[ICommandText](https://msdn.microsoft.com/library/ms714914.aspx)接口。  
  
## <a name="syntax"></a>语法

```cpp
template <class T >  
class ATL_NO_VTABLE ICommandTextImpl   
   : public ICommandImpl<T, ICommandText>  
```  
  
### <a name="parameters"></a>参数  
 *T*  
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
 请参阅[ICommandText::GetCommandText](https://msdn.microsoft.com/library/ms709825.aspx)中*OLE DB 程序员参考*。 *PguidDialect*默认情况下忽略参数。  

## <a name="setcommandtext"></a> Icommandtextimpl:: Setcommandtext
设置替换现有命令文本的命令文本。  
  
### <a name="syntax"></a>语法  
  
```cpp
STDMETHOD(SetCommandText)(REFGUID rguidDialect,   
   LPCOLESTR pwszCommand);  
```  
  
#### <a name="parameters"></a>参数  
 请参阅[icommandtext:: Setcommandtext](https://msdn.microsoft.com/library/ms709757.aspx)中*OLE DB 程序员参考*。 

## <a name="strcommandtext"></a> Icommandtextimpl:: M_strcommandtext
存储命令文本字符串。  
  
### <a name="syntax"></a>语法  
  
```cpp
CComBSTR m_strCommandText;  
```  
  
## <a name="see-also"></a>请参阅  
 [OLE DB 提供程序模板](../../data/oledb/ole-db-provider-templates-cpp.md)   
 [OLE DB 提供程序模板体系结构](../../data/oledb/ole-db-provider-template-architecture.md)
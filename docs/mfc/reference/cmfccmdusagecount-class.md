---
title: "CMFCCmdUsageCount 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CMFCCmdUsageCount
dev_langs:
- C++
helpviewer_keywords:
- CMFCCmdUsageCount class
ms.assetid: 9c33b783-37c0-43ea-9f31-3c75e246c841
caps.latest.revision: 20
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 0e0c08ddc57d437c51872b5186ae3fc983bb0199
ms.openlocfilehash: b264448af4041139018b181e2255988555267b89
ms.lasthandoff: 02/24/2017

---
# <a name="cmfccmdusagecount-class"></a>CMFCCmdUsageCount 类
跟踪 Windows 消息，例如当用户从菜单中选择某个项的使用计数。  
  
## <a name="syntax"></a>语法  
  
```  
class CMFCCmdUsageCount : public CObject  
```  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|||  
|-|-|  
|名称|说明|  
|`CMFCCmdUsageCount::CMFCCmdUsageCount`|默认构造函数。|  
|`CMFCCmdUsageCount::~CMFCCmdUsageCount`|析构函数。|  
  
### <a name="public-methods"></a>公共方法  
  
|||  
|-|-|  
|名称|说明|  
|[CMFCCmdUsageCount::AddCmd](#addcmd)|一个与给定的命令相关联的计数器将增加。|  
|[CMFCCmdUsageCount::GetCount](#getcount)|检索与给定的命令 ID 相关联的使用计数|  
|[CMFCCmdUsageCount::HasEnoughInformation](#hasenoughinformation)|确定此对象是否具有收集最小数量的跟踪数据。|  
|[CMFCCmdUsageCount::IsFreqeuntlyUsedCmd](#isfreqeuntlyusedcmd)|确定是否经常使用给定的命令。|  
|[CMFCCmdUsageCount::Reset](#reset)|清除所有命令的使用计数。|  
|[CMFCCmdUsageCount::Serialize](#serialize)|从存档读取此对象或将其写入存档。 (重写[cobject:: Serialize](../../mfc/reference/cobject-class.md#serialize)。)|  
|[CMFCCmdUsageCount::SetOptions](#setoptions)|设置的值共享`CMFCCmdUsageCount`类数据成员。|  
  
### <a name="data-members"></a>数据成员  
  
|||  
|-|-|  
|名称|说明|  
|`m_CmdUsage`|一个`CMap`将命令映射到其使用情况计数的对象。|  
|`m_nMinUsagePercentage`|命令，以将常用小使用率百分比。|  
|`m_nStartCount`|起始计数器，用于确定此对象是否具有收集最小数量的跟踪数据。|  
|`m_nTotalUsage`|所有跟踪命令计数。|  
  
### <a name="remarks"></a>备注  
 `CMFCCmdUsageCount`类映射到 32 位无符号的整数计数器数值的每个 Windows 消息标识符。 `CMFCToolBar`使用此类来显示常用工具栏项。 有关详细信息`CMFCToolBar`，请参阅[CMFCToolBar 类](../../mfc/reference/cmfctoolbar-class.md)。  
  
 您可以保留`CMFCCmdUsageCount`类程序的运行之间的数据。 使用[CMFCCmdUsageCount::Serialize](#serialize)方法可序列化类成员数据和[CMFCCmdUsageCount::SetOptions](#setoptions)方法以设置共享的成员数据。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CMFCCmdUsageCount](../../mfc/reference/cmfccmdusagecount-class.md)  
  
## <a name="requirements"></a>要求  
 **标头︰** afxcmdusagecount.h  
  
##  <a name="a-nameaddcmda--cmfccmdusagecountaddcmd"></a><a name="addcmd"></a>CMFCCmdUsageCount::AddCmd  
 一个与给定的命令相关联的计数器将增加。  
  
```  
void AddCmd(UINT uiCmd);
```  
  
### <a name="parameters"></a>参数  
  
|||  
|-|-|  
|参数|说明|  
|[in] `uiCmd`|指定命令计数器递增。|  
  
### <a name="remarks"></a>备注  
 此方法将新条目添加到命令计数站点地图结构`m_CmdUsage`，如果该条目不存在。  
  
 此方法没有任何效果在以下情况︰  
  
-   工具栏框架是在自定义模式 ( [CMFCToolBar::IsCustomizeMode](../../mfc/reference/cmfctoolbar-class.md#iscustomizemode)方法返回一个非零值)。  
  
-   该命令是指子菜单或菜单分隔符 (`uiCmd`等于 0 或-1)。  
  
- `uiCmd`指的是标准命令 (全局`IsStandardCommand`函数将返回一个非零值)。  
  
##  <a name="a-namegetcounta--cmfccmdusagecountgetcount"></a><a name="getcount"></a>CMFCCmdUsageCount::GetCount  
 检索与给定的命令 ID 相关联的使用计数  
  
```  
UINT GetCount(UINT uiCmd) const;  
```  
  
### <a name="parameters"></a>参数  
  
|||  
|-|-|  
|参数|说明|  
|[in] `uiCmd`|要检索命令计数器的 ID。|  
  
### <a name="return-value"></a>返回值  
 与给定的命令 ID 相关联的使用计数  
  
##  <a name="a-namehasenoughinformationa--cmfccmdusagecounthasenoughinformation"></a><a name="hasenoughinformation"></a>CMFCCmdUsageCount::HasEnoughInformation  
 确定此对象是否已接收到最小数量的跟踪数据。  
  
```  
BOOL HasEnoughInformation() const;  
```  
  
### <a name="return-value"></a>返回值  
 非零，如果此对象已收到最小数量的跟踪数据;否则为 0。  
  
### <a name="remarks"></a>备注  
 如果此方法返回一个非零值的总计数`m_nTotalUsage`，所有跟踪命令是等于或大于的初始计数`m_nStartCount`。 默认情况下，框架将设置初始计数 0。 您可以使用重写此值[CMFCCmdUsageCount::SetOptions](#setoptions)方法。  
  
 此方法由[CMFCMenuBar::IsShowAllCommands](../../mfc/reference/cmfcmenubar-class.md#isshowallcommands)来确定是否显示所有可用菜单命令。  
  
##  <a name="a-nameisfreqeuntlyusedcmda--cmfccmdusagecountisfreqeuntlyusedcmd"></a><a name="isfreqeuntlyusedcmd"></a>CMFCCmdUsageCount::IsFreqeuntlyUsedCmd  
 确定是否经常使用给定的命令。  
  
```  
BOOL IsFreqeuntlyUsedCmd(UINT uiCmd) const;  
```  
  
### <a name="parameters"></a>参数  
  
|||  
|-|-|  
|参数|说明|  
|[in] `uiCmd`|指定要检查的命令。|  
  
### <a name="return-value"></a>返回值  
 非零，如果经常使用的命令;否则为 0。  
  
### <a name="remarks"></a>备注  
 此方法返回 0，如果使用总命令`m_nTotalUsage`，为 0。 否则，此方法将返回非零，如果指定的命令使用其中的百分比大于最小百分比`m_nMinUsagePercentage`。 默认情况下，框架将最小百分比设置为 5。 您可以使用重写此值[CMFCCmdUsageCount::SetOptions](#setoptions)方法。 如果最小百分比为 0，则此方法返回非零，如果指定的命令计数大于 0。  
  
 [CMFCToolBar::IsCommandRarelyUsed](../../mfc/reference/cmfctoolbar-class.md#iscommandrarelyused)使用此方法来确定命令是否很少使用。  
  
##  <a name="a-namereseta--cmfccmdusagecountreset"></a><a name="reset"></a>CMFCCmdUsageCount::Reset  
 清除所有命令的使用计数。  
  
```  
void Reset();
```  
  
### <a name="remarks"></a>备注  
 调用此方法来清除所有项从的命令计数映射结构`m_CmdUsage`，并重置总命令用法， `m_nTotalUsage`、 计数器为 0。  
  
##  <a name="a-nameserializea--cmfccmdusagecountserialize"></a><a name="serialize"></a>CMFCCmdUsageCount::Serialize  
 从存档读取此对象或将其写入存档。  
  
```  
virtual void Serialize(CArchive& ar);
```  
  
### <a name="parameters"></a>参数  
  
|||  
|-|-|  
|参数|说明|  
|[in] `ar`|一个`CArchive`要序列化来自或发往对象。|  
  
### <a name="remarks"></a>备注  
 此方法进行序列化的命令计数映射结构`m_CmdUsage`，并且总命令的使用情况， `m_nTotalUsage`、 计数器来自或发往指定存档。  
  
 有关序列化示例，请参阅[序列化︰ 将对象序列化为](../../mfc/serialization-serializing-an-object.md)。  
  
##  <a name="a-namesetoptionsa--cmfccmdusagecountsetoptions"></a><a name="setoptions"></a>CMFCCmdUsageCount::SetOptions  
 设置的值共享`CMFCCmdUsageCount`类数据成员。  
  
```  
static BOOL __stdcall SetOptions(
    UINT nStartCount,  
    UINT nMinUsagePercentage);
```  
  
### <a name="parameters"></a>参数  
  
|||  
|-|-|  
|参数|说明|  
|[in] `nStartCount`|所有跟踪命令新初始计数。|  
|[in] `nMinUsagePercentage`|新的小使用率百分比。|  
  
### <a name="return-value"></a>返回值  
 `TRUE`如果该方法成功，`FALSE`如果`nMinUsagePercentage`参数是否大于或等于 100。  
  
### <a name="remarks"></a>备注  
 此方法可设置共享`CMFCCmdUsageCount`类数据成员`m_nStartCount`和`m_nMinUsagePercentage`到`nStartCount`和`nMinUsagePercentage`分别。 `m_nStartCount`通过使用[CMFCCmdUsageCount::HasEnoughInformation](#hasenoughinformation)方法来确定此对象是否具有收集最小数量的跟踪数据。 `m_nMinUsagePercentage`通过使用[CMFCCmdUsageCount::IsFreqeuntlyUsedCmd](#isfreqeuntlyusedcmd)方法，以确定是否经常使用给定的命令。  
  
 在调试生成中如果此方法生成断言失败`nMinUsagePercentage`参数是否大于或等于 100。  
  
## <a name="see-also"></a>另请参阅  
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [类](../../mfc/reference/mfc-classes.md)   
 [CMFCToolBar 类](../../mfc/reference/cmfctoolbar-class.md)


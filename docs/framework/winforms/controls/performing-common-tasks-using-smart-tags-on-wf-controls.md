---
title: 演练：使用 Windows 窗体控件上的智能标记执行常规任务
ms.date: 03/30/2017
helpviewer_keywords:
- DesignerAction object model
- smart tags
- designer actions
ms.assetid: cac337e6-00f6-4584-80f4-75728f5ea113
ms.openlocfilehash: d1c69d2e9e89e0a4fed767216e8743a0ac9ac81d
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/08/2018
ms.locfileid: "44201798"
---
# <a name="walkthrough-performing-common-tasks-using-smart-tags-on-windows-forms-controls"></a>演练：使用 Windows 窗体控件上的智能标记执行常规任务
在 Windows 窗体应用程序构造窗体和控件，如有需要反复执行的许多任务。 以下是一些你将遇到的执行常用任务：  
  
-   添加或删除选项卡上<xref:System.Windows.Forms.TabControl>。  
  
-   将控件停靠到其父级。  
  
-   更改的方向<xref:System.Windows.Forms.SplitContainer>控件。  
  
 若要加快开发速度，许多控件提供智能标记，可用于在设计时执行常见任务，比如在一个独立的上下文相关菜单。 这些任务称作*智能标记谓词*。  
  
 智能标记的设计器中的整个生存期保持附加到一个控件实例，并始终处于可用状态。  
  
 本演练涉及以下任务：  
  
-   创建 Windows 窗体项目  
  
-   使用智能标记  
  
-   启用和禁用智能标记  
  
 完成上述操作后，你将会了解这些重要布局功能所发挥的作用。  
  
> [!NOTE]
>  显示的对话框和菜单命令可能会与“帮助”中的描述不同，具体取决于你现用的设置或版本。 若要更改设置，请在 **“工具”** 菜单上选择 **“导入和导出设置”** 。 有关详细信息，请参阅[个性化设置 Visual Studio IDE](/visualstudio/ide/personalizing-the-visual-studio-ide)。  
  
## <a name="creating-the-project"></a>创建项目  
 第一步是创建项目并设置窗体。  
  
#### <a name="to-create-the-project"></a>要创建项目  
  
1.  创建一个名为"SmartTagsExample"的基于 Windows 的应用程序项目 (**文件** > **新建** > **项目** >  **Visual C#** 或**Visual Basic** > **经典桌面** > **Windows 窗体应用程序**)。  
  
2.  选择中的窗体**Windows 窗体设计器**。  
  
## <a name="using-smart-tags"></a>使用智能标记  
 智能标记上将其提供的控件的设计时将始终可用。  
  
#### <a name="to-use-smart-tags"></a>若要使用智能标记  
  
1.  拖动<xref:System.Windows.Forms.TabControl>从**工具箱**拖动到窗体。 请注意的智能标记标志符号 (![智能标记标志符号](../../../../docs/framework/winforms/controls/media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")) 旁边的显示<xref:System.Windows.Forms.TabControl>。  
  
2.  单击智能标记标志符号。 在标志符号旁边显示的快捷菜单，选择**添加选项卡**项。 观察到的新选项卡页添加到<xref:System.Windows.Forms.TabControl>。  
  
3.  拖动<xref:System.Windows.Forms.TableLayoutPanel>控件从**工具箱**拖动到窗体。  
  
4.  单击智能标记标志符号。 在标志符号旁边显示的快捷菜单，选择**添加列**项。 观察新列添加到<xref:System.Windows.Forms.TableLayoutPanel>控件。  
  
5.  拖动<xref:System.Windows.Forms.SplitContainer>控件从**工具箱**拖动到窗体。  
  
6.  单击智能标记标志符号。 在标志符号旁边显示的快捷菜单，选择**水平拆分器方向**项。 观察<xref:System.Windows.Forms.SplitContainer>现在是控件的分隔条水平。  
  
## <a name="see-also"></a>请参阅  
 <xref:System.Windows.Forms.TextBox>  
 <xref:System.Windows.Forms.TabControl>  
 <xref:System.Windows.Forms.SplitContainer>  
 <xref:System.ComponentModel.Design.DesignerActionList>  
 [演练： 向 Windows 窗体组件添加智能标记](https://msdn.microsoft.com/library/a6814169-fa7d-4527-808c-637ca5c95f63)

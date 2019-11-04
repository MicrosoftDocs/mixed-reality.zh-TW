---
title: 更新您的 SteamVR 應用程式
description: 將您的 SteamVR 應用程式更新為使用 Windows Mixed Reality 耳機最大化相容性的最佳作法。
author: thmignon
ms.author: thmignon
ms.date: 03/21/2018
ms.topic: article
keywords: SteamVR，相容性
ms.openlocfilehash: 6479130b14b8b50828ebecd3a648fd8a425aec15
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/01/2019
ms.locfileid: "73438210"
---
# <a name="updating-your-steamvr-application"></a>更新您的 SteamVR 應用程式
我們鼓勵開發人員測試並優化其 SteamVR 體驗，以在 Windows Mixed Reality 耳機上執行。 本檔涵蓋開發人員可以進行的一般改良功能，以確保他們的體驗在 Windows Mixed Reality 上的執行效果良好。

## <a name="initial-setup-instructions"></a>初始設定指示

若要開始在 Windows Mixed Reality 上測試您的遊戲或應用程式，請務必先遵循我們的[快速入門手冊。](https://aka.ms/WindowsMixedRealitySteamVR)

## <a name="controller-models"></a>控制器模型
1. 如果您的應用程式會呈現控制器模型：
    * 使用[Windows Mixed Reality 運動控制器模型](motion-controllers.md#rendering-the-motion-controller-model)
    * 使用 IVRRenderModel：： GetComponentState 取得元件部分的本機轉換（例如 指標姿勢）
2. 具有慣用手概念的經驗應該會從輸入 Api 取得提示，以區別控制器[（Unity 範例）](gestures-and-motion-controllers-in-unity.md#unity-buttonaxis-mapping-table)

## <a name="controls"></a>控制項

設計或調整控制項版面配置時，請記住下列保留的命令集：
1. 按一下**左側和右側類比操縱杆**會保留給 [串流**儀表板**]。
2. **Windows 按鈕**一律會讓使用者回到 Windows Mixed Reality 首頁。

可能的話，預設為以 thumb teleportation 為依據，以符合[Windows Mixed Reality home](navigating-the-windows-mixed-reality-home.md#getting-around-your-home) teleportation 行為

## <a name="tooltips-and-ui"></a>工具提示和 UI

許多 VR 遊戲會利用動作控制器的工具提示和重迭，讓使用者學習其遊戲或應用程式最重要的命令。 針對 Windows Mixed reality 調整您的應用程式時，我們建議您查看這部分的體驗，以確保工具提示會對應到 Windows 控制器模型。

此外，如果您的體驗中顯示控制器影像的任何時間點，請務必使用 Windows Mixed Reality 動作控制器來提供更新的映射。

## <a name="haptics"></a>Haptics

從[windows 10 2018 年4月更新](release-notes-april-2018.md)開始，現在支援 Haptics Windows Mixed Reality 的 SteamVR 體驗。 如果您的 SteamVR 應用程式或遊戲已包含對 haptics 的支援，則[Windows Mixed Reality 動作控制器](motion-controllers.md)現在應該可以正常執行（不需要額外的工作）。

Windows Mixed Reality 運動控制器會使用標準的 haptics 馬達，而不是在其他 SteamVR 運動控制器中找到的線性傳動器，這可能會導致略有不同的使用者體驗。 因此，我們建議使用 Windows Mixed Reality 動作控制器來測試和調整您的 haptics 設計。 例如，在 Windows Mixed Reality 動作控制器上，有時短 haptic 脈衝（5-10 毫秒）較不明顯。 若要產生更明顯的脈衝，請嘗試傳送較長的「按一下」（40-70ms），讓馬達在被告知關閉電源之前，有更多時間來加速。

## <a name="launching-steamvr-apps-from-windows-mixed-reality-start-menu"></a>從 Windows Mixed Reality 開始功能表啟動 SteamVR 應用程式

針對透過串流散發的 VR 經驗，我們已[更新 SteamVR Beta 的 Windows Mixed Reality](https://steamcommunity.com/games/719950/announcements/detail/1687045485866139800)以及最新的[Windows 測試人員](https://insider.windows.com)RS5 航班，讓 SteamVR 標題現在會顯示在 [所有應用程式] 的 Windows Mixed Reality [開始] 功能表中自動列出。 安裝這些軟體版本後，您的客戶現在就可以直接從 Windows Mixed Reality 首頁啟動 SteamVR 的標題，而不需要移除其耳機。

## <a name="windows-mixed-reality-logo"></a>Windows Mixed Reality 標誌

若要顯示您標題的 Windows Mixed Reality 支援，請移至應用程式登陸頁面上的 [編輯存放區頁面] 連結，按一下 [基本資訊] 索引標籤，然後向下流覽至 [虛擬實境]。 取消核取 [隱藏 Windows Mixed Reality]，然後再發佈至存放區。

## <a name="bugs-and-feedback"></a>Bug 和意見反應

改善 Windows Mixed Reality SteamVR 體驗時，您的意見反應非常寶貴。 請透過[Windows 意見反應中樞](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/filing-feedback)提交所有意見反應和 bug。 以下是一些[如何讓您的 SteamVR 意見](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/using-steamvr-with-windows-mixed-reality#sharing-feedback-on-steamvr)反應盡可能發揮效用的秘訣。

如果您有想要分享的問題或意見，也可以在我們的串流[論壇](https://steamcommunity.com/app/719950/discussions/)上聯繫我們。

## <a name="faqs-and-troubleshooting"></a>常見問題和疑難排解

如果您在設定或播放體驗時遇到一般問題，請[查看最新的疑難排解步驟](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/troubleshooting-windows-mixed-reality#steamvr)。

## <a name="see-also"></a>請參閱
* [安裝工具](install-the-tools.md)
* [耳機和動作控制器驅動程式歷程記錄](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/mixed-reality-software)
* [Windows Mixed Reality 最低電腦硬體相容性指導方針](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines)

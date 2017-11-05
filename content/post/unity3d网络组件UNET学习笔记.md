---
title: unity3d网络组件UNET学习笔记
date: 2016-01-22 09:08:51
tags: [unity3d,networking,unet]
description: NetworkManager组件是为了管理联网游戏的网络状态。实际上它完全是用HLAPI来实现的，对开发者来说它只是用另一种形式来实现了联网的功能。不管怎样它尽量简洁的包含了很多有用的功能。
---
内容翻译自<http://docs.unity3d.com/Manual/UNetOverview.html>
# Using the NetworkManager

>The NetworkManager is a component for managing the network state of a multiplayer game. It is actually implemented entirely using the HLAPI, so everything it does is available to developers in other forms. However the NetworkManager wraps up a lot of useful functionality into a single place and makes creating, running and debugging multiplayer games as simple as possible.

NetworkManager组件是为了管理联网游戏的网络状态。实际上它完全是用HLAPI来实现的，对开发者来说它只是用另一种形式来实现了联网的功能。不管怎样它尽量简洁的包含了很多有用的功能。


>The NetworkManager can be used entirely without scripting. It has inspector controls in the editor that allow configuration of all of its features. The NetworkManagerHUD supplies a simple, default user interface at runtime that allows the network game to be controlled by the user. For advanced uses, developers can derive a class from NetworkManager and customize its behaviour by overriding any of the virtual function hooks that it provides.

NetworkManager完全不需要编写代码就可以使用。它可以在编辑器中设置所有的参数。NetworkManagerHUD提供了一个简单的界面，可以让用户管理网络游戏。开发者也可以继承NetworkManager类，重写它的虚方法来自定义自己的功能。


> The NetworkManager features include:

> Game State Management
Spawning Management
Scene Management
Debugging Information
Matchmaking
Customization

### NetworkManager包含以下功能

* 游戏状态管理
* 场景管理
* 调试信息
* 匹配功能
* 本地化

> Getting Started with NetworkManager

> The NetworkManager can be used as the core controlling component of a multiplayer game. To get started, create an empty game object in your starting scene, or pick a convenient manager object. Then add the NetworkManager component from the Network/NetworkManager menu item. The newly added NetworkManager component should look something like:

### 开始学习NetworkManager

在多人联网游戏中NetworkManager是一个核心的组件。开始，在场景创建一个空物体，在它上面添加一个NetworkManager组件。现在它应该是下面这个样子：

![NetworkManagerInspector](http://docs.unity3d.com/uploads/Main/NetworkManagerInspector.png)

> The inspector for the NetworkManager in the editor allows you to configure and control many things related to networking.

NetworkManager的编辑窗口可以配置很多网络参数。

The NetworkManagerHUD is another component that works with the NetworkManager. It gives you a simple user interface when the game is running to control the network state. This is good for getting started with a network project, but not intended to be used as the final UI for a game. The Network ManagerHUD looks like:

NetworkManagerHUD可以提供一个简单的界面去控制游戏的网络状态。这对于开始学习网络组件的用户非常友好，但不建议做为最终的界面。

![NetworkManagerRuntimeUI](http://docs.unity3d.com/uploads/Main/NetworkManagerRuntimeUI.png)

![NetworkManagerMMUI](http://docs.unity3d.com/uploads/Main/NetworkManagerMMUI.png)

Real games will have a proper user interface for controlling the game state and to allow players to choose what kind of game to play. But, to get started, we can use this to control the game.


Game State Management

A Networking multiplayer game can run in three modes - as a client, as a dedicated server, or as a “Host” which is both a client and a server at the same time. Networking is designed to make the same game code and assets work in all of these cases. Developing for the single player version of the game and the multiplayer version of the game should be the same thing.

NetworkManager has methods for entering each of these modes. NetworkManager.StartClient(), NetworkManager.StartServer() and NetworkManager.StartHost() are all available to script code, so they can be invoked from keyboard input handlers or from custom user interfaces. The default runtime controls that can optionally be displayed also invoke these same functions. There are also buttons in the NetworkManagerHUD inspector available when in play mode that call the same functions:


### 游戏状态管理

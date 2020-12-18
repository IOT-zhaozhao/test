# C++演讲比赛管理系统模板

#### 介绍

该项目提供了一个演讲比赛（或抽奖比赛）管理系统的demo，用于C++初学者进行学习。核心功能为设置演讲人数(抽奖人数)，通过系统抽签，选出冠亚季军（或中奖的前三人），提供菜单界面，交互性良好。

### 项目分析

**1、比赛规则：**
（1）学校举行一场演讲比赛，共12人参加，比赛分两轮，第一轮为淘汰赛，第二轮为决赛，
（2）每个选手都有对应的编号：如10001——10012
（3）比赛方式：分组比赛，每组6个人
（4）第一轮分为两个小组，整体按照选手编号进行抽签后顺序演讲
（5）十名评委分别给每名选手打分，去除最高分和最低分，求平均分为本能选手的成绩
（6）当小组演讲完毕后，淘汰组内排名最后的三个选手，前三名晋级，进入下一轮比赛，
（7）第二轮为决赛，前三名胜出，
（8）每轮比赛过后需要显示晋级选手的信息

2、程序功能
（1）开始演讲比赛：完成整届比赛的流程，每个比赛阶段需要给用户一个提示，用户按任意键后继续下一个阶段
（2）查看往届记录：查看之前比赛前三名结果，每次比赛都会记录到文件中，文件用.CSV后缀名保存
（3）清空比赛记录：将文件中数据清空
（4）退出比赛程序：可以退出当前程序

#### 软件架构

.h文件（抽象类）：

- Speaker.h -- 演讲人员类
- speechManager.h -- 演讲管理类声明文件

.cpp文件（实现类）：

- speechManager.cpp --演讲管理类的具体实现
- Source.cpp --main函数执行入口

Speaker.h 演讲人员类

该类仅有两个成员变量，姓名与第一二轮成绩

```c++
class Speaker {
public:
	string m_Name;
	double m_Score[2];
};
```

speechManager.h 演讲管理系统的主体文件解析

```c++
SpeechManager(); //构造函数
~SpeechManager();//析构函数
void exitSystem(); //离开系统函数
void showMenu();  //显示菜单
void startSpeech(); //开始演讲
void speakDraw(); //演讲比赛人员抽签，确认演讲顺序
void speechContest(); //开始演讲比赛
void showScore(); //展示第一轮晋级人员
void saveScore(); //保存文件：当前比赛胜利的人员记录
void loadScore(); //读取文件：展示以往的冠亚季军
void clearScore(); //清楚文件：清空记录
void initSpeaker(); //初始化演讲者
void createSpeaker(); //创建12名选手

//成员函数
//第一轮比赛选手
ector<int>v1;
//第一轮	晋级选手
vector<int>v2;
//胜出的前三名
vector<int>vVitory;
//存放编号与选手
map<int, Speaker> mSpeaker;
//save record award winner
map<int, vector<string>> mRecordWinner;
//轮数
int m_Index;
```

#### 安装教程

1.  安装visual studio 2019
2.  使用vs打开文件夹下的Project1.vcxproj文件

#### 使用说明

1.  执行Source.cpp启动程序

#### 参与贡献

1.  Fork 本仓库
2.  新建 Feat_xxx 分支
3.  提交代码
4.  新建 Pull Request


#### 特技

1.  使用 Readme\_XXX.md 来支持不同的语言，例如 Readme\_en.md, Readme\_zh.md
2.  Gitee 官方博客 [blog.gitee.com](https://blog.gitee.com)
3.  你可以 [https://gitee.com/explore](https://gitee.com/explore) 这个地址来了解 Gitee 上的优秀开源项目
4.  [GVP](https://gitee.com/gvp) 全称是 Gitee 最有价值开源项目，是综合评定出的优秀开源项目
5.  Gitee 官方提供的使用手册 [https://gitee.com/help](https://gitee.com/help)
6.  Gitee 封面人物是一档用来展示 Gitee 会员风采的栏目 [https://gitee.com/gitee-stars/](https://gitee.com/gitee-stars/)
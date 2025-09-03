<h1 align="center">Hi 👋, I'm ZiZhen Zhao</h1>
<h3 align="center">A passionate developer and student from China</h3>

<p align="left"> <img src="https://komarev.com/ghpvc/?username=a1821216780" alt="a1821216780" /> </p>

- 🔭 I’m currently a student in Nanjing University of Aeronautics and Astronautics.
  
- 🌱 I’m currently learning Wind turbine dynamics simulation and modeling, Nonlinear structural dynamics analysis and design of long flexible blades.

- 👨‍💻 All of my projects are available at [http://www.openwecd.fun](http://www.openwecd.fun)

- 💬 Ask me about **everything**

- 📫 How to reach me **1821216780@nuaa.edu.cn**, 微信: stkmpc520

- [![My Skills](https://skillicons.dev/icons?i=py,git,github,c,cpp,anaconda,go,md,matlab,pycharm,vscode,windows,vim)](https://skillicons.dev)

- 🥐: The software HawtC2 for wind turbine simulation!

#### 01.1 HawtC2 功能与模块对比

|        Bladed模块        |    OpenFAST对应模块    |              HawtC对应模块              |                      HawtC完成进度与支持情况                      |               HawtC模型               |
| :----------------------: | :--------------------: | :--------------------------------------: | :---------------------------------------------------------------: | :-----------------------------------: |
|      Modal Analysis      | Bmodes(非OpenFAST模块) |                  BeamL                  |                       ✅基本实现，还在开发                       |          ✅CR/✅TK/⚠️GEBT          |
|     Wind Turbulence     |        TurbSim        |              WindL.SimWind              |                              ✅完成                              |          谐波叠加、风谱模型          |
|  Earthquake Generation  |       Earthquake       |                 SubFEML                 |                         ❌ 已规划，未开发                         |              线性有限元              |
|        Sea State        |   Sea State(V4.0.0)   |               HydroL.WaveL               |                              ✅完成                              |             JS/PM 谱模型             |
|        水动力模块        |        HydroDyn        |                 HyderoL                 |                        ⚠️只支持Spar平台                        | ❌势流理论（计划开发）、✅Morison方程 |
| Aerodynamic Information |        AeroDyn        |               AeroL/BeamL               |                              ✅完成                              |       BEMT/FVM 以及动态失速Oye       |
| Performance Coefficients | AeroDyn(不支持柔性Cp) |               AeroL/BeamL               |              ✅完成,❌ 柔性Cp未开发，可以使用MBD平替              |                   -                   |
|    Steady Power Curve    |        AeroDyn        |                 TurbineL                 |                              ✅完成                              |                   -                   |
| Steady Operational Loads |        AeroDyn        |                 TurbineL                 |                              ✅完成                              |                   -                   |
|   Steady Parked Loads   |        AeroDyn        |                 TurbineL                 |                              ✅完成                              |              浮动坐标法              |
|   Model Linearisation   |       FAST主模块       |              MSAL/TurbineL              |                      ⚠️ 正在开发当中。。。                      |                   -                   |
|  Electrical performance  |           -           |                    -                    |                             ❌ 不支持                             |                   -                   |
| Power Production Loading |   BeamDyn/ElastoDyn   | AeroL/MBD /ControL /HydroL/SubFEML/BeamL |                              ✅完成                              |               耦合模型               |
|       Normal Stop       |           -           | AeroL/MBD /ControL /HydroL/SubFEML/BeamL |          ⚠️ 可以模拟，但是没有直接提供功能选择，开发中          |               耦合模型               |
|      Emergency Stop      |           -           | AeroL/MBD//ControL /HydroL/SubFEML/BeamL |             ❌ 错误控制模块位于ControL当中，尚未开发             |               耦合模型               |
|          Idling          |   BeamDyn/ElastoDyn   |             AeroL/MBD /BeamL             |                              ✅完成                              |               耦合模型               |
|          Parked          |   BeamDyn/ElastoDyn   |     AeroL/MBD /HydroL/SubFEML/BeamL     |                              ✅完成                              |               耦合模型               |
|      Hardware Test      |           -           |                    -                    |                             ❌ 不支持                             |                   -                   |
|     Post Processing     |           -           |                  PostL                  | ✅ 部分支持（年发电量、疲劳载荷，极限载荷，雨流计数以完全支持！） |      S-N疲劳损伤理论、雨流计数法      |
|        Bladed API        |       pyOpenFAST       |                   APIL                   |                     外部应用接口，独有且便捷                     |                   -                   |
|          Batch          |       ❌ 不支持       |                  Batch                  |        ⚠️ 支持大部分工况的批次处理和运行，但代码尚未完善        |                   -                   |

#### 01.2  HawtC2 独有功能

| Bladed模块 |              OpenFAST模块              |         HawtC对应模块         |                 功能                 |                原理与模型                |
| :---------: | :-------------------------------------: | :---------------------------: | :----------------------------------: | :--------------------------------------: |
|  ❌不支持  |          IVABS(非OpenFAST模块)          |            ✅ PCSL            |       梁截面参数计算工具，独有       |                   FEM                   |
|  ❌不支持  |                ❌不支持                |           ✅ MoptL           |     多目标并行优化算法程序，独有     |   NSGA2/GDE3/MCell(改进的多线程c#实现)   |
|  ❌不支持  |                ❌不支持                |         ✅ APIL/MoptL         |      整机全参数一体化优化，独有      |                 耦合模型                 |
|  ❌不支持  |                ❌不支持                |         ✅ WTAI/MoptL         | 数据驱动与实时数据驱动代理模块，独有 |    Python、C++接口以及内置BP神经网络    |
|  ❌不支持  |               ✅ VTK支持               |            ✅ VTKL            |        数据显示与动画输出模块        |                    -                    |
| ❌只支持TMD | ⚠️只支持TMD(支持基础/塔架/叶片等结构) | ✅ TMD/TMDI(独有叶片)/陀螺仪 |     TMD/TMDI/陀螺仪下的减振计算     | MBD/FEM 多体动力学-有限元耦合模型的耦合 |

<p><img align="center" src="https://github-readme-stats.vercel.app/api?username=a1821216780&show_icons=true" alt="a1821216780" /></p>

<img  align="center"  src="https://github-readme-stats.anuraghazra1.vercel.app/api/top-langs/?username=a1821216780&theme=dark&hide_border=false&no-bg=true&no-frame=true&langs_count=10"/>

<p><a href="https://git.io/streak-stats"><img src="https://github-readme-streak-stats.herokuapp.com?user=a1821216780&theme=neon-dark" alt="GitHub Streak" /></a></p>


# 员工考勤管理系统

## 项目介绍
本项目是一个基于 **Spring Boot + Vue 3** 的员工考勤与信息管理系统，支持员工打卡、考勤统计、绩
效分数自动计算、数据导出、个人中心等功能。系统界面美观，操作简便，适合中小型企业日常考勤与人事管
理。

## 功能特点
- 员工打卡管理
  - 上班打卡
  - 下班打卡
  - 自动记录打卡时间
- 考勤状态管理
  - 正常出勤
  - 迟到
  - 早退
  - 缺勤
  - 请假
- 绩效评分系统
  - 基于考勤记录自动计算绩效分数
  - 迟到/早退扣2分
  - 缺勤扣5分
  - 请假扣1分
- 考勤统计
  - 个人考勤记录查询
  - 部门考勤统计
  - 月度考勤报表
- 考勤异常提醒
  - 自动统计考勤异常记录
  - 展示考勤不良员工列表

## 技术栈
### 后端
- Spring Boot 3.x
- MyBatis
- MySQL
- Maven

### 前端
- Vue.js
- Element UI
- Axios
- Vue Router

## 系统界面预览

- **首页仪表盘**：统计员工总数、部门数、男女比例、各部门人数分布、最新入职员工、公告等，支持数据可视化（条形图、饼图）。
- **部门管理**：支持部门的新增、编辑、删除，显示部门及最后操作时间。
- **员工管理**：支持员工信息的增删改查，字段包括工号、姓名、性别、手机号、部门、职位、薪资、入职时间、头像、最后操作时间等。
- **考勤管理**：支持上班/下班打卡，日历视图展示每日考勤状态，统计出勤、迟到、早退、缺卡、请假等，考勤日历采用可视化图表。
- **考勤报表**：按月统计考勤明细和绩效分数，支持一键导出Excel。
- **个人中心**：查看和修改个人信息、密码，支持请假申请。

### 后端部署
1. 环境要求
   - JDK 17+
   - Maven 3.6+
   - MySQL 8.0+

2. 数据库配置
   - 创建数据库：kaoqin
   - 修改`application.yml`中的数据库连接信息
- **员工考勤打卡**：上班签到、下班签退，自动记录考勤状态（正常、迟到、早退、缺卡、请假）。
- **绩效分数自动生成**：根据考勤状态自动计算绩效分数，明细和报表均可查看。
- **考勤数据统计与导出**：按月统计个人考勤，支持Excel导出，包含日期、签到/签退时间、状态、绩效分
数等。
- **员工与部门管理**：支持员工、部门的增删改查，信息一目了然。
- **个人中心与请假申请**：员工可查看个人信息、申请请假。
- **JWT登录认证**：安全的登录机制，所有接口需携带token访问。
- **权限控制**：区分普通员工和管理员（可扩展）。
- **数据可视化**：首页和考勤管理等页面集成了条形图、饼图、日历图等可视化组件，直观展示统计数据。

---

## 技术选型

- **前端**：Vue 3、Element Plus、Axios、ECharts（数据可视化）
- **后端**：Spring Boot、MyBatis、MySQL、JWT、POI（Excel导出）
- **数据库**：MySQL
- **工具/依赖**：Maven、Lombok、Jakarta Servlet

---

## 目录结构

```
项目根目录
├── kaoqin/                                   # 后端项目根目录
│   ├── src/                                 # 源代码目录
│   │   ├── main/
│   │   │   ├── java/org/xynu/kaoqin/       # Java源代码
│   │   │   │   ├── controller/             # 控制器层
│   │   │   │   ├── service/                # 服务层
│   │   │   │   ├── mapper/                 # MyBatis映射层
│   │   │   │   ├── entity/                 # 实体类
│   │   │   │   └── util/                   # 工具类
│   │   │   └── resources/
│   │   │       ├── mapper/                 # MyBatis XML映射文件
│   │   │       ├── static/                 # 静态资源
│   │   │       └── application.yml         # 配置文件
│   │   └── test/                           # 测试代码
│   ├── pom.xml                             # Maven配置
│   ├── mvnw                                # Maven Wrapper脚本
│   ├── mvnw.cmd                            # Maven Wrapper脚本(Windows)
│   └── .mvn/                               # Maven Wrapper配置
│
└── test_vue/                               # 前端项目根目录
    ├── src/                                # 源代码目录
    │   ├── api/                           # API接口
    │   ├── assets/                        # 静态资源
    │   ├── components/                    # 组件
    │   ├── router/                        # 路由配置
    │   ├── store/                         # 状态管理
    │   ├── utils/                         # 工具函数
    │   ├── App.vue                        # 根组件
    │   └── main.js                        # 入口文件
    ├── public/                            # 公共资源
    ├── dist/                              # 构建输出目录
    ├── node_modules/                      # 依赖包
    ├── package.json                       # 项目配置
    ├── package-lock.json                  # 依赖版本锁定
    ├── vue.config.js                      # Vue配置
    ├── babel.config.js                    # Babel配置
    ├── jsconfig.json                      # JavaScript配置
    └── .gitignore                         # Git忽略配置
```

## 部署与运行

### 1. 数据库准备

- 创建MySQL数据库（如`kaoqin`），导入表结构和初始数据。
- 主要表：`emp`（员工）、`attendance`（考勤）、`emp_expr`（工作经历）等。

### 2. 后端启动

1. 配置`application.yml`中的数据库连接信息。
2. 使用IDEA或命令行运行Spring Boot主类（如`KaoqinApplication.java`）。
3. 后端服务默认端口：`8080`。

### 3. 前端启动

1. 进入`test_vue`目录，安装依赖：
   ```bash
   npm install
   ```
2. 启动前端开发服务器：
   ```bash
   npm run dev
   ```
3. 前端默认端口：`5173`（或见项目配置）。

---

## 典型代码说明

### 1. 后端考勤导出（含绩效分数）

`AttendanceController.java` 片段：

```java
// 表头
header.createCell(0).setCellValue("日期");
header.createCell(1).setCellValue("签到时间");
header.createCell(2).setCellValue("签退时间");
header.createCell(3).setCellValue("状态");
header.createCell(4).setCellValue("绩效分数");
// 数据
for (Attendance a : list) {
    // ... 其它字段
    row.createCell(4).setCellValue(a.getPerformanceScore() == null ? "" : a.getPerformanceScore().toString());
}
```

## 使用说明
1. 员工打卡
   - 上班时间：9:00前打卡
   - 下班时间：18:00后打卡
   - 超过上班时间打卡记为迟到
   - 提前下班打卡记为早退

2. 绩效分数
   - 初始分数：100分
   - 迟到/早退：-2分
   - 缺勤：-5分
   - 请假：-1分
   - 分数低于60分将被标记为考勤异常

3. 考勤统计
   - 可查看个人历史考勤记录
   - 支持按月份筛选
   - 显示考勤状态分布统计

## 注意事项
1. 系统会自动在每天23:59检查未打卡记录，并标记为缺勤
2. 绩效分数会基于历史记录连续计算，不会重置
3. 请确保网络连接正常，以免影响打卡记录

## 开发团队
- 开发者：[cdzjzxyz]
- 联系方式：[1097187899@qq.com]

## 版本历史
- v1.0.0 (2024-05-19)
  - 实现基础考勤功能
  - 完成绩效评分系统
  - 添加考勤统计功能

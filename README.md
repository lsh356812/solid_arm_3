# [2022-1] Robot Control 실습


#### Gazebo Simulation for RoK-3.
본 패키지는 휴머노이드 로봇 RoK-3의 교육용 Gazebo Simulation 입니다.
이 문서는 패키지의 설명 문서이며, 구성은 다음과 같습니다.

* What to do before simulation

* Simulation Manual
  1. [Download](https://github.com/swan0421/RobotControl2022) and Setting RobotControl2022
  2. Libraries used in RobotControl2022 Package
  3. How to run RobotControl2022 package, **Please read section 2 before proceeding.**
----

## What to do before simulation 
1. [RoS-Kinetic](http://wiki.ros.org/kinetic/Installation/Ubuntu) install, link : http://wiki.ros.org/kinetic/Installation/Ubuntu
2. [Gazeobo-7](http://gazebosim.org/tutorials?cat=install&tut=install_ubuntu&ver=7.0) install, link : http://gazebosim.org/tutorials?cat=install&tut=install_ubuntu&ver=7.0
3. [Netbeans-IDE](https://netbeans.apache.org/download/index.html) install, link : https://netbeans.apache.org/download/index.html

> **Java install before Netbeans install**
* terminal
> ```
> sudo apt update
> sudo apt install openjdk-8-jdk
> java -version
> ```
---
> **Netbeans-IDE install**
##### **1. 기존 NetBeans가 설치되어 있는경우**
###### *`(NetBeans가 설치되어 있지 않다면 2번으로 이동)`*
* terminal
> ```js
> cd /usr/local/netbeans-x.x
> //기존 netbeans의 uninstall.sh가 있는 폴더로 이동. (x.x는 현재버전)
> //경로가 다를 수 있으니 확인할 것
>
> sudo sh uninstall.sh
> //uninstall 실행

##### **2. Apache NetBeans 13 IDE install Guide**

1. [NetBeans 13_linux install](https://www.apache.org/dyn/closer.cgi/netbeans/netbeans-installers/13/Apache-NetBeans-13-bin-linux-x64.sh) 링크로 접속 합니다.

2. HTTP 하단의 링크를 클릭하여 .sh 파일을 다운로드 받습니다.  
.sh 파일의 다운로드 경로는 `/home/user_name/Downloads` 로 설정합니다.  
*`(만약 다운로드가 되지 않는다면, 링크를 복사하여 **wget -c** 명령어로 직접 실행)`*  
* terminal
>```
>---example---
>wget -c https://dlcdn.apache.org/...linux-x64.sh
>```
3. 다운로드된 파일에 실행권한을 부여하고, 실행합니다.
* terminal
>```
>chmod +x Apache-NetBeans-13-bin-linux-x64.sh
>
>./Apache-NetBeans-13-bin-linux-x64.sh
>```  
##### **3.Apache NetBeans 13 Setting**
1. 설치된 applications 에서 Apache NetBeans IDE 13을 실행합니다.  

2. 상단 Menu의 Tools 항목 중 **Plugins**를 클릭합니다.

3. Plugins창이 뜨면, Settings 카테고리로 들어가서, **NetBeans 8.2 Plugin Portal 의 Active**에 체크한 후, **Available Plugins** 카테고리로 들어가 **check for Newest** 를 클릭하여 업데이트를 진행해 줍니다.

4. 업데이트를 진행 후 나타나는 c/c++ 에 install 을 체크하고 하단의 install 버튼을 클릭하여 설치를 진행합니다.  

##### **4. Create New Project**
1. 상단 Menu의 File 항목에서 New Project를 선택합니다.

2. Choose Project Step  
categories : **C/C++**  
Projects : **C/C++ Project with Existing Sources**  
<img width="700" src="./NetBeans 13 Setting Guide/choose project.png" alt="Choose Project">  
     
`next`

3. Select Mode Step  
specify the folder : **/home/user_name/catkin_ws**  
**`(user_name 의 경우 Ubuntu 설치 시 사용자가 설정한 이름을 입력합니다.)`**  
Build Host : **localhost**  
Tool Collection : **Default(GNU(GNU))**  
Use Build Analyzer **Check**  
Configuration Mode : **Custom**  
<img width="700" src="./NetBeans 13 Setting Guide/Select Mode.png" alt="Select Mode">  
    
`next`

4. Pre-Build Action Step  
**Pre-Build Step is Required uncheck**  
<img width="700" src="./NetBeans 13 Setting Guide/Pre-Build Action.png" alt="Pre-Build Action">  
    
`next`

5. Build Actions Step  
Working Directory : **/home/user_name/catkin_ws**  
Clean Command : **devel/env.sh catkin_make clean**  
Build Command : **devel/env.sh catkin_make**  
Clean and Build after Finish **check**  
<img width="700" src="./NetBeans 13 Setting Guide/Build Actions.png" alt="Build Actions">  
    
`next`

6. Source Files Step  
Source FIle Folders : **/home/user_name/catkin_ws**  
<img width="700" src="./NetBeans 13 Setting Guide/Source Files.png" alt="Source Files">  
    
`next`

7. Code Assistance Configuration Step  
Automatic Configuration **check**  
<img width="700" src="./NetBeans 13 Setting Guide/Code Assistance Configuration.png" alt="Code Assistance Configuration">  
    
`next`

8. Project Name and Location Step  
Project Name : **catkin_ws**  
Project Location : **/home/user_name/NetBeansProjects**  
Project Folder : **/home/user_name/NetBeansProjects/catkin_ws**  
Build Host : **localhost**  
Tool Collection : **Default(GNU(GNU))**  
<img width="700" src="./NetBeans 13 Setting Guide/Project Name and Location.png" alt="Project Name and Location">  
    
`하단의 빨간색 경고는 이미 해당 폴더가 이미 만들어져 있다는 경고이므로, 처음 세팅할 경우에는 등장하지 않습니다.`  
`finish`

----


4. [GitHub](https://github.com/)에 미리 가입한 상태면, 해당 패키지를 공동 작업하는데 있어 도움이됩니다.  
따라서, 가입을 희망합니다. 또한, `Token password`를 발급받기 바랍니다.  
[토큰 발급 방법](https://hoohaha.tistory.com/37) 을 참고하시기 바랍니다.  
*`토큰은 생성 이후에 다시 확인할 수 없으니, 따로 저장해두어야 합니다.`*


----
## Simulation Manual 
### 1.[Download](https://github.com/swan0421/RobotControl2022) and Setting RobotControl2022
1. [RobotControl2022 Repository](https://github.com/swan0421/RobotControl2022)에 접속, link : https://github.com/swan0421/RobotControl2022

2. 해당 Repository에 접속 후, 우측 상단의 Fork를 클릭하여, 본인의 Github Repository에 복제되었는지 확인합니다.  
(`swan0421/Robotcontrol2022` -> `User_id/Robotcontrol2022`)
```
Fork란?  

다른 사람의 Github Repository 에서 내가 수정하거나 기능을 추가하고자 할 때,  
해당 Repository를 내 Github Repository로 그대로 복제하는 기능이다.

Fork한 Repository는 원본 Repository와 연결되어 있어,  
원본 Repository에 변화가 생기면, Fork한 Repository에 반영할 수 있다.
```

3. 복제된 본인의 Repository에 접속 후에, `Code ▼`라는 초록색 버튼이 있는데 클릭하여 URL 주소 (https:/~)을 복사하거나,`Download ZIP` 을 통해 해당 패키지를 다운 받습니다.

4. NetBeans의 `Team` > `Git` > `clone` 을 누른후, `Repository URL`을 https://github.com/User_id/RobotControl2022.git 으로 설정합니다.  
`(본인의 Repository 경로)`  
(만약, NetBeans에서 `Team` > `Git` > `clone` 경로가 보이지 않는 경우, NetBeans 화면 좌측에 있는 Projects 패널에서 catkin_ws 를 클릭하면 보이며, 위의 경로는 git에 연동되었을 때 활성화되는 경로이므로 처음 연동하는 것이라면, Team > git > clone으로 해도 됨)  
User에는 GitHUB의 user_name을 쓰고, Password에는 GitHUB의 `Token password`를 입력한 후 NEXT를 누릅니다.

5. Select Remote Branches를 `master*` 로 선택하고 Next를 누릅니다.

6. Parent Directory를 사용자의 `home/user_name/catkin_ws/src` 경로로 설정하고, Clone name을 사용자가 원하는 이름으로 설정하고, (참고 : Clone Name은 패키지에 관련된 이름으로 써서 다른 폴더들과 구별 지을 것) Checkout Branch는 `master*` 로 설정하고, Remote Name은 origin으로 설정한 후 Finish를 누릅니다.

7. 사용자의 catkin_ws/src 위치에 Step5에서 설정한 Clone Name 을 갖는 폴더가 있는지 확인하고, 폴더 내부에 패키지 구성 파일들(world 폴더, src 폴더, launch 폴더 등)과 model 폴더(=`rok3_model`)이 있는지 확인합니다.

8. `rok3_model` 폴더를 `HOME/.gazebo/models/` 폴더로 가져와서 시뮬레이션을 위한 파일 셋팅을 마무리합니다.  
***(`.gazebo` 폴더가 보이지 않으면, `Ctrl+H` 를 눌러서 폴더 숨김 해제를 할 것)***
         
9. 패키지를 컴파일하기 위해 Netbeans에서 터미널 창을 열거나 기본 터미널 창에서 `catkin_make`을 입력하여 컴파일을 진행합니다. 
***(터미널 창이 안보인다면, Netbeans의 상단 `Winodow > IDE Tools > Termianl` 을 클릭)***

10. 만약, `catkin_make`가 안될 경우, section 2를 해보시기 바랍니다.
----


### 2.Libraries used in RobotControl2022 Package

| Library | Description |
| ------ | ----------- |
| [Eigen](https://eigen.tuxfamily.org/index.php?title=Main_Page)   | Eigen is a C++ template library for linear algebra: matrices, vectors, numerical solvers, and related algorithms.|
| [RBDL](https://rbdl.github.io/) | RBDL library contains highly efficient code for both forward and inverse dynamics for kinematic chains and branched models. |

**Recommended to re-install RBDL**

RBDL의 재설치를 권장합니다. 사용자마다 `root` 계정 혹은 `user` 계정으로 하기 때문에, Build 하는 과정에서 문제가 발생할 수 있습니다. 따라서, 다음과 같이 재설치를 해주시기 바랍니다. 본 패키지를 `root` 계정에서 사용할 경우, 재설치가 필요없을 수 있습니다.

**RBDL Build**

1. `RobotControl2022/src/RBDL/addons/urdfreader` 폴더 내에 있는 `CMakeList.txt` 파일에 `include_directories`를 다음과 같이 추가해줍니다.
* Before : 
``` js
IF (DEFINED ENV{ROS_ROOT})
	MESSAGE (STATUS "ROS found: $ENV{ROS_ROOT}")
	find_package(catkin REQUIRED COMPONENTS urdf)
```
* After :
``` js
IF (DEFINED ENV{ROS_ROOT})
	MESSAGE (STATUS "ROS found: $ENV{ROS_ROOT}")
	find_package(catkin REQUIRED COMPONENTS urdf)
	include_directories(include ${catkin_INCLUDE_DIRS})
```

2. RBDL make & install (**build 폴더가 존재할 경우, 삭제**)
RBDL 폴더에서 터미널 창을 켜고 아래의 명령어를 입력함으로써, RBDL 재설치를 끝냅니다.
``` js
mkdir build 
cd build/ 
cmake -D CMAKE_BUILD_TYPE=Release ../
cmake -D RBDL_BUILD_ADDON_URDFREADER=true ../
make 
sudo make install
```
3. 그리고 다시 패키지를 컴파일하기 위해 Netbeans에서 터미널 창을 열거나 기본 터미널 창에서 `catkin_make`을 입력하여 컴파일을 진행합니다.
----

### 3.How to run RobotControl2022 package
#### **!! 시뮬레이션 실행 전에 확인 해야하거나 셋팅 !!**

* #### Setting for Fixed / Floating Dynamics

`HOME/.gazebo/models/rok3_model`폴더에 있는 `model.sdf`를 엽니다. 그리고 Fixed / Floating Dynamics을 위해 `<fixed to world>`의 joint를 다음과 같이 셋팅 합니다.

**Setting Floating Dynamics in `model.sdf`**
``` js
<?xml version="1.0"?>
<sdf version='1.6'>
  <model name='rok3_model'>
  <!--joint name="fixed to world" type="fixed">
      <parent>world</parent>
      <child>base_link</child>
    </joint-->
.
.
.
  </model>
</sdf>
```


**Setting Fixed Dynamics in `model.sdf`**
``` js
<?xml version="1.0"?>
<sdf version='1.6'>
  <model name='rok3_model'>
  <joint name="fixed to world" type="fixed">
      <parent>world</parent>
      <child>base_link</child>
    </joint>
.
.
.
  </model>
</sdf>
```

다음으로, `catkin_ws/src/RobotControl2022/worlds`폴더에 있는 `rok3.world`를 엽니다. 그리고 Fixed / Floating Dynamics을 위해 모델의 `<pose frame>`을 다음과 같이 셋팅 합니다.

**Setting Floating Dynamics in `rok3.world`**
``` js
<?xml version="1.0" ?>
<sdf version="1.6">
  <world name="rok3">
.
.
.
    <include>
      <uri>model://rok3_model</uri>
      <pose frame=''>0 0 0.947 0 0 0</pose>
      <plugin name="rok3_plugin" filename="librok3_pkgs.so"/> 
    </include>
  </world>
</sdf>
```


**Setting Fixed Dynamics in `rok3.world`**
``` js
<?xml version="1.0" ?>
<sdf version="1.6">
  <world name="rok3">
.
.
.
    <include>
      <uri>model://rok3_model</uri>
      <pose frame=''>0 0 1.947 0 0 0</pose>
      <plugin name="rok3_plugin" filename="librok3_pkgs.so"/> 
    </include>
  </world>
</sdf>
```


* #### Check `model.urdf` file path for using RBDL in `rok3_plugin.cc`
* `rok3_plugin.cc`는 Gazebo main code 이며, `/catkin_ws/src/RobotControl2022/src`에 있습니다.
* **그리고, `rok3_plugin.cc`에서 사용자는 반드시 `Load(physics::ModelPtr _model, sdf::ElementPtr /*_sdf*/)`함수에서, 아래 코드 예시와 같이 `Addons::URDFReadFromFile()` 함수 안에 적용되어 있는 `rok3_model.urdf`의 경로를 확인해주시고, 틀린다면 바로잡아주시기 바랍니다.**

* **`rok3_model.urdf`는 `home/.gazebo/models/rok3_model/urdf` 폴더에 있으며, 파일 속성 확인을 통해 정확한 경로 확인하시기 바랍니다.**

**In `rok3_plugin.cc`**
``` js
void gazebo::rok3_plugin::Load(physics::ModelPtr _model, sdf::ElementPtr /*_sdf*/)
{
    /*
     * Loading model data and initializing the system before simulation 
     */

    //* model.sdf file based model data input to [physics::ModelPtr model] for gazebo simulation
    model = _model;

    //* [physics::ModelPtr model] based model update
    GetJoints();



    //* RBDL API Version Check
    int version_test;
    version_test = rbdl_get_api_version();
    printf(C_GREEN "RBDL API version = %d\n" C_RESET, version_test);

    //* model.urdf file based model data input to [Model* rok3_model] for using RBDL
    Model* rok3_model = new Model();
    Addons::URDFReadFromFile("/root/.gazebo/models/rok3_model/urdf/rok3_model.urdf", rok3_model, true, true);
    //↑↑↑ Check File Path ↑↑↑
    nDoF = rok3_model->dof_count - 6; // Get degrees of freedom, except position and orientation of the robot
    joint = new ROBO_JOINT[nDoF]; // Generation joint variables struct

    //* initialize and setting for robot control in gazebo simulation
    SetJointPIDgain();


    //* setting for getting dt
    last_update_time = model->GetWorld()->GetSimTime();
    update_connection = event::Events::ConnectWorldUpdateBegin(boost::bind(&rok3_plugin::UpdateAlgorithm, this));

}
```

**모든 준비 과정이 끝나면, `catkin_make`을 입력하여 컴파일을 진행합니다.**

```
catkin_make
```
**최종적으로, 다음과 같은 명령어를 통해 시뮬레이션 실행**

```
roslaunch rok3_study_pkgs rok3.launch
```

## 1. 실습 1 : 3-Link Planar Arm의 Forward Kinematics

* void Practice() 함수 만들기
```c
void Practice()
```
* Practice() 함수안에 matrix 생성 및 터미널창에 인쇄하기
* cout 사용
~~~c
std::cout << "C_IE = " << C_IE << std::endl;
~~~
* Load 함수 첫줄에 Practice() 함수 사용
* 3-link planar arm를 위한 Homogeneous Transformation Matrix 만들기
* 모든 링크의 길이는 1m로 가정
~~~c
MatrixXd getTransformI0()
MatrixXd jointToTransform01(VectorXd q)
MatrixXd jointToTransform12(VectorXd q)
MatrixXd jointToTransform23(VectorXd q)
MatrixXd getTransform3E()
~~~
* Forward Kinematics 만들기
~~~c
VectorXd jointToPosition(VectorXd q)
MatrixXd jointToRotMat(VectorXd q)
VectorXd rotToEuler(MatrixXd rotMat)
~~~

## 2. 실습 2 : RoK-3의 Forward Kinematics  

<img width="700" src="./RoK-3_img/RoK-3 Frame.jpg" alt="rok-3 frame">  
    
* Homogeneous Transformation Matrix 만들기
~~~c
MatrixXd getTransformI0()
MatrixXd jointToTransform01(VectorXd q)
MatrixXd jointToTransform12(VectorXd q)
MatrixXd jointToTransform23(VectorXd q)
MatrixXd jointToTransform34(VectorXd q)
MatrixXd jointToTransform45(VectorXd q)
MatrixXd jointToTransform56(VectorXd q)
MatrixXd getTransform6E()
~~~
* Forward Kinematics 만들기
~~~c
VectorXd jointToPosition(VectorXd q)
MatrixXd jointToRotMat(VectorXd q)
VectorXd rotToEuler(MatrixXd rotMat)
~~~
* q=[10;20;30;40;50;60] 일때, End-effector의 position과 Rotation Matrix 구하기
* 이때, Euler Angle 구하기

### 제출자료
1. source 코드
2. 출력된 결과물 capture 파일


# solid_arm_3

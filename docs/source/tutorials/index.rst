ROS 基本範例
===============================
此章節會說明ROS下節點(Node)間的溝通方式,而溝通方式可分為Topic, Message, Service, Action.

而在說明如何透過程式來建立這些溝通方式前,要先如何建立ROS的Package.

.. _create_package:

Create Package
---------------------------

ROS Package類似於程式專案,程式檔案及相關設定都會在這底下,例如函式庫相依、函式目錄路徑、編譯設定.

這提供兩種方式建立專案,一是透過ROS原本所自帶的 ``catkin_create_pkg`` 工具,二是透過VSCode的插件-``VSCode-ROS``

.. _catkin_create_pkg:

catkin_create_pkg
---------------------------
常用方式如下::
  
  $ catkin_create_pkg Package名稱 依賴專案1 依賴專案2

那假設想建立一個Package名為demo_topic,並依賴roscpp和std_msgs,指令如下::

  $ catkin_create_pkg demo_topic roscpp std_msgs

.. note::
  所以依照上面的例子的話,demo_topic為Package名稱,roscpp和std_msgs則是相依函式庫,另外注意Package必須為英文

.. _VSCode_ROS:

VSCode-ROS
---------------------
第一次使用VSCode開啟workspace的資料夾時,ROS插件會詢問是否設定ROS的distro,如果已安裝好kinetic版本,在選項裡就kinetic可以選擇.

選擇好後按下 ``Ctrl`` + ``p`` 會跳出命令欄,選擇選項裡的 ``ROS: Create Catkin Package`` , 首先輸入Package Name，上一段的例子來說就是 ``demo_topic`` , 再來則輸入依賴專案就是 ``roscpp std_msgs``

基本範例
----------------------------
.. toctree::
		:maxdepth: 1

		topicexample











 

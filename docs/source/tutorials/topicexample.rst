.. _class_Topic:
	
Topic
===================
Topic為在ROS裡Node之間溝通最基礎的方式,Topic的組成分為訊息的型態和地址,而只要知道Topic的型態和地址,任何Node都可以對此Topic進行發送或接收訊息。而從Topic接收訊息的一方稱為Subsriber(聆聽者),相反的發送訊息至Topic的一方稱為Publisher(發佈者).

而在這節將舉例一個Publisher,一個Subscriber透過一個Topic進行溝通

首先透過 :ref:`Create package <create_package>` 建立一個Package叫demo_topic，並相依 ``roscpp`` 、 ``std_msgs``。
``roscpp`` 為ROS提供的C++函式庫，而 ``std_msgs`` 為ROS提供的基本訊息型態。

Topic Publisher 範例程式
-----------------------------

    #include <ros/ros.h>
    #include "std_msgs/Int32.h"
    #include <iostream>

    int main(int argc, char **argv)
    {
        ros::init(argc, argv, "topic_publisher");
        ros::NodeHandle nh;
        ros::Publisher number_publisher = nh.advertise<std_msgs::Int32>("/number", 10);

        ros::Rate loop_rate(10);

        int number_count = 0;
        while (ros::ok()) {
            std_msgs::Int32 int32_msg;

            int32_msg.data = number_count;

            ROS_INFO("%d", int32_msg.data);//print data of int32_msg to screen

            number_publisher.publish(int32_msg);//publish int32_msg to topic (/number)

            ros::spinOnce();
            loop_rate.sleep();

            ++number_count;
        }

        return 0;
    }



